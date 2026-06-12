---
title: "Need help with getting windows back"
date: 2012-08-06
forum: New to Ubuntu
---

### Post by chairsgotoschool on 2012-08-06
I used wubi and put ubuntu on a hdd partition, i thought it would install it but it thinks that its a flash drive or something, now i cant get to my windows partition, i tried using my computers boot menu hoping i could boot from partitions there but i cant. summary is i have 2 partitions 1 with windows second has ubuntu and it automatically loads the ubuntu one. any help would be very helpful.

---

### Post by z3nhakr on 2012-08-06
wubi gives you two options when you install ubuntu. the second requires you to reboot BEFORE you install ubuntu. the first installs ubuntu then reboots. which did you choose?

---

### Post by bcbc on 2012-08-06
[Wubi]("https://wiki.ubuntu.com/WubiGuide") is supposed to boot using the Windows boot manager. Other than the first time (which boots direct to Ubuntu if you have Win7/vista) it should always give you a choice. Can you explain what happened in more detail, e.g. 
1. installed inside windows
2. rebooted to ubuntu
3. ?

Also, what version of windows you have. If Ubuntu loads and boots then download and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"). That will help us see what is going on.

---

### Post by chairsgotoschool on 2012-08-06
I did reboot now option so i think that would be rebooted to ubuntu, and im was using windows 8 consumer preview, i still should give me the option on what partition to boot from.

Also i cant get internet to work with ubuntu so downloading stuff is gonna be kinda hard

---

### Post by z3nhakr on 2012-08-06
did you create a new partition? How so? try booting a live usb or cd and then check that Both the windows partition and the windows boot manager partition are still intact.

---

### Post by chairsgotoschool on 2012-08-07
> **z3nhakr said:**
> did you create a new partition? How so? try booting a live usb or cd and then check that Both the windows partition and the windows boot manager partition are still intact.

not sure what you mean by live usb or cd, and in windows a few months ago i made a partition of 160gb cause i was going to have 2 pc's on 1 hdd but it turns out i didnt need the partition but i kept it just in case i decided to get ubuntu or something, in ubuntu i looked at my drives and it shows the windows boot one and 2 others, im assuming one of them is my windows stuff and the other is ubunu and my ubuntu stuff

---

### Post by bcbc on 2012-08-07
Can you drop to a terminal (Ctrl+Alt+T) and then run:
```
sudo fdisk -l
```
```
df -h
```
```
sudo os-prober
```

Post the output or a picture if easier

---

### Post by chairsgotoschool on 2012-08-07
> **bcbc said:**
> Can you drop to a terminal (Ctrl+Alt+T) and then run:
```
sudo fdisk -l
```
```
df -h
```
```
sudo os-prober
```

Post the output or a picture if easier

its 11pm where i live, i will try in the morning (in about 10 hours) i will post back when i do, and thanks for the help guys

---

### Post by chairsgotoschool on 2012-08-07
ok, i got the pictures here is the top part of it 
[http://i.imgur.com/T3fja.png?1](http://i.imgur.com/T3fja.png?1)
and the last part of it
[http://i.imgur.com/y1fCD.png?1](http://i.imgur.com/y1fCD.png?1)

---

### Post by peryang on 2012-08-07
You might be interested in the following threads:
[LIST=1]
[*]Windows 7 booting issue in XP machine
[*]Please Help -Black Desktop at Start Up
[*]Windows Explorer Malfunctioning - desperate need of help!
[*]Please help getting Windows XP user profile picture to wor..
[*]need help getting second activation code from ms
[/LIST]

---

### Post by bcbc on 2012-08-07
> **chairsgotoschool said:**
> ok, i got the pictures here is the top part of it 
[http://i.imgur.com/T3fja.png?1](http://i.imgur.com/T3fja.png?1)
and the last part of it
[http://i.imgur.com/y1fCD.png?1](http://i.imgur.com/y1fCD.png?1)

That fdisk command was -l, a lower case -L not a 'one'. But don't worry about going back for that one now.

So when you boot your computer, what's the first thing you see? Does it say "Preparing to install, press Esc for more options"? Or does it just boot straight up with no interaction?

---

### Post by chairsgotoschool on 2012-08-07
> **peryang said:**
> You might be interested in the following threads:
[LIST=1]
[*]Windows 7 booting issue in XP machine
[*]Please Help -Black Desktop at Start Up
[*]Windows Explorer Malfunctioning - desperate need of help!
[*]Please help getting Windows XP user profile picture to wor..
[*]need help getting second activation code from ms
[/LIST]

i dont see how those are at all relevant to my problem :confused:

---

### Post by chairsgotoschool on 2012-08-07
> **bcbc said:**
> That fdisk command was -l, a lower case -L not a 'one'. But don't worry about going back for that one now.

So when you boot your computer, what's the first thing you see? Does it say "Preparing to install, press Esc for more options"? Or does it just boot straight up with no interaction?

oops, i changed it anyway, here is that pic
[http://i.imgur.com/CHmQo.png?1](http://i.imgur.com/CHmQo.png?1)

when i boot it does my computers boot thing, then it opens up this (this was taken on my phone)

[http://i.imgur.com/I9bzE.jpg?1](http://i.imgur.com/I9bzE.jpg?1)

if you cant read it, it says installer boot menu at top then below list these options
run ubuntu from this usb
install ubuntu on a hard disk
test memory
boot from first hard disk
advanced options
help

---

### Post by bcbc on 2012-08-07
So... somehow you've set up /dev/sda3 as a 'USB' stick. It shows that only 805M is in use (107G free). It also has the boot flag set, which is why it keeps booting this 'USB' each time you power on the computer.

You could change the boot flag back to /dev/sda1 and it should boot Windows 8 since that is where os-prober identified it. But if you had Windows 8 files on /dev/sda3 that have been overwritten then Windows 8 may not boot correctly. Hopefully it's all on /dev/sda2 and you'll be okay.

A couple of things are puzzling... you say you used Wubi, but you also have a linux swap partition and this isn't possible with Wubi. Not to mention setting the boot flag and installing the ISO image to the partition. This sounds more like you used unetbootin.

So, if you are certain that /dev/sda3 didn't contain any key windows 8 files, that they're all on /dev/sda2 which looks like 115G or so) then you can go ahead and use GParted to change the boot flag from /dev/sda3 to /dev/sda1. It might not let you since /dev/sda3 is mounted, in which case you'll have to use a USB/CD to do it. Or maybe you can just put in your windows 8 DVD and repair it.

If you had important data on /dev/sda2 before you installed the ISO to it, then note that you can probably recover it using testdisk or photorec.

---

### Post by chairsgotoschool on 2012-08-07
> **bcbc said:**
> So... somehow you've set up /dev/sda3 as a 'USB' stick. It shows that only 805M is in use (107G free). It also has the boot flag set, which is why it keeps booting this 'USB' each time you power on the computer.

You could change the boot flag back to /dev/sda1 and it should boot Windows 8 since that is where os-prober identified it. But if you had Windows 8 files on /dev/sda3 that have been overwritten then Windows 8 may not boot correctly. Hopefully it's all on /dev/sda2 and you'll be okay.

A couple of things are puzzling... you say you used Wubi, but you also have a linux swap partition and this isn't possible with Wubi. Not to mention setting the boot flag and installing the ISO image to the partition. This sounds more like you used unetbootin.

So, if you are certain that /dev/sda3 didn't contain any key windows 8 files, that they're all on /dev/sda2 which looks like 115G or so) then you can go ahead and use GParted to change the boot flag from /dev/sda3 to /dev/sda1. It might not let you since /dev/sda3 is mounted, in which case you'll have to use a USB/CD to do it. Or maybe you can just put in your windows 8 DVD and repair it.

If you had important data on /dev/sda2 before you installed the ISO to it, then note that you can probably recover it using testdisk or photorec.

ok thanks you very much but could you explain how to change the boot flag, i have never used ubuntu before, and to help explain some things, i was using wubi cause it seemed easiest and it asked what drive to boot it on (i guess it meant usb) but i dont have one big enough so i though i have half my hdd partitioned so it should work :) but its using like a usb, im guessing if i did use a usb it would boot windows if i unplugged it

also, all my windows stuff should be on the other partition, i never used the half till ubuntu, thanks again

---

### Post by bcbc on 2012-08-07
Run GParted: hit windows key, type in "Gparted" and it will appear. Then select the partition /dev/sda3 and try to remove the bootflag as described [here]("http://gparted.org/display-doc.php?name=help-manual#gparted-manage-partition-flags"). And then select /dev/sda1 and set the boot flag on it.

If it doesn't let you (because /dev/sda3 is locked) then plan B would be to try it from the terminal (Ctrl+Alt+T). This is a post from oldfred: [http://ubuntuforums.org/showpost.php?p=11294161&postcount=3](http://ubuntuforums.org/showpost.php?p=11294161&postcount=3)

So for your purposes the command would be:
```
sudo sfdisk -A1 /dev/sda
```

Warning: using tools like sfdisk can be dangerous. You are encouraged to review the manual ("man sfdisk") and make sure the command is correct. e.g. there is this warning in the man page entry:
> sfdisk doesn't understand GUID Partition Table (GPT) and it is not designed for large partitions. In particular case use more advanced GNU parted(8 ).

But I guess if gparted doesn't let you change the boot flag, parted won't either. If you are nervous about sfdisk, then you should get an Ubuntu USB stick or CD and run Gparted from that. Or try Windows 8 repair.

---

### Post by chairsgotoschool on 2012-08-07
thank you all, bcbc i opened the gparted thing and just right clicked sda3 and unchecked boot and right clicked sda 1 and checked boot restarted then it booted windows, thanks

---

### Post by bcbc on 2012-08-07
> **chairsgotoschool said:**
> thank you all, bcbc i opened the gparted thing and just right clicked sda3 and unchecked boot and right clicked sda 1 and checked boot restarted then it booted windows, thanks

Great... 

My advice, since you have partitions available, is not to use Wubi. You need to boot from an Ubuntu CD or USB, choose to Install, and then select "Something else" and tell it to install on /dev/sda3 (set it as root (/) and format as ext4). If you don't do this Ubuntu will likely repartition /dev/sda2 and create a new swap partition, which you don't want.

If you are nervous about that, ask any of the many volunteers on ubuntuforums.org for assistance. It is not that complicated, but it can be a bit nerve-wracking the first time, especially after a bad experience like you had.

I still don't know how that happened to you with Wubi. If you can recall in detail then create a bug report. But it sounds like unetbootin was involved. 

Anyway, good luck!

---

