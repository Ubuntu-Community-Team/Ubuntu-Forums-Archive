---
title: "Reinstalled windows now i have reall problems"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by janes604 on 2008-11-07
So today i had to reinstall windows on my computer to be able to log into this site for work (stupid stupid stupid) 

So i reinstalled windows on part of my 2nd drive. 

and i lost grub.  so i followed some instructions from the ubuntus help pages 

sudo grub 

root (hd1,0) 

Setup (hd1)

quit


Now  i can get grub to load if i boot form that hard drive- it used to just load automaticly right to grub with out having to select that drive. 
When i select Ubuntu  it says error 14/or 15? file not found 
.........

so wtf did i do ?  please help

I hate windows and now im stuck in it 


fyi  ubuntu 8.04

---

### Post by randy78 on 2008-11-07
I use SuperGrubDisk when I have issues with Grub... Check here: [http://www.supergrubdisk.org/index.php?pid=5]("http://www.supergrubdisk.org/index.php?pid=5")

---

### Post by kansasnoob on 2008-11-07
It would help if you'd boot the live CD again and from terminal post the output of:

```
sudo fdisk -l
```

That's a lower case L.

I also wonder if when you restored grub you ran the command "find /boot/grub/stage1" after "sudo grub"?

---

### Post by bsharp on 2008-11-07
I find it easier to run the grub-install script instead of dropping to a grub shell.

E.G:
```
grub-install --root-directory=/boot/grub sda
```

Works every time for me.

---

### Post by janes604 on 2008-11-08
> **randy78 said:**
> I use SuperGrubDisk when I have issues with Grub... Check here: [http://www.supergrubdisk.org/index.php?pid=5]("http://www.supergrubdisk.org/index.php?pid=5")



Thanks that saved me ! 


and thanks to everyone for there Help!!!!


now im back to ubuntu and have my old grub back! but it doesn show my ¨new &#7813;indoze¨ partition ? any suggestions on how to fix that ?

---

### Post by zvacet on 2008-11-08
```
sudo fdisk -l
```

Post it here and then somebody will be able to help you.

---

### Post by randy78 on 2008-11-08
Cool, glad it worked! Keep that disk handy!

As far as not seeing your Windows partition, you'll need to add it into Grub manually.

In a terminal type: gksudo gedit /boot/grub/menu.lst

When it comes up, you'll need copy and paste this after the End Debian Automagic Kernels section, save and reboot:

title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

(Note that if your Windows partition is first, change hd0,1 to hd0,0)
As others have been saying, it would be much easier to give you a solution if you boot into a live cd and post the output of fdisk -l.

---

