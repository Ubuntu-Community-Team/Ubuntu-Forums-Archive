---
title: "[SOLVED] need help installing gparted"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by ben32b on 2008-05-28
I recently installed ubuntu on my hard drive, and noticed that gparted didn't come already installed like it came on the livecd.

So I downloaded gparted, extracted it, opened the "gparted-0.3.7" folder, then tried running the file called "GParted Partition Editor", but I get this error:
> 
**There was an error launching the application**
Details: Failed to execute child process "/usr/
local/sbin/gparted" (No such file or directory)


Why did I get this error and how can I fix it so that I can run gparted?

---

### Post by halitech on 2008-05-28
why not just install it from Synaptic?

---

### Post by ben32b on 2008-05-28
I don't know how to do that, I just installed ubuntu for my first time today.

---

### Post by halitech on 2008-05-28
go to System - Administration - Synaptic

search for Gparted and put a check beside it then click apply

---

### Post by Aeph on 2008-05-28
Go to System->Administration->Synaptic Package Manager in the menu. Then just search gparted, select it, and install.

---

### Post by Oldsoldier2003 on 2008-05-28
```
sudo apt-get install gparted
``` its faster than digging around in synaptic :)

---

### Post by halitech on 2008-05-28
> **Oldsoldier2003 said:**
> ```
sudo apt-get install gparted
``` its faster than digging around in synaptic :)

and then he comes back and asks where does he type in that command ;)

ps. - open a terminal - Applications - Accessories - terminal

---

### Post by ben32b on 2008-05-28
synaptic worked for me, thank you :)

---

### Post by ben32b on 2008-05-28
How can I manage partitions on the hard drive that ubuntu is installed on if I can't unmount it since ubuntu is using it?

Do I need to use a live cd or is there an easier way?

---

### Post by Oldsoldier2003 on 2008-05-28
> **ben32b said:**
> How can I manage partitions on the hard drive that ubuntu is installed on if I can't unmount it since ubuntu is using it?

Do I need to use a live cd or is there an easier way?

you need a live cd since you cannot unmount your operating system

---

### Post by tialen on 2008-05-28
is there anyway to install gparted 0.3.7 or even 0.3.6 on ubuntu?? the version that comes with ubuntu and that is released to the package manager is 0.3.5 and it has all sorts of bugs dealing with large disks...

---

### Post by starcannon on 2008-05-28
You can use your Ubuntu Linux Livecd or you can use the gparted livecd:

[gParted-LiveCD]("http://gparted.sourceforge.net/livecd.php")

---

### Post by Oldsoldier2003 on 2008-05-28
> **tialen said:**
> is there anyway to install gparted 0.3.7 or even 0.3.6 on ubuntu?? the version that comes with ubuntu and that is released to the package manager is 0.3.5 and it has all sorts of bugs dealing with large disks...

go to the gparted website and download the source and compile it. it only takes a few minutes and you'll have the latest greatest gparted.

in a nutshell:
```
sudo apt-get install build-essential
sudo apt-get build-dep gparted
```


download the tarball from the gparted site and extract it
```
cd <to the gparted directory you created when you extracted the tarball>
./configure
make
```

now you can either install directly from source or create a .deb file

from source:
```
sudo make install
```


if you want to make a .deb - (btw do not cd from the directory you were working in)

```
sudo apt-get install checkinstall
sudo checkinstall
```

just hit enter for the questions it asks unless you feel like filling in the info (it doesn't matter)

alternatively you can do

```
checkinstall --install=no
``` and it will just create the .deb without installing it.

---

