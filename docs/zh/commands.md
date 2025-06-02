# elinKernel 命令参考

> **🚧 翻译进行中** - 本文档正在翻译中，详细内容请参考 [英文完整版](../en/commands.md)。

本指南介绍 elinKernel 交互式命令行中的所有可用命令。

## 概述

elinKernel 启动后，您可以使用包含以下类别的交互式命令行：

- **系统信息** - 检查系统状态和配置
- **嵌入式文件系统操作** - 管理文件和测试 ext4 实现
- **ELF 操作** - 加载和分析 ELF 二进制文件
- **系统控制** - 关机、重启和清屏

## 系统信息命令

### `help`
显示可用命令及其说明。

```
elinKernel> help
```

### `version`
显示 elinKernel 版本信息。

```
elinKernel> version
```

### `memory`
显示通过 `SYS_GETMEMINFO` 检测到的内存区域。

```
elinKernel> memory
```

### `ext4check`
检查嵌入式 ext4 文件系统状态和超级块信息。

```
elinKernel> ext4check
```

**示例输出**：
```
EXT4 Filesystem Check
====================

✅ EXT4 filesystem is active and healthy!

📊 Superblock Information:
   Magic: 0xef53 ✅
   Inodes: 65536
   Blocks: 65536
   Block size: 4096 bytes
   Volume: elinKernel
```

### `disktest`
测试文件系统操作，包括初始化、文件列表和读取。

```
elinKernel> disktest
```

### `diskdump [块号]`
显示文件系统块信息（教育用途）。

```
elinKernel> diskdump 0
```

### `syscall`
显示系统调用信息和架构。

```
elinKernel> syscall
```

## 嵌入式文件系统操作

### `ls`
使用 `SYS_GETDENTS` 列出所有文件及其大小。

```
elinKernel> ls
```

### `cat <文件名>`
使用 `SYS_OPEN` 显示文件内容。

```
elinKernel> cat hello.txt
```

### `touch <文件名>`
使用文件系统 + `SYS_OPEN` 创建新的空文件。

```
elinKernel> touch newfile.txt
```

### `rm <文件名>`
使用 `SYS_UNLINK` 删除文件。

```
elinKernel> rm oldfile.txt
```

## ELF 操作

### `elf-info <文件名>`
分析 ELF 二进制文件结构并显示详细信息。

```
elinKernel> elf-info hello.elf
```

### `elf-load <文件名>`
将 ELF 二进制文件加载到内存并显示入口点/段。

```
elinKernel> elf-load hello.elf
```

### `elf-exec <文件名>`
加载 ELF 二进制文件并准备执行（模拟）。

```
elinKernel> elf-exec hello.elf
```

### `elf-demo`
内置示例 ELF 头演示。

```
elinKernel> elf-demo
```

## 系统控制

### `shutdown`
使用 `SYS_ELINOS_SHUTDOWN` 优雅关闭 elinKernel 并退出 QEMU。

```
elinKernel> shutdown
```

### `reboot`
使用 `SYS_ELINOS_REBOOT` 重启系统。

```
elinKernel> reboot
```

### `clear`
使用 `SYS_WRITE` 清除屏幕。

```
elinKernel> clear
```

## 📖 完整文档

详细的命令说明、参数和示例，请参考英文完整版：

- [📖 英文完整版](../en/commands.md) - 包含所有命令的详细说明和示例

## 🤝 参与翻译

如果您愿意帮助完善此文档的中文翻译：

1. 参考英文版本的完整内容
2. 翻译命令说明和示例
3. 保持技术术语的准确性
4. 提交 Pull Request

---

> **提示**: 完整的命令参考和详细示例请参考英文文档。 