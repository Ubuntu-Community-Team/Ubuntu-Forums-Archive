---
title: "[SOLVED] GRUB menu gone, replaced by terminal!"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by nathanscottdaniels on 2008-08-26
GAH!  So much for user-friendly! I did one of the many daily updates and it asked me to restart and I did but when I came to where it would ask Ubuntu or XP, it was a black terminal looking screen with an explanation of what the Tab key does.  So my guess is my GRUB's menu.lst is gone and I never made a backup. I have the ever-useful Live CD to do stuff if needed.  Please help.

---

### Post by Pa100ka on 2008-08-26
Don't know if this will help, but just in case...

I installed Ubuntu (8.0.4) with my USB hard drive unplugged - to persuade the installer to use my internal hard disk. Afterwards I plugged the USB drive in and all was hunky dory. However, when I came to reboot, all I got was GRUB_ on a black screen. I shut down, unplugged the USB drive, restarted again and all was well. I can plug in the (NTFS) USB drive and it auto mounts perfectly. It is a mystery to me why GRUB won't work with it.

Pa100ka

---

### Post by nathanscottdaniels on 2008-08-26
Sorry, that doesn't really apply to me.

---

### Post by caljohnsmith on 2008-08-26
Do you have more than one HDD? From your Live CD, please post the output of:
```
sudo fdisk -lu
```
Find your Ubuntu partition in the form sdXY, and then do:
```
sudo mount /dev/sdXY /mnt
cat /mnt/boot/grub/menu.lst
sudo grub
grub> find /boot/grub/stage1
grub> quit
```
And post the results.

---

### Post by nathanscottdaniels on 2008-08-26
> **caljohnsmith said:**
> Do you have more than one HDD? From your Live CD, please post the output of:
```
sudo fdisk -lu
```
Find your Ubuntu partition in the form sdXY, and then do:
```
sudo mount /dev/sdXY /mnt
cat /mnt/boot/grub/menu.lst
sudo grub
grub> find /boot/grub/stage1
grub> quit
```
And post the results.

One HDD

I cant copy and paste the terminal output because my laptop requires bootleged drivers to connect to the internet which I can't get on a Live CD

fdisk -lu: (minus start and end columns because I don't feel like typing that much)
```

Device    Boot      Blocks    ID   System
/dev/hda1 *        63681660    7   HPFS/NTFS
/dev/hda3           9767520   83   Linux
/dev/hda4           1851897+  82   Linux swap/ Solaris

```

I ran the above code but no joy, still only seeing the terminal-like screen when I reboot.

---

### Post by -Zeus- on 2008-08-26
from the live cd, open a terminal and try this;

```
/:$ sudo grub
grub> root (hd0,2)
grub> setup (hd0)
grub> exit
```

If you reboot, it should be fixed.  Then, open your /boot/grub/menu.lst and add this at the bottom

```
title     Windows
root      (hd0,0)
makeactive
chainloader +1
```

Now you can boot to windows

---

### Post by nathanscottdaniels on 2008-08-26
> **-Zeus- said:**
> from the live cd, open a terminal and try this;

```
/:$ sudo grub
grub> root (hd0,2)
grub> setup (hd0)
grub> exit
```

If you reboot, it should be fixed.  Then, open your /boot/grub/menu.lst and add this at the bottom

```
title     Windows
root      (hd0,0)
makeactive
chainloader +1
```

Now you can boot to windows

Nope that didn't work either.  

Is there a way to boot from the GRUB terminal screen when I turn the laptop on?  Typing 'boot' says the kernel isn't loaded and I don't know how to load the kernel.

---

### Post by caljohnsmith on 2008-08-26
> **nathanscottdaniels said:**
> Nope that didn't work either.  

You need to give more details if you want help. So what exactly doesn't work--do you see the Grub menu on startup yet? Do you get any Grub errors?

---

### Post by nathanscottdaniels on 2008-08-26
> **caljohnsmith said:**
> You need to give more details if you want help. So what exactly doesn't work--do you see the Grub menu on startup yet? Do you get any Grub errors?

Sorry.

Alright, from the beginning.
[LIST]
[*]I install a bunch of the random daily updates from the update manager.  Everything went by as usual...
[*]...except for the fact that this time, there was a little icon in the status area saying I need to restart to finish the updates
[*]I restarted
[*]After BIOS and POST screens, my GRUB menu normally comes up with a list of operating systems for me to choose.
[*]However, this time, the menu did not come up.  Instead, a black screen with white text did and the exact text on that screen said:
[*]```
[ Minimal BASH-like line editing is supported.  For the
first word, TAB lists possible command completions.  Anywhere
else, TAB lists the possible completions of a device/filename.]

grub>
``` 
[*]which led me to describe it as terminal-like because I can type commands after grub>
[*]I got to my Vista desktop and search for help on Yahoo!
[*]Giving up, I come here and ask for help.
[*]I hunt down and dust off my Live CD
[*]After trying everything aforementioned, I am still in the exact same situation as before my original post (i.e. no GRUB menu, same terminal-like screen...)
[/LIST]

---

### Post by caljohnsmith on 2008-08-26
When you get the grub CLI on startup, try this:
```
grub> find /boot/grub/menu.lst
```
That should return (hd0,1), if it doesn't use whatever it returns, but let me know:
```
grub> cat (hd0,1)/boot/grub/menu.lst

```
So does the above command show you your full menu.lst? Also, please post your complete menu.lst back here so we can make sure there is nothing wrong with any of it. If you need to, you can follow my directions from post #4 to print your menu.lst from the Live CD so you can simply copy and paste it.

Also on startup, in the grub CLI, try:
```
grub> root (hd0,0)
grub> makeactive
grub> chainloader +1
grub> boot
```
Does that boot Windows?

---

### Post by nathanscottdaniels on 2008-08-26
1st command returned (hd0,2)

2nd command does show full menu.lst as well as change the colors form blue background to cyan foreground.

3rd command: HOLY CRAP Windows loaded! 

menu.lst: (I used a thumb drive this time)

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
default		1

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=fa46339e-7640-4d10-8172-cd647ae926a9 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false
```

I see a lack of operation system lists in that file.

---

### Post by caljohnsmith on 2008-08-26
OK, it's starting to make alot more sense now. Basically you don't have any entries for any operating systems in your menu.lst. :) Please do the following from the Live CD:
```
sudo mount /dev/sda3 /mnt  [COLOR="Blue"][note it may be hda3 instead of sda3, use what works][/COLOR]
gksudo gedit /mnt/boot/grub/menu.lst &
```
First change the "groot (hd0,0)" to "groot (hd0,2)". Then do the following:
```
sudo blkid | grep sda3
ls -l /mnt/boot
```
That will show your sda3 partition UUID, and also show all your kernel files. Then at the bottom of the menu.lst file, add:
```

title		Ubuntu
root		(hd0,2)
kernel		[COLOR="Blue"]/boot/vmlinuz-2.6.24-19-generic [/COLOR]root=UUID=[COLOR="Blue"]77677cb5-6e56-4936-a373-80c15de06bca[/COLOR] ro quiet splash
initrd		/boot/[COLOR="Blue"]initrd.img-2.6.24-19-generic[/COLOR]
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows
root (hd0,0)
makeactive
chainloader  +1
```
Replace the blue entries above with whatever is the latest kernel in your /boot directory that you listed above, and also replace the UUID with your own UUID for sda3. That should hopefully work.

---

### Post by nathanscottdaniels on 2008-08-26
OMG That worked!  Thank You!  What do you think caused my os list to vanish?

---

### Post by caljohnsmith on 2008-08-27
> **nathanscottdaniels said:**
> OMG That worked!  Thank You!  What do you think caused my os list to vanish?
Glad you're up and running again. :) I'm not sure what caused all your OS entries to get deleted in the menu.lst, but I would recommend making a backup of that menu.lst in case it happens again. Also, just for completeness and if you haven't done it all ready, I would add the "recovery mode" and "memtest86+" options to your menu.lst (or at least the recovery mode, as that can save you sometimes):
```

title		Ubuntu (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=77677cb5-6e56-4936-a373-80c15de06bca ro [COLOR="Blue"]single[/COLOR]
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

```
In other words, copy over whatever Ubuntu entry is working for you right now (has the correct kernel, initrd.img and UUID), remove the "splash" and "quiet" options from the kernel line, and replace them with "single". 

And lastly, to make a backup of that menu.lst:
```
cp /boot/grub/menu.lst /boot/grub/[COLOR="Blue"]menu.lst.082708[/COLOR]
```
Or name the copied file whatever you want; I usually just attach a date like above.

---

