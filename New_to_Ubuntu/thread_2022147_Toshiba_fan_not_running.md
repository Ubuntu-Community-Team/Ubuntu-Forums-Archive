---
title: "Toshiba fan not running"
date: 2012-07-10
forum: New to Ubuntu
---

### Post by SyniTh on 2012-07-10
My fan is still not running. 

Im using Toshiba Satellite M500 at Xubuntu 12.04. 

fn keys are not usable as well. I installed Xubuntu alongside with Windows.

After typing the first step from ashima, it said:

E:  Unable to locate package sensors-applet. 

Please help. Thanks. I would want to use and learn linux in my pc.

---

### Post by oldos2er on 2012-07-10
Post moved to its own thread.

---

### Post by SyniTh on 2012-07-10
Original Post by Ashima 

"This was almost doing my head in.
Thought about having to run Windows or sell my new laptop.
Same fan problems with Fedora, PClinuxOS
Here is what works for me. Toshiba L500. 64bit Ubuntu 10.04

first. sudo apt-get install sensors-applet
next. sudo sensors-detect

next. answer yes to everything.

exit then restart computer.

next. sudo gedit /etc/default/grub and then change

GRUB_CMLINE_LINUX_DEFAULT="quiet splash"

to read

..."quiet splash acpi_osi=Linux"

next. sudo update-grub to update /boot/grub/grub.cfg

exit then restart computer.


MY FAN NOW STOPS AND STARTS WHEN IT SHOULD



Hope this helps."


I followed this but the first step ddn't work for me. 

Are there any fixes? Please help.

---

### Post by HermanAB on 2012-07-10
Hmm, as the proud owner of a burned out Toshiba Satellite U500, I would say that your best solution is to install Windows, sell the infernal thing on Ebay and buy a Lenovo.

Otherwise, if you are handy with a Dremel and a soldering iron, cut a large square out of the bottom of the machine, solder some wires to the fan (from a USB port) so that it always runs and then glue the square back.

If you don't feel adventurous at all, buy a 'laptop cooler' and hope it doesn't burn out.

What you should **not** do, is try to disassemble the machine from the top down to get to the fan.  There are teenie weenie little connectors that can break very easily, so this is not recommended at all.

---

### Post by SyniTh on 2012-07-10
> **HermanAB said:**
> Hmm, as the proud owner of a burned out Toshiba Satellite U500, I would say that your best solution is to install Windows, sell the infernal thing on Ebay and buy a Lenovo.

Otherwise, if you are handy with a Dremel and a soldering iron, cut a large square out of the bottom of the machine, solder some wires to the fan (from a USB port) so that it always runs and then glue the square back.

If you don't feel adventurous at all, buy a 'laptop cooler' and hope it doesn't burn out.

What you should **not** do, is try to disassemble the machine from the top down to get to the fan.  There are teenie weenie little connectors that can break very easily, so this is not recommended at all.

:D

I would want to wait. Some toshiba owners had it worked out. Can anyone help me. Thank you so much.

---

### Post by Redblade20XX on 2012-07-11
> **SyniTh said:**
> :D

I would want to wait. Some toshiba owners had it worked out. Can anyone help me. Thank you so much.

The first step is :
```
sudo apt-get update
```
```
sudo apt-get install lm-sensors
```

then you do :
```
sudo sensors-detect
```

Hope this helps! :)

- Red

---

### Post by HermanAB on 2012-07-11
"Some toshiba owners had it worked out"

Yes, some Satellite versions work and some not.  Your M500 is probably in the "won't work" category, since it is likely the same hardware as mine, just with a different language option (different symbols painted on the keyboard).

The main problem is that if you wait long enough for a software solution, then the machine will burn out and these machines are practically irreparable - you cannot buy a new mother board - nobody stocks them.  Therefore Ebay is the safest solution.

---

### Post by SyniTh on 2012-07-11
> **Redblade20XX said:**
> The first step is :
```
sudo apt-get update
``````
sudo apt-get install lm-sensors
```then you do :
```
sudo sensors-detect
```Hope this helps! :)

- Red

It did! Thank you so much! 

But when i typed this: sudo gedit /etc/default/grub

it said command not found.

---

### Post by Redblade20XX on 2012-07-11
> **SyniTh said:**
> It did! Thank you so much! 

But when i typed this: sudo gedit /etc/default/grub

it said command not found.

Did you check through the file manager to see if the file exists?
Also post the output of:
```
ls /etc/default
```- Red

---

### Post by SyniTh on 2012-07-12
> **Redblade20XX said:**
> Did you check through the file manager to see if the file exists?
Also post the output of:
```
ls /etc/default
```- Red


Thanks here's the output of 

```
ls /etc/default
``````
 
acpid         brltty         dbus        keyboard    rcS                useradd
acpi-support  cacerts        devpts      locale      rsync
alsa          console-setup  grub        nss         rsyslog
apport        crda           halt        ntfs-3g     saned
avahi-daemon  cron           irqbalance  ntpdate     speech-dispatcher
bootlogd      cups           kerneloops  pulseaudio  ufw

```

I really appreciate your help red. Thank you so much. 

I also tried installing my nvidia driver from Settings>Additional Drivers

It didnt work out. All i get is a black screen after the xubuntu loadscreen. I reinstalled the OS agen.

---

### Post by Miljet on 2012-07-12
Your error says "command not found", not "file not found." That means that you are not using gedit for your test editor. I don't know what text editor xubuntu uses. Look under accessories and see what text editor you are using. Then substitute that for "gedit" in the command.

---

### Post by SyniTh on 2012-07-12
> **Miljet said:**
> Your error says "command not found", not "file not found." That means that you are not using gedit for your test editor. I don't know what text editor xubuntu uses. Look under accessories and see what text editor you are using. Then substitute that for "gedit" in the command.

xubuntu uses leafpad. I already tried coding 

```
 sudo leafpad/etc/default/grub 
```

i also installed gedit. Then coded

```
 sudo gedit/etc/default/grub 
```
or 
```
 sudo gedit 
```

all says command not found. 

Thank you for the help.

---

### Post by Miljet on 2012-07-12
In your first two examples, you left out a space. There should be a space between the name of the editor and the beginning of the path to the file. 

For example: ```
sudo leafpad /etc/default/grub
```

I don't know why the last example doesn't open gedit unless it is not installed.

---

### Post by SyniTh on 2012-07-12
Its the space indeed. Thanks.

I was able to open the grub in gedit. From this line 

GRUB_CMLINE_LINUX_DEFAULT="quiet splash"

i changed it to 

GRUB_CMLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"

then update-grub. Rebooted. The fn keys now work but the fan is still  not running. Im still hoping though. Thank you for your help.[/QUOTE]

---

### Post by Redblade20XX on 2012-07-13
> **SyniTh said:**
> Its the space indeed. Thanks.

I was able to open the grub in gedit. From this line 

GRUB_CMLINE_LINUX_DEFAULT="quiet splash"

i changed it to 

GRUB_CMLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"

then update-grub. Rebooted. The fn keys now work but the fan is still  not running. Im still hoping though. Thank you for your help.[/QUOTE]

You can try pushing another parameter:
```
acpi.power_nocheck=1
```

if that doesn't get the fans operational, 
remove 
```
acpi_osi=Linux
```
and 
```
acpi.power_nocheck=1
```

and add
```
noacpi
```

- Red

---

### Post by SyniTh on 2012-07-13
I tried your suggestions but that fan isn't operational still. 

```
 quiet splash acpi_osi=Linux
```
```
 quiet slash acpi.power nocheck=1
```In both codes the fan wasnt working but the fn keys do. 

```
 quiet slash noacpi
```both the fn keys and the fan wont work.

---

### Post by Redblade20XX on 2012-07-13
> **SyniTh said:**
> I tried your suggestions but that fan isn't operational still. 

```
 quiet splash acpi_osi=Linux
``````
 quiet slash acpi.power nocheck=1
```In both codes the fan wasnt working but the fn keys do. 

```
 quiet slash noacpi
```both the fn keys and the fan wont work.

Can you also try this one (remove the other ones)?
```
noacpi=force
```

Then remove the previous one and substitute it with:
```
acpi=force
```

If neither of these two doesn't get the fans working, then you probably have 
a BIOS problem.

Have you updated the BIOS?

And what is the output of?
```
sensors
```

- Red

---

### Post by SyniTh on 2012-07-14
Here's the output of the sensors.

```
acpitz-virtual-0
Adapter: Virtual device
temp1:        +79.0°C  (crit = +108.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +74.0°C  (high = +90.0°C, crit = +90.0°C)
Core 1:       +74.0°C  (high = +90.0°C, crit = +90.0°C)

nouveau-pci-0800
Adapter: PCI adapter
temp1:        +77.0°C  (high = +100.0°C, crit = +110.0°C)

```

Both the codes didn't get the fan operational. I think i have to update my BIOS. Thank you sir for the help.

---

### Post by SyniTh on 2012-07-14
Guys! The fan did work already! But now the display is lost.

I installed the NVIDIA driver from (additional drivers).

I rebooted, then chose ubuntu from the boot selection menu.
Surprisingly, the fan was operational already!. The Load-screen resolution became lower and after it i got an all black display then nothing happens. 

If i press the power switch, it displays the loadscreen then it turns off. 

I guess im almost there! This is really giving me hopes.

Is it the NVIDIA driver? Is there other ways i can install the NVIDIA driver? Im using G210M geforce cuda 512mb. Thank you!!! Please help. Im exited. :)))

---

### Post by Redblade20XX on 2012-07-14
> **SyniTh said:**
> Guys! The fan did work already! But now the display is lost.

I installed the NVIDIA driver from (additional drivers).

I rebooted, then chose ubuntu from the boot selection menu.
Surprisingly, the fan was operational already!. The Load-screen resolution became lower and after it i got an all black display then nothing happens. 

If i press the power switch, it displays the loadscreen then it turns off. 

I guess im almost there! This is really giving me hopes.

Is it the NVIDIA driver? Is there other ways i can install the NVIDIA driver? Im using G210M geforce cuda 512mb. Thank you!!! Please help. Im exited. :)))

Try this from the command line,
```
sudo apt-get --purge remove nvidia-*
```

Then look here for installing the most current driver:
[http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html](http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html)

Glad it's finally working!

- Red

---

### Post by SyniTh on 2012-07-16
> **Redblade20XX said:**
> Try this from the command line,
```
sudo apt-get --purge remove nvidia-*
```Then look here for installing the most current driver:
[http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html](http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html)

Glad it's finally working!

- Red

Sadly, its still not operational. I installed the driver following the steps in the site. 

The Additional driver indicates: 

 This driver is activated but not currently in use. The Loadscreen is at a low resolution. And the fan isn't working still. :( 

Im still trying. And researching. Hope one day this problem will be solved.

---

### Post by SyniTh on 2012-07-16
I used this code in the grub. 

```
 acpi.power nocheck=1
```The fan is now operational in after 5 mins in the workspace. I doubt if the fan works if i reboot it.

---

### Post by Redblade20XX on 2012-07-16
> **SyniTh said:**
> Sadly, its still not operational. I installed the driver following the steps in the site. 

The Additional driver indicates: 

 This driver is activated but not currently in use. The Loadscreen is at a low resolution. And the fan isn't working still. :( 

Im still trying. And researching. Hope one day this problem will be solved.

Did you go back into additional drivers and remove the previously installed Nvidia driver?

If you installed the driver based on the site I've given you, you should have a unity launcher for nvidia. Go into the Unity search option and type nvidia. 

Does anything show up? If it does, what version of the driver does it state?

- Red

---

### Post by SyniTh on 2012-07-17
> **Redblade20XX said:**
> Did you go back into additional drivers and remove the previously installed Nvidia driver?

If you installed the driver based on the site I've given you, you should have a unity launcher for nvidia. Go into the Unity search option and type nvidia. 

Does anything show up? If it does, what version of the driver does it state?

- Red

The driver version is 302.17 from system> nvidia x settings. 
The load-screen is still resolution. But everything works fine except for the fan.

---

