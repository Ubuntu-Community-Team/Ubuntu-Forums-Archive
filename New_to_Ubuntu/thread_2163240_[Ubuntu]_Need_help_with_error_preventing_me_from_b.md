---
title: "[Ubuntu] Need help with error preventing me from booting into Ubuntu 11.04."
date: 2013-07-17
forum: New to Ubuntu
---

### Post by skaldicpoet9 on 2013-07-17
I have an issue with a Ubuntu 11.04. It seems like it is an issue with the filesystem as I am getting this error:

```

busybody v1.17.1 (ubuntu 1:1.17.1-10ubuntu1) built in she'll (ash) enter 'help' for a list of built in commands.

(Initramfs)

```

The only idea I have at this point is to try running fdisk and seeing if it can repair the error. 

I can't boot into Ubuntu and am afraid that I wont be able to recover from this. I am wondering if worse comes to worse how would I backup my files to an external HDD from the command line?

Thanks for any help in advance

---

### Post by Impavidus on 2013-07-17
Try booting from a live disk. You should be able to make backups of your files that way.

Ubuntu 11.04 is end of life. Instead of trying to solve your problem, I recommend you install a supported version of Ubuntu or one of its lighter flavours.

---

### Post by skaldicpoet9 on 2013-07-17
Are all versions of the Ubuntu .iso Live CDs? I have a copy of Ubuntu 11.10 on a disc, but when I boot the disc it just takes me to a screen with the install/language options. I don't see an option for booting from the disc. 

If I have to is their a simple way to copy my files from the command line to an external HDD? I can reach the command line with the disc, but am not sure how (if at all) to boot into the Live CD.

---

### Post by howefield on 2013-07-17
> **skaldicpoet9 said:**
> I have a copy of Ubuntu 11.10 on a disc, but when I boot the disc it just takes me to a screen with the install/language options. I don't see an option for booting from the disc.

Is this the screen that you see ?

PS. 11.10 is also end of life, but will probably do what you need to access and save your files.

---

### Post by silconsystem on 2013-07-17
Hi there, I recovered from a similar error some time ago, I have a bootable usb stick with Lubuntu and have used it for over two years already, it helped me get out of a lot of situations that I thought would be the end of my OS && files.
Boot the live usb/cd

use the network manager to connect to the internet and use google to search for any errors displayed when you try to boot in the browser
make a mount point in the terminal i.e: sudo mkdir /mount/_**ubuntu**_
mount the partition containing your OS: sudo mount /dev/sd_**x**_ /mount/_**ubuntu**_ 
make it the root directory: sudo chroot /mount/_**ubuntu**_

find threads similar to your problem and mostly you'll find your awnser sooner than you'd expect
If you have boot problems concerning grub/grub2
Theres a great tool called [COLOR=#333333][FONT=Ubuntu] [/FONT][/COLOR][Ubuntu-rescue-remix]("http://ubuntu-rescue-remix.org/")
and a LiveResqueCD (can be used as usb also) with super grub2disk and lots of other tools too

Dont delete partitions until youve tried absolutely everything !! and good luck

*** _**this**_ is the disk and OS fitting to your situation ***

---

### Post by silconsystem on 2013-07-17
[SIZE=2][FONT=system][COLOR=#000000]Hi there, I recovered from a similar error some time ago, I have a bootable usb stick with Lubuntu and have used it for over two years already, it helped me get out of a lot of situations that I thought would be the end of my OS && files.[/COLOR]
[COLOR=#000000]Boot the live usb/cd[/COLOR]

[COLOR=#000000]use the network manager to connect to the internet and use google to search for any errors displayed when you try to boot in the browser[/COLOR]
[COLOR=#000000]make a mount point in the terminal i.e: sudo mkdir /mount/[/COLOR]_**ubuntu**_
[COLOR=#000000]mount the partition containing your OS: sudo mount /dev/sd[/COLOR]_**x**_[COLOR=#000000] /mount/[/COLOR]_**ubuntu**_
[COLOR=#000000]make it the root directory: sudo chroot /mount/[/COLOR]_**ubuntu**_

[COLOR=#000000]find threads similar to your problem and mostly you'll find your awnser sooner than you'd expect[/COLOR]
[COLOR=#000000]If you have boot problems concerning grub/grub2[/COLOR]
[COLOR=#000000]Theres a great tool called [/COLOR][Ubuntu-rescue-remix]("http://ubuntu-rescue-remix.org/")
[COLOR=#000000]and a LiveResqueCD (can be used as usb also) with super grub2disk and lots of other tools too[/COLOR]

[COLOR=#000000]Dont delete partitions until youve tried absolutely everything, dont panic and make hasty decisions, take your time to read what the errors may imply !!
google is your best friend in these situations, and so is the terminal 
good luck !![/COLOR]

[COLOR=#000000]*** [/COLOR]_**this**_[COLOR=#000000] is the disk and OS fitting to your situation ***[/COLOR][/FONT][/SIZE]

---

