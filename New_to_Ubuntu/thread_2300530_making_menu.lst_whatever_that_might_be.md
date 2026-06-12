---
title: "making /menu.lst whatever that might be"
date: 2015-10-26
forum: New to Ubuntu
---

### Post by lazaros2 on 2015-10-26
Okay guys , this post will let you in to what my situation is : [http://www.rmprepusb.com/tutorials/125](http://www.rmprepusb.com/tutorials/125) .
I am trying to create a dual partition USB in which the one partition is persistent Ubuntu and the other one is a YUMI multiboot one, from which I can launch programs like SeaTools and Parted MAgic and Memtest( .iso's ).
So I've done everything this post asks me to do, and then I got to that damned "make /menu.lst). No idea how to do that . Help please.

Things to keep in mind :
1)I am a COMPLETE noob when it comes to Ubuntu, so any help will have to be as thorough as possible.
2)There is no option in YUMI that would allow me to install Persistent Ubuntu, therefore I will/would be skipping Step 2 and instead  I will/would install Ubuntu as persistent via a CD. Not sure if that changes anything.

Thanks in advance!

---

### Post by grahammechanical on 2015-10-26
It is as the tutorial says: "that's it." Tutorials always says something like that without explaining what was done.

After installing grub4dos you go to you edit a file called menu.lst. A text editor should be able to do it. The file will be found a \menu.lst. This is grub4 dos not grub4linux so it is the back-slash ( \ ) not the forward slash ( / ).

And you edit according to the pattern shown.
> 
[FONT=arial][COLOR=#0000FF]itle Boot to Partition 1\n Run syslinux from partition 1[/COLOR][/FONT] [FONT=arial][COLOR=#0000FF]root (hd0,0)[/COLOR][/FONT]

 [FONT=arial][COLOR=#0000FF]chainloader (hd0,0)+1[/COLOR][/FONT]

 [FONT=arial][COLOR=#0000FF]boot[/COLOR][/FONT]

 [FONT=arial][COLOR=#0000FF]
[/COLOR][/FONT]
 [FONT=arial][COLOR=#0000FF]title Boot to Partition 2\n Run syslinux from partition 2[/COLOR][/FONT]


 [FONT=arial][COLOR=#0000FF]root (hd0,1)[/COLOR][/FONT]


 [FONT=arial][COLOR=#0000FF]chainloader (hd0,1)+1[/COLOR][/FONT]


 [FONT=arial][COLOR=#0000FF]boot[/COLOR][/FONT]




Or you mess around with editing menu.lst until it works the way you want.

Regards.

---

### Post by lazaros2 on 2015-10-26
Okay, to begin with thank you for your reply. Given you probably understand very well what I am doing, I will ask some more questions:
The Grub4dos file, that I created via RMPrepUSB , was created/made when I was on Partition1 , which will eventually be the Ubuntu partition. The other partition, Partition2, is the one in which I will be running all of my utility programs. In P2 , I have already run YUMI and installed Memtest86, while in P1 I have done nothing but install Grub4dos. Therefore, right now , P1 only has a grldr file in it, while partition 2 has these files : [http://imgur.com/DYojMHO](http://imgur.com/DYojMHO)  .
I am guessing the \menu.lst file will/should be located in the partition that I created Grub4dos in?
I really dont know where to look for \menu.lst.
Also, do I need to install Grub4dos in both partitions or only the one?
Also, does it matter that I have not run YUMI in P1? I know YUMI makes the multiboot file which I think(?) is needed, but then again I also understand Grub4dos is something independent from YUMI? 
I am really confused, sorry for asking so many things.

---

### Post by oldfred on 2015-10-26
Not answering your specific issue, but suggesting alternatives.

I consider grub4dos the last boot loader I might attempt to use. It is based on the legacy grub and not well maintained. It will not work with newer UEFI based systems.

Ubuntu's live installer uses two different boot loaders. It uses syslinux for BIOS boot and grub2 for UEFI boot. And grub2 is the default boot loader for the actual install of Ubuntu whether UEFI or BIOS.

With my larger flash drives I do a full install of Ubuntu and then have a data partition with several ISO that I can directly boot/loopmount from the grub2 installed with the full install. That is just like a hard drive ISO boot, several links below.
With smaller flash drives I just install grub2 directly to flash drive and manually create a grub.cfg to loopmount the ISO. With grub2 the grub.cfg has replaced the menu.lst of grub legacy & has a somewhat different configuration. 

       This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
[URL="https://wiki.archlinux.org/index.php/Multiboot_USB_drive"]https://wiki.archlinux.org/index.php/Multiboot_USB_drive
[/URL]
 Tools for booting ISO
[http://ubuntuforums.org/showthread.php?t=2289225](http://ubuntuforums.org/showthread.php?t=2289225)
Not ISO boot, uses syslinux - sudodus
     One pendrive for all PC (Intel/AMD) computers
[http://ubuntuforums.org/showthread.php?t=2259682](http://ubuntuforums.org/showthread.php?t=2259682)
UEFI & BIOS & Live installer
[URL="http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506"]http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506
[/URL]
 Multiboot flash drive with second partition 
[http://ubuntuforums.org/showthread.php?t=2260697](http://ubuntuforums.org/showthread.php?t=2260697)

There now are many scripts to create multiboot flash drives.
These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
[https://sourceforge.net/projects/multibootusb/files/](https://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
[http://ubuntuforums.org/showthread.php?t=2175738](http://ubuntuforums.org/showthread.php?t=2175738)
Uses grub4dos to boot many ISO and other bootable files
[http://www.rmprepusb.com/tutorials/72---easyboot---a-grubdos-multiboot-drive-that-is-easy-to-maintain/e2bv1](http://www.rmprepusb.com/tutorials/72---easyboot---a-grubdos-multiboot-drive-that-is-easy-to-maintain/e2bv1)
Another: multiboot055.sh
[http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/](http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/)
See yumi for multi-boot versions
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-via-grub2-using-linux/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-via-grub2-using-linux/)
[URL="https://wiki.archlinux.org/index.php/Multiboot_USB_drive"]
[/URL]

---

### Post by yancek on 2015-10-26
menu.lst is simply a text file which will be located in the /boot/grub directory and which you create with a text editor.  Examples are posted in the site you linked to so you would need to modify to suit your needs.

If you can't create persistence with YUMI, use something that will do the job.  Unetbootin will and I believe pendrivelinux will but have never used it myself.

You might be better off doing an actual install of Ubuntu on one partition as suggested and either adding another partition with whatever tools you want or putting them on the same partition.  Doing that will give you a grub.cfg file to which you can add entries and/or update-grub.  You should be able to boot Linux utilities from the first partition if they are on the second but you could probably put it all on one partition.

---

### Post by Mike_Walsh on 2015-10-26
I'm going to set myself at odds here with the vast majority of the Ubuntu membership, most of whom are very comfortable messing around with, and reconfiguring, GRUB2.

As you see from my sig, I run 'Puppy Linux' as dual-boot, together with Xubuntu 14.04.3 LTS. Now, in Xubuntu, I do a straight forward install; but when I've added Puppy to the mix, I use the Grub4DOS boot configuration tool, that has been supplied as standard with every Puppy that's ever been released.....all the way back to version 1!

Rather than try to edit GRUB2, to add a stanza for booting Puppy (I **hate **GRUB2...sorry!) I use Grub4DOS to create a multi-boot menu which will allow me to choose what I boot into. The way it's been configured for Puppy, it's a GUI-based affair, that is point-and-click all the way through. It finds **everything** that's installed, no matter **what** it is, and creates an editable list of boot entries for you.

In contradiction of [COLOR=#ff0000]oldfred[/COLOR]'s assertion that Grub4DOS is unmaintained (which, to be fair, I think he is correct about.....in **[COLOR=#000000]general usage[/COLOR]**), the Puppy version **is** maintained by our extremely active community, and is perfectly safe to use. I've no wish to offend oldfred; the man is a fount of wisdom when it comes to GRUB issues (I have myself benefited from his advice on more than one occasion).....and he **has** provided an extensive list of links for you to look through.

I would have to review a few of my own boot entries (at the last count, I'm currently running no fewer than five 'Pups'), but I think there ought to be a way to achieve what you want, if you wish to use Grub4DOS.....something along the lines of that which [COLOR=#ff0000]grahammechanical[/COLOR] has outlined for you. 

The 'menu.lst' file is a standard part of Grub4DOS, as [COLOR=#ff0000]yancek[/COLOR] has explained. (That's a small 'L', not a '1'..!)

Of course, you may decide you wish to be guided by the suggestions of our Ubuntu community, since the version of Grub4DOS which you would have to use here is not the maintained 'Puppy' version.

---------------------------------------------------------------------------------------------------------------

EDIT: I would hazard a guess that maybe a few members of the community are perhaps getting a wee bit fed up of my constant 'banging on' about 'Puppy' at every opportunity.....but I honestly believe it to be the most easy-to-use, newbie-friendly (and powerful!) small, lightweight, and well-supported Linux distro out there today. And the majority of recent releases are based on 'buntu binaries **anyway**. I remain **totally** unrepentant..! :D 

And as for my use of Grub4DOS, it is oft-quoted in these very same  forums (paraphrase):-

'....use whatever works for you...'

I rest my case.\\:D/


Regards,

Mike. :)

---

### Post by lazaros2 on 2015-11-01
Well, thank you all for your help, I managed to do this using grml-rescueboot ([https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)) . You've all been a real help guys, I am grateful! Cheers!

---

