---
title: "[SOLVED] where did this extra operating system come from?"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by adamogardner on 2008-05-30
Compound problem:   I have  asierra wireless aircard AC595U from verizon; questions 1, I'm trying to virtual box in order to get this broadband connection in my Ubuntu partition. Is this the correct avenue,  how do I properly install Virtual box?   question 2;  Some error to install something with the kernal (generic) did not work so I tried the "server" package from Synaptic P-mananger and it installed this fuzzy server version of ubuntu that has poor resolution.  It doesn't shut down and I want to know why is this here and I have 3 operating systems to boot? How do I not let this happen again. How do I eliminate this third operating system?   These questions are all stiched together by a common effort of trying to use Virtual box.  Any help will be great.

---

### Post by adamogardner on 2008-05-30
maybe you should just hang in the windows.  This problem you've been dealing with for 4 weeks isn't going to just go away.  windows is home.  waiting for help with ubuntu will just lead you to further problems and further need for help.

---

### Post by adamogardner on 2008-05-30
yeah thanks for the advice, but I'm totally stoked to learn this operating system and champion it about the world.  Can you help me clarify a solution to my specified problem?

---

### Post by timcredible on 2008-05-30
why not run the connection in ubuntu?  this is a wireless broadband connection, right?  if the verizon card is usb, it's super easy to get to work in linux - click on the link in my sig and read the article about verizon wireless broadband.

---

### Post by adamogardner on 2008-05-30
no but maybe someone else can.  Of course your silly posting got shoved into this hole and never made the top of the list on page one  so good luck trying to be heard

---

### Post by adamogardner on 2008-05-30
ok tim will do but your the first person who has said it would be easy
    what about ridding myself of this ghostly OS that appeared in my grub and self loads if i miss the countdown then won't shut down completely so i have to hit the power button?

---

### Post by forestpixie on 2008-05-30
I assume that you have had an upgrade - you will have more than 1 option in your boot menu now - pick an older one and see if you can boot that - then you can edit you menu for the time being.

Installing virtualbox will probably not help to get the net working as it uses the existing one.

Installing the server version is probably not going to help you much.

---

### Post by adamogardner on 2008-05-30
WOW that was easy but now all it says is "dialing..."  I should note that i am currently already connected on some network or another called netgear.  do I need to disable this?  i'm reluctant to try it because I can't always easily get back online.

---

### Post by adamogardner on 2008-05-30
ok so i read the log.. the last line reads.." wv dial err   modem not responding".  translation?

---

### Post by adamogardner on 2008-05-30
n,  tim helped me rule out using virtual box.  I'm close to having the connection but the log showed that it could not work (as I mentioned just above).  yes he GRUB shows me 3 systems to boot.  i started with windows then ubuntu710 (updated yes) then all of a sudden this wacky third party showed up.  once after i shut down my computer an alarm went off louder than i ever heard my computer getfor about 30 seconds (a long time when you don't know whether to take cover or not)  OK so I want to never go into it again.  I just want to dissapear it.  HOW?

---

### Post by forestpixie on 2008-05-30
Once you've booted again - open a terminal and run this command then post the output here

```
cat /boot/grub/menu.lst
```

---

### Post by adamogardner on 2008-05-30
I typed it in (exactly). no such file or directory

---

### Post by forestpixie on 2008-05-30
The l is a L not a 1

---

### Post by wolfen69 on 2008-05-30
if you still cant figure it out, instead of spending hours trying to get it going, spend **1** hour doing a fresh install. alot of problems can be fixed this way.

---

### Post by adamogardner on 2008-05-30
sorry bout the Ell    saw that and 2nd guessed the wrong choice.  I see I just sent stuff about my password.  not sure what it means but I'm sure someone else might.   is this bad?

---

### Post by adamogardner on 2008-05-30
$ cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=b268eb6a-59da-462c-a80d-897b34edbf38 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title           Ubuntu 7.10, kernel 2.6.22-14-server
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-server root=UUID=b268eb6a-59da-462c-a80d-897b34edbf38 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-server
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-server (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-server root=UUID=b268eb6a-59da-462c-a80d-897b34edbf38 ro single
initrd          /boot/initrd.img-2.6.22-14-server

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=b268eb6a-59da-462c-a80d-897b34edbf38 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=b268eb6a-59da-462c-a80d-897b34edbf38 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista/Longhorn (loader)
root            (hd0,1)
savedefault
makeactive
chainloader     +1

---

### Post by forestpixie on 2008-05-30
IF you want to remove the server from there so that you only have the original buntu and win you can comment out the server lines. As you only actually installed the server because you were rtryingto get net working you might be better of uninstalling it. I don't know a whole lot about the server I assume you can remove it how you installed it - through synaptic.

If for the moment you only want to remove it from the list then you can, we can backup it up first. If you're not sure about the command paste them :)

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.3005
gksudo gedit /boot/grub/menu.lst
```

Go to where you have this
## ## End Default Options ## 

put a # at the beginning of the 2 title lines for the server, eg.

#title Ubuntu 7.10, kernel 2.6.22-14-server
 close and save and they won't appear when you reboot.

As far as your password in terminal - if that is the first time you've done it then it doesn't appear as a security measure.

I can't help with the wireless problem unfortunately - but wolfen has a good point, especially if the server install starts top cause problems.

---

### Post by Therion on 2008-05-30
Okay I've read this entire thread but I'm confused by what I'm reading.  Let me see if I understand the situation.

It sounds like you have three separate kernels you can boot to from your GRUB menu ("three OS'es" as you call them).

Do you want to run Ubuntu as the ONLY operating system on your PC, or do you want Ubuntu AND Windows at the same time on the same PC?

I see you are trying to install Virtual Box.  Virtual Box will let you run Windows on a Ubuntu PC, but it doesn't really have anything to do with your broadband connection or your wireless card.

So... Question One:  Do you want to install Ubuntu on your PC and REMOVE Windows entirely?  You could then, if you want, run Windows using Virtual Box.  But the BIG question is... Are you okay with installing Ubuntu as your ONLY operating system and saying goodbye to your Windows install?

---

### Post by adamogardner on 2008-05-30
thanks but we are dealing with a fresh install.  I'm also cautious because I've heard horror stories about a grub error about not recognizing windows (cause I have that too), and The white screen of "why me?"  It took me a great effort to get this sucker working.  I'm well on my way and to freshly install would be last case scenario.

---

### Post by adamogardner on 2008-05-30
no   for the meanwhile I want to keep windows, learn about running windows inside ubuntu and then ultimately getting rid of windows.  but not now.  what  i want to rid myself of is that first kernal listed in the terminal output   the kernal that is followed by (server) there are two listed. one is recovery style  everything else I'd like to keep for now.

---

### Post by adamogardner on 2008-05-30
ok Thankyou all, thankyou forest pixie,  I have come a long way since this morning.

---

### Post by adamogardner on 2008-05-30
but alas, I uninstalled the virtual box but the server kernal is still in the grub menu.  I don't want to follow the directions to hide it because it is still clutter in my system.

---

### Post by forestpixie on 2008-05-30
Uninstall it then - I'm not sure how you installed it in the first place, it would help if you said how you did, I'd like to know before I try and help get rid of it.

Uninstalling virtualbox will have no impact on the kernels you have installed here.

@therion - there are 2 kernels, 1 is server 1 is not and the other os is windows.

---

### Post by adamogardner on 2008-05-30
ok   i started new thread  and i think found my answer there.  so I'm going to say goodbye and please feel free to see how this problem was solved.  (and hopefully it is).

---

### Post by forestpixie on 2008-05-30
I've already seen the other one - you shouldn't really double post ;)

I've been looking and there are a few howto pages aropund for broadcom wireless.

Can you mark this one solved. Good luck.

---

