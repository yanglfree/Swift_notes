## 用汇编来分析Swift编程本质

#### 汇编语言的种类

- 8086汇编（16bit）
- x86汇编（32bit）
- x64汇编（64bit）
- ARM汇编（嵌入式、移动设备）



x86、x64汇编根据编译器的不同，有两种书写格式：

- Intel： Windows派系
- AT&T: Unix派系



iOS开发接触的最主要的汇编语言是：

- AT&T汇编 -> iOS模拟器
- ARM汇编 -> iOS真机设备



leaq: 地址传递 直接将内存地址进行传递

mov: 值传递 将地址的值取出来进行传递



#### 常见汇编指令

![image-20200508155628788](https://tva1.sinaimg.cn/large/007S8ZIlgy1gel3jcb7g0j31og0rkauv.jpg)





movq 内存空间, %rax 将内存空间的值放到rax寄存器中

addq $0x1,%rax 让rax寄存器与1相加



rip存储的事指令的地址

CPU要执行的下一条指令地址就存储在rip中

#### lldb指令

##### 常用的指令

si、finish、 s、 ni、 n



#### 寄存器

##### 寄存器的具体用途

- rax常作为函数返回值使用
- 常用的寄存器16个：rax、rbx、rcx、rdx、rsi、rdi、rbp、rsp、r8、r9、r10、r11、r12、r13、r14、r15
- rdi、rsi、rdx、rcx、r8、r9等寄存器常用于存放函数参数
- rsp、rbp用于栈操作
- rip作为指令指针
  - 存储着CPU下一条要执行的指令的地址
  - 一旦CPU读取一条指令，rip会自动指向下一条指令（存储下一条指令的地址）



##### 常用规律

- 内存地址格式为：-0x10(%rbp): 一般是局部变量，栈空间

- 内存地址格式为：0x4bdc(%rip): 一般是全局变量，全局区（数据段）

- 内存地址格式为：0x10(%rax): 一般是堆空间
