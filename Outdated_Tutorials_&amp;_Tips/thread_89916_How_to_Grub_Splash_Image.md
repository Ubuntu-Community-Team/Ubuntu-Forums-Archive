---
title: "How to: Grub Splash Image"
date: 2005-11-13
forum: Outdated Tutorials &amp; Tips
---

### Post by wondering_jew on 2005-11-13
Heres how I added a grub splash image: (with info I gathered from various places)

First you'll probably want to make a backup of the file we are going to be editing so in a terminal type something to the effect of  "sudo cp /boot/grub/menu.lst /boot/grub/menu.lstbak" you could probably name the backup whatever and put it where ever just remember where and what just in case.

Next find your grub splash image (It has to be a *.xpm.gz file)
there are a few at gnome-look.org and grub actually comes with a few located in /boot/grub/splashimages. For simplicities sake I moved the file I downloaded to /boot/grub/splashimages so it could be with its friends and I would always know where to find it.

Then open (as root) /boot/grub/menu.lst in the text editor of your choosing
in my case this was "sudo vim /boot/grub/menu.lst"  Then I added the line
"splashimage=(hd0,0)/boot/grub/splashimages/myfilename.xpm.gz" at almost the very beginning of the file, mine looked like this:

```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.
splashimage=(hd0,0)/boot/grub/splashimages/grubuntu.xpm.gz

```

*note* I used (hd0,0) because I boot from hda1 if you boot from hda6 for example this would be (hd5,0) should you be in doubt scroll down in menu.lst until you see the kernel options and look for a line that says "root" and use whatever it tells you on that line. 

I also found the option that turns on hidden menus (so you have to push esc to see it) and deleted the uncommented line that only reads "hiddenmenu" since I did this before I knew it worked I'm not sure if its necessary but from my experience it doesn't hurt anything.

Then I saved my changes restarted and it worked.

---

### Post by ubuntu_demon on 2005-11-14
I wrapped code-tags around the beginning of your menu.1st to prevent emoticons.

This is about how to create the image :
[http://www.tldp.org/LDP/LG/current/jayanth.html](http://www.tldp.org/LDP/LG/current/jayanth.html)

---

### Post by frodon on 2005-11-14
Additional informations : [http://ubuntuforums.org/showthread.php?t=30341](http://ubuntuforums.org/showthread.php?t=30341)

---

### Post by bored2k on 2005-11-14
The GUI way: 
[LIST]
[*]Grubconf.
[http://rapidshare.de/files/7628940/grubconf_0.5.1-4ubuntu2_i386.deb.html](http://rapidshare.de/files/7628940/grubconf_0.5.1-4ubuntu2_i386.deb.html)
[*]BUM. [http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)
[/LIST]

Splash images: [http://www.schultz-net.dk/grub.html](http://www.schultz-net.dk/grub.html)

---

### Post by NeoChaosX on 2005-11-14
Another good GRUB image is [this one](http://gnome-look.org/content/show.php?content=29985), which matches the Usplash theme.

---

### Post by Ali_Taimur on 2005-11-14
Here is one for kubuntu

---

### Post by Greeface on 2005-11-14
I believe you can just put the file named 'splash.xpm.gz' in /boot/grub and do a 'update-grub' in the terminal and it will find it and do it for you.

---

### Post by throntax on 2005-11-15
Im also pretty sure Gimp 2.2 has the .xpm file format available as a save option, so you could make your own or alter existing ones... neato!

---

### Post by james4e on 2005-11-15
[QUOTE=wondering_jew]

*note* I used (hd0,0) because I boot from hda1 if you boot from hda6 for example this would be (hd5,0) should you be in doubt scroll down in menu.lst until you see the kernel options and look for a line that says "root" and use whatever it tells you on that line. 
[/QUOTE]

There is a mistake. if you boot from hda6, you should use (hd0, 5) instead of (hd5,0)!

---

### Post by frodon on 2005-11-15
[QUOTE=throntax]Im also pretty sure Gimp 2.2 has the .xpm file format available as a save option, so you could make your own or alter existing ones... neato![/QUOTE]It's explain in the link i gave in post 3 ;)

---

### Post by Biased turkey on 2005-11-16
Just changed my grub splash on my computer at work ( I have a secret drive so my boss doesn't know I run Linux durong my lunch time )
I replaced the original image with the Grubuntu one.
Everything went smoothly.
Thanks for that tip wondering_jew.
The Grubuntu splash image really looks nice.
That encourages me to create my own boot splash image: A pint of foamy dark brown Guinness beer or Newcastle Brown Ale , that should perfectly match the brown color of Ubuntu.
P.S. In case you didn't guess,I'm a homebrewer. I declare the Newcastle Brown Ale being the "official" beer of Ubuntu, it's healthier than Redbull full of cafeine.

---

### Post by ashrack on 2006-01-15
Aren't GNOME SYSTEM TOOLS suppose to have the graphical support for bootloaders:
> Cross-platform configuration utilities for GNOME
The GNOME System Tools are a fully integrated set of tools aimed to make easy
the job that means the computer administration on an UNIX or Linux system.
They're thought to help from the new Linux or UNIX user to the system
administrators.

Its main advantages are:
 * Full integration with the new GNOME Control Center.
 * An user-friendly interface to carry out the main administration tasks.
 * The use of a common user interface in every system.
 * A common structure that makes easy the development of new system tools.
Nowadays there are tools for managing:
 - Users and groups
 - Date and time
 - Network configuration
 [COLOR="Red"]- Bootloaders[/COLOR]

---

### Post by ghostcom97 on 2006-01-16
[QUOTE=Greeface]I believe you can just put the file named 'splash.xpm.gz' in /boot/grub and do a 'update-grub' in the terminal and it will find it and do it for you.[/QUOTE]
This is true - there's no need of editing the grub config with any fancy gui tools. Just copy the desired *.xpm.gz file to /boot/grub/splash.xpm.gz and run ```
sudo update-grub
```.
Then grub vill add the needed config stuff to the menu.lst

---

### Post by noob_Lance on 2006-01-16
the image that is going to be the splashscreen... does NOT have to me a .gz file... i have used a normal 14 color .xpm file for the last week or so and it never gives me any trouble..

---

### Post by ki2 on 2006-05-17
Hi,
Thanks for your reply
1. I could create a folder in /dev/grub/images  but I cannot copy my image file there " Error writing to this folder- you don not have permissions" so my image file is on the /desktop/images
How can I write to the image folder and change permissions
and 
currently my menu.lst file says:
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
default		4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR="Red"][B]hiddenmenu
[/B][/COLOR]
# Pretty colours
#color cyan/blue white/blue



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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda2 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

what do I change here for HDD ?

[QUOTE=wondering_jew]Heres how I added a grub splash image: (with info I gathered from various places)

First you'll probably want to make a backup of the file we are going to be editing so in a terminal type something to the effect of  "sudo cp /boot/grub/menu.lst /boot/grub/menu.lstbak" you could probably name the backup whatever and put it where ever just remember where and what just in case.

Next find your grub splash image (It has to be a *.xpm.gz file)
there are a few at gnome-look.org and grub actually comes with a few located in /boot/grub/splashimages. For simplicities sake I moved the file I downloaded to /boot/grub/splashimages so it could be with its friends and I would always know where to find it.

Then open (as root) /boot/grub/menu.lst in the text editor of your choosing
in my case this was "sudo vim /boot/grub/menu.lst"  Then I added the line
"splashimage=(hd0,0)/boot/grub/splashimages/myfilename.xpm.gz" at almost the very beginning of the file, mine looked like this:

```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.
splashimage=(hd0,0)/boot/grub/splashimages/grubuntu.xpm.gz

```

*note* I used (hd0,0) because I boot from hda1 if you boot from hda6 for example this would be (hd5,0) should you be in doubt scroll down in menu.lst until you see the kernel options and look for a line that says "root" and use whatever it tells you on that line. 

I also found the option that turns on hidden menus (so you have to push esc to see it) and deleted the uncommented line that only reads "hiddenmenu" since I did this before I knew it worked I'm not sure if its necessary but from my experience it doesn't hurt anything.

Then I saved my changes restarted and it worked.[/QUOTE]

---

### Post by shane2peru on 2006-05-24
This is a great howto!  Thanks for the info.  1.  Can the bootimage be changed to a higher resolution?  It looks cheap on my screen at boot up.  It is better than nothing, but doesn't look professional.  How can I make the boot image a higher resolution?  Thanks!

Shane

---

### Post by autocrosser on 2006-07-04
Here's how I did it--

Installation:

Copy the file ("what-the-name-is".xpm.gz or .xpm) to /boot/grub

Code: sudo cp "what-the-name-is".xpm.gz or.xpm /boot/grub

Then add the following line to your /boot/grub/menu.lst:

Code: sudo gedit /boot/grub/menu.lst (or your favorite editor--nano--kate)

splashimage=(hd1,0)/boot/grub/"what-the-name-is".xpm.gz or .xpm

Change the (hd1,0) if you have a different setup

Then make sure that Grub is updated

Code: sudo update-grub

Enjoy your new Grub Splash

---

### Post by Megatog615 on 2006-07-26
Why does this screw up the menu when I enable the splash? What happens is, the splash image is displayed over top of everything else, and I can't see my selection in the menu, however, I can still see the menu. Is this because the entire image is black except for the center?

---

### Post by Shea7993 on 2009-08-31
Okay this was quite educational, i got to learn how to do something i wasnt exactly looking for lol... Im stil a newb, I got directed here looking for a way to change the splash screen when my linux boots up (much like how I use to edit the wingdoze bootup splash), 
however this method only creates a splash screen for the grub loader when you select your operating system... but what i was looking for (and im sure others too) is how to change the splash loader that comes after the grub loader, just before gnome GUI splash screen (so not that splash either) meh...

Any help?

---

