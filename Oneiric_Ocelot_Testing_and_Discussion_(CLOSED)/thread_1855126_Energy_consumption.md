---
title: "Energy consumption"
date: 2011-10-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lvanderree on 2011-10-05
I noticed a very big difference in power consumption.

In Mint (and 11.04) I could tweak my system (mainly by turning off (by acpi) and disabling the Radeon = second videocontroller) to use only 11.000 mW

However in 11.10 I cannot get my system to use less than 25.000 mW!

that is a Sony Vaio Sa-series being empty 2,5 times faster!

Are there more people experiencing this problem, and has anyone found a solution yet? powertop --calibrate doesn't seem to have any effect.

```

grep rate /proc/acpi/battery/BAT2/state 
present rate:            29636 mW

```

---

### Post by viperdvman on 2011-10-05
I too am unsure how to reduce energy consumption in Ubuntu (any version). I know my Asus EeePC's specs say up to 6 hours, but with proprietary ATI drivers, I can only get up to 5 hours.

I haven't tried this in 11.10 using Unity 2D yet.

---

### Post by cariboo on 2011-10-05
This is a know problem with the 3.0 kernel, and affects all distributions using it, this has been discussed several time in this sub-forum. The problem affects laptops/netbooks that have pci-e mostly. 

THere are a couple of things to try:

Install powertop and run:

```
sudo powertop --calibrate
```

or

install [Jupiter]("http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html")

---

### Post by xyzzyman on 2011-10-05
Have you turned on all the power setting 'tuneables' in powertop? And do you set your CPU frequency to ondemand?

---

### Post by makitso on 2011-10-05
Install Jupiter, it will make a world of difference!

[http://ubuntuforums.org/showthread.php?t=1854019](http://ubuntuforums.org/showthread.php?t=1854019)

---

### Post by lvanderree on 2011-10-06
I had already tried powertop --calibrate, but unfortunately didn't noticed any improvements, so I thought it was just a calibration test, not making any adjustments.

I now also tried Jupiter, but unfortunately again, even though it gets great reviews, I still don't see any big differences.

I also tried pcie_aspm=force to grub, but again no difference...

grep rate /proc/acpi/battery/BAT2/state 
still returns a present rate of 26312 mW

I am going to try Fuduntu from USB now, and see how that will perform.

Thanks for the feedback though

---

### Post by lvanderree on 2011-10-06
Hmmm Fuduntu doesn't recognize my display correctly, it has been translated, both horizontally and vertically, making it impossible to see the top menu. I could operate it with ALT+F1 and I could start applications with ALT+F2 of course.

However I could already notice that my laptop was warm, and in the terminal I could see a power consumpution of 30W this time...

I don't see why I can tweak Mint to 13W and nothing else can come close. I would like to have Ubuntu (11.10 preferably) since this runs much more stable (no deb-hell) when installing third party applications. And I think I am getting to like Unity more and more

---

### Post by fuduntu on 2011-10-06
> **lvanderree said:**
> Hmmm Fuduntu doesn't recognize my display correctly, it has been translated, both horizontally and vertically, making it impossible to see the top menu. I could operate it with ALT+F1 and I could start applications with ALT+F2 of course.

However I could already notice that my laptop was warm, and in the terminal I could see a power consumpution of 30W this time...

I don't see why I can tweak Mint to 13W and nothing else can come close. I would like to have Ubuntu (11.10 preferably) since this runs much more stable (no deb-hell) when installing third party applications. And I think I am getting to like Unity more and more

There is a new xorg in our testing repository, enable it in /etc/yum.repos.d/fuduntu.repo and update.

30W doesn't sound right, make an account over at Fuduntu Forum and give us a snapshot of all the panes from powertop (without making any changes).

---

### Post by lvanderree on 2011-10-06
Ok thanks!

I will try it later tonight and give back feedback at the Fuduntu Forum

---

### Post by flipper T on 2011-10-06
wow !

installed Jupiter about 12 hours ago & it has transformed my laptop from some type of deafeningly loud steam-punk room heater into a zen master, calm & quiet & probably tasty at kung fu.

only ever use it plugged in, so battery life not a concern.

but, again wow. fan noise almost imperceptible. keep checking to make sure laptop is turned on.

---

### Post by viperdvman on 2011-10-06
On my netbook running Ubuntu 11.04, Jupiter is quite useful and allows my computer to run in Eco mode when disconnected from AC power. Without it, I was getting a little over 3 hours from the battery. With Jupiter installed and running, I've gotten up to 4 hours... 5 when running the proprietary ATI graphics driver (which sucks ar running Adobe Flash).

I'll vouch for Jupiter. It's nice that Fuduntu comes with Jupiter preinstalled :)

---

### Post by lvanderree on 2011-10-06
Apparently it takes a while before I get access to the fuduntu forum, so I already want to let you know from here that I got the results.

I uploaded them to my server at: [http://fun4me.demon.nl/~leon/fuduntu/](http://fun4me.demon.nl/~leon/fuduntu/)

the two tgz files contain the dumps, one normal output, one after calllbration with powertop

---

### Post by fuduntu on 2011-10-06
> **lvanderree said:**
> Apparently it takes a while before I get access to the fuduntu forum, so I already want to let you know from here that I got the results.

I uploaded them to my server at: [http://fun4me.demon.nl/~leon/fuduntu/](http://fun4me.demon.nl/~leon/fuduntu/)

the two tgz files contain the dumps, one normal output, one after calllbration with powertop

Jupiter won't be able to fix that, it looks like you have a lot of driver issues on that system.

---

### Post by lvanderree on 2011-10-06
In Fubuntu that might be true:

Display was translated. as described earlier and wireless wasn't working either.

However in Ubuntu everything seems to be working fine. Only thing I notice is the touchpad not recognizing multitouch, but more people have this issue. And in Mint I can see the power consumption is much lower, so I know it should be possible!

Anyway thanks for your help again

---

### Post by clemmy on 2011-10-07
> **cariboo907 said:**
> This is a know problem with the 3.0 kernel, and affects all distributions using it, this has been discussed several time in this sub-forum. The problem affects laptops/netbooks that have pci-e mostly.

I'm experiencing the same regression on my sony vaio vpcsb. With oneiric it drains ~ 17W (radeon OFF, wifi ON, medium screen backlight). It was used to drain ~ 11W with natty in the same conditions.

I don't think it's kernel related. I run a 3.0 kernel on natty for some time, and I'm pretty sure that the energy consumption was similar to the original kernel.

Moreover, natty's kernel was already affected by the very popular power regression regarding pcie_aspm.

So I presume this regression should be somehow related to the software running on natty.

---

### Post by tista on 2011-10-07
> **clemmy said:**
> I'm experiencing the same regression on my sony vaio vpcsb. With oneiric it drains ~ 17W (radeon OFF, wifi ON, medium screen backlight). It was used to drain ~ 11W with natty in the same conditions.

I don't think it's kernel related. I run a 3.0 kernel on natty for some time, and I'm pretty sure that the energy consumption was similar to the original kernel.

Moreover, natty's kernel was already affected by the very popular power regression regarding pcie_aspm.

So I presume this regression should be somehow related to the software running on natty.

Hi clemmy,

I agree with you... ;)
Ubuntu seems to eat power huge more and more with releasing...

And I'm using SONY VAIO Z (i5 2410M, Intel HD3000), then oneiric drains around 26W (must be 10W or lower!!). :S So battery could keep only 2.5 or 3 hours instead of 6 hours vendor suggested on Win7?!

I think this "bug" is really critical than compiz's minor one!! lol

---

### Post by lvanderree on 2011-10-12
with the help of the latest Jupiter (release 0.0.51) I am now down to:


grep rate /proc/acpi/battery/BAT2/state 
present rate:            20743 mW


so, 10 more Watts to go, but there is a start

---

### Post by SushiR on 2011-10-12
I'm on a Samsung N150 (a netbook), and with my usual habit to surf and sometimes listening to music, I'm about 10 W average (that's what powertop reports). But I installed samsung-tools, which comes in with a lot of power management. Anyway, I'm a happy camper...

---

### Post by lvanderree on 2011-10-13
Is there a Ubuntu/Linux-System guru who can tell me what I can do to investigate the power consumption any further?

Running PowerTop seems to show a big usage due to audio components, but how can I debug this any further? Can I maybe compile my own kernel to optimize things for my system? any tips are welcome, willing to read/try/learn anyhting (or at least a lot ;)).

---

### Post by dino99 on 2011-10-13
> **lvanderree said:**
> Is there a Ubuntu/Linux-System guru who can tell me what I can do to investigate the power consumption any further?

Running PowerTop seems to show a big usage due to audio components, but how can I debug this any further? Can I maybe compile my own kernel to optimize things for my system? any tips are welcome, willing to read/try/learn anyhting (or at least a lot ;)).

you can install/run valgrind
[https://wiki.ubuntu.com/Valgrind](https://wiki.ubuntu.com/Valgrind)

---

### Post by clemmy on 2011-10-13
On my vaio i have some improvements with powertop's tunables, but i don't know how to get those changes permanent.

I can go from ~17W to ~14W, not bad. But at the moment I have to open powertop, go to Tunables tab and toggle every switch marked with BAD.
In particular I had two unused peripheals draining ~400 mW each, (fingerprint reader and ethernet card) After activating the PM of those peripheals via powertop, now the drain 0mW..



another remarbable thing that i spotted in powertop is that the display backlight is reported three times (draining ~800 mW each time). Maybe it's just a powertop problem, but I think I'll make a natty live usb to see if it was the same.

---

### Post by flipper T on 2011-10-13
as far as i know, you cannot make the "tunables" permanent, which somewhat undermines the app's usefulness. making the changes each time you reboot just isn't going to do.

needs fixing.

---

### Post by clemmy on 2011-10-13
> **flipper T said:**
> as far as i know, you cannot make the "tunables" permanent, which somewhat undermines the app's usefulness. making the changes each time you reboot just isn't going to do.

needs fixing.
Fair enough.
Apparently PowerTOP is just a monitoring tool, and those settings should be applied by other component of the OS. Indeed previous versions of powertop did not have those switches at all..


Now we just need to understand how to apply those settings.. I've tryed jupiter and it doesn't improve the situation...

---

### Post by fuduntu on 2011-10-13
> **clemmy said:**
> Fair enough.
Apparently PowerTOP is just a monitoring tool, and those settings should be applied by other component of the OS. Indeed previous versions of powertop did not have those switches at all..


Now we just need to understand how to apply those settings.. I've tryed jupiter and it doesn't improve the situation...

Take the tuneables that powertop provides, and add them to Jupiter.

[http://sourceforge.net/apps/mediawiki/jupiter/index.php?title=Kernel](http://sourceforge.net/apps/mediawiki/jupiter/index.php?title=Kernel)

EDIT: @ Clemmy below (can't reply because it's closed).  Congrats, you found the hook that Jupiter uses.

It's cool that you put your own script there, but that is the point of Jupiter .. not having to do that.

---

### Post by clemmy on 2011-10-13
> **fuduntu said:**
> Take the tuneables that powertop provides, and add them to Jupiter.

[http://sourceforge.net/apps/mediawiki/jupiter/index.php?title=Kernel](http://sourceforge.net/apps/mediawiki/jupiter/index.php?title=Kernel)

Hey, thank's!

Following your advice I did some more research on internet, and eventually found that there is a software already installed that execs some scritps every time tha laptop is plugged/unplugged. It's pm-utils and it execs script inside /etc/pm/power.d/  so I decided to create a script for handling those values.

I found a very useful script on this italian blog:
[http://blog.liberailvoip.it/2010/04/27/ubuntu-lucid-lynx-acer-aspire-one-impostazioni-ottimizzate-autonomia-prestazioni/](http://blog.liberailvoip.it/2010/04/27/ubuntu-lucid-lynx-acer-aspire-one-impostazioni-ottimizzate-autonomia-prestazioni/)

and modified it as follows:
```
#!/bin/sh

# Shell script to reduce energy consumption when running battery. Place
# it in /etc/pm/power.d/ and give execution rights.

# This is a modified version of an original version of by Skumpic and is
# available here: http://blog.liberailvoip.it/2010/04/27/
# ubuntu-lucid-lynx-acer-aspire-one-impostazioni-ottimizzate-
# autonomia-prestazioni/




# Disable Wake On Lan
ethtool -s eth0 wol d


if on_ac_power; then

# Start AC powered settings --------------------------------------------#

 
# Disable laptop mode
echo 0 > /proc/sys/vm/laptop_mode
 
# Set SATA channel: max performance
for foo in /sys/class/scsi_host/host*/link_power_management_policy;
do echo max_performance > $foo;
done
 
# Set Max Power for wifi interface
# change value according to your hardware!
iwconfig wlan0 txpower 14    
 
# Disable wifi power saving
iwconfig wlan0 power off
 
# CPU Governor: Performance
for foo in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor;
do echo performance > $foo;
done 

# Disabile USB autosuspend
for foo in /sys/bus/usb/devices/*/power/level;
do echo on > $foo;
done

# Disable PCI autosuspend
for foo in /sys/bus/pci/devices/*/power/control;
do echo on > $foo;
done
 
# Disabile audio_card power saving
echo 0 > /sys/module/snd_hda_intel/parameters/power_save_controller
echo 0 > /sys/module/snd_hda_intel/parameters/power_save
 
# End AC powered settings ----------------------------------------------#





else






# Start battery powered settings ---------------------------------------#
 
# Enable Laptop-Mode disk writing
echo 5 > /proc/sys/vm/laptop_mode
 
# Set SATA channel to power saving
for foo in /sys/class/scsi_host/host*/link_power_management_policy;
do echo min_power > $foo;
done
 
# Activate wifi power saving
iwconfig wlan0 power timeout 500ms
 
# Reduce wifi txpower
iwconfig wlan0 txpower 5
 
# Select Ondemand CPU Governor
for foo in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor;
do echo ondemand > $foo;
done
 
# Activate USB autosuspend
for foo in /sys/bus/usb/devices/*/power/level;
do echo auto > $foo;
done

# Activate PCI autosuspend
for foo in /sys/bus/pci/devices/*/power/control;
do echo auto > $foo;
done
 
# Activate audio card power saving
# (sounds shorter than 5 seconds will not be played)
echo 5 > /sys/module/snd_hda_intel/parameters/power_save
echo 1 > /sys/module/snd_hda_intel/parameters/power_save_controller
 
# End battery powered settings -----------------------------------------#




 
fi

```

I have not reached natty's power consumption yet, but at least I've improved a little bit.

---

