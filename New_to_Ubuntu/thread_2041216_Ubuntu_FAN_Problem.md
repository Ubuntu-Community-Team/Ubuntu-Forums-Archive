---
title: "Ubuntu FAN Problem"
date: 2012-08-12
forum: New to Ubuntu
---

### Post by balkrish999 on 2012-08-12
I have, a  [SIZE=1][/SIZE]HP - Compaq Presario CQ61-330SA Laptop

and installed Ubuntu, latest version, and installed all the updates, problem is that my Fan is very very loud and is always ON, 
 
How can i make it work normally?[SIZE=1] [SIZE=2]and how do i check my Laptops CPU Temperature[/SIZE] 

Thank You
[/SIZE]

---

### Post by GreatDanton on 2012-08-12
To check Cpu temperature install lm-sensors. In terminal type:```
sudo apt-get install lm-sensors
```

After installation type:
```
sudo sensors-detect
```
Answer yes on all questions and that's it.

After that if you want to check temperature type ```
sensors
``` in terminal.

---

### Post by balkrish999 on 2012-08-12
> **GreatDanton said:**
> To check Cpu temperature install lm-sensors. In termin
After that if you want to check temperature type ```
sensors
``` in terminal.


Thanks, but what about the FAN Problem? Which is always ON

---

### Post by dummy910 on 2012-08-12
a program called Jupiter solved this exact problem for me just recently.  

install the program and it loads into the panel upon startup and I selected 'power saving' from the 'performance' section of the drop-down menu... works like a charm it does.

[http://www.jupiterapplet.org/index.html](http://www.jupiterapplet.org/index.html)

---

### Post by Petro Dawg on 2012-08-12
> **dummy910 said:**
> a program called Jupiter solved this exact problem for me just recently.  

install the program and it loads into the panel upon startup and I selected 'power saving' from the 'performance' section of the drop-down menu... works like a charm it does.

[http://www.jupiterapplet.org/index.html](http://www.jupiterapplet.org/index.html)

ditto

---

### Post by balkrish999 on 2012-08-12
How do i download it?


From here :
[http://www.jupiterapplet.org/downloads.html](http://www.jupiterapplet.org/downloads.html)

i go to here?  then what ?

[https://launchpad.net/~webupd8team/+archive/jupiter](https://launchpad.net/~webupd8team/+archive/jupiter)

where do i download it? thanks

---

### Post by ub07 on 2012-08-12
Just want to add that psensor is a great program that will give you a graph of your sensor data so you can keep an eye on the temperatures as read by the sensors. You can get psensor in the software center.

---

### Post by balkrish999 on 2012-08-12
Installed Jupitar but no luck, Fan is Still on and Temperature is 75*Degrees C  and on windows its around 50.

---

### Post by mr-woof on 2012-08-12
Did this have windows on before? If yes, was the fan loud then? It could be that the laptop is overheating, hence the fan on full and it needs a clean. Dust keeps the heat in..

---

### Post by Mark Phelps on 2012-08-12
Sorry to be the bearer of bad news ... but ... there is a known kernel bug with recent Ubuntu versions that prevents it from throttling the CPU back on idle -- hence, it's running all the time, getting hot, and driving the fan.

Since Jupiter did not work, unless someone comes up with a hack that does (unlikely, but possible), continuing to run the laptop while it is overheating like this risks permanent damage.

While it will most likely shut off suddenly when it gets too hot, to save the CPU, all that heat is shortening the life of the hard drive and other components.

This is an ongoing problem that was only fixed for SOME processors in 12.04.

---

### Post by ub07 on 2012-08-12
> **Mark Phelps said:**
> Sorry to be the bearer of bad news ... but ... there is a known kernel bug with recent Ubuntu versions that prevents it from throttling the CPU back on idle -- hence, it's running all the time, getting hot, and driving the fan.

Since Jupiter did not work, unless someone comes up with a hack that does (unlikely, but possible), continuing to run the laptop while it is overheating like this risks permanent damage.

While it will most likely shut off suddenly when it gets too hot, to save the CPU, all that heat is shortening the life of the hard drive and other components.

This is an ongoing problem that was only fixed for SOME processors in 12.04.

This is very worrisome to me. I too have a laptop running 12.04 that overheats and turns itself off, although it does so randomly as the temperature will suddenly increase and within a few seconds it will reach the trip point of 100 degrees C.

HOWEVER, I've been helped by the good people here and we have set my ATI GPU power profile to "low" and that seems to really have helped matters, and I have not had a shutdown since. I'm wondering if the OP has graphics driver problem too.

Also, it looks like my CPU is throttling back in the system monitor.

Can you please provide more information/links as to the nature of the bug and for what processors it has been fixed because, as I've said, I'm worried?

Edit: I have spent considerable time researching this bug, and it appears that Canonical has applied patches to the 3.2 kernel that should resolve this issue (even though it will not be addressed in the generic kernel until 3.3). The bug apparently affected mainly Intel processors which the OP does not have. This, of course, does not mean that there isn't still a problem, but it is a reason to look elsewhere for a possible solution.

---

### Post by balkrish999 on 2012-08-13
> **mr-woof said:**
> Did this have windows on before? If yes, was the fan loud then? It could be that the laptop is overheating, hence the fan on full and it needs a clean. Dust keeps the heat in..


Its on a dual boot,  and No This does not happen with windows and im 99% sure its nothing to do with the dust. something else.

---

### Post by balkrish999 on 2012-08-14
So what can i do?

---

### Post by NikTh on 2012-08-14
> **balkrish999 said:**
> So what can i do?

Hi , 
can you give the results of 

```
lscpu 
lspci -nnk | grep -iA2 vga
sensors
```Thanks

---

### Post by balkrish999 on 2012-08-15
> **NikTh said:**
> Hi , 
can you give the results of 

```
lscpu 
lspci -nnk | grep -iA2 vga
sensors
```Thanks

Here, it is  --???  Whats Use does that do? or have????

>     
Architecture:          i686
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    2
Socket(s):             1
Vendor ID:             AuthenticAMD
CPU family:            16
Model:                 6
Stepping:              2
CPU MHz:               800.000
BogoMIPS:              4388.86
Virtualisation:        AMD-V
L1d cache:             64K
L1i cache:             64K
L2 cache:              512K
krishna@ubuntu:~$ lspci -nnk | grep -iA2 vga
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series] [1002:9712]
    Subsystem: Hewlett-Packard Company Device [103c:363f]
    Kernel driver in use: fglrx_pci

---

### Post by NikTh on 2012-08-15
> **balkrish999 said:**
> Here, it is  --???  Whats Use does that do? or have????

Hi , 
first command is only info about cpu and I can see that you installed a 32bit OS to a 64 capable Cpu. You could install Ubuntu 64 bit. (better behavior - faster )

Second command,  I can see you use closed source driver (fglrx) instead of pre-installed driver (radeon). If you used radeon , maybe with one command we could drop the temperature of graphic card .. but..

....I cannot see 3rd command ```
sensors
``` . Do you installed lm-senors package ? 
Open a terminal and do.. ```
sudo apt-get install lm-sensors
sudo sensors-detect
``` 
in 2nd command hit Enter to all questions .. 
reboot your PC and give the results of
```
sensors
``` so we can see the temperature. 
Thanks

---

### Post by balkrish999 on 2012-08-16
> **NikTh said:**
> Hi , 
first command is only info about cpu and I can see that you installed a 32bit OS to a 64 capable Cpu. You could install Ubuntu 64 bit. (better behavior - faster )

Second command,  I can see you use closed source driver (fglrx) instead of pre-installed driver (radeon). If you used radeon , maybe with one command we could drop the temperature of graphic card .. but..

....I cannot see 3rd command ```
sensors
``` . Do you installed lm-senors package ? 
Open a terminal and do.. ```
sudo apt-get install lm-sensors
sudo sensors-detect
```in 2nd command hit Enter to all questions .. 
reboot your PC and give the results of
```
sensors
``` so we can see the temperature. 
Thanks


Here

acpitz-virtual-0
Adapter: Virtual device
temp1:        +47.0°C  (crit = +100.0°C)

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +48.6°C  (high = +70.0°C)
                       (crit = +115.5°C, hyst = +110.5°C)



And, the fan is cool but is always blowing, i installed 64 bit version but it went even more Hot the fan, how do i disable the Graphics Card Driver? from additional drivers?

Edit i went additional drivers and removed that one

---

### Post by NikTh on 2012-08-16
Hi , 
temperature seems to be OK . 

> ```
acpitz-virtual-0
Adapter: Virtual device
temp1:        +47.0°C  (crit = +100.0°C)

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +48.6°C
```I don't understand why fan works all the time and pc closes . 
If you uninstalled fglrx driver (yes from additional drivers) then you must now have the radeon open source driver. 
The result of this command 
```
lspci -nnk | grep -iA2 vga
``` should return 
```
Kernel driver in use : radeon
```You can apply a command and see if fan - temperature behavior better . 
Apply from terminal 
```
sudo -i 
echo low >  /sys/class/drm/card0/device/power_profile
exit
```wait 30 seconds and then give this command 
```
cat /sys/class/drm/card0/device/power_profile
``` should return 
```
low
```Above code is not permanent . Is for one session only. If meet your needs (drop temp) and you want to make it permanent we can add it to rc.local. 
Thanks

---

### Post by Mark Phelps on 2012-08-16
For those who asked, the link below is to the kernel bug:

[https://bugs.launchpad.net/ubuntu/+source/cpufreqd/+bug/901232]("https://bugs.launchpad.net/ubuntu/+source/cpufreqd/+bug/901232")

---

### Post by blortuga on 2012-08-27
Intel® Core™ i7-3612QM CPU @ 2.10GHz × 8 . . .

I have lm-sensors installed, dell-devices, 12.04 64-bit.

I went through many conniptions trying to get cpu temperature, throttling, ati driver, and fan speed to "work".

It nominally works - (at least it's safe; it rarely throttles so high that it overheats, so I assume that the kernel fixes for THIS CPU are in-place).

But, I needed to set up Conky to monitor CPU temperature, throttling, and fan speed.  Since this laptop is pretty much a beast, I generally keep the CPU throttled at a minimum (manually) with the indicator-bar widget.  The CPU usually sticks around 44 to 48 C, but the fan runs full-blast with the dell-devices kernel extension running.

If I use i8kfan to slow the fan down, the temperature usually remains tame, unless I throttle up the CPU.   On-demand auto scaling usually works pretty well also.  But if the CPU ramps up after I have manually slowed the fan, heat will climb until either the laptop overheats (I never let that happen) - I need to either shut down the process, or manually (use i8kfan) to increase the fan speed.

On very CPU-intensive and high-IO tasks, if I set the CPU to Performance or even OnDemand - the fan, running at full-blast, is insufficient to keep this system cool, and manual intervention is required.  An example of this is the Amarok script for scanning a music library for moodbar data, in parallel for all CPUs. I got my CPUs up to 80 C fans at full blast, and the CPUs wouldn't scale back. - and I had to shut the script down.  I don't know if this is an issue with the scaling/fan algorithm in the kernel, or if it's an engineering issue with the cooling system of the laptop.  (most likely the former - but it's an unusually abusive scenario).

---

