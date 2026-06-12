---
title: "Crazy idle temperatures with default Nouveau driver (Geforce 8400m)"
date: 2011-08-14
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by kaldor on 2011-08-14
See attachment from sensors.

This is from a USB drive and is idle. All I did was install the lm-sensors package. I know that Nouveau lacks heat management, but does anyone else have temperatures this high? I'd hate to start watching YouTube or something on this.

Edit: Since posting this, it's gone up to over 85 degrees. This is just crazy :(

Also note that with proprietary drivers, this idles at ~50 to 60 degrees.

Edit 2: Just had to turn off the laptop. It became so hot that it was uncomfortable to have my hands on it, and the sides (with metal ports, etc) hurt to the touch. I've never had the laptop get this hot before.

---

### Post by pjd99 on 2011-08-14
I don't know about the nouveau driver, but those idle temps don't seem too out of the ball park. My 8600M GS runs at 61 degC idle but if I fire up HoN (or anything that requires full performance from the GPU), it will hit 105 no worries. It looks high, but it doesn't alarm till 115.

If the driver lacks heat management like you've said, I'd guess that the frequency governor lacks control, resulting in increased power consumption and heat dissipation.

---

### Post by kaldor on 2011-08-14
Yes, but doing *nothing at all*? 

My machine hits 80 degrees when I play games. My machine hit 90 degrees by just sitting there for 10 minutes on Nouveau.

---

### Post by sgage on 2011-08-14
> **kaldor said:**
> See attachment from sensors.

This is from a USB drive and is idle. All I did was install the lm-sensors package. I know that Nouveau lacks heat management, but does anyone else have temperatures this high? I'd hate to start watching YouTube or something on this.

Edit: Since posting this, it's gone up to over 85 degrees. This is just crazy :(

Also note that with proprietary drivers, this idles at ~50 to 60 degrees.

Edit 2: Just had to turn off the laptop. It became so hot that it was uncomfortable to have my hands on it, and the sides (with metal ports, etc) hurt to the touch. I've never had the laptop get this hot before.

I will not use nouveau because it drives my card too hot - a solid 15 degrees C hotter than the proprietary nvidia drivers. The rendering is inferior in any case - I use Stellarium a lot, and it's a bit clunky in nouveau. I'd probably put up with it, though, if it weren't for the heat issue.

---

### Post by kaldor on 2011-08-14
> **sgage said:**
> I will not use nouveau because it drives my card too hot - a solid 15 degrees C hotter than the proprietary nvidia drivers. The rendering is inferior in any case - I use Stellarium a lot, and it's a bit clunky in nouveau. I'd probably put up with it, though, if it weren't for the heat issue.

15 degrees hotter is nothing compared to the up to double than on NVIDIA. 

I think heat and power should be the focus for open source driver developers. Features and stability are great, but it's kinda moot if it fries your hardware :(

PS: I wonder why Canonical doesn't have any employees working on open source drivers? Nouveau or Radeon developers from a company like Canonical could really help the default Ubuntu experience a lot.

---

### Post by el_koraco on 2011-08-14
Now you see what sucky power management on a laptop means.

---

### Post by VinDSL on 2011-08-14
I ran Nouveau drivers for a while, and...

Increased GPU temps are a common complaint.

My 7600 GT ran mad hot, at first, but...

I took my computer to the garage and produced a massive dust cloud by blowing it out with 125 psi compressed air.

After that, temps returned to a normal range.

There is no doubt that Nouveau drivers stress the GPU.  Having your heatsink/fan packed with dust bunnies, skin mites, cookie crumbs, et cetera, adds to the temps exponentially.

So, sorry for being rudimentary, but you might consider doing some housekeeping, before giving up on Nouveau drivers.  ;)

Other than heat issues, they work great, these days!

---

### Post by sgage on 2011-08-14
> **VinDSL said:**
> I ran Nouveau drivers for a while, and...

Increased GPU temps are a common complaint.

My 7600 GT ran mad hot, at first, but...

I took my computer to the garage and produced a massive dust cloud by blowing it out with 125 psi compressed air.

After that, temps returned to a normal range.

There is no doubt that Nouveau drivers stress the GPU.  Having your heatsink/fan packed with dust bunnies, skin mites, cookie crumbs, et cetera, adds to the temps exponentially.

So, sorry for being rudimentary, but you might consider doing some housekeeping, before giving up on Nouveau drivers.  ;)

Other than heat issues, they work great, these days!

Sorry, identical conditions, radically different temps. Nothing to do with dust. The nouveau drivers run much hotter, period. And they work sort of OK, but certainly not great.

I am sticking with nvidia drivers.

---

### Post by kaldor on 2011-08-14
> **VinDSL said:**
> I ran Nouveau drivers for a while, and...

Increased GPU temps are a common complaint.

My 7600 GT ran mad hot, at first, but...

I took my computer to the garage and produced a massive dust cloud by blowing it out with 125 psi compressed air.

After that, temps returned to a normal range.

There is no doubt that Nouveau drivers stress the GPU.  Having your heatsink/fan packed with dust bunnies, skin mites, cookie crumbs, et cetera, adds to the temps exponentially.

So, sorry for being rudimentary, but you might consider doing some housekeeping, before giving up on Nouveau drivers.  ;)

Other than heat issues, they work great, these days!

Well those cleaning-related things obviously make a difference, but temperatures are fine and stable on my laptop with the proprietary drivers.

---

### Post by cariboo on 2011-08-15
I have a 6600GT agp that was running in the mid 60° C range with the nouveau too, but I was having a problem with the cooling fan, replacing the fan with a much larger OEM CPU fan solved the problem, now it runs in the mid 40° range even with the nouveau driver. This was a more drastic solution, but it worked for me. :)

---

### Post by kaldor on 2011-08-15
I should mention that I'm currently on my laptop with the proprietary NVIDIA driver on Fedora 15. I am running a few different programs and also using YUM, yet the temperatures are quite low:

```
$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +45.0°C  (crit = +120.0°C)
temp2:        +41.0°C  (crit = +120.0°C)

```

I don't remember Nouveau ever getting up to 90 degrees in heat; that's more than double when *doing absolutely nothing*. Could this be a possible bug in Oneiric/kernel?

---

### Post by kaldor on 2011-08-24
I'm gonna have to bump this.

I was trying Fedora 16 on my laptop, and the idle temperatures were quite high and ranging from 60 to 75. I decided to test Nouveau's 3d capability, so I ran OpenArena with the native resolution. Performance was smooth and flawless. While in game, sensors showed temperatures between 84 and 88. 

Now, to Oneiric. After letting my laptop cool down I booted 11.10. Within 5 minutes, sensors showed 85 degrees. Minutes after that, it went beyond 90 when doing absolutely nothing.

This leads me to believe there's a problem in Ubuntu 11.10. Fedora 16, while still too hot, can keep the temperatures much lower after a few minutes of gaming whereas Ubuntu 11.10 went much hotter after I just stared at the desktop for a couple of minutes.

Note that both distros were 64-bit and tested on the same Live USB.

---

### Post by RobinJ1995 on 2011-09-28
I've got the same problem, appart from the fact that in Oneiric the temperatures are going up to 109°C (not higher than that only because it shutted down my laptop at that point).
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/858916](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/858916)

---

### Post by ventrical on 2011-09-28
> **VinDSL said:**
> I ran Nouveau drivers for a while, and...

Increased GPU temps are a common complaint.

My 7600 GT ran mad hot, at first, but...

I took my computer to the garage and produced a massive dust cloud by blowing it out with 125 psi compressed air.

After that, temps returned to a normal range.

There is no doubt that Nouveau drivers stress the GPU.  Having your heatsink/fan packed with dust bunnies, skin mites, cookie crumbs, et cetera, adds to the temps exponentially.

So, sorry for being rudimentary, but you might consider doing some housekeeping, before giving up on Nouveau drivers.  ;)

Other than heat issues, they work great, these days!

You took the words right out of my mouth Vin!!

 Every laptop I repair first has to have the cooling-fan grid inspected and then subsequently clean.  it is amazing how fast a <lint-block> can build up between the fan and the grid.  Compressed air or hand cleaning is a first proceedure I use always. Plus it is also a good step to eliminate other problems. I also re-heat-sync-grease the processors on older machines.

Sounds like the OP is setting up for thermal runaway and once that starts there is no stopping it. Otherwise, if taken care of, semiconductors theoretically have an infinite lifetime.

:)

---

### Post by ventrical on 2011-09-28
> **kaldor said:**
> I'm gonna have to bump this.

I was trying Fedora 16 on my laptop, and the idle temperatures were quite high and ranging from 60 to 75. I decided to test Nouveau's 3d capability, so I ran OpenArena with the native resolution. Performance was smooth and flawless. While in game, sensors showed temperatures between 84 and 88. 

Now, to Oneiric. After letting my laptop cool down I booted 11.10. Within 5 minutes, sensors showed 85 degrees. Minutes after that, it went beyond 90 when doing absolutely nothing.

This leads me to believe there's a problem in Ubuntu 11.10. Fedora 16, while still too hot, can keep the temperatures much lower after a few minutes of gaming whereas Ubuntu 11.10 went much hotter after I just stared at the desktop for a couple of minutes.

Note that both distros were 64-bit and tested on the same Live USB.

  I have a fairly newer GF0210/218/512 and it has a dual powered fan and Oneric correctlt engages the fan when hot , but that is on a tower/desktop, and I am using  nvidia current(binary).

---

### Post by nrundy on 2011-09-28
> **kaldor said:**
> 
Now, to Oneiric. After letting my laptop cool down I booted 11.10. Within 5 minutes, sensors showed 85 degrees. Minutes after that, it went beyond 90 when doing absolutely nothing.

This leads me to believe there's a problem in Ubuntu 11.10. Fedora 16, while still too hot, can keep the temperatures much lower after a few minutes of gaming whereas Ubuntu 11.10 went much hotter after I just stared at the desktop for a couple of minutes.

Note that both distros were 64-bit and tested on the same Live USB.

Oneiric is running hot for everyone no matter what vid drivers they are running. Even the Intel integrated setup is running extremely hot. It's not just people's perceptions that it's running hot. You can look on Phoronix at the benchmarks and you can see some numbers. 

IMHO, this issue should be the highest priority for Canonical to fix. For 12.04, I would put as many developers as it takes to get this under control. Everything else should take a back seat to fixing the heat/power issues.

---

### Post by kaldor on 2011-09-28
> **nrundy said:**
> Oneiric is running hot for everyone no matter what vid drivers they are running. Even the Intel integrated setup is running extremely hot. It's not just people's perceptions that it's running hot. You can look on Phoronix at the benchmarks and you can see some numbers. 

IMHO, this issue should be the highest priority for Canonical to fix. For 12.04, I would put as many developers as it takes to get this under control. Everything else should take a back seat to fixing the heat/power issues.

While I don't think allocating all resources to one bug is a good idea, I definitely think that these heat and power bugs in the kernel should be considered as extremely severe. I won't be able to use a newer distro on my laptop until these issues are solved.

There's no way I can use a laptop which idles at up to 100 degrees celcius (or higher, if I don't turn the thing off out of fear).

---

### Post by effenberg0x0 on 2011-09-28
Heat / Power Consumption on Linux (not just Ubuntu) is not at its best moment right now. Again, not an Ubuntu issue, for the most part.

There's an issue in which some BIOS are not reporting speeds correctly. Governor is, in this cases, locked in performance. Mostly for Core 2 Duo. Requires ACPI kernel options. Kernel, affects everyone, all distros.

There are two-core Intel CPUs in which only CPU0 is stepping. CPU1 is locked on MaxSpeed. Kernel, affects everyone, all distros.

There's problems with some AMD (Phenom II X6 Black Edition) TurboCore feature, in which the OnDemand governor is set to oscillate between MaxSpeed and MaxSpeed (3.7GHz to 3.7GHz). Kernel, affects everyone, all distros. I edited my /etc/init.d/ondemand to fix it.

```

for CPU_SCALLING_MIN_FREQ in /sys/devices/system/cpu/cpu*/cpufreq/scaling_min_freq
    do
        [ -f $CPU_SCALLING_MIN_FREQ ] || continue
        echo -n 800000 > $CPU_SCALLING_MIN_FREQ
    done

```There's stuff like this: [http://ubuntuforums.org/showthread.php?t=1848385](http://ubuntuforums.org/showthread.php?t=1848385). Intel CPUs locked on performance.

Also, check NVidia-Settings. I've seen a couple cards continuously locked on Performance Level 2 (Maximum Performance), which is wrong when you set it to adaptive (OnDemand 0 to 2). Initially I thought it had to do with npviewer.bin zombie, but I was wrong. Can't find the cause. Seen it on Open Source and Proprietary.

IMHO, I believe many people were** NOT** using hw accel in the desktop in previous versions. Now they are. **So they WILL see temperature rise**, no matter if using the Open Source or Proprietary Driver. The idea that the VGA GPU is IDLE in a hw accelerated desktop is not true. It's not idle: Compiz is running. It was probably more idle when people were using Metacity and no Compiz.

Another important thing I should mention:** DO NOT **trust sensors only. Just tested it right now: It says my GPU is on 46º but my Fluke Infrared Thermometer says 38º. Sorry, I trust Fluke much more than a single cheap Chinese thermistor.

As mentioned above: Compressed Air is great. Sand down / polish the base of a pure coper heatsink (not the crappy aluminum OEM most cards come with) + get a decent cooler ([http://www.bit-tech.net/hardware/cooling/2010/05/19/graphics-card-coolers-investigated/1](http://www.bit-tech.net/hardware/cooling/2010/05/19/graphics-card-coolers-investigated/1)) + apply Artic Silver 5 or similar + check for proper case cooling plan (round cables, fans, decent PSU, etc) == 15° to 25°C less depending on the hardware. Underclocking GPU or VGA mem is always an option too.

---

### Post by lucazade on 2011-09-28
@effenberg0x0

so.. does this affect only ubuntu or all distros?! It is not clear from your post... lol.. jokin :)

---

### Post by cariboo on 2011-09-28
> **nrundy said:**
> Oneiric is running hot for everyone no matter what vid drivers they are running. Even the Intel integrated setup is running extremely hot. It's not just people's perceptions that it's running hot. You can look on Phoronix at the benchmarks and you can see some numbers. 

IMHO, this issue should be the highest priority for Canonical to fix. For 12.04, I would put as many developers as it takes to get this under control. Everything else should take a back seat to fixing the heat/power issues.

I have to disagree, I'm running a Compaq Mini 1100, with Intel chipset, it seems to be running at the same temp as it always has, I've run every thing since Lucid on this system, and it always seems to run at around 50-55° C. See the screenshot.

BTW, this syem has a 3-cell battery.

---

### Post by sgage on 2011-09-28
I tried the nouveau drivers again today for the first time since mid-August. Performance has really improved, but the heat issue is still present, and very real.

Under identical loads, identical conditions, nouveau runs a solid 18-20 degrees C hotter than nvidia-current.

This is with a GeForce 8500 GT and a 32-bit install at the moment.

It's not just dust bunnies in the fan, sorry. This is a real issue.

---

### Post by ventrical on 2011-09-28
I have an Acer Extensa 4420/AMD64AthlonX2 ATi Radeon Express 1250/3GBDDR2

dale@ubuntu:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +39.0°C  (crit = +95.0°C)
temp2:        +42.0°C  (crit = +110.0°C)

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:   +37.0°C  
Core0 Temp:   +35.0°C  
Core1 Temp:   +39.0°C  
Core1 Temp:   +44.0°C  

dale@ubuntu:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +38.0°C  (crit = +95.0°C)
temp2:        +41.0°C  (crit = +110.0°C)

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:   +37.0°C  
Core0 Temp:   +34.0°C  
Core1 Temp:   +37.0°C  
Core1 Temp:   +44.0°C  

dale@ubuntu:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +39.0°C  (crit = +95.0°C)
temp2:        +42.0°C  (crit = +110.0°C)

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:   +38.0°C  
Core0 Temp:   +35.0°C  
Core1 Temp:   +38.0°C  
Core1 Temp:   +44.0°C  

dale@ubuntu:~$ 


And running compiz cube/anims. running for 5 1/2 hours.

---

### Post by effenberg0x0 on 2011-09-28
> **lucazade said:**
> @effenberg0x0

so.. does this affect only ubuntu or all distros?! It is not clear from your post... lol.. jokin :)

LOL... I've been accused of being an undercover Fedora / Puppy fanboy && Ubuntu hater recently. Gotta make things pretty clear. 

So, once more: Kernel==ALL DISTROs, NOT UBUNTU, NOT (*)BUNTU, they rock LOL. I LIKE UBUNTU, DON'T HURT MY FAMILY PLEASE.

---

### Post by lucazade on 2011-09-28
> **effenberg0x0 said:**
> LOL... I've been accused of being an undercover Fedora / Puppy fanboy && Ubuntu hater recently. Gotta make things pretty clear. 

So, once more: Kernel==ALL DISTROs, NOT UBUNTU, NOT (*)BUNTU, they rock LOL. I LIKE UBUNTU, DON'T HURT MY FAMILY PLEASE.

hahaahha

We love all desktops ... OHM!

---

### Post by ventrical on 2011-09-28
> **sgage said:**
> I tried the nouveau drivers again today for the first time since mid-August. Performance has really improved, but the heat issue is still present, and very real.

Under identical loads, identical conditions, nouveau runs a solid 18-20 degrees C hotter than nvidia-current.

This is with a GeForce 8500 GT and a 32-bit install at the moment.

It's not just dust bunnies in the fan, sorry. This is a real issue.

1 How do I install Nouveau drivers for ATI?
2. How do I install Nvidia drivers for GEforce 218/512MB

---

### Post by effenberg0x0 on 2011-09-28
Nouveau vs NVidia Proprietary is a matter of clocks IMHO. Nouveau is looking more fluid because it is stuck in higher clock longer than proprietary. Thus, it heats more.

[B]Example 1:
[/B]Do this: Install the proprietary NVidia, go to nvidia-settings, set:
Video_Texture - Sync to VBlank = On
OpenGL - Sync && Allow_Flip= On
Image Settings - High QUality
Anti aliasing - Enhance Application Settings
Anisotropic Filtering - Override Application Settings
Texture Sharpening - On
Powermizer preferred mode - Prefer Maximum Performance
Play that 1080P mkv fresh from newzbin for 10 minutes, open 10 glxgears simultaneously. 

Touch the GPU with the tip of your tongue for as long as you can. Taste, Temp and Performance is equal to Nouveau. 

[B]Example 2: 
[/B]My memory clock with NVidia-Proprietary: Oscillates between 125MHz and 1500MHz
My memory clock with Nouveau: Fixed at 1804MHz. Go figure.

Regards,
Effenberg

---

### Post by effenberg0x0 on 2011-09-28
> **ventrical said:**
> 1 How do I install Nouveau drivers for ATI?
2. Hoe do I install Nvidia drivers for GEforce 218/512MB

1. Nouveau = NVIDIA, not ATI. ATI=fglrx, Catalyst, etc
2. GT218 GPU = GeForce 200 Series = GeForce210 = 280.13 (current). NVidia Driver Site Search (32-bit) [http://www.nvidia.com/object/linux-display-ia32-280.13-driver.html](http://www.nvidia.com/object/linux-display-ia32-280.13-driver.html) . See supported hardware.
[B]
32-bit[/B]
```

cd
mkdir nvidia_driver
cd nvidia_driver
wget http://us.download.nvidia.com/XFree86/Linux-x86/280.13/NVIDIA-Linux-x86-280.13.run
sudo chmod +x NVIDIA-Linux-x86-280.13.run 
sudo service lightdm stop 
sleep 30 && sudo killall -s KILL X
cd
cd nvidia_driver
sudo ./NVIDIA-Linux-x86-280.13.run (Answer Yes, Yes, Yes, Yes, Yes, Yes, etc)
sudo service lightdm start (but *sudo reboot now* is preferred)

```[B]64-bit
[/B]```

cd 
mkdir nvidia_driver
cd nvidia_driver
wget http://us.download.nvidia.com/XFree86/Linux-x86_64/280.13/NVIDIA-Linux-x86_64-280.13.run
sudo chmod +x NVIDIA-Linux-x86_64-280.13.run 
sudo service lightdm stop 
sleep 30 && sudo killall -s KILL X
cd
cd nvidia_driver
sudo ./NVIDIA-Linux-x86_64-280.13.run (Answer Yes, Yes, Yes, Yes, Yes, Yes, etc)
sudo service lightdm start (but *sudo reboot now* is preferred)

```**EDIT**
You know what, don't be an idiot like me. Instead of starting lightdm after installing the driver, do a proper reboot like a normal human being is supposed to.

[B]EDIT 2
[/B]Code humanized. Run this thing on a VT. Once it stops lightdm and kills X there goes your terminal window.

---

### Post by ventrical on 2011-09-28
OK.. I did all those settings for nvidia current proprietary and it toggles between 60-61 - even when running complex graphics games.

  As for the nouveau driver .. after I run that code can I get my normal driver back ? :):)

---

### Post by ventrical on 2011-09-28
OK... I tried it one line of code at a time and the whole bundle and it hangs right here both times.

dale@ubuntu:~$ cd && wget [http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86/280.13/NVIDIA-Linux-x86-280.13.run&lang=us&type=GeForce](http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86/280.13/NVIDIA-Linux-x86-280.13.run&lang=us&type=GeForce) && sudo chmod +x NVIDIA-Linux-x86-280.13.run 
[1] 2635
[2] 2636
--2011-09-28 17:41:33--  [http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86/280.13/NVIDIA-Linux-x86-280.13.run](http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86/280.13/NVIDIA-Linux-x86-280.13.run)
Resolving [www.nvidia.com](www.nvidia.com)... [sudo] password for dale: 67.69.196.33, 67.69.196.75
Connecting to [www.nvidia.com|67.69.196.33|:80](www.nvidia.com|67.69.196.33|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1100 (1.1K) [text/html]
Saving to: `confirmation.php?url=%2FXFree86%2FLinux-x86%2F280.13%2FNVIDIA-Linux-x86-280.13.run.1'

100%[======================================>] 1,100       --.-K/s   in 0s      

2011-09-28 17:41:34 (60.4 MB/s) - `confirmation.php?url=%2FXFree86%2FLinux-x86%2F280.13%2FNVIDIA-Linux-x86-280.13.run.1' saved [1100/1100]

---

### Post by effenberg0x0 on 2011-09-28
Its expecting your sudo password. Let me be normal and break that into something human-ready. I'll edit the original post.

Regards,
Effenberg

**EDIT**
Code humanized. Sometimes I forget I am a Cylon.

---

### Post by effenberg0x0 on 2011-09-28
> **ventrical said:**
> OK.. I did all those settings for nvidia current proprietary and it toggles between 60-61 - even when running complex graphics games.


Well, it depends on the card. For example, my favorite desktop has a GTS450. Its a card known for running a little hot although it is power efficient (fermi). See [http://www.anandtech.com/show/3909/nvidias-geforce-gts-450-pushing-fermi-in-to-the-mainstream/16](http://www.anandtech.com/show/3909/nvidias-geforce-gts-450-pushing-fermi-in-to-the-mainstream/16) . There's a chart with temperatures on "idle" and "load" (running crysis).

Your is a mobile unit, but is known for getting a little hot too. [http://forum.notebookreview.com/sony/273654-geforce-8400m-gt-idle-temperatures.html#post3690121](http://forum.notebookreview.com/sony/273654-geforce-8400m-gt-idle-temperatures.html#post3690121)

Different architectures: hard to compare tdps, temperatures.

Regards,
Effenberg

---

### Post by ventrical on 2011-09-28
I think I blew up my monitor. POP!!!

#^$#$&#*!!!

I get most everything but when I go to click the dash I get a pitch black background. Everything is working - just a black hole when I click on the Unity dash.

serves me right.

---

### Post by ventrical on 2011-09-28
The monitor and nvidia card are ok .. I think i just crashed Unity in some way.

---

### Post by effenberg0x0 on 2011-09-28
> **ventrical said:**
> The monitor and nvidia card are ok .. I think i just crashed Unity in some way.

280.13 is pretty reliable, been using for a lot of time with no problem at all.

Regards,
Effenberg

---

### Post by ventrical on 2011-09-29
> **effenberg0x0 said:**
> 1. Nouveau = NVIDIA, not ATI. ATI=fglrx, Catalyst, etc
2. GT218 GPU = GeForce 200 Series = GeForce210 = 280.13 (current). NVidia Driver Site Search (32-bit) [http://www.nvidia.com/object/linux-display-ia32-280.13-driver.html](http://www.nvidia.com/object/linux-display-ia32-280.13-driver.html) . See supported hardware.
[B]
32-bit[/B]
```

cd
mkdir nvidia_driver
cd nvidia_driver
wget http://us.download.nvidia.com/XFree86/Linux-x86/280.13/NVIDIA-Linux-x86-280.13.run
sudo chmod +x NVIDIA-Linux-x86-280.13.run 
sudo service lightdm stop 
sleep 30 && sudo killall -s KILL X
cd
cd nvidia_driver
sudo ./NVIDIA-Linux-x86-280.13.run (Answer Yes, Yes, Yes, Yes, Yes, Yes, etc)
sudo service lightdm start (but *sudo reboot now* is preferred)

```[B]64-bit
[/B]```

cd 
mkdir nvidia_driver
cd nvidia_driver
wget http://us.download.nvidia.com/XFree86/Linux-x86_64/280.13/NVIDIA-Linux-x86_64-280.13.run
sudo chmod +x NVIDIA-Linux-x86_64-280.13.run 
sudo service lightdm stop 
sleep 30 && sudo killall -s KILL X
cd
cd nvidia_driver
sudo ./NVIDIA-Linux-x86_64-280.13.run (Answer Yes, Yes, Yes, Yes, Yes, Yes, etc)
sudo service lightdm start (but *sudo reboot now* is preferred)

```**EDIT**
You know what, don't be an idiot like me. Instead of starting lightdm after installing the driver, do a proper reboot like a normal human being is supposed to.

[B]EDIT 2
[/B]Code humanized. Run this thing on a VT. Once it stops lightdm and kills X there goes your terminal window.

I just noticed _64!!  I have a 32 bit system. I know the PCIe card is 64 bit.

---

### Post by lucazade on 2011-09-29
> **ventrical said:**
> I just noticed _64!!  I have a 32 bit system. I know the PCIe card is 64 bit.

yes.. and a ps2 mouse is 12bit... it doesn't matter the pcie card.

---

### Post by ventrical on 2011-09-29
Ahhh

dale@ubuntu:~/nvidia_driver$ sudo ./NVIDIA=Linux-x86-280.13.run
usage: sudo -h | -K | -k | -L | -V
usage: sudo -v [-AknS] [-g groupname|#gid] [-p prompt] [-u user name|#uid]
usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U user name] [-u
            user name|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u user
            name|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u user
            name|#uid] file ...
dale@ubuntu:~/nvidia_driver$ sudo ./NVIDIA-Linux-x86-280.13.run
[sudo] password for dale: 
sudo: ./NVIDIA-Linux-x86-280.13.run: command not found
dale@ubuntu:~/nvidia_driver$ sudo ./NVIDIA-Linux-x86-280.13. run
sudo: ./NVIDIA-Linux-x86-280.13.: command not found
dale@ubuntu:~/nvidia_driver$ dir
NVIDIA-Linux-x86_64-280.13.run
dale@ubuntu:~/nvidia_driver$ sudo ./NVIDIA-Linux-x86_64-280.13.run

ERROR: this .run file is intended for the
Linux-x86_64 platform, but you appear to be
running on Linux-x86.  Aborting installation.

dale@ubuntu:~/nvidia_driver$

---

### Post by ventrical on 2011-09-29
> **effenberg0x0 said:**
> Well, it depends on the card. For example, my favorite desktop has a GTS450. Its a card known for running a little hot although it is power efficient (fermi). See [http://www.anandtech.com/show/3909/nvidias-geforce-gts-450-pushing-fermi-in-to-the-mainstream/16](http://www.anandtech.com/show/3909/nvidias-geforce-gts-450-pushing-fermi-in-to-the-mainstream/16) . There's a chart with temperatures on "idle" and "load" (running crysis).

Your is a mobile unit, but is known for getting a little hot too. [http://forum.notebookreview.com/sony/273654-geforce-8400m-gt-idle-temperatures.html#post3690121](http://forum.notebookreview.com/sony/273654-geforce-8400m-gt-idle-temperatures.html#post3690121)

Different architectures: hard to compare tdps, temperatures.

Regards,
Effenberg

Nope... not a mobile unit.. not the one with the nvidia card. Tower Desktop!

---

### Post by effenberg0x0 on 2011-09-29
Sorry, I was under the impression you were talking about a GeForce 8400m, which is a laptop VGA ([http://www.nvidia.com/object/geforce_8400M.html](http://www.nvidia.com/object/geforce_8400M.html)). That's the OP card, my bad.

You can download both the 32-bit and 64-bit NVidia 280.13 driver at NVidia website without using wget as I had suggested, of course. 
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

You'll just have to chmod them +x and sudo sh the correct .run file. It has to be done at a VT, no X session running, which is why I suggested stopping lightdm, killing X remains before executing.

Regards,
Effenberg

---

### Post by sgage on 2011-09-29
> **effenberg0x0 said:**
> Well, it depends on the card. For example, my favorite desktop has a GTS450. Its a card known for running a little hot although it is power efficient (fermi). See [http://www.anandtech.com/show/3909/nvidias-geforce-gts-450-pushing-fermi-in-to-the-mainstream/16](http://www.anandtech.com/show/3909/nvidias-geforce-gts-450-pushing-fermi-in-to-the-mainstream/16) . There's a chart with temperatures on "idle" and "load" (running crysis).

Your is a mobile unit, but is known for getting a little hot too. [http://forum.notebookreview.com/sony/273654-geforce-8400m-gt-idle-temperatures.html#post3690121](http://forum.notebookreview.com/sony/273654-geforce-8400m-gt-idle-temperatures.html#post3690121)

Different architectures: hard to compare tdps, temperatures.

Regards,
Effenberg

Hard to compare temps between different cards, but I'm talking about the temperature delta between nouveau and nvidia drivers on the same card. This difference is around 18-20 degrees C. Something is wrong with the nouveau drivers.

If you have a card that is "known for getting a little hot", you will want to stay away from nouveau...

---

### Post by lucazade on 2011-09-29
> **sgage said:**
> Hard to compare temps between different cards, but I'm talking about the temperature delta between nouveau and nvidia drivers on the same card. This difference is around 18-20 degrees C. Something is wrong with the nouveau drivers.

If you have a card that is "known for getting a little hot", you will want to stay away from nouveau...

Nouveau Driver Power Management Against The NVIDIA Blob
[http://www.phoronix.com/scan.php?page=article&item=nouveau_power_comparison&num=1](http://www.phoronix.com/scan.php?page=article&item=nouveau_power_comparison&num=1)

---

### Post by el_koraco on 2011-09-29
> **sgage said:**
>  Something is wrong with the nouveau drivers.


It's extremely simple. Nouveau and radeon don't have the frequency downclocking abilities of nvidia and fglrx. Higher clock, higher temperatures. You can set radeon to do some kind of frequency management via xorg.conf, but it's not in the same league. None of this really surprises me, ATI and Nvidia usually take years to set stuff up properly with Windows once the driver ABI is changed, so you can only imagine what a bunch of open source enthusiasts can do with reverse engineering and halfassed documentation.

---

### Post by effenberg0x0 on 2011-09-29
> **effenberg0x0 said:**
> My memory clock with NVidia-Proprietary: Oscillates between 125MHz and 1500MHz
My memory clock with Nouveau: Fixed at 1804MHz. Go figure.


> **el_koraco said:**
> 
It's extremely simple. Nouveau and radeon don't have the frequency  downclocking abilities of nvidia and fglrx. Higher clock, higher  temperatures. You can set radeon to do some kind of frequency management  via xorg.conf, but it's not in the same league. None of this really  surprises me, ATI and Nvidia usually take years to set stuff up properly  with Windows once the driver ABI is changed, so you can only imagine  what a bunch of open source enthusiasts can do with reverse engineering  and halfassed documentation.     


> **sgage said:**
> 
Hard to compare temps between different cards, but I'm talking about the  temperature delta between nouveau and nvidia drivers on the same card.  This difference is around 18-20 degrees C. Something is wrong with the  nouveau drivers.
 
 If you have a card that is "known for getting a little hot", you will want to stay away from nouveau...


Exactly. Moreoever, on nouveau, I can see the GTS450 running actually overclocked in comparison to the proprietary driver. It certainly justifies the temperature.

However, I think it's important to mention that there are people reporting hotter cards even with the proprietary driver. My only theory is that these people maybe were not using a hw accelerated desktop back in previous Ubuntu and now they are, which would mean the card is not "as idle as before".

Regards,
Effenberg

---

### Post by el_koraco on 2011-09-29
> **effenberg0x0 said:**
> 
However, I think it's important to mention that there are people reporting hotter cards even with the proprietary driver. My only theory is that these people maybe were not using a hw accelerated desktop back in previous Ubuntu and now they are, which would mean the card is not "as idle as before".

Regards,
Effenberg

I can reverse-attest to that. With Compiz, my card was idling at 50-55 C. With scrotwm and no compositing, it's at a steady 45-48. All with fglrx.

---

### Post by cariboo on 2011-09-29
Using the closed source driver, my Geforce 210 runs at 40-45°C. See screenshot

---

### Post by sgage on 2011-09-29
"My only theory is that these people maybe were not using a hw accelerated desktop back in previous Ubuntu and now they are, which would mean the card is not "as idle as before".

Could be, but so what? Forget comparing one card to another. Or one load to another.

The point is this ...

Same card
Same load
Same computer
Same conditions
Same ambient temperature

Nouveau runs 18-20 degrees C hotter than nvidia. Up the load, and nouveau still runs 18-20 degrees hotter. It's been reported by many many people over the months (if not years).

I've replicated this on 2 different rigs, 2 different nvidia cards. It's clear as crystal.

Something is wrong with nouveau. If they are overclocking, why? Heat is the enemy of semiconductors - they really need to deal with this.

---

### Post by effenberg0x0 on 2011-09-29
Not to mention the environmental issues. Nouveau developers can't sleep well at night knowing their driver clearly contributes to global heating just so we can have faster and fancier glxgears in our boxes. We should torch them.

Regards,
Effenberg

PS: CoTG (Cult of The Gear) guys will probably shot me first.

---

### Post by ventrical on 2011-09-29
> **cariboo907 said:**
> Using the closed source driver, my Geforce 210 runs at 40-45°C. See screenshot


  I dropped down to the 3.0.0-11 kernel and my temp dropped own by 11 C.

---

### Post by sgage on 2011-09-29
> **effenberg0x0 said:**
> Not to mention the environmental issues. Nouveau developers can't sleep well at night knowing their driver clearly contributes to global heating just so we can have faster and fancier glxgears in our boxes. We should torch them.

Regards,
Effenberg

PS: CoTG (Cult of The Gear) guys will probably shot me first.

Ah yes! I never thought of the Global Warming angle! :KS

---

### Post by el_koraco on 2011-09-29
> **effenberg0x0 said:**
> S It has to be done at a VT, no X session running, which is why I suggested stopping lightdm, killing X remains before executing.

Is this really the case or are you just being too careful? fglrx from AMD's site has an install GUI, you don't need to run amdconfig --initial anymore, and stuff like that, even though all the guides recommend stopping X partially or completely.

---

### Post by effenberg0x0 on 2011-09-29
[LEFT]No, as far as I know it stops the install if it detects X. It has been that way for some time, I believe it still is. On the other hand, adding a KILLALL instead of a ps ax | grep -i or pidof piping to a kill, using a -s KILL signal instead of a more usual signal, and also a sleep 30s, is something I wouldn't do myself cause its totally overkill: But that is supposed to work for any clueless folk that might read the help forum and paste it in a terminal. Same for wget instead of "go download the driver" ... But, from what I seen, most helpers also post more basic/bulletproof commands instead of the more compact ones. It's a good practice. You see, I care LOL :)

Regards,
Effenberg


[/LEFT]

---

### Post by mc4man on 2011-10-02
Here on a laptop with a 04/01 cooling system (dell 1300m/ nvidia 8400m) while there is a small diff between nouveau & nvidia, there is a huge diff between kernel versions.

The latest was producing an almost unusable front left case temp - the ram is front middle, I think front left is HDD

The idle & at use cpu temp was also increased ( though with this laptop ambient temp is also a big factor

Switching back to a 2.6 kernel has made a huge difference here - 10 - 15+ C on the cpu, even more so on the front case temp

At least for me good riddance to the 3.whatever kernel

---

