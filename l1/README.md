## 环境准备

- 只在 Mac 上实验过，其他系统请自行尝试。
- `NASM`	[汇编编译器](http://www.nasm.us/)
```sh
    brew install nasm
```

- `QEMU`	可调试的模拟器 (比 `bochs` 更容易使用)
```sh
    brew install qemu
```

- `GDB`	调试工具

## 启动

	make    编译并生成可用的软盘镜像  
	make boot	启动  

这个 `bootloader` 非常简单，没有任何可见的输出, 需要在调试环境来查看寄存器操作的效果。

## 调试

```sh
$ make debug
```
qemu 开机后会自动挂起，开始监听调试端口（默认端口1234），等待调试指令。
具体 qemu --help 查看相关参数意义。

在另一个 `shell` 中输入

```sh
$ gdb
$ target remote :1234
$ info reg   ;查看寄存器值
$ c
$ ^ctrl-c    ;手动执行（bootloader 无限循环中，故需终止)
$ info reg 	
```

即可查看到寄存器的数值。
