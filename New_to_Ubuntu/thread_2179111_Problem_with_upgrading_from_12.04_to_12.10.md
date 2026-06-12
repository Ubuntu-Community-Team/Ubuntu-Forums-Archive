---
title: "Problem with upgrading from 12.04 to 12.10"
date: 2013-10-06
forum: New to Ubuntu
---

### Post by hjordur on 2013-10-06
Hi! I'm new to using Ubuntu and installed the 12.04 LTS a couple of days ago. Today I decided to try to update it to 12.10 and maybe after that to 13.04. I started updating to 12.10 and everything went fine until all the updates were installed and I got asked to restart my computer. I restarted, and when my computer was starting I saw the Ubuntu loading screen after which the screen went completely black (my monitor said it didn't get any input). At first I thought that maybe the computer was still doing something, so I waited. But after couple of hours nothing had happened. The screen was still black and the computer didn't response to any input, so I thought I'd shut it down and try again, but the result was still the same. Is there something I can do to fix this or do I need to install the operating system all over again?

---

### Post by heir4c on 2013-10-06
Hold in the <shift> when the boot screen of your computer (Bios). Then you must see the Grub menu. That is a list with text. 
Ubuntu
Ubuntu (recovery...)
memory
memory....

I can't go in details but you will see.
Go with the arrow-keys to the second line and click on it.
A lot of text passes across the screen.
Then you come in a menu.
I can't see it at the moment or control it but I thought there is a line what something say about the xserver or the graphics.
When you see that line, select with arrow-keys that line and click Enter.
Let the computer do his job
If not than you choose the option where you can log in as root.
I don't now if it will work but when you log in than try to type this:
startx
and Enter.
If it don't work and you return to the menu than you choose the first option and click Enter.
Now he start trough. (I hope :))

---

### Post by hjordur on 2013-10-07
Thanks for the quick answer! :)

I managed to get to the Grup menu and tried the things that you suggested, but unfortunately to no avail. I tried the failsafeX option, which was supposed to be a graphical safe mode, but it produced an error like this:

[COLOR=#000080]Fatal server error:
no screens found
Please check the log file at "/var/log/Xorg.failsafe.log" for additional infromation[/COLOR]

The I tried to login as root and use the startX command. It gave me lots of parameters that I could use with the command, and after that an error like this:

[COLOR=#000080]Fatal server error:
could not create lock file in /tmp/.tX0-lock

xinit: giving up
xiniti: unable to connect to X server: connection refused
xinit: server error
xauth: error in locking authority site root/.Xauthority[/COLOR]

[COLOR=#000000]I then tried to go to the first option after selecting the Ubuntu recovery option (continuing the start up)[/COLOR], and I got to what seemed like a text based version of Ubuntu. I was able to login to my user account and give console commands, but there wasn't any graphics. 

What should I do now?

---

### Post by heir4c on 2013-10-07
Here you can use also use the command: startx
Hopefully it will work here.

---

### Post by hjordur on 2013-10-07
I tried the startx command again while logged in with my user account, and this time it gave a different error. That feels like progress. :) The error said that there were no screens found, just like when trying to start in safe mode. Could this error maybe be fixed by giving some kind of parameter to the command?

Also, when I searched the Internet I found this: [http://www.ubuntux.org/cant-start-ubuntu-in-grphical-mode](http://www.ubuntux.org/cant-start-ubuntu-in-grphical-mode)
I tried the suggestion given there, but it didn't solve the problem either.

---

### Post by heir4c on 2013-10-07
That's an (very) old tread (2006) and the command work no longer, I think. (here a different command that you can try: sudo Xorg -configure )
It's a long time ago I have problems with my screen, so I it's a little bit difficult to see directly a solution.

Look for your monitor cable if he is not disconnected. (Why I think not of that before) and:
Plug the monitor in a other computer or Laptop (if you have one) and see if he works there. Maybe the monitor is broken. (you never know)
Or it is a driver issue. Or something with the Graphics card?

If you can in the Hard Disk via live-cd/usb you can look for the Xorg log:
> Please check the log file at "/var/log/Xorg.failsafe.log" for additional infromation

---

### Post by Julian_Treadwell on 2013-10-27
It's not a monitor error, I've just had exactly the same error trying to upgrade to 12.10 from 12.04.  I've reinstalled 12.04 and my screen is fine.

---

### Post by Bashing-om on 2013-10-27
Julian_Treadwell; Hi ! My welcome to the forum.

In that 12.10 install the black screen indicates to me that an appropriate driver for the graphics card was not found.
Post back the output of terminal codes:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

```
to show what card and driver is presently in use (12.04)
Also the kernel version you are running may have great relevance;
```

uname -a

```
older ATI cards and newer kernels no workie with proprietary drivers.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Julian_Treadwell on 2013-10-29
julian@ubuntu:~$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: Pitcairn XT [Radeon HD 7870 GHz Edition]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:42 memory:d0000000-dfffffff memory:fdc80000-fdcbffff ioport:ee00(size=256) memory:fdc00000-fdc1ffff
julian@ubuntu:~$ lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Pitcairn XT [Radeon HD 7870 GHz Edition] [1002:6818]
	Subsystem: Hightech Information System Ltd. Device [1787:2321]
	Kernel driver in use: radeon
	Kernel modules: radeon
julian@ubuntu:~$ uname -a
Linux ubuntu 3.8.0-32-generic #47~precise1-Ubuntu SMP Wed Oct 2 16:19:35 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by Bashing-om on 2013-10-29
Julian_Treadwell; Hey ,

Your output shows that you have the open source driver "radeon" installed and loaded on that 12.04 install and the latest kernel supporting version 12.04 is also installed. Your card " [AMD/ATI] Pitcairn XT [Radeon HD 7870 GHz Edition] " I expect to have good support also with the proprietary drivers, if one should elect to install them ( Additional Drivers).
I am surprised version 12.10 is not stable with the open source driver; Did you try the proprietary drivers ?

How about dual booting your system with 12.04 and version 12.10 ? We can then see if version 12.10's graphics issue can be isolated and resolved.

[INDENT][INDENT]where there are solutions there are no problems
[/INDENT][/INDENT]

---

