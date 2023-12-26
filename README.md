# Container-Theory

# Linux Process Address Space

#### https://stackoverflow.com/questions/32746996/how-linux-process-address-space-is-stored
#### https://unix.stackexchange.com/questions/500256/linux-3-1-split-and-physical-map

#### Every process has a 4GB virtual address space:
#### The upper 1 GB, reserved and mapped to the shared OS kernel code and data structure (the same OS kernel code are mapped to multiple process virtual address spaces)
#### The lower 3 GB, available to the private user space process, including stack, code, data (global variable), heap (new object)
#### All threads within a process are sharing the same 4GB virtual address space
#### When a thread makes the system call (read/write files from the hard drive or receive/send packets over TCP/IP), the CPU will stop running the thread and start running the kernel code within the calling process's address space

![image](https://github.com/yinanericxue/Container-Theory/assets/102645083/cedf4840-8309-4c5b-a815-12e36385470e)

<img width="348" alt="image" src="https://github.com/yinanericxue/Container-Theory/assets/102645083/62db6ba0-79c0-4ce9-b471-d8f1928b1329">

#### Heap = new object (say written in java), more memory will be added depending on how much is really need it
#### Global variables - data segment
#### The actual manually written code - text segment


# Physical Memory and Virtual Memory
#### https://bottomupcs.sourceforge.net/csbu/x2816.htm
#### https://learn.microsoft.com/en-us/windows-hardware/drivers/gettingstarted/virtual-address-spaces
#### https://en.wikipedia.org/wiki/Virtual_address_space

#### A process reads or writes to the virtual memory/address space
#### The CPU translates the virtual address to a physical address

#### Access an address:  EFEA 1AFE
#### look up the red by using the high 16 bits and then check the blue by using the low 16 bits

#### The red: 64K x 4 B = 128 KB
![image](https://github.com/yinanericxue/Container-Theory/assets/102645083/3bc9fff9-a250-4ffa-ac5f-22f18a5b4f93)

#### Strength of this method: only need extra memory as you go, don't need to start with excessive in the start
#### Weakness 1: once reaching 4gb, there will be wasted memory
#### Weakness 2: during every look there is a two step address conversion

