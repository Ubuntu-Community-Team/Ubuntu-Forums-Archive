---
title: "Can't boot help"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by siddharthshukla on 2008-08-14
i installed ubuntu recently along with XP as dual boot. I heard about the benefits of the ext3 file system and hence wanted to convert all my partitions except one(having xp)to ext3. i already had ubuntu installed on one of the partitions.In doing this i did something stupid as i used the XP bootable Cd to free one of the partitions(by del it and later format it using gparted to ext3)which was situated in btw the windows and ubuntu partitions.When i rebooted after deleting the partition i booted directly into XP and ubuntu wasn't detected. Since i have Fs driver installed i was able to read the ubuntu partition and found all files were intact including /boot and /boot/grub.i think grub was installed on the xp partition and when using the XP bootable cd to del the other partition the grub was overwritten resulting in this problem. Please help me fix this issue as i don't want to install a fresh copy of ubuntu again(as i would have to install all packages again). Is there a way to reinstall grub.please help me out.this is how my partitions are

1. c: =  xp installed here
2. d:= empty , this is the one i dleted and reformatted as ext3
3. e:= ubuntu installed here
4. f:= swap for ubuntu

---

### Post by lisati on 2008-08-14
If you have an "alternate" installation CD you might be able to use the "Rescue a broken system" option, which will ask you a number of questions. Answer them to the best of your ability. You will then be able to reinstall Grub.

---

### Post by siddharthshukla on 2008-08-14
No i only have the Ubuntu 8.04 amd64 live cd.. Is there no way i can use this to reinstall Grub???

---

### Post by lisati on 2008-08-14
There are ways, but we might have to search for them. 
You might want to search the forums for "SuperGrub"

---

### Post by siddharthshukla on 2008-08-14
i found this thread :[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+deleted](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+deleted)

will this help me reinstall grub and further after reinstalling will i be able to dual boot Xp and ubuntu?????

---

### Post by dhughes on 2008-08-14
> **siddharthshukla said:**
> No i only have the Ubuntu 8.04 amd64 live cd.. Is there no way i can use this to reinstall Grub???


 Sure you can, although I never had much luck doing it myself when I was having boot problems recently. Pretty much you have to go to the Terminal and enter a few commands. 

 This explains it far better than I can since I never really got it to work! [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

 There's also a LiveCD called SuperGrub that helps you but it's a bit cryptic and hard to follow.

** edit:**  siddharthshukla and lisati beat me to it

---

### Post by sandysandy on 2008-08-14
thats a good thread. also super grub disk is nice.

[www.supergrubdisk.org/](www.supergrubdisk.org/)

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

also post output of
[COLOR="Blue"]
sudo fdisk -lu[/COLOR]
[COLOR="Green"]
cat /boot/grub/menu.lst[/COLOR]

regards

---

### Post by lisati on 2008-08-14
I was about to jump in with [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) but spotted others had made some suggestions.

---

### Post by dodle on 2008-08-14
This helped me:  [http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub]("http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub")

---

