---
title: "[SOLVED] Accessing root with python"
date: 2008-09-09
forum: Programming Talk
---

### Post by swappo1 on 2008-09-09
Hello, 

I tried accessing my root drive through python but was denied permission.  I also tried accessing my usb flash drive and also was denied permission.  How would I get permission?  Can I obtain permission through python while I am accessing those drives?  Here is what I used:```
>>> import os
>>> for files in os.popen('/ ls -v').readlines():
...     print files[:-1]
... 
sh: /: Permission denied

```

---

### Post by LaRoza on 2008-09-09
That isn't a valid command "\ ls -v". 

If you want to list things in /, use "ls -v /".

---

### Post by imdano on 2008-09-09
Python has to be executed as root to begin with.  I don't think there is any way to elevate privileges once its already running.  Just start python like this and you should get access ```
sudo python
```

---

### Post by swappo1 on 2008-09-09
Ok, I got it to list the files in /. using:
```
>>> for files in os.popen('ls -v /').readlines():
...     print files[:-1]
... 
bin
boot
cdrom
dev
etc
home
initrd
initrd.img
initrd.img.old
lib
lib32
lib64
lost+found
media
mnt
opt
proc
root
sbin
srv
sys
tmp
usr
var
vmlinuz
vmlinuz.old

```

Thanks for the help.

---

### Post by pmasiar on 2008-09-09
> **imdano said:**
> Python has to be executed as root to begin with.  I don't think there is any way to elevate privileges once its already running.  

... and if there was such way to gain sudo, it would be serious security bug and promptly fixed 8-)

---

### Post by elmoosecapitan on 2008-09-09
you try: ```
var_name = 'sudo ls -v /'
os.popen(var_name).readlines()
```

Python is slightly flexible like that.


cheers

---

### Post by swappo1 on 2008-09-09
Thanks for the help everyone.  I was able to get it to work without sudo.  The reason I was denied permission was due to putting the backslash before ls -v instead of after.  With the re-written code it works fine.

---

