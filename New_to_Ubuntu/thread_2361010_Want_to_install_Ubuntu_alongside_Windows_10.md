---
title: "Want to install Ubuntu alongside Windows 10"
date: 2017-05-11
forum: New to Ubuntu
---

### Post by springbox26 on 2017-05-11
Hey all,

So, I'm wanting to install Ubuntu onto my HP Notebook, but I still need Windows 10 for certain programs for school, etc. I was wondering what would be the best way for me to have both Windows 10 and Ubuntu on my computer (prefer not to use a virtual machine). I have about 800GB of HDD space, if that helps.
Also, how would I choose which OS to boot my computer into when I turn it on, and, how would I switch between OS when needed. 

Thanks in advance,
Springbox26 :)

---

### Post by QIII on 2017-05-11
Hello!

Multi-booting is a dangerous proposition.  Make sure you back up absolutely everything you want.  Use the Windows tools to first defrag and then shrink your Windows partitions.

Then, ***before  you do anything***, read [this]("https://help.ubuntu.com/community/WindowsDualBoot").  It will probably be very confusing and make you think of even more questions.  That's my point in asking you to read it!  :)  After your head is spilling questions out your ears, come back and ask for whatever explanations you need until you are absolutely satisfied that you know exactly what you are doing.

That said:  If you are new to Linux, I would highly recommend that you do use some form of virtualization at least for a time.  That gives you the luxury of trying things, breaking things, fixing things and having a good time without worrying about ruining your system and being stuck.

Cheers!

---

### Post by yancek on 2017-05-11
Since you have windows 10, it would be a good idea to determine if you are using UEFI and if windows was pre-installed, that is quite likely.   If it is UEFI, you need to install Ubuntu UEFI also or you will have problems booting.  See the Ubuntu documentation at the link below on dual booting with UEFI.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I'd also check your HP Manual for the notebook as HP does not comply with UEFI standards which complicates the install under UEFI.  It would definitely be less risky to use some type of virtual software or test a Live DVD or flash drive if you have not done that.  Good Luck.

---

### Post by mastablasta on 2017-05-11
another vote for "virtualisation first" from me. if default ubuntu is too "heavy" in WM, use Xubuntu or Lubuntu instead. they can be preety light and fast. this comes from me and i run it in virtualbox on a single core AMD with 4 GB ram (was only 2GB before and it still ran well) and Windows XP as host. :-)

---

### Post by RobGoss on 2017-05-11
First I want to welcome you to the forum, second thank you for considering Ubuntu as one of the goto desktops good choice

Dual booting is good for so people but may not be good for others, so make sure it's something you really want to do, yes I'm also a dual booted for many reasons 

Making a complete backup is a smart choice just in case something goes wrong. Running the live installer will give you the first impressions of the Ubuntu desktop

Do your homework and understand what Linux is all about then, decide what might be the way to approach Ubuntu

This will be a good article for starters
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by milkness on 2017-05-13
Have you ran Ubuntu via a USB yet on your system to see if it likes Ubuntu and Ubuntu likes it? Like the others have said about UEFI can be a problem but their are tutorials and such out there.

If you did not know, your hardive would have been split into sections (like a pie or a cake) by windows called partitioning. Each partition is a slice of the pie/cake, but strangely there can only be 4 slices called "Primary" partitions. Windows 10 would have most likely taken up all your 4 primary partition space which can be a problem. You can see this if you boot from a USB drive with Ubuntu on it and click "Try Ubuntu", look for a program called "GParted", it will show you your hardrive and it's partitions. If your lucky and only have 3 primary partitions, then you can shrink the biggest one with the "800 GB" of free space left to something like 500 GB or something and leave Ubuntu with 300 GB of free space for it to use.

 You can then create a sneaky cheating way of getting around the 4 primary partition rule by  creating a extended partition which allows you to sneak as many Primary partitions as you want into it. Apply all the changes and  run the Ubuntu installer and clicking the "something else option". Select the "extended partition" and create one partition inside it, about 1 GB and select the mount feature as /boot/efi with a partitioning type of fat32, the another about he size of 4 GB , select it's type as swap , no need to specify where to mount, and finally create one last partition mounted at /  make sure it is a ext4 and make it use up all the remanding space. Make sure that grub is install on the entire hardrive (just select the entire drive from the selection box) and click install.

Have fun!

---

