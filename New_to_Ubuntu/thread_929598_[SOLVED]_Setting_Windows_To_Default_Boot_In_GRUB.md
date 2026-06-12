---
title: "[SOLVED] Setting Windows To Default Boot In GRUB"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by StunnerAlpha on 2008-09-25
Ey guys, I want to change my default boot option to Windows. how do I go about doing this? I looked this up in help and support and it tells me to do this:
grub-set-default[OPTION]entry

But I am not sure what to put in the [OPTION] area for Windows XP.

Any help appreciated, thanks!

---

### Post by kpkeerthi on 2008-09-25
Can you post your grub file?
```
cat /boot/grub/menu.lst
```

---

### Post by Elfy on 2008-09-25
Post your menu list and we can see :)

Run this command in a terminal and post the output

```
cat /boot/grub/menu.lst
```

---

### Post by indytim on 2008-09-25
You would have gotten better results if you had done a search on GRUB default.  

There are many ways to change the default option on the GRUB menu.  Here's a link to a recent thread on the same subject.
[http://ubuntuforums.org/showthread.php?t=927377&highlight=GRUB+default]("http://ubuntuforums.org/showthread.php?t=927377&highlight=GRUB+default").

You can also edit (after making a backup copy) at super user level:
/boot/grub/menu.lst   (that's "l" like in L) file.  It's pretty heavily commented so you should be able to figure it out.

IndyTim

p.s.  I'm glad you at least did a search before posting.. wish more people would do the same

---

### Post by StunnerAlpha on 2008-09-25
```

aaron@T60:~$ cat /boot/grub/menu.lst
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
timeout		10

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
# kopt=root=UUID=96f7c2f8-241c-41ba-bc0c-62fc202ee188 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
# defoptions=quiet splash

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=96f7c2f8-241c-41ba-bc0c-62fc202ee188 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=96f7c2f8-241c-41ba-bc0c-62fc202ee188 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

aaron@T60:~$ 



```

Thanks!

---

### Post by WWSmith36 on 2008-09-25
Try making this edit

```
gksu gedit /boot/grub/menu.lst

```
Change this line
default 0

to
default 3

If that doesn´t work try default 4.  I´m only say this because I don´t know how grub will react to having that blank root statement (not sure if it counts it or not).

---

### Post by Elfy on 2008-09-25
You could change default 0 to default 4

But when you get kernel updates it will need to be changed again, or you could move the whole windows stanza above the automagic line.

In which cut 
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

and move it above the line which reads

> ### BEGIN AUTOMAGIC KERNELS LIST

and leave the default as 0

To backup and edit the file
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.2509
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Elfy on 2008-09-25
@WWSmith36, for your information - any _title_ gets counted by grub

so default 3 would try to boot nothing and 4 would be correct.

---

### Post by StunnerAlpha on 2008-09-25
How do I mark this thread as solved? And of course, thanks for the help guys.

---

### Post by Paqman on 2008-09-25
For future reference, if you don't want to hack the files manually you can just install [startupmanager](apt:startupmanager) to do this for you. It does a lot of other useful stuff, too.

---

### Post by asmoore82 on 2008-09-25
[SIZE="3"]**_[COLOR="Red"]WARNING to ALL!![/COLOR]_**[/SIZE]

I just tested StartupManager on MY Up to Date 8.04 Hardy and it [COLOR="Red"]_fails_[/COLOR] to do this task properly!

check this tread and view my post(#10): [http://ubuntuforums.org/showthread.php?t=688814](http://ubuntuforums.org/showthread.php?t=688814)

(if you read that thread all the way to the end, you will see what StartUpManager fails to do: set the updatedefaultentry option)

:KS

P.S. forestpixie has the right idea as well.

---

### Post by kansasnoob on 2008-09-25
> **Paqman said:**
> For future reference, if you don't want to hack the files manually you can just install [startupmanager](apt:startupmanager) to do this for you. It does a lot of other useful stuff, too.

+1 and then some!

If I read right no one suggested the OP backup their menu list so if the OP hoses it are they going to be around to fix it.

I have what I think is an unpopular opinion: developers spend lots of time building guis to make life easy for the common user! When we choose to ignore their accomplishments we're dissing those developers and at the same time turning people away from Ubuntu because "it's just too hard"!

Just my opinion!

---

### Post by StunnerAlpha on 2008-09-25
> **kansasnoob said:**
> +1 and then some!

If I read right no one suggested the OP backup their menu list so if the OP hoses it are they going to be around to fix it.

I have what I think is an unpopular opinion: developers spend lots of time building guis to make life easy for the common user! When we choose to ignore their accomplishments we're dissing those developers and at the same time turning people away from Ubuntu because "it's just too hard"!

Just my opinion!

Someone mentioned to me that I backup my file before modifying. I followed what that person said about pasting the code for windows above that one line and it works perfectly now.

Not using GUIs is good if the task can be accomplished easier and with less problems than a GUI can offer. I am majoring in Computer Science and don't mind getting "down and dirty" with the system. When there is more support for Ubuntu, sure I see more people moving to it due to ease of use but until then I only really see the computer savvy fellows using/giving it a try.

---

### Post by Paqman on 2008-09-25
> **asmoore82 said:**
> 
(if you read that thread all the way to the end, you will see what StartUpManager fails to do: set the updatedefaultentry option)


Would it have to, given that it also limits the number of kernels? The default number will always be the same.

---

### Post by kansasnoob on 2008-09-25
> **asmoore82 said:**
> [SIZE="3"]**_[COLOR="Red"]WARNING to ALL!![/COLOR]_**[/SIZE]

I just tested StartupManager on MY Up to Date 8.04 Hardy and it [COLOR="Red"]_fails_[/COLOR] to do this task properly!

check this tread and view my post(#10): [http://ubuntuforums.org/showthread.php?t=688814](http://ubuntuforums.org/showthread.php?t=688814)

(if you read that thread all the way to the end, you will see what StartUpManager fails to do: set the updatedefaultentry option)

:KS


P.S. forestpixie has the right idea as well.

I'll have to look into that. Startupmanager is working fine in my 8.10 test partition ............. so well that I haven't been in Hardy since early AM.

---

### Post by kansasnoob on 2008-09-25
> Not using GUIs is good if the task can be accomplished easier and with less problems than a GUI can offer. I am majoring in Computer Science and don't mind getting "down and dirty" with the system. When there is more support for Ubuntu, sure I see more people moving to it due to ease of use but until then I only really see the computer savvy fellows using/giving it a try.

Well, I've brought more than 30 "elderly" folks into the Ubuntu fold (many of whom wer still stuck with win 98 and ME) and they want things to be simple! Point-n-click simple!

I'm not suggesting that command line should be retired, just simply that we embrace the ongoing development of Ubuntu and Linux in general! The development of guis is a large part of that!

Just a difference of opinion I guess.

---

### Post by Paqman on 2008-09-25
> **kansasnoob said:**
> 
I'm not suggesting that command line should be retired, just simply that we embrace the ongoing development of Ubuntu and Linux in general! The development of guis is a large part of that!


Couldn't agree more. The CLI should be an option for anyone that wants it, but you shouldn't have to use it for routine admin tasks.

---

### Post by StunnerAlpha on 2008-09-25
> **kansasnoob said:**
> Well, I've brought more than 30 "elderly" folks into the Ubuntu fold (many of whom wer still stuck with win 98 and ME) and they want things to be simple! Point-n-click simple!

I'm not suggesting that command line should be retired, just simply that we embrace the ongoing development of Ubuntu and Linux in general! The development of guis is a large part of that!

Just a difference of opinion I guess.

The command line is just so powerful and efficient, if you know how to use it, you can shave off loads of time rather than fishing around to get things done via GUI. I semi-agree with you, GUI's should be embraced, but they aren't even close to where they need to be as yet, and until then I am not willing to stick solely to GUIs.

---

### Post by RealG187 on 2008-09-25
I did this just today (family PC and family is Windows noobs)

but yah change the default to the number on the list starting at 0. So for me Windows was the 6th option, so I put 5.

then sudo update-grub

---

### Post by indytim on 2008-09-26
To mark the posting with thanks, the thanks "button" is the little "star" icon on the bottom right.

Good Luck,

IndyTim

---

