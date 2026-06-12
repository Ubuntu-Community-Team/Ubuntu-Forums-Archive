---
title: "Booting from Grub freezes"
date: 2013-02-18
forum: New to Ubuntu
---

### Post by Cnidarian1 on 2013-02-18
Alright, so I think some people may have had this problem before but the answers people gave them didn't work for me.  I should say that I'm almost completely new to Ubuntu and Linux.  The extent of my experience with them is using them since I installed Ubuntu yesterday.  I have been using Windows on my pc for 6 months, and yesterday I installed Ubuntu in a separate partition.  It's worked great for me since then, but after about a day when I choose Ubuntu from the Grub menu it just freezes at a purple screen.  The Ubuntu logo and loading dots only come up for a second after I push the power button to shut down.  I am using a Radeon HD 6750 card.  Thanks for any help!

---

### Post by Bashing-om on 2013-02-18
Cnidarian1; Hi ! Welcome to the forum.

Try this to load a graphics driver.
Boot ubuntu ->soon as the bios screen clears depress and hold the shift key-> grub menu;
With the first entry highlighted, press "e" for edit -> boot parameters screen -> arrow down and across to the line containing the phrase "quiet splash" and insert the term "nomodeset" -with out the quotes- -> ctl+x to continue the boot process.
login.
Additional Drivers:
12.04 version: launcher on left side of screen -> System Settings -> Additional Drivers;
install the recommended driver.
12.10 version: launcher -> Ubuntu Software Center ->Software sources -> Additional Drivers (tab) -> install the recommended driver.

Reboot.
[INDENT][INDENT]all good now ?

[/INDENT][/INDENT]

---

### Post by Cnidarian1 on 2013-02-18
I don't know if I'm doing something wrong, but after pushing ctrl+x after inputting the parameter it just deposits me back at the purple screen.  And I omitted this before, but perhaps I should mention that I did already install new drivers for my video card, but they were the "experimental, still in beta" versions, so maybe there's a bug with them or something.

---

### Post by Bashing-om on 2013-02-18
Cnidarian1;
Do not know as if properly done should boot into ubuntu with out Kernel Mode Setting enabled thus using the on board vesa graphics driver.
Ensure your edit resembles this:
> linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro nomodeset quiet splash  (3,2,0-24 XX whatever and the long string of the UUID will be different, we want "nomodeset" inserted correctly).

And try again. -> change the driver from Additional drivers; 
Reboot to see the effect.

[INDENT][INDENT]hth

[/INDENT][/INDENT]

---

### Post by Cnidarian1 on 2013-02-18
Yeah, it just brings me to the purple screen as before.  I noticed that particular line in the boot parameters has "$vt_handoff" at the end, and your example didn't.  Don't know if that would do anything.  Thanks for all your help, anyway.  If it's getting to be more trouble than it's worth, I could just reinstall Ubuntu and install different drivers.

---

### Post by Bashing-om on 2013-02-18
Cnidarian1; VT_handoff = 7 ; Virtual Terminal ->7 (gui). Older version//

Try it with that parameter deleted also. It really should boot to the desk top.
When you get the desktop, just (re)install a better graphics driver from the Additional Drivers utility.

Else; we will look into file system corruption (?).
Or try and look at the boot messages on the console, A bit complicated but, can be done.

Not a bad thought either, to boot to a text login and see what results.
[INDENT][INDENT]one thing at a time

[/INDENT][/INDENT]

---

### Post by Cnidarian1 on 2013-02-18
It brings me back to the purple screen for about 20 seconds, then to a black screen with a blinking cursor in the top corner.  Oh well, at least it did something.

---

### Post by Bashing-om on 2013-02-19
Cnidarian1;

Strange - to say the least !

OK, lets see if you can log in from a text console:

In that grub menu boot parameter line delete the quiet splash vt_handoff=7 and insert the term text. ctl-x to continue to boot. -> boot messages ->
text login:
enter username and execute with the enter key -> password -> enter your password (will get no response to screen). Execute with the enter key.
Enter the terminal code:
```
startx
```what results? (please advise of exact error generated)
If you get a GUI desktop ctl+alt+f1 brings you back to this terminal, ctl+alt+f7 returns you to the GUI desktop.
[INDENT]don't know but things will get clearer
[/INDENT]

---

### Post by Cnidarian1 on 2013-02-19
```
/etc/X11/xinit/xserverrc: 3: exec: /usr/bin/X: not found
xinit: giving up
xinit: unable to connect to X server: No such file or directory
xinit: server error
```

That's what it spat out.

---

### Post by Bashing-om on 2013-02-19
Cnidarian1; 
Yuk ! ,,,,To me that is indicative of file system corruption.
I see at least three avenues to approach for a solution.
1. Is to run a file system check and repair from the liveCD.
2. Try and (re)install Xserver and the desk top.
3. As this is a fairly recent install, highly consider (re)installing the operating system, right now there is no telling what else might be corrupted.

That said, I have no heartburn at all to try and repair the present system. It will be a learning experience for sure. At any time we can (re)install the OS. As the operating system has functioned properly prior to this episode, will conclude that the install medium is good. A (re)install of the OS will be the quickest resolution.

[INDENT]your call, what do you want to do 
[/INDENT]

---

### Post by Cnidarian1 on 2013-02-19
I think, why not try and fix this install.  I'd probably learn a thing or two new about Linux, and I think I can do just about everything I'd want to do in Windows in the meantime.

---

### Post by Bashing-om on 2013-02-19
Cnidarian1; That's the spirit !

Ok, let's make sure that the file system is intact.

#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s):
run:
```
 sudo fdisk -l
``` to know what partitions are what.
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required;
```
sudo e2fsck -C0 -p -f -v /dev/sda1
```#if errors: -y auto answers yes for fixes needing response --see man e2fsck;
```
sudo e2fsck -f -y -v /dev/sda1
```Clear as mud ? if not sure ask me !

If the file system check goes well, I have another method in mind to try and get the GUI up.
[INDENT]one step at a time.
[/INDENT]

---

### Post by Cnidarian1 on 2013-02-20
I think I did everything right...

It gave me a lot of statistics about disk usage, but nothing that seems like an error.

---

### Post by Bashing-om on 2013-02-20
Cnidarian1; Outstanding; Let us proceed on.
 Let's see if you can boot to the desktop via the "recovery mode".

At the grub menu choose the "recovery mode" kernel -> recovery console -> choose "resume normal boot" Expect advisory about "low graphics mode" OK at this point.

Can you now log into the desk top ?
If so, now try and install a graphics driver from the "Additional Drivers" utility.

Else we are going to be looking at what display you have and the supporting card and driver.

[INDENT]hope'n to see

[/INDENT]

---

### Post by Cnidarian1 on 2013-02-20
It just gives me a text console.

---

### Post by Bashing-om on 2013-02-20
Cnidarian1; Shucks ...

Let's see if we can see what is loaded and claimed for display/drivers.
Go to any text login -> login to the system;
terminal commands:
To see your graphics card and info:
```

sudo lshw -C display
lspci | grep VGA
lspci -nnk | grep -iA3 vga
```When this checks out will consider what to (re)install.
[INDENT][INDENT]water is 2 feet high and rising
 
[/INDENT][/INDENT]

---

### Post by Cnidarian1 on 2013-02-20
For the first command:
```
*-display
description: VGA compatible controller
product: Juniper LE [Radeon HD 6700 Series]
vendor: Hynix Semiconductor (Hyundai Electronics)
physical id: 0
bus info: pci@0000:01:00.0
version: 00
width: 64 bits
clock: 33MHz
capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
configuration: driver=radeon latency=0
resources: irq:43 memory:d0000000-dfffffff memory:fe620000-fe63ffff ioport:e000(size=256) memory:fe600000-fe61ffff
```
Second command:
```
01:00.0 [color=red]VGA[/color] compatible controller: Advanced Micro Devices [AMD] nee ATI Juniper LE [Radeon HD 6700 Series] [1002:68bf]
```
And then the third one:
```
01:00.0 [color=red]VGA[/color] compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Juniper LE [Radeon HD 6700 Series] [1002:68bf]
Subsystem: Hightech Information System Ltd. Device [1787:2009]
Kernel driver in use: radeon
Kernel modules: radeon
```

---

### Post by Bashing-om on 2013-02-20
Cnidarian1;

Card is detected, driver is loaded, should workie. So Why is Xserver unhappy ?

> /etc/X11/xinit/xserverrc: 3: exec: /usr/bin/X: not found 
xinit: giving up
xinit: unable to connect to X server: No such file or directory
xinit: server errorTaking it at it's word, Well let's just see.
terminal code:
```
ls -la /usr/bin/X
```My Systems output:
> sysop1@1204-a:~$ ls -la /usr/bin/X
-rwsr-sr-x 1 root root 10184 Jan  3 10:23 /usr/bin/XDoes the file exist on you system.

[INDENT]inquiring minds want to know

[/INDENT]

---

### Post by Cnidarian1 on 2013-02-20
> ls: cannot access /usr/bin/X: No such file or directory

I deduce that that's not supposed to happen.

---

### Post by Bashing-om on 2013-02-20
Cnidarian1; 

Teach us not to pay attention to what the system is telling us ! Yes, that should not happen, got no idea what could have happened such that the file is no longer in existence.

OK, Let's rebuild.
"#" == comments only.
Terminal commands:
    ```
 sudo service lightdm stop #terminates X - just in case it is trying to run
#Remove existing xorg using the following command
    sudo apt-get remove --purge xserver-xorg
#Install xorg using the following command
    sudo apt-get install xserver-xorg
#Reconfigure xorg using the following command
    sudo dpkg-reconfigure xserver-xorg
#reboot the system
sudo shutdown -r now
```Then tell me that it works.

---

### Post by Cnidarian1 on 2013-02-21
Huzzah!  The problem appears to be completely fixed!  In fact, I am now posting this from my fully restored Ubuntu OS.  Thanks for all your time and effort spent, Bashing-om!  If I have any other problems, I won't hesitate to make a new thread about them.

---

### Post by Bashing-om on 2013-02-21
Cnidarian1; Hey, Outstanding!

You are more than welcome -> welcome to the world of open source in general and ubuntu in particular !

Don't be a stranger, come back and help.

---

