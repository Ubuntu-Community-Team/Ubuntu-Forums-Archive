---
title: "Need help on booting issue"
date: 2015-09-14
forum: New to Ubuntu
---

### Post by Asiful_Nobel on 2015-09-14
I have installed Ubuntu 14.04 as stand-alone OS on my Asus-1215P laptop a couple of weeks ago. After installation, it worked fine; but yesterday when I turned on the laptop, it went to the grub menu as usual. However, after that it started having problems:

There were messages like ACPI Probing Failed, then ^[[6~^ kept printing. Then another message was that my cifs drive could not be mounted, after that everything goes into a loop....Bunch of lines printing over a over again, Ubuntu loading screen keeps flashing time to time.


I tried to boot from recovery mode and it worked then, but the resolution is so low and ^[[6~^ was still printed a bunch of times. After googling some more, I tried using the command parameter from grub menu multiple times in combination with acpi=off, nomodeset and nosplash. Now, although Ubuntu successfully booted using all three options, the performance and graphics of the OS is like booting from recovery mode. So, what should I do to solve this problem?

**P.S**: My laptop's 'L' key and "Enter"/"Return" key does not work, so keep in mind that when giving helpful suggestions/solutions.
**P.P.S**: The laptop only has Intel's integrated graphics card and the processor is Intel N570 atom. I am not using any proprietory additional drivers.

---

### Post by Bashing-om on 2015-09-14
Asiful_Nobel; Hi ! Welcome to the forum .

In order to prosecute this issue a terminal is a must.
Somehow, someway, somewhere get a functional keyboard and we will continue to find the fault.

[INDENT][INDENT]gotta have the tools to work with
[/INDENT][/INDENT]

---

### Post by Asiful_Nobel on 2015-09-23
Update: Got a functional usb keyboard. What do to now?

---

### Post by Bucky Ball on 2015-09-23
Welcome. Please use default font and point size. Thanks. I have edited your first post.  :) 

How old is the video card? How old is the computer and other hardware? Added any new hardware, for instance, RAM lately? This sounds like hardware if Ubuntu is working fine but is in low-graphics only.

Have you installed a third-party driver for graphics or you were using the open-source noveau one? Could you open a terminal and post the output of this back here:

```
sudo lshw -C video
```

Did you do an update/upgrade prior to switching off the laptop then switching it on to this mess?

---

### Post by Asiful_Nobel on 2015-09-23
The laptop is 4 years old and its model is Asus 1215P. No, I have not installed new hardware on it or any third-party graphics driver.
I had updated the usual things like updating everything after installing first time. But other than that I did not update anything else.

```
sudo lshw -C video
```

Output:```

*-display:0 UNCLAIMED
       description: VGA compatible controller
       product: Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:f7e00000-f7e7ffff ioport:dc00(size=8) memory:d0000000-dfffffff memory:f7d00000-f7dfffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f7e80000-f7efffff
```

---

### Post by Bashing-om on 2015-09-23
Asiful_Nobel; Well !

Now we have pertinent information .
From that output we know that a graphics driver is not loaded.
But, it is Intel, I have no experience with this graphic's chip set. Anything I can add will be just speculation on my part.
Let's await advisement from those who do have experience.

[INDENT][INDENT]all to the good
[/INDENT][/INDENT]

---

### Post by Geoffrey_Arndt on 2015-09-23
You could also see what happens if booting from a live usb (like "System Rescue CD" or "Parted Magic").

See [http://www.distrowatch.com](http://www.distrowatch.com)  . . . to obtain access to a bunch of different live iso images.

note:  it may also be worthwhile to see if disk is throwing any errors (run disks program to test).

---

### Post by Asiful_Nobel on 2015-09-23
Geoffrey_Arndt: I tried to reinstall Ubuntu from liveUSB on that laptop. But when I selected "Try Ubuntu without Install", Ubuntu loading screen appears and keeps flashing. So, then I tried to install Fedora from liveUSB and it could not continue installation because of some kind of loop and kept flashing the screen. Meanwhile the laptop still works, if I boot from recovery mode. However, the laptop performance and graphics is poor.

---

### Post by Asiful_Nobel on 2015-09-23
I do not know what happened, but after using Ubuntu in reduced performance mode(if you know, what I mean) for a while, everything stopped responding and Ubuntu froze. So, I turned it off using the power button and I removed the battery of the laptop for a while. When I hooked-up the battery with the laptop again and turned it on, everything became OK again.

In order to find the reason behind all this, I am posting the output of ```
sudo lshw -C video
```

Output:
  ```
*-display:0
       description: VGA compatible controller
       product: Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:28 memory:f7e00000-f7e7ffff ioport:dc00(size=8) memory:d0000000-dfffffff memory:f7d00000-f7dfffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f7e80000-f7efffff
```

---

### Post by Asiful_Nobel on 2015-09-23
So,I guess the problem is with my laptop's integrated graphics card; because after rebooting again, the previous problems came back i.e. flashing screen and loading screen loop. Therefore, is there anything I can do other than fixing the graphics card?

---

### Post by Bashing-om on 2015-09-23
Asiful_Nobel; Wheeeelll ...

All I can suggest as you do have a driver that can and does load:
> 
 configuration: driver=i915 latency=0 

sometimes ;
Is to open up the lap top - not something a novice should attempt on a laptop, some are not so easy to do -
and reseat the graphics card and check all the connections .

Verify once more the settings in bios.

Restart the machine, and see what now .

[INDENT][INDENT][INDENT]Maybe yes
[/INDENT][/INDENT][/INDENT]

---

### Post by Geoffrey_Arndt on 2015-09-23
The first thing I would try (assuming you have at least 1 GiB of ram) is to do a full install of Ubuntu-Mate or Linux Mint Mate.    The video requirement is much less than Ubuntu, so it's worth a try.   Plus the Mate desktop is much lighter and more responsive on older equipment (especially considering the Atom cpu).

---

### Post by Asiful_Nobel on 2015-09-24
Bashing-om and Geoffrey_Arndt, your suggestions have been helpful. But I have found a temporary work-around which is that when Ubuntu's flashing loading screen/the default purple screen appears  during boot, tapping the "**shift**" key a few times seems to make the flashing screen normal again and Ubuntu boots normally after that just like it should be. 

Don't know why this works, but it works. :D

---

### Post by Bucky Ball on 2015-09-24
Excellent. See the first link in my signature. Also, now you're in, get things up to date with these commands:

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

This will NOT upgrade your current release to a newer one, only the software in your current release. Good luck. :)

---

