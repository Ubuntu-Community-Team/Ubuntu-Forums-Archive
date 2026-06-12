---
title: "boot repair disc,didn't"
date: 2012-11-03
forum: New to Ubuntu
---

### Post by john fox on 2012-11-03
hi folks,
just loaded ubuntu a few days ago on a presario desk top computer with windows xp with a dual boot to ubuntu.
well it didn't dual boot, I downloaded the boot repair  unto a cd, ran the repair disc. after running the repair disc it said everything was fixed, but it wasn't. when I boot up it goes directly to ubunto with no option to go into windows
I made a copy of the address as I was told to, it's.
[http://paste2.org/p/2421920](http://paste2.org/p/2421920)
that was the first address I got, I thought maybe I didn't do something right so I tried a second time and still no joy. but I did get another address. the second address is,
[http://paste2.org/p/2422000](http://paste2.org/p/2422000)
can I get some help please? do I need to give  more information?

---

### Post by oldfred on 2012-11-03
It shows two entries for Windows in your grub menu. One is Windows 2000 as it did not correctly see the recovery (Do not use that one)  and then  your XP install in sda2. It will be the last in your menu or at the bottom. Can you not scroll down in menu?

---

### Post by SWGraphics291 on 2012-11-03
Are you sure you clicked install alongside/Dual Boot in ubuntu installation?

---

### Post by john fox on 2012-11-03
what menu?
when I boot up I don't get a menu? it goes right to ubuntu.
when I boot up and hit the escape button  I only get the option to boot in hdd or cd? with no option as to weather I want windows or ubuntu?

---

### Post by john fox on 2012-11-03
starwars29,
I am pretty sure I did but, if I didn't what can I do about that now?

---

### Post by The Cog on 2012-11-03
Try holding the left shoft key down as it boots - that might make the GRUB meu appear.

And you could try reinstalling GRUB with these two commands:
```
sudo update-grub
sudo grub-install /dev/sda
```

---

### Post by newb85 on 2012-11-03
> **The Cog said:**
> Try holding the left shoft key down as it boots

That's Shift

---

### Post by john fox on 2012-11-03
thanks, but holding the shift key didn't work.
about the commands, where do I enter them?
I know, I am a dummy when it comes to anything computer.

---

### Post by oldfred on 2012-11-03
Are you booting CD not the hard drive from BIOS? 

It is installed, so remove CD and see if hard drive boots.

You should not have to go into BIOS once installed. And once installed it is a bit quicker if you boot hard drive first, but then when you want to boot CD you have to remember to change it back or use one time boot key which most systems have now.

---

### Post by john fox on 2012-11-03
no, I'm not trying to boot from cd or bios.
just turning on the computer and it goes directly to ubuntu.

---

### Post by JKyleOKC on 2012-11-03
Run boot-repair yet a third time, and this time open the "advanced options" dialog and make sure that the "unhide menu" check box is checked. You can change the associated 10-second default to something longer if you want.

The default setting for a Ubuntu installation is to hide the menu and open the topmost entry. Pressing the (right-hand) shift key during the time that the hidden menu is active is supposed to un-hide the menu, but it's often almost impossible to hit the correct time slot.

EDIT: Your second report indicates that it did unhide the menu, so at this point let's see what the grub defaults actually are on your machine. Click "Places" and navigate to the "/etc" folder, from there into the "default" folder, and when there, open the "grub" file in an editor. Click Ctrl-A to highlight the entire file, Ctrl-C to copy the content into your clipboard, then open your browser (while still leaving the grub file open in the editor; this is important) to come back here, reply to this message, and click Ctrl-V to paste the entire content of your grub default file into the message. Then click Ctrl-A again to highlight everything, and click the "#" icon at the top of the message editor. From this we will have a better idea of what is going wrong...

---

### Post by john fox on 2012-11-03
well this is embarrassing I can't even find "places" to click on?
am I beyond help?

---

### Post by newb85 on 2012-11-03
> **john fox said:**
> well this is embarrassing I can't even find "places" to click on?
am I beyond help?

No you're not.  "Places" would have been a helpful thing to look for if you were using Gnome fallback.  I assume you're not.

Click the Home Folder icon in the launcher.  When nautilus opens, find "File System" along the left side, under Computer, and click it.  From there, you should be able to find the etc folder.

---

### Post by JKyleOKC on 2012-11-03
Thanks for the hints, newb85. I'm using xubuntu and don't know the Unity interface at all, so gave slightly wrong instructions.

John, when you get to the /etc folder my instructions should work properly for you from there on in...

---

### Post by john fox on 2012-11-03
OK, 
now lets try this.
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
 is what we need?

---

### Post by JKyleOKC on 2012-11-03
OldFred, does this set of defaults look right to you? Seems to me, after reading the "info" reference shown in its comments, that the hidden_timeout line value should be changed to 10 and the line uncommented -- but John's second bootinfo report indicated that boot-repair had made its changes and my own default list has exactly the same values as John's, but gives me the menu and the specified time in which to change the selection...

John, best wait for OldFred or possibly Yann (boot-repair's author) to come in with suggestions. I don't see anything here that looks suspicious!

---

### Post by oldfred on 2012-11-03
I do not see anything wrong either. But I rarely edit this file.

Sometimes a video issue, so I might uncomment this line just by removing the #:

 #GRUB_GFXMODE=640x480

From terminal copy & paste this into terminal:
```

gksudo gedit /etc/default/grub
```Then remove #

Then run this:

```
sudo update-grub
```

Edit
Just use Boot-Repair:

Boot-Repair --> Advanced options --> GRUB options tab --> tick the "Uncomment GFXMODE" option --> Apply

---

### Post by john fox on 2012-11-03
OK, joy joy.
y'all are great and I thank you for your patience.
I can now dual boot!
unticking the uncomment worked, joy, joy.
again thank you all for your help.
john

---

### Post by oldfred on 2012-11-03
Glad that worked, now onto the next issue. :)

If you do have other issues post a new thread with as much detail in the title as you can.

---

### Post by john fox on 2012-11-03
thanks oldfred,
yes, I'm sure I will have many other "issues" and expect to be around often.
john

---

