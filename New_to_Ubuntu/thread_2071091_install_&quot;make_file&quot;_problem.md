---
title: "install &quot;make file&quot; problem"
date: 2012-10-14
forum: New to Ubuntu
---

### Post by TFSinclair on 2012-10-14
I'm trying to install a set of drivers for a piece of Ham Radio gear. I dowloaded the drivers for Linux from the manufacturers site and am trying to get the drivers installed.

When trying to install the "make file" of the drivers, I get the following error mesage.
Any help will be greatly appreciated.

tearlach@tearlach-KQ495AA-ABA-a6500f:~$ clean:
clean:: command not found
tearlach@tearlach-KQ495AA-ABA-a6500f:~$ $(MAKE) -C $(KDIR)/build SUBDIRS=$(PWD) clean
MAKE: command not found
KDIR: command not found
PWD: command not found
-C: command not found
tearlach@tearlach-KQ495AA-ABA-a6500f:~$ 
tearlach@tearlach-KQ495AA-ABA-a6500f:~$ install:
No command 'install:' found, did you mean:
 Command 'install' from package 'coreutils' (main)
install:: command not found
tearlach@tearlach-KQ495AA-ABA-a6500f:~$ cp cp210x.ko $(KDIR)/kernel/drivers/usb/serial/
KDIR: command not found
cp: cannot stat `cp210x.ko': No such file or directory
tearlach@tearlach-KQ495AA-ABA-a6500f:~$ grep -w "cp210x" /etc/modules || printf "%s\n" "cp210x" >> /etc/modules
cp210x
tearlach@tearlach-KQ495AA-ABA-a6500f:~$ modprobe cp210x
tearlach@tearlach-KQ495AA-ABA-a6500f:~$ rmmod cp210x
ERROR: Removing 'cp210x': Operation not permitted
tearlach@tearlach-KQ495AA-ABA-a6500f:~$ modprobe cp210x

---

### Post by MG&amp;TL on 2012-10-14
Normal procedure is to install *make* and *build-essential* , then run:

```
make
```

in that directory. If you don't get any errors from that, you're good to go and

```
sudo make install
```

with a bit of luck, whatever it is 'just works'.

If you DO get errors, post them here. It normally means you need another package.

Hint: there's normally a file labelled "README" in the top-level. Try opening that and see if it has any instructions.

It's a horrible system, but it's better than autoconf. Good luck!

---

