---
title: "Ubuntu 8.04 reboot very slow"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by wariskampar on 2008-05-19
Hello, 

I found that 'my'(because a lot of people say it suppose to be fast) Ubuntu reboot very slow (about 2 minute plus) compare to XP (about 1 minute plus). Is it because I install Ubuntu on Logical drive while XP on Primary drive. I really dont know. Btw this is the structure of my partition(from Partition Magic within XP)
Local Disk (C:)  NTFS        Primary 
(*)              Extended    Primary
New Volume (E:)  NTFS        Logical
Local Disk (F:)  NTFS        Logical
Local Disk (*.)  Linux Ext3  Logical
SWAPSPACE2 (*.)  Linux Swap  Logical

Whay should I do to enjoy fast reboot in Ubuntu? Btw, I'm using Intel Pentium M, 1.83Gz. 1024 RAM. Any assitance highly appreciated

---

### Post by hermes0710 on 2008-05-19
Can you post your /etc/fstab file?

---

### Post by kesman on 2008-05-19
It doesn't matter what partition yuo have Ubuntu installed. What you could do, is to boot up Ubuntu and log in normally. Then in terminal, run
```

sudo gedit /boot/grub/menu.lst

```
and find the line with
#defoptions="quiet splash"
and remove those words. Then reboot your machine and you should now see what's going in during Ubuntu boot. You'll notice the step it hangs and then post back here and we'd see what could be done to it.

---

### Post by philinux on 2008-05-19
Takes mine about 12 seconds to shutdown. About 40 seconds after grub to login screen. Then 20 seconds to load desktop.

If you install and run startupmanager you can tick the box to show text at startup. You can then see the boot messages scrolling by. You may see the boot process hang somewhere. 

Other option is to edit grub and remove the quiet option from the kernel line. Same effect as above.

---

### Post by hermes0710 on 2008-05-19
I think that his discs are checked for errors every single time, he should post his fstab file

---

### Post by wariskampar on 2008-05-19
Hello, 

@hermes0710: I dont know how to get the fstab file. "bash: /etc/fstab: Permission denied" is the message i got when I enter that line in terminal. 

@kesman: i'll do that now and will post feedback immediately.

wow! this community is super fast!

---

### Post by hermes0710 on 2008-05-19
Open a terminal and execute:

```
cat /etc/fstab
```

Post the output here

---

### Post by wariskampar on 2008-05-19
@hermes0710: here is my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=a3972a39-4b18-43b1-9848-f5788689ccbf /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=177befd4-be3f-4cb6-bc23-0357a348b971 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


@kesman: i already delete #defoptions="quiet splash". here is the result
shutdown 12 second
GRUB to Login 65-70 second 
Login to Desktop 20 -25 second

---

### Post by hermes0710 on 2008-05-19
Your fstab is fine. Following philinux's suggestion, in which part while starting do you see the longest time spending?

---

### Post by wariskampar on 2008-05-19
@hermes0710: the longest is from GRUB to Login. The progress bar will stop for a while in the middle (of the bar) as if processing something. Hope my explanation is clear enough for you.

---

### Post by hermes0710 on 2008-05-19
Not exactly... While from grub to login, do you see any text? (You are supposed to see the progress bar and below that a box with text indicating current process). Enable text in usplash in order to see from the text in which operation spends most of the startup time

---

### Post by wariskampar on 2008-05-19
OK. I install startup manager using Synaptic Package Manager and after enable the text here is the result. The progress bar seem stuck at this two processes;
Waiting for Root File System 
Reading files needed to boot

---

### Post by philinux on 2008-05-19
I would suggest it's the way the drives are setup as you said in first post.

In my old machine I had the bios set to use the ubuntu drive as the primary master and the windows drive the slave.

If you tinker with the bios make sure to write down your original settings as a backup.

---

### Post by spiderbatdad on 2008-05-19
Slow boot is usually the result of hardware detection problems. Read the output of ```
dmesg
``` and edit the kernel line in /boot/grub/menu.lst according to the suggestions provided by dmesg, for example, "APIC disabled by bios, try using 'lapic.'
So. gksu gedit /boot/grub/menu.lst delete --quiet splash from the end of the kernel line and add lapic.
```
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=604f2b74-7f64-424f-a8bf-1160a71d9ea3 ro **lapic pci=routeirq**
initrd		/boot/initrd.img-2.6.24-16-generic
quiet
savedefault
```

---

### Post by wariskampar on 2008-05-19
@philinux: i also think that will solve the problem but will consider it as my last resort 
@spiderbatdad: no offense but i really dont understand how to follow your instruction. when i key in dmesg in terminal, it list down all my hardware etc but i can not see any suggestion. i also type "gksu gedit /boot/grub/menu.lst" but after key in my password nothing seem to happen. when i manually go to /boot/grub/menu.lst, i can not find "--quiet splash from the end of the kernel" to delete and subsequently add "lapic". i must admit that today is my second day in Ubuntu:)

---

### Post by spiderbatdad on 2008-05-19
How about this: ```
dmesg > dmesg.txt
```that will place a text file of dmesg in your home directory. Right click on that file and select "Archive." Upload that archive here using the "manage attachment" tool below this reply window.

---

### Post by wariskampar on 2008-05-19
Hello, here is the dmesg file. I'm a bit paranoid about my system security so having said that hopefully the attached file doesnt have any info that can compromise my security (MAC Address etc).

---

### Post by Austin_KW on 2008-05-19
Install boot chart 
```
 sudo apt-get install bootchart
```
Reboot and look in /var/log/bootchart/ for the graphic ***.png*** of the boot process, Either look at it yourself or post it back here. 

Boot problems are often obvious, delays without CPU or disk activity.


Also first check "cat /etc/usplash.conf" Does the splash match your monitor resolution as this can cause delays

---

### Post by spiderbatdad on 2008-05-19
Here is the kernel line: Kernel command line: root=UUID=xxx(some numbers) ro splash

You should be able to edit /boot/grub/menu.lst. If gedit isnt working, you can try nano...a little scarrier looking:```
sudo nano /boot/grub/menu.lst
```Again use the arrow key to scroll down to the section under: ####END DEFAULT OPTIONS#### and go to the end of the line that begins with the word 'kernel.' It looks like local apic is present on your machine so try just deleting 'splash' from the end of that line and add 'pci=routeirq' without quotes. Save the file by pressing Ctrl-o then hit enter to confirm the file name and Ctrl-x to exit. Then reboot. I will look through your dmesg some more, but it generally seems ok. By removing splash you will also get a verbose boot, and you will be able to see where the process is hanging. Here is an example of my dmesg if you want to compare the two. You can see my kernel line looks like: Kernel command line: root=UUID=604g2b51-7g25-424f-a7cg-10700b21d9cs2 ro lapic pci=routeirq

Looks like you have a usb device causing an error...the routeirq may fix that. You might also want to turn off bluetooth start-up services in System>>Preferences>>Start up Programs, if you don't use it.

---

### Post by wariskampar on 2008-05-19
@spiderbatdad: ok, after my sys reboot fairly fast (delete "splash" and replace with "pci=routeirq". but i dont see any progress bar anymore right? is that what you call verbose boot. btw, for confirmation here is my dmesg.txt again

I can not find System>Preference>Start Up. Where should I look to disable bluetooth

---

### Post by spiderbatdad on 2008-05-19
> **wariskampar said:**
> @spiderbatdad: ok, after my sys reboot fairly fast (delete "splash" and replace with "pci=routeirq". but i dont see any progress bar anymore right? is that what you call verbose boot. btw, for confirmation here is my dmesg.txt again

Yes that is what I was referring to by verbose boot. Now that boot is faster, you can also do a one-time profile of the process to gain a few more seconds.
From the grub menu at start-up (where you select which os to boot) Edit the default kernel by pressing 'e' to edit. If you do not have a dual boot setup, it is possible the grub menu is hidden. In which case, press esc as the system starts.
After pressing 'e' to edit the kernel, use the arrow key to move to the kernel line and press 'e' again. Go to the end of the line...after pci=routeirq add profile, so it looks like: ```
Kernel command line: root=UUID=xxx(some numbers) ro pci=routeirq profile

``` Now hit enter, then 'b' to boot. This boot will take slightly longer as the system creates a profile of the process, subsequent boots will be faster. This is** not** a change made to the file /boot/grub/menu,lst, as that would cause a profile to run everytime...you don't want that.

---

### Post by wariskampar on 2008-05-19
OK, i will do that during next Boot. 

From the Start-Up Manager, at Boot Option tab, my Display resolution is stated 640x480 with 8 bits color depth where as my Screen Resolution is 1024x800. Do I have to change this as well to gain some speed

---

### Post by spiderbatdad on 2008-05-19
> **wariskampar said:**
> OK, i will do that during next Boot. 

From the Start-Up Manager, at Boot Option tab, my Display resolution is stated 640x480 with 8 bits color depth where as my Screen Resolution is 1024x800. Do I have to change this as well to gain some speed

Not sure. Also these boot parameters, ie pci=routeirq can be tricky to determine what will be most effective. On some hp machine I have had the best results with noapic nolapic. so the end of the kernel line looks like: ro noapic nolapic

You can try some other option, if you like, from the grub menu, as explained regarding 'profile.' This way you dont have to edit /boot/grub/menu.lst while you experiment. If noapic nolapic works better you can make the change permanent in /menu.lst 

You can also specify vga for resolution in the kernel like like so:
ro pci=routeirq vga=791
or
ro noapic nolapic vga=791

This table explains vga settings:
```
	640x480   800x600   1024x768   1280x1024   1600x1200
8bit	769	   771       773        775         777
15bit   784        787       790        793         796
16bit   785        788       791        794         797
24bit   786        789       792        795         798
```

---

### Post by MyR on 2008-07-04
this might help
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/227003](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/227003)

peace

---

