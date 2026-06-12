---
title: "Power consumption raised significantly in natty: fix released"
date: 2011-09-22
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lucazade on 2011-09-22
```
SRU Justification:

Impact: Since 2.6.36 (23016bf0d25), Linux prints the existence of "epb" in /proc/cpuinfo,
    Since 2.6.38 (d5532ee7b40), the x86_energy_perf_policy(8) utility has
    been available in-tree to update MSR_IA32_ENERGY_PERF_BIAS.

    However, the typical BIOS fails to initialize the MSR, presumably
    because this is handled by high-volume shrink-wrap operating systems...

    Linux distros, on the other hand, do not yet invoke x86_energy_perf_policy(8).
    As a result, WSM-EP, SNB, and later hardware from Intel will run in its
    default hardware power-on state (performance), which assumes that users
    care for performance at all costs and not for energy efficiency.
    While that is fine for performance benchmarks, the hardware's intended default
    operating point is "normal" mode...

    Initialize the MSR to the "normal" by default during kernel boot.

    x86_energy_perf_policy(8) is available to change the default after boot,
    should the user have a different preference.

Patch: commit abe48b108247e9b90b4c6739662a2e5c765ed114 upstream

Changed in linux (Ubuntu Natty):
assignee:	 Canonical Kernel Team (canonical-kernel-team) &#8594; Tim Gardner (timg-tpi)
status:	 Confirmed &#8594; In Progress
Tim Gardner (timg-tpi) on 2011-09-21
Changed in linux (Ubuntu Natty):
status:	 In Progress &#8594; Fix Committed

```
at least for natty the fix is commited and patch was sent upstream .. soon on our oneiric screens? :)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131)

---

### Post by kaldor on 2011-09-22
woah, I'll be checking this out for sure. Natty and Fedora work fine for me, but Oneiric killed my battery in under 15 minutes. Pretty odd though since this regression should have affected me on kernels 2.6.38 and 2.6.40.

---

### Post by makitso on 2011-09-22
Yup, my T60 Thinkpad  takes about 2.5 hours to kill the battery doing nothing, 11.10 takes 20 minutes.

---

### Post by ventrical on 2011-09-22
I'm going to test this with my Acer Extensa.

---

### Post by effenberg0x0 on 2011-09-22
I have a Dell and a Lenovo laptop which were dying quick on Natty no matter what I tried in terms of workarounds. Desktops with personal APC UPS were also down in 2/3 of average time. Hope this fixes it. 

But, more importantly (for me): I use a script to log sensors, smartd / hddtemp, apcupsd, CPU load, etc and report to a server every n minutes, so I can import the csv on Excel and run a macro to graph / use statistics on it, to detect when a machine is overloaded, some HDD will fail, some cooler stopped, PSU is off limits, etc. 

Looking at the generated spreadsheet, I was kind of worried about some 10%-20% average increase in CPU temperatures (desktops and laptops) in some machines when running idle on Natty, in comparison to Maverick ones, and was currently lost on finding the culprit. I think it might solve some of these thermal issues.

Thanks,
Effenberg

---

### Post by MacUntu on 2011-09-22
Does anyone know what hardware is affected by that change? My Arrandale CPU (i5-560M) currently seems to run at its lowest frequency when idle (ondemand setting I guess).

> because this is handled by high-volume shrink-wrap operating systems

Ouch, that sounds a bit like envy. :P

---

### Post by fjgaude on 2011-09-22
> **MacUntu said:**
> Does anyone know what hardware is effected by that change? My Arrandale CPU (i5-560M) currently seems to run at its lowest frequency when idle (ondemand setting I guess).

> because this is handled by high-volume shrink-wrap operating systems

Ouch, that sounds a bit like envy. :P

My Intel i5 seems to have its voltage changed as demand changes... so maybe things are okay with 11.10, should get better with the next kernel update. It's set to lowest voltage at startup. Do you know of a panel indicator I could use; now I'm with gkrellm.

---

### Post by flipper T on 2011-09-22
i could be imagining things, but since the start of this week my laptop is noticeably quieter and cooler.

as for battery life, no idea, it died many years ago.

---

### Post by cariboo on 2011-09-22
After running:

```
sudo powertop --calibrate
```

on my Compaq Mini 1100, I get about 3hrs. usage when running on the 3 cell battery.

---

### Post by ventrical on 2011-09-22
> **cariboo907 said:**
> After running:

```
sudo powertop --calibrate
```on my Compaq Mini 1100, I get about 3hrs. usage when running on the 3 cell battery.


 I tried this command in Edubuntu 11.04 in Unity and it said 'command not found' so is this exclusive to Oneiric only I pressume ?

---

### Post by MacUntu on 2011-09-22
Yes, Natty includes the powertop version that is useful but doesn't have that command, while the one in Oneiric kinda sucks as it doesn't report wakeups: [https://bugs.launchpad.net/ubuntu/+source/powertop/+bug/834725](https://bugs.launchpad.net/ubuntu/+source/powertop/+bug/834725)

---

### Post by ventrical on 2011-09-22
I just tried it on Oneiric on an Acer Extensa and it says the same thing that is said in natty - 'command not found'!


Ok... I dled  from synaptic and get this:

dale@ubuntu:~$ sudo powertop --calibrate
[sudo] password for dale: 
sudo: powertop: command not found
dale@ubuntu:~$ sudo -i sudo powertop --calibrate
sudo: powertop: command not found
dale@ubuntu:~$ sudo powertop --calibrate
[sudo] password for dale: 
Cannot load from file /var/cache/powertop/saved_results.powertop
Cannot load from file /var/cache/powertop/saved_parameters.powertop
Starting PowerTOP power estimate calibration 
Calibrating idle
Calibrating: disk usage 
Calibrating backlight
.... device /sys/class/backlight/acpi_video0/brightness 
Calibrating idle
Calibrating: CPU usage on 1 threads
Calibrating: CPU usage on 4 threads
Calibrating: CPU wakeup power consumption
Calibrating: CPU wakeup power consumption
Calibrating: CPU wakeup power consumption
Calibrating USB devices
.... device /sys/bus/usb/devices/usb1/power/control 
.... device /sys/bus/usb/devices/usb2/power/control 
.... device /sys/bus/usb/devices/usb3/power/control 
.... device /sys/bus/usb/devices/usb4/power/control 

etc...

took right  over.
wireless also goes on again - off again

---

### Post by flipper T on 2011-09-22
silly question, but have you installed powertop ?

---

### Post by ventrical on 2011-09-22
> **flipper T said:**
> silly question, but have you installed powertop ?

:)

Doh. :)

It has been a long day :)

---

### Post by cariboo on 2011-09-22
> **ventrical said:**
> I just tried it on Oneiric on an Acer Extensa and it says the same thing that is said in natty - 'command not found'!


Ok... I dled  from synaptic and get this:

dale@ubuntu:~$ sudo powertop --calibrate
[sudo] password for dale: 
sudo: powertop: command not found
dale@ubuntu:~$ sudo -i sudo powertop --calibrate
sudo: powertop: command not found
dale@ubuntu:~$ sudo powertop --calibrate
[sudo] password for dale: 
Cannot load from file /var/cache/powertop/saved_results.powertop
Cannot load from file /var/cache/powertop/saved_parameters.powertop
Starting PowerTOP power estimate calibration 
Calibrating idle
Calibrating: disk usage 
Calibrating backlight
.... device /sys/class/backlight/acpi_video0/brightness 
Calibrating idle
Calibrating: CPU usage on 1 threads
Calibrating: CPU usage on 4 threads
Calibrating: CPU wakeup power consumption
Calibrating: CPU wakeup power consumption
Calibrating: CPU wakeup power consumption
Calibrating USB devices
.... device /sys/bus/usb/devices/usb1/power/control 
.... device /sys/bus/usb/devices/usb2/power/control 
.... device /sys/bus/usb/devices/usb3/power/control 
.... device /sys/bus/usb/devices/usb4/power/control 

etc...

took right  over.
wireless also goes on again - off again

It does take 3 -4 minutes to calibrate after you run the command, on my systems the screen blanks a couple of times, and the wireless light goes on and off a couple of times. The one unfortunate things is that the settings can't be save, so you have to do the calibration every time you use the laptop/netbook on battery.

---

### Post by alphacrucis2 on 2011-09-22
Interesting. I wonder if the patch will be accepted upstream.

---

### Post by ventrical on 2011-09-22
Whoops then. I think I busted my battery because I re-booted before it was done it's routine and now I got %3 critical of what was once giving me 1 hour and 45 mins on Linux Mint.

---

### Post by ventrical on 2011-09-22
Ok .. I got my battery back on my other Acer.  It was a strange bug that the battery dropped down to %3 in like 2 minutes.

Also I could not get the  Unity Screen to come up.

There is something right from the get -go that affects the battery-geometry even before the install of PowerTop.

 Now it will just purr on Linux Mint for about 2 hours.

 Don't mean to be off topic or off-distro. Just reporting a battery-reportage-anomoly.

---

### Post by keithpeter on 2011-09-22
> **makitso said:**
> Yup, my T60 Thinkpad  takes about 2.5 hours to kill the battery doing nothing, 11.10 takes 20 minutes.

I have a T60-1952 (early, with 1024/768 graphics). Would I see this booting from cd-rom or only if installed?

---

### Post by ventrical on 2011-09-22
Heres a screenshot from Mint 10.

1/2 hour and it only dropped to %99 and Iv'e been surfing  for that half hour.

  I have another smaller hhd with Oneiric on it and am going to try that with powerTop.

---

### Post by ventrical on 2011-09-22
Yep... just too jumpy for me!  I got it working but when I went to take a screenshot it went into a panic, but did not crash. The fluctuations really swing from hi to low .. so it is hard to get a good reading and one can't really do anything in that mode. Perhaps as a static machine it may last a while - but  it renderers my PC relatively useless to do any work.  Sure hope they get this one fixed.

---

