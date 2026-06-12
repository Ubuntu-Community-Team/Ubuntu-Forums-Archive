---
title: "make getting error - 'archheaders' failed"
date: 2017-04-11
forum: New to Ubuntu
---

### Post by sara8 on 2017-04-11
```
client@client:~$ cd /usr/src/linux-headers-4.4.0-72-generic/
client@client:/usr/src/linux-headers-4.4.0-72-generic$ sudo make oldconfig
[sudo] password for client: 
scripts/kconfig/conf  --oldconfig Kconfig
#
# configuration written to .config
#
client@client:/usr/src/linux-headers-4.4.0-72-generic$ sudo make prepare
scripts/kconfig/conf  --silentoldconfig Kconfig
make[1]: *** No rule to make target 'arch/x86/entry/syscalls/syscall_32.tbl', needed by 'arch/x86/entry/syscalls/../../include/generated/asm/syscalls_32.h'.  Stop.
arch/x86/Makefile:199: recipe for target 'archheaders' failed
make: *** [archheaders] Error 2
```


i can't to use the make command at anywhere?
What is the reason?
pls clear me asap..

---

