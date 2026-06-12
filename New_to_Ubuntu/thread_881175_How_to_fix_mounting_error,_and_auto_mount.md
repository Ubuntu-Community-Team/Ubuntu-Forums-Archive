---
title: "How to fix mounting error, and auto mount?"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by ricoco on 2008-08-05
Sorry for making this over written thread.  But I still have a problem with mounting even after I fixed a mounting problem before.

I have a 4G usb memory stick, and my computer keep showing "cannot mount volume".   Somehow I cannot mount manually too.


In addition, error in command line kept showing like this;

my-laptop:~$ mount /dev/sdc1
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Somebody, please help this beginner linux user:(
Also, does anybody knows if there any easy way to auto mount from next time?

---

### Post by raedbenz on 2008-08-05
hi,
try 
```
mount /dev/sdc1 /mnt
```
or
```
mount /dev/sdc1 /media/disk
```

---

### Post by cgkades on 2008-08-05
What file system type is your thumb drive formatted?

---

### Post by ricoco on 2008-08-05
thanks for the quick reply, but the error 
"only root can do that" 
keep coming up on both commands....


I am not sure why my computer does not consider me as a root...

---

### Post by ricoco on 2008-08-05
how to find the file system of my usb?

Sorry for the dumb question...

---

### Post by raedbenz on 2008-08-05
Go to my computer, then right click on the usb stick "Properties" and check the bottom of the window

---

### Post by bodhi.zazen on 2008-08-05
What file system on the USB device ?

---

### Post by ricoco on 2008-08-05
It said "unknown"....

I do not know why my computer does not recognize my usb anymore:(

---

### Post by cgkades on 2008-08-05
type "sudo [command]" to do something as root

You are a user, not root. Though, you are part of the wheel group (users allowed to sudo)

> **ricoco said:**
> thanks for the quick reply, but the error 
"only root can do that" 
keep coming up on both commands....


I am not sure why my computer does not consider me as a root...

---

### Post by cgkades on 2008-08-05
do you have a windows box nearby? you can check on that. Right click on it in my computer, then click properties
> **ricoco said:**
> It said "unknown"....

I do not know why my computer does not recognize my usb anymore:(

---

### Post by raedbenz on 2008-08-05
look, if u dont have any important data in ur USB i suggest to foramt it. Use GParted. install it using synaptics.

---

### Post by cgkades on 2008-08-05
Though he might want to format it fat so he can exchange files with a windows computer, unless you are feeling brave and rebellious of course :)

> **raedbenz said:**
> look, if u dont have any important data in ur USB i suggest to foramt it. Use GParted. install it using synaptics.

---

### Post by limasierra on 2008-08-05
You're saying that you're removable device is sdc1 but it may not always be as this. The first removable device plugged onto your computer will be sdb1, the second will be sdbc1, the third will be sdd1...

So if you have no other removable devices plugged onto your computer the memory stick will be sdb1.

Mount it using```
mount /dev/sdb1 /media/thenameofthefolder
```

Also make sure that the folder you designated for the memory stick exists, and if it doesn't create it:```
mkdir /media/thenameofthefolder
```

Notice that you may need root permissions to use the previous commands. If so use:```
sudo mount /media/thenameofthefolder
```
```
sudo mkdir /media/thenameofthefolder
```

---

### Post by ricoco on 2008-08-05
Thank you!!!  Typing "sudo"  worked!

And thanks to everybody who helped me out!
:)


Also, the usb mounts automatically as well!

;)

---

