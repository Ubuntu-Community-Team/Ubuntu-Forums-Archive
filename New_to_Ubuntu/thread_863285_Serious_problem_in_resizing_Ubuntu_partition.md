---
title: "Serious problem in resizing Ubuntu partition"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by brunolopes446 on 2008-07-18
Hello everybody
My computer has two partitions: One called "Vista" where windows vista is installed and a partition called "Data", where I install all windows vista applications and stuff like that. But after that, I resized the "Data" partition and left 15GB of free space. Then, I boot from ubuntu cd, and I installed ubuntu of free space. But now I notice that 15gb is not enough for me. So what can I do now to have more space available on ubuntu?
I've resized the "Data" partition again to leave more 10GB's of free space, but I can merge those 10GB os free space with the 15GB where ubuntu is installed!
I've installed a few programs in windows vista but I can't expand ubuntu partition, I've tried gParted in ubuntu, and even with a liveCd of ubuntu but when I try to increase the size of the 15gb "partition" (because it's not really a partition, it's free space where I installed ubuntu) it has only 0,07mb to increase... Even if I have 10gb's of free space in the disk... 

What can I do now? Help me please! :confused:

---

### Post by DGortze380 on 2008-07-18
gparted should do it, (I don't have access to my VM right now or I'd give you step by steps)... I think you need to move your partitions so the free space is following your ubuntu partition then extend ubuntu partition to use free space. CAUTION: moving and resizing partitions takes some time and can cause partitions to be corrupted.

My suggested would be to format a new partition with the free space. Just choose the right format for your needs.

---

### Post by manishtech on 2008-07-18
That 10GB of extra space is free space(raw space)?

If it is so , then I would better suggest you to delete both partitions and then create a 25GB partition from this free space.
I know this is a a big decision since I have never been successful in resizing the root partition (where ubuntu is installed)

---

### Post by drs305 on 2008-07-18
15GB is normally enough for an ubuntu install. If you have a lot of data files in your ubuntu install you might consider moving the data to another partition. You might also move your /home folder to the extra partition instead of trying to merge the two. 

Here is a link for moving your /home partition:
[ Create a separate home partition in Ubuntu]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by mlentink on 2008-07-18
Also, please make sure the partitions you are trying to change are not presently mounted. GParted cannot do its magic on mounted partitions/drives

---

### Post by brunolopes446 on 2008-07-18
> **manishtech said:**
> That 10GB of extra space is free space(raw space)?

If it is so , then I would better suggest you to delete both partitions and then create a 25GB partition from this free space.
I know this is a a big decision since I have never been successful in resizing the root partition (where ubuntu is installed)
I'm not sure. I've booted ubuntu liveCd and started gParted and I resized a partition to have free space on the disk. I says "Non-allocated".

> **DGortze380 said:**
> gparted should do it, (I don't have access to my VM right now or I'd give you step by steps)... I think you need to move your partitions so the free space is following your ubuntu partition then extend ubuntu partition to use free space. CAUTION: moving and resizing partitions takes some time and can cause partitions to be corrupted.

My suggested would be to format a new partition with the free space. Just choose the right format for your needs.
How can I do what you said? Move my partitions so the free space is following my ubuntu partition...

> **drs305 said:**
> 15GB is normally enough for an ubuntu install. If you have a lot of data files in your ubuntu install you might consider moving the data to another partition. You might also move your /home folder to the extra partition instead of trying to merge the two. 

Here is a link for moving your /home partition:
[ Create a separate home partition in Ubuntu]("http://www.psychocats.net/ubuntu/separatehome")

I know that 15Gb is enough for an ubuntu install, but I have lot of big data files... Moving the data to another partition? How? By creating one with (for example) 25Gb, and then copy all the folders and files that are on my ubuntu installation? Moving my home partition? I'm going to check that link ;)
> **mlentink said:**
> Also, please make sure the partitions you are trying to change are not presently mounted. GParted cannot do its magic on mounted partitions/drives
I think that they are not mounted because I've booted up ubuntu from the liveCD... but maybe I'm wrong :confused:

---

### Post by mlentink on 2008-07-18
Actually booting the Live-CD would automatically mount all built-in partitions if they are mountable. FAT-32 and NTFS partitions are mountable, so they will be automatically mounted. Do they show up on your desktop? Then right-click them and select unmount before you try to do anything in GParted.

---

### Post by brunolopes446 on 2008-07-18
> **mlentink said:**
> Actually booting the Live-CD would automatically mount all built-in partitions if they are mountable. FAT-32 and NTFS partitions are mountable, so they will be automatically mounted. Do they show up on your desktop? Then right-click them and select unmount before you try to do anything in GParted.
They don't appear on my desktop. And I don't know why I can't even open Vista and Data partitions now... (in ubuntu liveCD). Have I damaged anything on the partitions? I can post a printscreen if you want... But I can open the "partition" where ubuntu is installed... 
Isn't that strange?
Oh my god, now I have two problems! Or is this normal?

---

### Post by manishtech on 2008-07-18
> I'm not sure. I've booted ubuntu liveCd and started gParted and I resized a partition to have free space on the disk. I says "Non-allocated".

I meant to say,increasing size of a partition,not decreasing.
Unallocated is what I refer to as raw.

---

### Post by DGortze380 on 2008-07-18
ok, lets slow down for a second, you're trying to do too many different things at once.

1) post the output of: df -l (thats a lowercase L)
2) Your Options:
     a) Backup your data, delete your Ubuntu Partitions, reinstall with a new partitioning scheme
     b) Attempt to move partitions around and merge your existing ubuntu partition with your free space. (honestly, probably more trouble than it's worth, and there's a good chance it won't work)
     c) use your existing free space, create a new data partition, use it for more files.
     d) move /home to it's own partition using your existing free space.


at this point you may want to consider a combination of a and b. back up your files, delete your / partion and swap. reinstalling with 3 partitions, / , /home and swap.

like I said, first lets see what you have. post df-l or a screen shot of gparted.

---

### Post by brunolopes446 on 2008-07-18
> **DGortze380 said:**
> ok, lets slow down for a second, you're trying to do too many different things at once.

1) post the output of: df -l (thats a lowercase L)
2) Your Options:
     a) Backup your data, delete your Ubuntu Partitions, reinstall with a new partitioning scheme
     b) Attempt to move partitions around and merge your existing ubuntu partition with your free space. (honestly, probably more trouble than it's worth, and there's a good chance it won't work)
     c) use your existing free space, create a new data partition, use it for more files.
     d) move /home to it's own partition using your existing free space.


at this point you may want to consider a combination of a and b. back up your files, delete your / partion and swap. reinstalling with 3 partitions, / , /home and swap.

like I said, first lets see what you have. post df-l or a screen shot of gparted.

ubuntu@ubuntu:~$ sudo df -l
Sistema de Ficheiros         blocos-  1K Utilizados disponíveis Use% Montado em
tmpfs                  1557452     16004   1541448   2% /lib/modules/2.6.24-16-generic/volatile
tmpfs                  1557452     16004   1541448   2% /lib/modules/2.6.24-16-generic/volatile
varrun                 1557452       104   1557348   1% /var/run
varlock                1557452         0   1557452   0% /var/lock
udev                   1557452        56   1557396   1% /dev
devshm                 1557452        12   1557440   1% /dev/shm
tmpfs                  1557452        16   1557436   1% /tmp

---

### Post by brunolopes446 on 2008-07-18
> **manishtech said:**
> I meant to say,increasing size of a partition,not decreasing.
Unallocated is what I refer to as raw.
Ok, so it's raw free space (unallocated).

---

### Post by DGortze380 on 2008-07-18
> **brunolopes446 said:**
> ubuntu@ubuntu:~$ sudo df -l
Sistema de Ficheiros         blocos-  1K Utilizados disponíveis Use% Montado em
tmpfs                  1557452     16004   1541448   2% /lib/modules/2.6.24-16-generic/volatile
tmpfs                  1557452     16004   1541448   2% /lib/modules/2.6.24-16-generic/volatile
varrun                 1557452       104   1557348   1% /var/run
varlock                1557452         0   1557452   0% /var/lock
udev                   1557452        56   1557396   1% /dev
devshm                 1557452        12   1557440   1% /dev/shm
tmpfs                  1557452        16   1557436   1% /tmp

sorry. forgot you were on a live cd. going to need the gparted screenshot.

---

### Post by brunolopes446 on 2008-07-18
> **DGortze380 said:**
> sorry. forgot you were on a live cd. going to need the gparted screenshot.

Ok
here it is: [img]http://img360.imageshack.us/img360/1269/captureiz4.png[/img]

---

### Post by brunolopes446 on 2008-07-18
DGortze380, about your options, I've been thinking and the most practical for my case would be: b) Attempt to move partitions around and merge your existing ubuntu partition with your free space. (honestly, probably more trouble than it's worth, and there's a good chance it won't work)

But you said that there is lot of trouble and a good chance it won't work... so... I don't know what to do now... but I think that the option a) Backup your data, delete your Ubuntu Partitions, reinstall with a new partitioning scheme
would be the easiest way to get what I need...

---

### Post by kansasnoob on 2008-07-18
Bruno,

Well I hope you don't mind me calling you Bruno:confused:

I'd like to see you slow down a bit. I see no reason to "move" anything. And I'm not being "disagreeable" with others offering advice, you can ask 10 Ubuntu users and probably get upwards of 20 opinions!

First you scare me a bit when you say, "Oh my god, now I have two problems! Or is this normal?"

What I'd do at this point is restart, remove the Live CD and make sure all is well! If everything still boots and all your data seems to be intact then lets do some things to get you where you want to go ............. simply and slowly!

If all seems well, that is you find out no damage is done so far, then I'd start with having you burn a GParted Live CD, and I'm fully aware that you can use the Ubuntu Live CD but this will be much faster and the Gparted Live CD takes about 5 minutes to download and burn. The latest stable version is 0.3.7-7.iso.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

If you decide to restart and remove the Ubuntu live CD I'd like to see a new screenshot, from the installed OS rather than the Live CD, just to be absolutely sure nothing has changed.

---

### Post by brunolopes446 on 2008-07-18
> **kansasnoob said:**
> Bruno,

Well I hope you don't mind me calling you Bruno:confused:

I'd like to see you slow down a bit. I see no reason to "move" anything. And I'm not being "disagreeable" with others offering advice, you can ask 10 Ubuntu users and probably get upwards of 20 opinions!

First you scare me a bit when you say, "Oh my god, now I have two problems! Or is this normal?"

What I'd do at this point is restart, remove the Live CD and make sure all is well! If everything still boots and all your data seems to be intact then lets do some things to get you where you want to go ............. simply and slowly!

If all seems well, that is you find out no damage is done so far, then I'd start with having you burn a GParted Live CD, and I'm fully aware that you can use the Ubuntu Live CD but this will be much faster and the Gparted Live CD takes about 5 minutes to download and burn. The latest stable version is 0.3.7-7.iso.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

If you decide to restart and remove the Ubuntu live CD I'd like to see a new screenshot, from the installed OS rather than the Live CD, just to be absolutely sure nothing has changed.

Thanks for your help.
I'm downloading right now gParted Live CD...
Here is a gParted screenshot from the installed OS (ubuntu):
[img]http://img524.imageshack.us/img524/4278/capture2ud5.png[/img]
Now I'm going to check if I can boot windows vista well...

---

### Post by kansasnoob on 2008-07-18
I must run an errand but I'll be back.

Ah good! We posted at the same time, give me a few minutes. I have a breif errand to run.

---

### Post by kansasnoob on 2008-07-18
I must say the totally blank "white" partitions scare the hell out of me!

I'll be back in 5 or 10 minutes.

---

### Post by manishtech on 2008-07-18
A point to note.. Merging the partitions is possible only if they are contigious.... If there is a free space, then partition A, then partition B, then you cant merge this free space with partition B and create a bigger partition.

---

### Post by brunolopes446 on 2008-07-18
I can boot Vista & ubuntu well and seems to be everything ok! Sorry for the false alarm 

-----

Kansasnoob,
- What can I do now with gParted live cd after booting up the cd? What should I do?

- I must say that my computer (Toshiba A200-21T has a technology called "Intel® Turbo Memory (1 GB)". I think that it affects the partitions...

---

### Post by brunolopes446 on 2008-07-18
> **manishtech said:**
> A point to note.. Merging the partitions is possible only if they are contigious.... If there is a free space, then partition A, then partition B, then you cant merge this free space with partition B and create a bigger partition.

That's practically what I wanted in the beggining! But now I can see that it's impossible, so I'm looking for solutions, so thanks you all for your help

---

### Post by kansasnoob on 2008-07-18
I wonder why the last screen shot showed both Vista partitions as blank? That doesn't really matter now.

What you want to do is give up some space from the Vista data partition (sda3) and allocate that space to Ubuntu (sda5 which is inside sda4)) and they are contiguous!

So you want to begin by resizing (shrinking) sda3. Easy does it! sda3 is nearly half used and it's 119.76 now, that means about 60gb is used. I'd personally reduce it to no less than 90gb which will free up nearly 30 gb. Quite simply the more you reduce the size of sda3 the more likely you are to result in data loss!

I'll continue this post. Do you get what I'm saying so far?

---

### Post by kansasnoob on 2008-07-18
After resizing sda3 I'd restart and remove the GParted Live CD, or the Ubuntu Live CD depending on which one you use, (BTW: I like using the GParted Live CD but it's safer to use gparted from the Ubuntu Live CD).

What we want to see is what we've accomplished. Is sda 3 smaller? Does everything still work? (There is always a small chance of something "breaking" during partitioning)!

What you should now see is an unpartitioned space between sda3  and sda4 (sda 5,6, &7 are all within #4)

---

### Post by brunolopes446 on 2008-07-18
> **kansasnoob said:**
> I wonder why the last screen shot showed both Vista partitions as blank? That doesn't really matter now.

What you want to do is give up some space from the Vista data partition (sda3) and allocate that space to Ubuntu (sda5 which is inside sda4)) and they are contiguous!

So you want to begin by resizing (shrinking) sda3. Easy does it! sda3 is nearly half used and it's 119.76 now, that means about 60gb is used. I'd personally reduce it to no less than 90gb which will free up nearly 30 gb. Quite simply the more you reduce the size of sda3 the more likely you are to result in data loss!

I'll continue this post. Do you get what I'm saying so far?
I think yes!
What I understood is to reduce the size of Data or Vista partitions to have free space. That's ok, that's what I've already done! And now, how can I allocate that space to Ubuntu?

---

### Post by brunolopes446 on 2008-07-18
I'm going to boot Ubuntu LiveCD to reduce the size of "Data" partition, ok? Is that what you're saying?
On the installed ubuntu I can't do anything with that partition... in gParted appears a orange triangule with an exclamation point next to the name of the partition... (I don't know if I explained well, but there's no problem on posting a print screen)

---

### Post by brunolopes446 on 2008-07-18
Kansasnoob,
Now I have 10gb's of unallocated free space that I reduced from my Data partition. Now I want to add those 10gb's of free space into my ubuntu "partition". Note: I'm currently on ubuntu liveCD and I've resized the partition with ubuntu liveCD

---

### Post by kansasnoob on 2008-07-18
> "'m going to boot Ubuntu LiveCD to reduce the size of "Data" partition, ok? Is that what you're saying?


Yes, that's sda3! And make it no smaller than 90gb (I'd prefer no smaller thya 100gb)

---

### Post by kansasnoob on 2008-07-18
> Note: I'm currently on ubuntu liveCD and I've resized the partition with ubuntu liveCD

Cool! I think I made you waste a CD on burning that Gparted CD.

Now ....... be very patient while I spell the rest of this out ........ I'm going to see you thru this OK?

Just don't jump and do something ahead of time, if I say "wait" then wait, OK?

---

### Post by brunolopes446 on 2008-07-18
> **kansasnoob said:**
> Yes, that's sda3! And make it no smaller than 90gb (I'd prefer no smaller thya 100gb)

Ok but now there is a problem. When the grub is loading, it says ERROR 17.
I have only reduced the size of Data partition in 10Gb. I have **no** backup of anything.

---

### Post by kansasnoob on 2008-07-18
So now you want to resize sda4 so it takes over the unallocated space between sda3 and sda 4, OK? You should be able to do that by clicking resize on sda4.

There is a slight possibility that you may have to "move" sda 4 first, but I think Gparted sorted that out.

---

### Post by brunolopes446 on 2008-07-18
> **kansasnoob said:**
> So now you want to resize sda4 so it takes over the unallocated space between sda3 and sda 4, OK? You should be able to do that by clicking resize on sda4.

There is a slight possibility that you may have to "move" sda 4 first, but I think Gparted sorted that out.

Besides the Grub problems { oh my god, how can I solve this now withou a backup? } that I refered on my last post, here is the printscreen when I try to resize the ubuntu partition [http://img300.imageshack.us/img300/5134/capture3fb2.png](http://img300.imageshack.us/img300/5134/capture3fb2.png)

I have already tryed to do this ... but in the printscreen you will notice that besides the fact that there is free space in the disk, it doesnt seems to detect, because I cant go over the size of what I already have... In other words, I cant increase the size of the ubuntu partition, even with 10gb of free space in the disk

---

### Post by kansasnoob on 2008-07-18
> **brunolopes446 said:**
> Ok but now there is a problem. When the grub is loading, it says ERROR 17.
I have only reduced the size of Data partition in 10Gb. I have **no** backup of anything.

You did resize only sda3, eh?

Can you send a new screenshot of Gparted?

---

### Post by kansasnoob on 2008-07-18
Based on this image nothing has been resized:

[http://img300.imageshack.us/img300/5134/capture3fb2.png](http://img300.imageshack.us/img300/5134/capture3fb2.png)

It's identical to the previous screenshots.

I'm not sure why you're having the GRUB error 17. If you can boot Ubuntu try a simple:

```
sudo apt-get autoclean

```

to free up some badly needed space in Ubuntu.

In Gparted are you clicking "apply" before you exit?

---

### Post by brunolopes446 on 2008-07-18
> **kansasnoob said:**
> Based on this image nothing has been resized:

[http://img300.imageshack.us/img300/5134/capture3fb2.png](http://img300.imageshack.us/img300/5134/capture3fb2.png)

It's identical to the previous screenshots.

I'm not sure why you're having the GRUB error 17. If you can boot Ubuntu try a simple:

```
sudo apt-get autoclean

```

to free up some badly needed space in Ubuntu.

In Gparted are you clicking "apply" before you exit?
On that screenshot I have not applied the changes...but now they are applied
I cant boot anything, because when grub is loading, the error appears, so I cant choose the OS. I dont know if it is secure to run that command on ubuntu liveCD... Is that safe? I am afraid of damaging even more things
But by the way, here is my menu.lst
```


# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		2

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=1edfa1b9-dbfb-4e33-8b6e-60040ea1653a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash locale=pt_PT

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1



title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1edfa1b9-dbfb-4e33-8b6e-60040ea1653a ro quiet splash locale=pt_PT
initrd		/boot/initrd.img-2.6.24-16-generic
quiet



# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other:
root

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1edfa1b9-dbfb-4e33-8b6e-60040ea1653a ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by kansasnoob on 2008-07-18
Yeah, I'm not great at menu lists, but it looks like yours is hosed. Nothing about resizing one NTFS partition should have done that, but
look:

Your menu list shows:

> title		Windows Vista/Longhorn (loader)
root		(hd0,1)


and:

> title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,5)

And when I look at your screenshot(s) thats just wrong.

Wait!

---

### Post by brunolopes446 on 2008-07-18
> **kansasnoob said:**
> Yeah, I'm not great at menu lists, but it looks like yours is hosed. Nothing about resizing one NTFS partition should have done that, but
look:

Your menu list shows:



and:



And when I look at your screenshot(s) thats just wrong.

Wait!

So what can I do now? Fix it... but how?
Shoul I increase the size of de partition Data, to include the 10gb of free space? Should I try it to fix the problem? Or it won't work?  I really don't know what to do know... Now I can only use my computer with ubuntu liveCD :confused::confused::confused:

---

### Post by kansasnoob on 2008-07-18
OK, this is right:

> title Windows Vista/Longhorn (loader)
root (hd0,1) 

Wait.

---

### Post by brunolopes446 on 2008-07-18
> **kansasnoob said:**
> OK, this is right:



Wait.

Ok I wait but it still giving me "Error 17" when the grub is loading. Thanks for your help

---

### Post by kansasnoob on 2008-07-18
Since sda5 is your Ubuntu partition this makes no sense to me:

> title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,5)

But there's no way that should have changed just resizing sda3!

Sda5 should be (hd0,4).

So I'm lost!

I've never, ever had drive allocations change during a partitioning! Never!

---

### Post by brunolopes446 on 2008-07-18
> **kansasnoob said:**
> Since sda5 is your Ubuntu partition this makes no sense to me:



But there's no way that should have changed just resizing sda3!

Sda5 should be (hd0,4).

So I'm lost!

I've never, ever had drive allocations change during a partitioning! Never!

I think that it has  always been like that ((hd0,5)).
But I'm going to undo what I've done with partitions (merge the free space with "Data" partition). And then I'm going to see if it works or not...

---

### Post by kansasnoob on 2008-07-18
> **brunolopes446 said:**
> Ok I wait but it still giving me "Error 17" when the grub is loading. Thanks for your help

Well, let me double check myself but I think you now need to edit your menu list ................... but it makes no sense for that to happen from what I told you to do! None at all!

And again, wait! I especially have trouble with menu lists because of the columns of ####. They induce seizures and I must print the lists and then fold over the offensive parts and diddle longer than most.

---

### Post by brunolopes446 on 2008-07-18
> **kansasnoob said:**
> Well, let me double check myself but I think you now need to edit your menu list ................... but it makes no sense for that to happen from what I told you to do! None at all!

And again, wait! I especially have trouble with menu lists because of the columns of ####. They induce seizures and I must print the lists and then fold over the offensive parts and diddle longer than most.

Yeah, I know that, it doesn't make any sense. But In the past I had problems with grub, because things like this: "(hda0,4)" were wrong... And it gaves me the error only when I try to boot the OS selected with the location of the respective OS wrong. So, it doesn't affect the loading of grub, but only the loading of the respective operating system!

I've already merged the 10gb of free space with the Data partition but it still giving me error 17 while the grub is loading...

---

### Post by kansasnoob on 2008-07-18
> I think that it has always been like that ((hd0,5)).
But I'm going to undo what I've done with partitions (merge the free space with "Data" partition). And then I'm going to see if it works or not...

hd0,5 (aka sda6) is a swap partition according to gparted, then again you have two swap partitions. Maybe someone built a separate GRUB partition:confused:

What I don't understand is why none of the changes made show up on a screenshot.

---

### Post by brunolopes446 on 2008-07-18
> **kansasnoob said:**
> hd0,5 (aka sda6) is a swap partition according to gparted, then again you have two swap partitions. Maybe someone built a separate GRUB partition:confused:

What I don't understand is why none of the changes made show up on a screenshot.

I'm so confused :confused:

I followed this tutorial:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

and when I run this command (of that tutorial):
```

find /boot/grub/stage1

```
it displays: hd(0,4)
and in the tutorial too this is written:
```

Find /boot/grub/stage1 has grub locate the file stage1. What this does is **tell us where grub's files are**. Only a small part of grub is located on the mbr, the rest of grub is in your boot folder. Grub needs those files to run the setup. So you find the files and then you tell grub where to locate the files it will need for setup.
```

---------------

**_Edit:_**
And it worked!
Now I can boot windows vista and ubuntu!
But to boot ubuntu I had to change hd(0,5) to hd(0,4).
Now it** seems** to be all ok!
Let's get back to the initial problem, yeah? Lol

---

### Post by kansasnoob on 2008-07-18
> **brunolopes446 said:**
> Yeah, I know that, it doesn't make any sense. But In the past I had problems with grub, because things like this: "(hda0,4)" were wrong... And it gaves me the error only when I try to boot the OS selected with the location of the respective OS wrong. So, it doesn't affect the loading of grub, but only the loading of the respective operating system!

I've already merged the 10gb of free space with the Data partition but it still giving me error 17 while the grub is loading...

The thing is that reducing the size of a Vista/ntfs partition is NOT going to effect GRUB, but your Ubuntu partition was crunched for room.

This should not have been that difficult. Shrink sda3, expand sda4, then consider what to to with the multiple Swap's and expand sda5.

My only fear of breakage had to do with the Vista partition(s).

---

### Post by kansasnoob on 2008-07-18
> Edit:
And it worked!
Now I can boot windows vista and ubuntu!
But to boot ubuntu I had to change hd(0,5) to hd(0,4).
Now it seems to be all ok!
Let's get back to the initial problem, yeah? Lol

OK, do you still have that extra 10gb?

---

### Post by brunolopes446 on 2008-07-18
> **brunolopes446 said:**
> That's practically what I wanted in the beggining! But now I can see that it's impossible, so I'm looking for solutions, so thanks you all for your help

> **kansasnoob said:**
> OK, do you still have that extra 10gb?
No, because I've merged that 10gb with Data partition

---

### Post by kansasnoob on 2008-07-18
Well, yell at me. I don't know why that happened, but this is doable! What you need to do is shrink sda3, then "grow" sda4. (All of your Ubuntu is within sda4) Now you know you must save each and every change, you can't wait and save several changes at once. 

After shrinking sda3 you'll be able to expand sda4 (your Ubuntu) but before doing so this would be a great time to delete sda7 and give that space to sda6, then you'll end up with one larger swap and you can then allow sda5 to take over all the unallocateds space inside sda4.

Clear as mud:confused:

---

### Post by kansasnoob on 2008-07-18
Well, I'm worn out!

This is not complicated. I have no idea why that GRUB thing popped up.

You need to shrink sda3 (no more than 30gb) and save that change. Then expand sda4 and save that change. Then maybe delete (sda6 and expand sda7, both swap), then go ahead and give everything that's left to Ubuntu sda5!

Just think of sda4 as a peanut shell with multiple nuts inside!

I'm just worn out!

---

### Post by brunolopes446 on 2008-07-18
> **kansasnoob said:**
> Well, yell at me. I don't know why that happened, but this is doable! What you need to do is shrink sda3, then "grow" sda4. (All of your Ubuntu is within sda4) Now you know you must save each and every change, you can't wait and save several changes at once. 

After shrinking sda3 you'll be able to expand sda4 (your Ubuntu) but before doing so this would be a great time to delete sda7 and give that space to sda6, then you'll end up with one larger swap and you can then allow sda5 to take over all the unallocateds space inside sda4.

Clear as mud:confused:
I've already shrinked sda3 but when I try to grow sd4 there's no space to put in sd4, as I explained a few post's ago. I've included a printscreen too.

> **kansasnoob said:**
> Well, I'm worn out!

This is not complicated. I have no idea why that GRUB thing popped up.

You need to shrink sda3 (no more than 30gb) and save that change. Then expand sda4 and save that change. Then maybe delete (sda6 and expand sda7, both swap), then go ahead and give everything that's left to Ubuntu sda5!

Just think of sda4 as a peanut shell with multiple nuts inside!

I'm just worn out!
Just for curiosity, why do you say "You need to shrink sda3 (**_no more than 30gb_**)"?
And to shrink sda3 and grow sda4 I should do that with an ubuntu liveCD right?

---

### Post by brunolopes446 on 2008-07-19
Can someone answer me please?

---

### Post by phoenix_abhi on 2008-07-19
Hey forget about all those things, u have put 24 miserable hours. Now do this in simple and realisitc way

1. UR Vista partitions is too large, which can accomodate the data (necessary) partition in it. I meant transfer all those data to a folder inside the vista part. Now delete the data partition.

2. Do u  have t take anything from Ubuntu? take backup, if u are installed so many apps and it is a pain to down load it again, Browse and d/l [COLOR="SandyBrown"]APTonCD[/COLOR]. Which will create a ISO for the all installation done after the Ubuntu installation.After successful Ubuntu installation re apply the image, ur Uptodate.

3. Delete all the partitions. Now u have vista, and a lot of raw space available, if u want more resize the Vista partition, but [COLOR="Blue"]defragment[/COLOR] the partition before resizing it.

4. Use Gparted or whatever u want, allot a minimum 10 GB for root(\), 15 GB for home and 3-4 GB for swap when installing Ubuntu. If u have so much data making another partition is also good, inside Ubuntu.

In the final look
1. Vista (90 GB or more)
2. Data  (u created it again and re transfereed the data back)
3. Ubuntu root
4. Home
5. Swap
6. ur choice

It will take hardly one hour ( data transfer is depend upon ur machine)

Hope this will solve ur pained call

---

### Post by brunolopes446 on 2008-07-19
> **phoenix_abhi said:**
> Hey forget about all those things, u have put 24 miserable hours. Now do this in simple and realisitc way

1. UR Vista partitions is too large, which can accomodate the data (necessary) partition in it. I meant transfer all those data to a folder inside the vista part. Now delete the data partition.

2. Do u  have t take anything from Ubuntu? take backup, if u are installed so many apps and it is a pain to down load it again, Browse and d/l [COLOR="SandyBrown"]APTonCD[/COLOR]. Which will create a ISO for the all installation done after the Ubuntu installation.After successful Ubuntu installation re apply the image, ur Uptodate.

3. Delete all the partitions. Now u have vista, and a lot of raw space available, if u want more resize the Vista partition, but [COLOR="Blue"]defragment[/COLOR] the partition before resizing it.

4. Use Gparted or whatever u want, allot a minimum 10 GB for root(\), 15 GB for home and 3-4 GB for swap when installing Ubuntu. If u have so much data making another partition is also good, inside Ubuntu.

In the final look
1. Vista (90 GB or more)
2. Data  (u created it again and re transfereed the data back)
3. Ubuntu root
4. Home
5. Swap
6. ur choice

It will take hardly one hour ( data transfer is depend upon ur machine)

Hope this will solve ur pained call

Sorry to say this, but I think that it gives me a lot of work. And I need two partition for vista, a Data one and another where are the OS files. 
What I'm going in a few days is format my computer, and create a third partition (30gb) instead of leaving raw/free space in the disk. ;)

And thanks for the program "APTonCD"! I'm going to use it.

---

### Post by pgte3 on 2008-07-19
The Ubuntu install guide states the the minimum requirements for an install of Ubuntu 8.04 is at least 4 GB of disk space (for full installation and swap space).

You say that you partition is 15 GB. This should be more than enough space of Ubuntu. I am not sure why you need more space?

I would format an extra partition for data and mount it to your Ubuntu image.

---

### Post by kansasnoob on 2008-07-20
I'm sorry to have dropped this hard, but just to recap:

Post #8:

You said: "They don't appear on my desktop. And I don't know why I can't even open Vista and Data partitions now... (in ubuntu liveCD). Have I damaged anything on the partitions? I can post a printscreen if you want... But I can open the "partition" where ubuntu is installed...
Isn't that strange?
Oh my god, now I have two problems! Or is this normal?"

That's a major problem!

Post #23:

I said: "So you want to begin by resizing (shrinking) sda3. Easy does it! sda3 is nearly half used and it's 119.76 now, that means about 60gb is used. I'd personally reduce it to no less than 90gb which will free up nearly 30 gb. Quite simply the more you reduce the size of sda3 the more likely you are to result in data loss!"

But still in post #51:

You ask: "Just for curiosity, why do you say "You need to shrink sda3 (no more than 30gb)"?"

When you experienced the GRUB problem (which is unusual) I got you through it, but you argued the whole way! When I asked you to wait you (undid) the "shrinking" of sda3, and I never saw evidence of free (unallocated) space between sda3 and sda4! All of your Ubuntu is within sda4!

With some older versions of Gparted you could only move left to right, or vice-versa in some situations but I used both the Hardy version and 0.3.7-7 GParted yesterday and you can do this!

Had you been resizing a Vista OS partition I would have had you start with this:

[http://www.ehow.com/how_2262528_extend-ntfs-partitions-windows-vista.html?ref=fuel&utm_source=yahoo&utm_medium=ssp&utm_campaign=yssp_art](http://www.ehow.com/how_2262528_extend-ntfs-partitions-windows-vista.html?ref=fuel&utm_source=yahoo&utm_medium=ssp&utm_campaign=yssp_art)

But since it was a data partition you should have been OK with Gparted. (Remember the 150% rule!)

Maybe study: [http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

But I got especially frustrated when you just wouldn't listen to me!

I'll bet you never did try running a simple:

```
sudo apt-get autoclean
```

to try and clean up Ubuntu!

```
sudo apt-get clean
```

would even go a step further (dumping old .deb files) but you reject every reasonable offer to solve this problem.

End rant!

---

