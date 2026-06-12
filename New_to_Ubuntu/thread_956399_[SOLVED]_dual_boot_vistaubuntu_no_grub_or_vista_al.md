---
title: "[SOLVED] dual boot vista/ubuntu no grub or vista all of a sudden"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by dartdc97 on 2008-10-23
hello all i am very new to ubuntu and dual booting.  i succeeded in the dual boot process by partitioning my 260GB HD using vista, and installing ubuntu in the new 15 GB partition with an ubuntu cd that i burned from an iso.  everything went smooth and ive been trying to become more familiar with the linux environment without ruining my vista partition. i use GRUB to do the booting, and that was going well also until my last restart.  i was in vista and i just finished loading visual studio for school.  after restarting, GRUB did not load and ubuntu was automatically loaded.  i am in dire need of help to understand why this is happening.  i NEED to get back into vista and dont know why or how this happened.  ive tried restarting 4 times and each time theres is just a black screen until the ubuntu sign in screen loads.  help please! i dont mind using GRUB to bootload, but i would like to know where it went.  i would also like to know why after a few restarts and updates, more versions of ubuntu loaded themselves onto GRUB without me knowing how they got there, or how to remove them.  ( mind you this is before GRUB stopped working)  any help is greatly appreciated!!   :confused:

---

### Post by FutanariKitty on 2008-10-23
Well, a few things first.

The 'other' versions of Ubuntu are not what you may think they are, they are just newer versions of the kernel, the chunk of code that sits between your software and hardware. Getting up-to-date kernels is always a good thing, so don't fret about that. They only take up a few megs of space total as it is, and having an older backup around just in case the newer one breaks compatibility is wise.

Second, if you're getting into Ubuntu and haven't explicitly changed your bootloader, you can be quite sure that GRUB is still there doing just what it's supposed to do. In Ubuntu, GRUB is set to automatically load whatever OS is default (normally Ubuntu). The only way around this is to press Escape when prompted just after your POST tests. You should see a prompt saying something to the effect of "Press 'Esc' to enter menu...' with about a 3 second countdown timer.

You said you're getting nothing but a black screen? No Ubuntu progress bar, or even GRUB messages? Peculiar to say the least. The lack of video output until the login screen could be a framebuffer issue...

Could you post your system specs, and the output of /boot/grub/menu.lst? If I can't help, then someone more knowledgable could aid you with a bit more info.

---

### Post by philinux on 2008-10-23
If ubuntu is loading then grub is doing it if you haven't changed anything.

Reboot but this time after the mobo splash screen hit the esc key to pause grub.

---

### Post by garyed on 2008-10-23
It sounds like your grub menu got hidden.
When booting up get there should be a flash "grub loading" accross the screen 
& if you hit "esc" that should get you to the menu. It sounds like you need to edit your /boot/grub/menu.lst file. Two things need to be checked.

hiddenmenu  ( should have a "#" sign in front of it.)
timeout 10 ( or any number for the amount of seconds you want to delay the menu)

---

### Post by dartdc97 on 2008-10-23
permission denied when i type /boot/grub/menu.lst

and there is absolutely no splash screen on shutdown/ restart until ubuntu login screen.  no memory check or original loading screen saying hit F1 or F12 for boot option anymore.

BTW thank you for such quick responses!

---

### Post by Bartender on 2008-10-23
Another thing to try - I have no idea if this will work but can't see the harm.  There's a point-and-click interface for managing which OS starts up called Start-Up Manager (SUM).  

So you're in Ubuntu.  Start up Synaptic Package Manager, type start-up manager into the search window.  You have to be online, of course.
And maybe someone can correct me if that's not the exact term for the application.  Sometimes Synaptic won't find what you're looking for if you don't type it accurately.

Lots of google hits on this.  here's one.
[http://vhxn.wordpress.com/2008/10/11/use-startup-manager-to-edit-boot-menu-in-ubuntu/](http://vhxn.wordpress.com/2008/10/11/use-startup-manager-to-edit-boot-menu-in-ubuntu/)

Once you've got SUM installed, go into it and tell it you want Vista to boot first.  Then reboot and we'll hope that Vista starts for you.  I have no idea why you're not seeing the GRUB Stage 1 screen.  You may have to try repairing GRUB, something I'm not familiar with but thousands of posts on the subject and it doesn't sound very difficult.

EDIT:  try   sudo /boot/grub/menu.lst
EDIT #2:   if you NEED Vista and Ubuntu is just an experiment, also try repairing the Vista MBR.  This will make Ubuntu unbootable but at least Vista should work again.  Lots of posts on this too - it's not hard.  I've never used the Super Grub Disk but supposedly that lets you fix the MBR.  Then you could always try re-installing Ubuntu at a later date.

---

### Post by dartdc97 on 2008-10-23
permission denied when typing /boot/grub/menu.lst line

yea im quite confident that i will be able to load vista somehow, but that doesnt help me with the GRUB problem.  its very strange that there is absolutely no video until the login.  i just did a restart and as i did i pressed escape, and ubuntu did not load, but the screen stayed black, as if the writing was on the wall, but i couldnt see it.  because not until i hit enter after about 2 minutes of black screen did the login finally load

edit: after typing: sudo /boot/grub/menu.lst
command not found

---

### Post by philinux on 2008-10-23
Just to clear things up.

Its startupmanager and it's in synaptic or open a terminal from apps/ accessories.

sudo apt-get install startupmanager

you run it from system>admin menu

tick the box to show text during start up. and show the splash screen

also its'

gksudo gedit /boot/grub/menu.lst

---

### Post by Duck2006 on 2008-10-23
To view the menu'lst in the terminal.

cat /boot/grub/menu.lst

To edit the menu.lst

gksudo gedit /boot/grub/menu.lst

Some info on grub.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by dartdc97 on 2008-10-23
ok typed: cat /boot/grub/menu.lst
got this:

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
timeout		15

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=4550ab26-394f-4172-ba27-271e3b7dbde2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
# defoptions=quiet splash vga=786

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=4550ab26-394f-4172-ba27-271e3b7dbde2 ro quiet splash vga=786
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=4550ab26-394f-4172-ba27-271e3b7dbde2 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-server
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-server root=UUID=4550ab26-394f-4172-ba27-271e3b7dbde2 ro quiet splash vga=786
initrd		/boot/initrd.img-2.6.24-19-server
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-server (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-server root=UUID=4550ab26-394f-4172-ba27-271e3b7dbde2 ro single
initrd		/boot/initrd.img-2.6.24-19-server

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4550ab26-394f-4172-ba27-271e3b7dbde2 ro quiet splash vga=786
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4550ab26-394f-4172-ba27-271e3b7dbde2 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

john@Toshiba:~$

---

### Post by garyed on 2008-10-23
Try this ( you'll have to enter your password after the command)
In terminal: ```
 sudo cp /boot/grub/menu.lst /boot/grub menu2.lst
```
That just makes a backup of you current menu.lst.
Then do:
```
 gksudo gedit /boot/grub/menu.lst 
```
Look for a line that says " hiddenmenu " & put a "#" sign in front of it
Then look for a line that says "timeout " it should be followed by a number
" timeout 10 " would mean show the menu for 10 seconds before going into the default OS. Put whatever number you want after "timeout".

I just saw your menu.lst & don't think my suggestion will help.
One other thing you can try is change 
"default  0" to  "default  8" 
to see if that gets you into Vista.

Then save the file & reboot. 
Good luck

---

### Post by dartdc97 on 2008-10-23
does anyone have an idea as to where my mobo splash screen went?  so if i change this value to 8 instead of 0, it might load vista as the default OS, but then how would i ever boot back into ubuntu?  i still wont have an accessible bootloader, or anything but black screen until vista, or whatever will load, loads:confused:

---

### Post by philinux on 2008-10-23
Like I asked before try pressing the esc key at boot up. This should pause grub and give you it's menu of boot choices.

---

### Post by garyed on 2008-10-23
There's some good tutorials on reinstalling grub which might work & save you some headaches if you can't find the answer to your problem.   
I'm pretty much of a novice myself but I've had to mess with grub & menu.lst a few times so I hoped I could help.

---

### Post by dartdc97 on 2008-10-23
> **philinux said:**
> Like I asked before try pressing the esc key at boot up. This should pause grub and give you it's menu of boot choices.
well yes i tried that but like i said earlier i still just get a black screen, and if i hit escape during that time before ubuntu login screen, it would pause the loading, im guessing, because i can only see black.  it seems as though hitting esc does just that, but i cannot visually see it. 
so when ubuntu loaded i used the start up manager and checked the show splash and text options, chose vista as my default OS, and now Vista loads after the black screen.  so still no GRUB, and now vista loads, but i have no clue how i would go about booting into ubuntu lol due to the black screen until vista loads.  no mobo splash, no nothing.

---

### Post by philinux on 2008-10-23
Ok so thats cleared that up. How it got like this I've no idea.
Ok try this. Reboot and press esc as before. At the black screen press the up arrow a few times then press enter. See what boots. I know its a shot in the dark, no pun intended.

---

### Post by dartdc97 on 2008-10-23
haha yes it is a shot in the dark.  since i used start up man. to assign vista as default, i get the black screen until vista loads.  in the dark right after reboot, i press escape, hit down 3 times (as per old GRUB format i should be highlighting an ubuntu kernel) and hit enter.  it takes some breaths and loads vista.

---

### Post by FutanariKitty on 2008-10-23
> **dartdc97 said:**
> haha yes it is a shot in the dark.  since i used start up man. to assign vista as default, i get the black screen until vista loads.  in the dark right after reboot, i press escape, hit down 3 times (as per old GRUB format i should be highlighting an ubuntu kernel) and hit enter.  it takes some breaths and loads vista.

You know, if you can get into Vista, perhaps you should look into updating your BIOS. The video failure in such a way is bizarre, and likely not OS related in the slightest.

---

### Post by razerbug on 2008-10-23
I tri-boot Vista, Hackintosh and Ubuntu studio, with Vista as my primary. Although I've got these on different HDD's (for exactly this reason, need to protect my proper windows PC)

but I found out of all of them the Vista Boot Loader works the best. 

If you can get back into Vista (and I would recommend interrupting you're BIOS loading at start up and booting the vista partition to do this -if it lets you- ) try EasyBCD which is a free program for windows and comes with preset OSx and Linux boot configs.

Worked fine for me with OSx - although there are two ways to boot linux with and without grub, so takes a bit of playing with.

---

### Post by dartdc97 on 2008-10-23
> **FutanariKitty said:**
> You know, if you can get into Vista, perhaps you should look into updating your BIOS. The video failure in such a way is bizarre, and likely not OS related in the slightest.

well kitty you hit it on the head first post.  good job!  after loading into vista i realized that i had a serial cable connection from a dual display and decided to check video card settings.  i re-enabled my second display and then disabled it making sure laptop display was the primary.  rebooted and there it was! i never rebooted with the second display on but im willing to bet if i did GRUB would have been displayed. everyone was a great help though i definitely learned a thing or two.

---

### Post by FutanariKitty on 2008-10-24
Fantastic! Glad to be of service.

You wouldn't believe how many times I've done similar things toying with multiple displays with finnicky BIOSes.

---

### Post by errold32 on 2008-11-28
Thanks for this post, I whas having the same problem. I fixed it by setting the multiple display option in my bios to use the internal laptop screen on boot.

---

