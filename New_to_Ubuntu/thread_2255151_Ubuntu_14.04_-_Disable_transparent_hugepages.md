---
title: "Ubuntu 14.04 - Disable transparent hugepages"
date: 2014-12-02
forum: New to Ubuntu
---

### Post by paul@gloomoot on 2014-12-02
Hello, 

Because of an installation I'm making I need to disable transparent hugepages.
By default, transparent_hugepages are enabled, as you can see here:

```
$ cat /sys/kernel/mm/transparent_hugepage/enabled
[always] madvise never

```

The tutorials I found ([http://unix.stackexchange.com/questions/99154/disable-transparent-hugepages](http://unix.stackexchange.com/questions/99154/disable-transparent-hugepages), [http://doc.nuodb.com/display/doc/Linux+Installation](http://doc.nuodb.com/display/doc/Linux+Installation)) suggested that I first try and do this:

[PHP]$ sudo echo never > /sys/kernel/mm/transparent_hugepage/enabled
bash: /sys/kernel/mm/transparent_hugepage/enabled: Permission denied
[/PHP]

So I tried to add the mention transparent_hugepage=never to my /etc/default/grub and then ran upgrade-grub and rebooted but no dice.

Am I using the wrong parameter? The wrong file?

I haven't used ubuntu in about 6 years so I may need a refresher :)

Thanks in advance for your help!

---

### Post by paul@gloomoot on 2014-12-02
Problem solved using hugeadm : [http://manpages.ubuntu.com/manpages/trusty/man8/hugeadm.8.html](http://manpages.ubuntu.com/manpages/trusty/man8/hugeadm.8.html)

---

### Post by Impavidus on 2014-12-03
FYI:
[PHP]$ sudo echo never > /sys/kernel/mm/transparent_hugepage/enabled
bash: /sys/kernel/mm/transparent_hugepage/enabled: Permission denied
[/PHP]
This runs the echo command with root permissions, but not the output redirect (the > /path/to/file part). The process trying to write to the file is not echo, but the shell, which runs with your permissions, not root's. One way to solve this is using the **tee** command, which directs standard input to a file (and to standard output):```
echo "Some text" | sudo tee /path/to/root/file >/dev/null
```The final part (>/dev/null) is just to prevent "Some text" from being echoed to the terminal and is optional.

Alternatively, use a root shell. Then the output redirect will work.

---

### Post by zexelon2 on 2015-09-21
Quick question... how do I do this on Ubuntu 15.04? 

I have tried hugeadm and also manually however it just tells me that /sys/kernel/mm/transparent_hugepage/ is missing and when I check for the directory, sure enough it is missing on 15.04.

---

### Post by Per_Funke on 2015-12-22
check this:

root@eclipse:/home/xhosa# **echo always** >/sys/kernel/mm/transparent_hugepage/enabled
root@eclipse:/home/xhosa# cat /sys/kernel/mm/transparent_hugepage/enabled
**[always] **madvise never

root@eclipse:/home/xhosa# **echo never** >/sys/kernel/mm/transparent_hugepage/enabled
root@eclipse:/home/xhosa# cat /sys/kernel/mm/transparent_hugepage/enabled always madvise** [never]**

look! No hands, no tee, no hugeadm
:0)

---

