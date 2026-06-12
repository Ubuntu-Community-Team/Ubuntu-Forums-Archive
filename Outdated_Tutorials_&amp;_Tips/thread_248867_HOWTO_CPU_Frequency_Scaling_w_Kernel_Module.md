---
title: "HOWTO: CPU Frequency Scaling w/ Kernel Module"
date: 2006-09-01
forum: Outdated Tutorials &amp; Tips
---

### Post by pharcyde on 2006-09-01
I thought I would write a little howto on how to get cpu frequency scaling to work directly with the kernel modules.  These modules are generally more efficient for performance computing and battery life.

**Prerequisites**
kernel >= 2.6.9

**Step 1: Enable BIOS Support**
Enter your BIOS at boot and make sure Cool'n'Quiet (AMD) or SpeedStep (Intel) is enable for you CPU.  Some BIOS may not have  option at all.  If that is the case it is probably enabled by default.  Other BIOS may have the option but it is listed as another name altogether.  If that is the case check your BIOS manual for more info.

**Step 2: Remove Userspace Scaling Software**
powernowd
```
sudo apt-get remove powernowd
```
cpudyn
```
sudo apt-get remove cpudyn
```

**Step 3: Install CPU Module**
Identify your cpu type by runnig the command
```
cat /proc/cpuinfo
```
You can also Check the following links
AMD CPU Chart - [http://www.tomshardware.com/2005/11/21/the_mother_of_all_cpu_charts_2005/page20.html](http://www.tomshardware.com/2005/11/21/the_mother_of_all_cpu_charts_2005/page20.html)
Intel CPU Chart - [http://www.tomshardware.com/2005/11/21/the_mother_of_all_cpu_charts_2005/page21.html](http://www.tomshardware.com/2005/11/21/the_mother_of_all_cpu_charts_2005/page21.html)

[COLOR="Green"]AMD Sempron/Athlon/MP ( K7 )[/COLOR]
Socket Types: A, Slot A
```
sudo modprobe powernow-k7
```
[COLOR="Green"]AMD Duron/Sempron/Athlon/Opteron 64 ( K8 )[/COLOR]
Socket Types: 754, 939, 940, S1 ( 638 ), AM2 ( 940 ), F ( 1207 )
```
sudo modprobe powernow-k8
```
[COLOR="Blue"]Intel Core Duo[/COLOR]
```
sudo modprobe speedstep-centrino
```
[COLOR="Blue"]Intel Pentium M[/COLOR]
```
sudo modprobe speedstep-centrino
```
[COLOR="Red"]Others (Unknown)[/COLOR]
I'm not entirely sure which cpus are supported using this module.  If your cpu doesn't work with one of the above methods try this one.
```
sudo modprobe acpi-cpufreq
```

**Step 4: Scaling Modules**
```

sudo modprobe cpufreq_conservative
sudo modprobe cpufreq_ondemand
sudo modprobe cpufreq_powersave
sudo modprobe cpufreq_stats
sudo modprobe cpufreq_userspace

```

**Step 5: Testing/Configuration**
Show Available Governors
```

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors

```
You should see output similar to
```

powersave conservative ondemand performance

```

[COLOR="Blue"]conservative[/COLOR]
Description: CPU frequency is scaled based on load in incremental steps up and down.
```

sudo -s
echo conservative > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```
Advanced Configuration Options
```
cd /sys/devices/system/cpu/cpu0/cpufreq/conservative
```

[COLOR="Blue"]ondemand[/COLOR]
Description: CPU frequency is scaled based on load.
```

sudo -s
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```
Advanced Configuration Options
```
cd /sys/devices/system/cpu/cpu0/cpufreq/ondemand
```

[COLOR="Blue"]performance[/COLOR]
Description: CPU only runs at max frequency regardless of load.
Configuration Dir: N/A
```

sudo -s
echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```

[COLOR="Blue"]powersave[/COLOR]
Description: CPU only runs at min frequency regardless of load.
Configuration Dir: N/A
```

sudo -s
echo powersave > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```

**Step 6: Load Modules at Boot**
Add the following lines to the end of /etc/modules
```

cpufreq_conservative
cpufreq_ondemand
cpufreq_powersave
cpufreq_stats
cpufreq_userspace
[COLOR="Red"][Module from Step 3][/COLOR]

```

**Step 7: Configure Modules at Boot**
This step needs to be done in order for the modules to retain your settings.
Make sure you have sysfsutils installed 
```
sudo apt-get install sysfsutils
```
Then add the following lines to /etc/sysfs.conf
```
devices/system/cpu/cpu0/cpufreq/scaling_governor=[COLOR="Blue"]ondemand[/COLOR]
```
Where [COLOR="Blue"]ondemand[/COLOR] can be changed to another governor type (i.e. conservative, powersave, etc.).  You can also add other configuration options that are specific to the governor selected.

**Useful Links**
[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)
[http://martin.ankerl.org/category/linux/](http://martin.ankerl.org/category/linux/)
[http://gentoo-wiki.com/HOWTO_Undervolt_a_Pentium_M_CPU](http://gentoo-wiki.com/HOWTO_Undervolt_a_Pentium_M_CPU)
[http://wejp.k.vu/projects/howto_cnq_athlon_64_x2/](http://wejp.k.vu/projects/howto_cnq_athlon_64_x2/)

---

### Post by gumbeto on 2006-09-02
Hi, I was trying to follow your "How To" because, since yesterday, the cpu governors stoped working for me and I get always the maximum frequency, regardless of the load.
When I got to step 4, however, I got this error:

FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.15-26-386/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): Device or resource busy

I have no idea what I am doing wrong and I  would apreciate any help.
Thanx a lot
gumbeto

---

### Post by foxy123 on 2006-09-02
> Step 4) Intel CPU Module
Code:

sudo modprobe speedstep-centrino



I have an Intel CPU, but it uses acpi_cpufreq instead of speedstep-centrino. I am not sure if it is important.

---

### Post by gumbeto on 2006-09-02
do u know how can I check if my cpu is like yours in that aspect?
thanks

---

### Post by gumbeto on 2006-09-02
do u know how can I check if my cpu is like yours in that aspect?
thanks

---

### Post by HAARP on 2006-09-02
Athlon user should use **powernow-k7**
Athlon 64 users **powernow-k8**

Doesn't work for me tho. Probably because I have a Mobile CPU on an old desktop board

```
FATAL: Error inserting powernow_k7 (/lib/modules/2.6.15-26-k7/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k7.ko): No such device

```

Frequency scaling worked under Windoze.

---

### Post by pharcyde on 2006-09-02
Thanks for replies guys.  I've updated the how-to with better information related to different devices.  I only have a AMD64 k8 and Intel Pentium M Centrino.  These two work for me with the methods I've outlined here in Breezy 32bit and 6.06 64bit installs.  I will try to update it with more information related to other AMD and Intel chips once I have more info from others.

---

### Post by gumbeto on 2006-09-02
hi again. In my case, the contents of /proc/cpuinfo is the following:

```
gumbeto@gumbeto-laptop:/lib/modules/2.6.15-26-386/kernel/arch/i386/kernel/cpu/cpufreq$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 2.00GHz
stepping        : 8
cpu MHz         : 798.116
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe est tm2
bogomips        : 1598.35


```

As I said, the module speedstep-centrino didn't work for me so I tried 

```
sudo modprobe acpi-cpufreq
```

It didn't complain and I continued with the tutorial but unfortunatly it didn't solve my problem. I think I'll post my problem in a separate thread when I have time, after searching for any related posts.
Anyway, thanks for the tutorial and for the replies

Gumbeto

---

### Post by rigor on 2006-09-03
Hi friends,
for my centrino i use this utility on winxp
[http://www.pbus-167.com/]("http://www.pbus-167.com/"), to control not only cpu multipler, but also CPU multipler, and bus of ati card. =D> =D> 

and i find this for linux
[http://gentoo-wiki.com/HOWTO_Undervolt_a_Pentium_M_CPU]("http://gentoo-wiki.com/HOWTO_Undervolt_a_Pentium_M_CPU")

of course ... i'm very noobye....of linux, so i'm waiting for your comments. :-\" :-\"

---

### Post by nolodude on 2006-09-03
I have Asus K8V-MX mobo with Sempron 2600+ which does support Cool 'n Quiet in Windows, but apparently it doesn't work well with Powernowd in Linux.

I tried modprobe powernow-k8, modprobe acpi-cpufreq and even modprobe powernow-k7 but they all give the same error: 
```
# modprobe powernow-k8
FATAL: Error inserting powernow_k8 (/lib/modules/2.6.15-26-k7/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k8.ko): No such device

```

Guess I'm out of luck here, or what?

---

### Post by foxy123 on 2006-09-03
> **nolodude said:**
> I have Asus K8V-MX mobo with Sempron 2600+ which does support Cool 'n Quiet in Windows, but apparently it doesn't work well with Powernowd in Linux.

I tried modprobe powernow-k8, modprobe acpi-cpufreq and even modprobe powernow-k7 but they all give the same error: 
```
# modprobe powernow-k8
FATAL: Error inserting powernow_k8 (/lib/modules/2.6.15-26-k7/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k8.ko): No such device

```

Guess I'm out of luck here, or what?

it should be k8 as far as I know.

---

### Post by pharcyde on 2006-09-03
Yes the Sempron 2600+, is actually a K8 device.

---

### Post by rannyman on 2006-09-03
> 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 9
model name      : Intel(R) Pentium(R) M processor 1500MHz
stepping        : 5
cpu MHz         : 598.145
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 tm pbe est tm2
bogomips        : 1197.64


Everything goes fine until step 5:
> $ echo conservative > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
bash: /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor: Permission denied

Any Ideas?

---

### Post by foxy123 on 2006-09-03
> **rannyman said:**
> Everything goes fine until step 5:

Any Ideas?

do the following
```
sudo -s
echo conservative > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

---

### Post by rannyman on 2006-09-03
> **foxy123 said:**
> do the following
```
sudo -s
echo conservative > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

That did it.
Still getting use to using sudo. I moved from debian to I am use to 'su' to do what I need.

---

### Post by Paulo Wageck on 2006-09-04
Thanks!
Like a charm...
Now I can do folding@#home at 100% CPU .... 
AvatarX@FAH (Ubuntu Team)

---

### Post by pcolamar on 2006-09-08
Pharcyde, 
  I wonder if Step6 should refer to Step3 rather than Step2 (see below).
Am I wrong ?

Cheers

---Quote --
Step 6: Load Modules at Boot
Add the following lines to the end of /etc/modules
Code:

cpufreq_conservative 
cpufreq_ondemand 
cpufreq_powersave 
cpufreq_stats 
cpufreq_userspace 
[Module from **Step 2**]  <--------- **Step3** maybe !?

---

### Post by pharcyde on 2006-09-08
Thanks proclamar. You are quite right!  I will fix this immediately.

> **pcolamar said:**
> Pharcyde, 
  I wonder if Step6 should refer to Step3 rather than Step2 (see below).
Am I wrong ?

Cheers

---Quote --
Step 6: Load Modules at Boot
Add the following lines to the end of /etc/modules
Code:

cpufreq_conservative 
cpufreq_ondemand 
cpufreq_powersave 
cpufreq_stats 
cpufreq_userspace 
[Module from **Step 2**]  <--------- **Step3** maybe !?

---

### Post by pcolamar on 2006-09-10
Is there any graphic application to switch among the different freq.scaling config's ?

"cat xxxxx >/......"  is not very practical

I used to use Kpowersave but it work with cpufreqd and powersaved !

How can I replace it ?


Thanks

---

### Post by mcgrawj on 2006-09-10
Thanks for the tutorial, seems very helpful, but I'm sad to say that I'm getting stumped.

I'm running a Sempron 2600+ (slot 757), my BIOS settings say that Cool'n'Quiet is enabled, and there's another CPU setting enabled along the lines of 'CPU stepping'. I've removed Powernowd.

When I run 'cat /proc/cpuinfo', it reads:
```
# cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 28
model name      : AMD Sempron(tm) Processor 2600+
stepping        : 0
cpu MHz         : 1608.050
cache size      : 128 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt 3dnowext 3dnow
bogomips        : 3217.83

```

Now, when I try to install the CPU module, I get:
```
# modprobe powernow-k8
FATAL: Error inserting powernow_k8 (/lib/modules/2.6.15-26-server/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k8.ko): No such device

```

It's the same story for the generic ACPI and the K7. I see that others are having the same issue, same processor.

Has anyone got the Sempron 2600+ to work? Is there something obvious I'm missing? I guess that I should point out I'm attemtping this is Ubuntu-Server-6.06.

Thanks

---

### Post by ephman on 2006-09-11
thanks for the howto!  awesome now my machine feels like it should with all the speed i have under the hood.  noticed such a huge difference, no lagging now.  whew...  using the performance option.  great stuff.

thanks,
ephman

---

### Post by Buddha443556 on 2006-09-11
> I'm running a Sempron 2600+ (slot 757), my BIOS settings say that Cool'n'Quiet is enabled, and there's another CPU setting enabled along the lines of 'CPU stepping'. I've removed Powernowd.
AFAIK any (non-mobile) Sempron less than 3000+ does not have Cool'n'Quiet. 

Check [AMD Athlon™ 64 Processor Power and Thermal Data Sheet]("http://www.amd.com/us-en/assets/content_type/white_papers_and_tech_docs/30430.pdf") [[COLOR="Red"]PDF[/COLOR]] to be sure. The datasheet for the CPU needs to show at least Min P-State to be a Cool'n'Quiet CPU. The more P-States the better.

---

### Post by Pootas on 2006-09-11
Now this may sound like a n00b question but Im running an AMD64 3200+ on a K7 kernel so under /ect/modules I know I have to put

cpufreq_conservative
cpufreq_ondemand
cpufreq_powersave
cpufreq_stats
cpufreq_userspace
[Module from Step 3]

But how should the last line look ie:

[powernow-k8] 
or
powernow-k8

Do you see what I mean....I've done everything else I'm just a bit confused about how the last line should be formatted...

Thanks in advance

---

### Post by jdong on 2006-09-11
Just as an FYI, in Edgy Eft ondemand will be automatically loaded in favor of powernowd by the powernowd startup script, if your CPU can use ondemand without choking (SpeedSteps and other older-generation CPU's had considerable delays on frequency switches, so they will be using powernowd instead)

---

### Post by pcolamar on 2006-09-12
No [], just 

powernow-k8

PC

---------------
> **Pootas said:**
> Now this may sound like a n00b question but Im running an AMD64 3200+ on a K7 kernel so under /ect/modules I know I have to put

cpufreq_conservative
cpufreq_ondemand
cpufreq_powersave
cpufreq_stats
cpufreq_userspace
[Module from Step 3]

But how should the last line look ie:

[powernow-k8] 
or
powernow-k8

Do you see what I mean....I've done everything else I'm just a bit confused about how the last line should be formatted...

Thanks in advance

---

### Post by Pootas on 2006-09-12
> **pcolamar said:**
> No [], just 

powernow-k8

PC

---------------

I've tried that but my CPU remains at 2.2Ghz....

CPU scaling was working with Powernowd till I changed from a 386 kernel to K7... Maybe there is some issue there but I just cannot get it to work...

---

### Post by pcolamar on 2006-09-13
Well, actually I have got similar problem too.

No matter what I was choosing in Step7, the laptop was always going back to Performance configuration after a while.

Furthermore, I have not be able to find an other GUI to the scaling_governor.

I prefered to go back to powersaved in order to use Kpowersave GUI even if I have the impression that powernow-k8 (my cpu is Turion 64) reacts faster and better in ondemand mode.


I'll check this Thread periodically to see if there is any change

---

### Post by juve on 2006-09-15
Problems: with Athlon XP mobile 2000+ on Desktop-PC (mobo: ECS K7S5A chipset: SiS735)

I get the same errors as some of you:
```
FATAL: Error inserting powernow_k7 (/lib/modules/2.6.15-26-k7/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k7.ko): No such device

```

I tried to get proper CPU scaling on FC5 some time ago, but did not succeed.

[LIST=1]
[*]I read somewhere that i had to recompile my kernel with cpufreq support.
[*]I read that i had to manually edit the freq_tables because my CPU would not be properly detected
[/LIST]

nevertheless, here's some output:
```
juve@juve:~$ cat /proc/cpuinfo processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 8
model name      : mobile AMD Athlon(tm) XP 2000+
stepping        : 1
cpu MHz         : 1673.940
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow
bogomips        : 3349.70

```

Does anybody know if it is possible to get cpu-freq support (without kernel recompiling) for my setup

Thx,
Juve

---

### Post by HAARP on 2006-09-16
This could be of interest:
[http://www.yggdrasl.demon.co.uk/code/](http://www.yggdrasl.demon.co.uk/code/)
We need someone to compile the powernow-k7 module with this patch for the Ubuntu kernel. I'm looking into this, but don't expect anything yet.

btw, I don't have the "no such device errors" anymore. Now I get this:
```
#modprobe powernow-k7; dmesg | tail -n 4
FATAL: Error inserting powernow_k7 (/lib/modules/2.6.15-26-k7/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k7.ko): Unknown symbol in module, or unknown parameter (see dmesg)
[17580497.260000] powernow_k7: disagrees about version of symbol cpu_data
[17580497.260000] powernow_k7: Unknown symbol cpu_data
[17580549.700000] powernow_k7: disagrees about version of symbol cpu_data
[17580549.700000] powernow_k7: Unknown symbol cpu_data

```

edit: Should've rebooted after kernel update.


```

# modprobe powernow_k7; dmesg | tail -n 7
FATAL: Error inserting powernow_k7 (/lib/modules/2.6.15-26-k7/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k7.ko): No such device
[17179674.576000] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[17179674.580000] powernow: No PST tables match this cpuid (0x7a0)
[17179674.580000] powernow: This is indicative of a broken BIOS.
[17179674.580000] powernow: Trying ACPI perflib
[17179674.580000] powernow: ACPI perflib can not be used in this platform
[17179674.580000] powernow: ACPI and legacy methods failed
[17179674.580000] powernow: See http://www.codemonkey.org.uk/projects/cpufreq/powernow-k7.shtml
```

---

### Post by pharcyde on 2006-09-18
I believe a lot of you are having problems because the bios does not have a processor state table available.  If that is the case, then the kernel modules will not work.

There are a few options.

1) Try to get an updated bios with support with ptable support for your cpu.

2) Recompiling the kernel as suggested by others. Look at the following links.

[http://www.yggdrasl.demon.co.uk/code/](http://www.yggdrasl.demon.co.uk/code/) (Provided by HAARP)
[http://wejp.k.vu/projects/howto_cnq_athlon_64_x2/](http://wejp.k.vu/projects/howto_cnq_athlon_64_x2/) (At the bottom of the howto instructions)

---

### Post by HAARP on 2006-09-19
> **pharcyde said:**
> I believe a lot of you are having problems because the bios does not have a processor state table available.  If that is the case, then the kernel modules will not work.

Yup. That's exactly it.

> 
1) Try to get an updated bios with support with ptable support for your cpu.

No can do, my BIOS isn't being maintained anymore. Too old.

> 2) Recompiling the kernel as suggested by others. Look at the following links.
Wouldn't a kernel module suffice?

---

### Post by Rollerbob on 2006-09-20
This may help some people. I'm running an Athlon 64 X2 dual core machine and finally got Cool 'n' Quiet working (not sure about the 'Quiet' bit but that's probably because of my cheapo PSU!)

I installed the K8 SMP kernel using Synaptic and followed the instructions in this howto. However I, like others, got the following error:

[PHP]# modprobe powernow-k8
FATAL: Error inserting powernow_k8 (/lib/modules/2.6.15-26-k7/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k8.ko): No such device[/PHP]

I was pretty sure that I had enabled the Cool'n'Quiet in the BIOS of my motherboard (ASUS A8V-VM). However, being a bit of a noob, I had only enabled 'Power Management' thinking this was the name for Cool'n'Quiet.

After rooting around in the BIOS interface, I found the real Cool'n'Quiet option, so I enabled it and this solved all the problems.

Incidentally, because I have two CPUs, I have a line for each in my /etc/sysfs.conf. I assume this is correct.

[PHP]devices/system/cpu/cpu0/cpufreq/scaling_governor=ondemand
devices/system/cpu/cpu1/cpufreq/scaling_governor=ondemand[/PHP]

---

### Post by igsimon on 2006-09-29
I have Ondemad set up per this HOW TO. It works when I first boot up switching frequencies fine. After a short time it seems to stick at the highest frequency setting when I do not seem to have any load. I have AMD64 X2 processor.

---

### Post by igsimon on 2006-09-30
ondemand is working fine -  turnsout BEAGLED somehow is getting in a state that it uses 100% of cpu for long periods of time

---

### Post by Nabor on 2006-11-16
Why is this entry of all modules in /ets/modules necessary?

I know, it's necessary because without this entries the powersaved doesn't work during system startup (edgy) but it works when restarting it manualy...

I want to understand that... what is the difference?

Because the modules will be loaded in both cases otherwise a manualy restart auf powersaved would also fail or not?

Nabor

---

### Post by linuxguiri on 2006-11-22
> **jdong said:**
> Just as an FYI, in Edgy Eft ondemand will be automatically loaded in favor of powernowd by the powernowd startup script, if your CPU can use ondemand without choking (SpeedSteps and other older-generation CPU's had considerable delays on frequency switches, so they will be using powernowd instead)

Does this imply that either the speedstep or powernow module is also loaded?

I have a Core 2 Duo T5600 and I'm having trouble with the cpu freq being locked at maximum after resume from suspend. 

I tried following this howto (removing powernowd and installing modules) but the max. cpufreq continued and it broke network manager after resume from suspend.

So then, I tried reinstalling powernowd and removing the modules, but I can't remove the speedstep-centrino or the cpufreq-ondemand modules because they are in use. Is this because powernowd is calling both of them?

---

### Post by dutchmega on 2006-11-26
I'm wondering if the voltage is also being lowered. I don't want to use Cool & Quiet because I have overclocked my CPU and when the voltage drops, it gets a bit unstable

---

### Post by lazyd2 on 2006-11-27
I believe that in **"Step 5"** for Dual Core processors it should be> sudo -s
echo conservative > /sys/devices/system/cpu/**cpu0**/cpufreq/scaling_governor
echo conservative > /sys/devices/system/cpu/**cpu1**/cpufreq/scaling_governor
and again the same in /etc/sysfs.conf```
devices/system/cpu/**cpu0**/cpufreq/scaling_governor=ondemand
devices/system/cpu/**[B]cpu1**[/B]/cpufreq/scaling_governor=ondemand
```

Thanks for the how to=D>

---

### Post by gotak on 2006-12-14
I tired this and my cpu freq is stuck a 1 ghz what gives?

---

### Post by Lomz on 2006-12-19
Hi

thanks for a wonderfull howto, mi problem is that when I restart the computer it seems like it somehow doest remember this settings, and I need to run all the commands again.
And I am not using a live cd...

Anybody has an idea about how to solve this?

---

### Post by pixelboy on 2006-12-23
Hey guys..

IS this how-to the best way to get my AMD X2 4600+ up to speed on my EDGY AMD64 install?

She's running at half pace :(


> processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4600+
stepping        : 2
cpu MHz         : 1000.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni cx16 lahf_lm cmp_legacy svm cr8_legacy
bogomips        : 2011.80
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4600+
stepping        : 2
cpu MHz         : 1000.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni cx16 lahf_lm cmp_legacy svm cr8_legacy
bogomips        : 2011.80
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

---

### Post by Lomz on 2006-12-27
> **Lomz said:**
> Hi

thanks for a wonderfull howto, mi problem is that when I restart the computer it seems like it somehow doest remember this settings, and I need to run all the commands again.
And I am not using a live cd...

Anybody has an idea about how to solve this?

Nobody knows?

---

### Post by cb474 on 2007-02-24
If I use this method for frequency scaling, instead of the default use of powernowd, is there a way to automatically have different settings when on ac and when on battery? I want to use ondemand for ac and conservative for battery.

Also, does this method mean that the settings in the Power Management Preferences window no longer do anything? Should those settings, especially "prefer power savings over performance," be turned off in order not to conflict with the frequency governor set up in this how-to?

Thanks.

---

### Post by bodycoach2 on 2007-02-25
I used this when I had dapper on my machine, and it worked. I was able to throttle my cpu from 300 MHz, up to 2.8 GHz. I found that going lower than 1 GHz didn't increase battery life, but I used 1.4 when I was on batteries. I used the instructions from the Ubuntu document storage facility, but that site no longer comes up.

I upgraded to edgy, but now when I try to modprobe speedstep-centrino, it give me there error (not found). I tried the acpi one too, but no luck.

I know frequency scaling works on this computer, but with the upgrade to edgy, I can't get it going.

---

### Post by bodycoach2 on 2007-02-27
> **bodycoach2 said:**
> I used this when I had dapper on my machine, and it worked. I was able to throttle my cpu from 300 MHz, up to 2.8 GHz. I found that going lower than 1 GHz didn't increase battery life, but I used 1.4 when I was on batteries. I used the instructions from the Ubuntu document storage facility, but that site no longer comes up.

I upgraded to edgy, but now when I try to modprobe speedstep-centrino, it give me there error (not found). I tried the acpi one too, but no luck.

I know frequency scaling works on this computer, but with the upgrade to edgy, I can't get it going.

Ubuntu Document Storage Facility is back up. I found the answer:

> sudo modprobe p4_clockmod

Frequency scaling is working. Most excellent.

---

### Post by jbmech006 on 2007-03-15
I am having the same problem with the clock speed being stuck at 1Ghz. I followed the steps and everything was working great until I restarted. After I restarted the CPU freq was stuck at 1Ghz. I ran through the steps again with no success. I tried to run  $sudo modprobe p4_clockmod and got the following error "FATAL: Error inserting p4_clockmod (/lib/modules/2.6.17-11-386/kernel/arch/i386/kernel/cpu/cpufreq/p4-clockmod.ko): Device or resource busy" Do I need to kill some process before I attempt to run that command? Thanks for any help you guys have.

---

### Post by jbmech006 on 2007-03-15
I should have posted this above, this is my CPU information:

Intel Core Duo
processor: 0
vendor_id: GenuineIntel
cpu family: 6
model: 14
model name: Genuine Intel(R) CPU T2400  @ 1.83GHz
stepping: 8
cpu MHz: 1000.000
cache size: 2048 KB
fdiv_bug: no
hlt_bug: no
f00f_bug: no
coma_bug: no
fpu: yes
fpu_exception: yes
cpuid level: 10
wp: yes
flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pni monitor vmx est tm2 xtpr
bogomips: 3661.77

---

### Post by Steve White on 2007-03-15
pharcyde,

You might also want to point out to your duller readers that if they have dual cores, they should repeat the governor setting for each core. (Would have helped me.)

---

### Post by jbmech006 on 2007-03-15
Yeah I have instances of the scaling_governor for each cpu, so that's not the problem. Still need input on how to fix the scaling support.

---

### Post by fNNR on 2007-04-02
Hi

I'm a super-noob, and I don't quite understand step 6. Could someone maybe explain it a little better for me, perhaps with an example of what to type in at the kernel?

Thanks in advance!

---

### Post by ptitpoul on 2007-04-04
With Feisty Fawn (updated from edgy), step 6 (Add modules in /etc/modules) is not necessary, at least on my PC (amd athlon 64 with powernow-k8). So, pharcyde, maybe you should precise for which release it's necessary.

---

### Post by fidolip on 2007-04-04
Hi!

I tried to follow your HOWTO and everything seemed to be alright, but when I restarted my computer I got a message:

```

CPU frequency scaling unsupported
You will not be able to modify the frequency of your machine. Your machine might be misconfigured or not have hardware support for CPU frequency scaling.

```

and now my CPU freq is always on it's maximum. Could someone help me with either changing it back to how it used to be or fixing this problem?

Processor is Intel Centrino and I have dapper drake.

---

### Post by Joriz on 2007-04-04
> **Lomz said:**
> Hi

thanks for a wonderfull howto, mi problem is that when I restart the computer it seems like it somehow doest remember this settings, and I need to run all the commands again.
And I am not using a live cd...

Anybody has an idea about how to solve this?

I have the same problem here hmz

Nevermind,  i placed something wrong in modules.conf hehe, works fine now, nice tutorial

---

### Post by cdeel77 on 2007-04-05
Thanks for the great HOWTO!

I tried doing this with my Pentium 4 (1.4 GHz; family 15 model 0 stepping 7) running Edgy Server.

I used the "p4_clockmod" module. I checked the CPU freq with 3 methods:
```
cat /proc/cpuinfo
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq
cpufreq-info
```
Before loading module, freq was 1406.274 (seems normal, right?)
After loading module, was 2200.000

**Is my CPU *really* running at 2.2 GHz? **If so, that could be a bad (overheating) thing, right? And how did that happen?

Output of cpufreq-info:
```
analyzing CPU 0:
  driver: p4-clockmod
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 550 MHz - 2.20 GHz
  available frequency steps: 550 MHz, 825 MHz, 1.10 GHz, 1.38 GHz, 1.65 GHz, 1.93 GHz, 2.20 GHz
  available cpufreq governors: performance
  current policy: frequency should be within 550 MHz and 2.20 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 2.20 GHz.
```
Should I just use "cpufreq-set --max 1375000" to limit the top speed, or do I have an unusual problem?

I've also tried loading the generic "acpi-cpufreq" module, but I get "FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.17-11-server/kernel/arch/i386/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device"

Thanks for any help/advice! (Just trying to reduce power consumption/heat buildup on my lightly-used home server. I intend to use "ondemand" governor.)

---

### Post by jbmech006 on 2007-04-10
I posted earlier in this forum about a problem I was having after I followed the steps listed in the howto. Basically my CPU scaling was unsupported after I rebooted and was locked at 1.83ghz (I have an Intel Core Duo processor). To fix the problem I installed the powernowd package from synaptic package manager. Rebooted Gnome (Ctrl-Alt-Backspace) and now my CPU scaling support is working again. I hope this helps people with a similar problem.

---

### Post by bobreeves on 2007-04-14
Thanks for this most helpful post. I screwed around for days trying to get powernowd or cpudyn working with absolutely no success. 

With your tutorial, I now have CPU scaling functioning on my Toshiba Satellite, and running in demand mode. I am running a Parsix distro (Knoppix based), and knew that CPU scaling should work, as it worked by default in Ubuntu.

Great job!

Bob Reeves

---

### Post by Adahn on 2007-04-28
when I attempt to 'sudo modprobe powernow-k8' I get this error:

FATAL: Error inserting powernow_k8 (/lib/modules/2.6.20-15-generic/kernel/arch/x86_64/kernel/cpufreq/powernow-k8.ko): No such device

I get a similar error with modprobe acpi-cpufreq

this:  cpufreq-info
gets me this:  no or unknown cpufreq driver is active on this CPU

anyideas?

I'm running a mobile athlon64 in a desktop board.  Scaling works fine in windows.

tony@tony-desktop:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 36
model name      : Mobile AMD Athlon(tm) 64 Processor 3400+
stepping        : 2
cpu MHz         : 910.719
cache size      : 1024 KB
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm
bogomips        : 1822.84
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

---

### Post by aerowinged on 2007-05-09
I followed this tutorial, 
But when i got to part my CPU0 does not have the directory. So instead i just finished the tutorial with CPU1. But when i restarted the computer, i still got the "CPU Scaling unsupported" message.
Could it not be working because i am missing this directory from my CPU0 folder. Where can i get the necessary files to replace it?

I also tried this: 
I installed cpufreqd. And in the details this is what i got. (just the last 2 lines)

> :Setting up cpufreqd 2.2.1-2 ... 
No cpufreq interface installed, not starting cpufreqd 

So then i installed powernowd which automatically uninstalled cpufreqd. And this is was it said at the end of the details

> * Starting powernowd...
/etc/init.d/powernowd: 156: cannot create /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor: Directory nonexistent
* CPU frequency scaling not supported
...done. 

So i think that this missing directory i have in CPU0 in the cause of the whole problem. What can i do!? CPU Scaling works fine in windows, so i know its not my hardware.



Here are the details of my processor:

> processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz
stepping        : 6
cpu MHz         : 1828.859
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3661.16
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz
stepping        : 6
cpu MHz         : 1828.859
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3657.81
clflush size    : 64

Please help me! thanks guys

---

### Post by kaar3l on 2007-05-17
My T5600 works out of box, on 1000mhz and 1800mhz. i use kubuntu

---

### Post by matburton on 2007-05-24
Hey,

I'm using Feisty and want to set my governor to conservative at boot. But everything I try doesn't seem to work.

I made a script that runs with run level 2 that did either
```

sudo cpufreq-selector -g conservative

```
or
```

echo conservative > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```

But both didn't work and swapping from run level 2, down to 1 and back up to 2 showed that the governor was just set back to ondemand whatever it was previously.

Then I tried installing and using sysfsutils by changing /etc/sysfs.conf but that had no effect either.

Is Feisty different?
How do I set the default governor in feisty?

Thanks, Mat

**Edit:**
I fixed my problem. I had a look at how powernowd starts in /etc/init.d and edited the script slightly to always set the governor to conservative.
I quick sudo /etc/init.d/powernowd restart confirmed that this worked ;)

---

### Post by skymera on 2007-06-01
i get that same error!!
i got Intel Core 2
and i tried all of em, no luck!!!!

puzzling.

---

### Post by lakofka on 2007-06-17
I'm getting the error about /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor too.
I've got an HP Pentium M laptop (dv1325EA). 
Anyone know why this isn't working?

---

### Post by jcdx on 2007-06-19
> **Adahn said:**
> when I attempt to 'sudo modprobe powernow-k8' I get this error:

FATAL: Error inserting powernow_k8 (/lib/modules/2.6.20-15-generic/kernel/arch/x86_64/kernel/cpufreq/powernow-k8.ko): No such device

I get a similar error with modprobe acpi-cpufreq

this:  cpufreq-info
gets me this:  no or unknown cpufreq driver is active on this CPU

anyideas?

I'm running a mobile athlon64 in a desktop board.  Scaling works fine in windows.

tony@tony-desktop:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 36
model name      : Mobile AMD Athlon(tm) 64 Processor 3400+
stepping        : 2
cpu MHz         : 910.719
cache size      : 1024 KB
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm
bogomips        : 1822.84
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc
.

I have the same problem
# sudo modprobe powernow-k8
FATAL: Error inserting powernow_k8 (/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k8.ko): No such device

# dmesg | grep AMD
[   14.329800] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-50 stepping 02
[   14.420697] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-50 stepping 02
[    1.964000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[  439.392000] powernow-k8: Found 2 AMD Turion(tm) 64 X2 Mobile Technology TL-50 processors (version 2.00.00)
[  826.332000] powernow-k8: Found 2 AMD Turion(tm) 64 X2 Mobile Technology TL-50 processors (version 2.00.00)
[  829.912000] **powernow: This module only works with AMD K7 CPUs**

I can start powernowd with out any error message.
I installed kubuntu 7.04 32 bit version and found the this problem does not occur in the amd64 version. But I want the 32 bit version. Is there a way to get the powernow working ?

Regards jcdx

---

### Post by skaramanger on 2007-07-10
Greetings fellow Ubuntu users struggling with frequency scaling.
I'm having a devil of a time with my Gateway SOLO 5300.  The specs. as per Gateways site claims acpi 1.1 support and apm support.  I have initially tried powernowd, but switched to cpufreqd upon reading this thread.  I get and error messages when cpufreqd tries to start:
stating to the effect that /sys/devices/system/cpu/cpu0/cpufreq/scaling_govenor doesn't exist and frequency scaling is not supported.  When I tried to create the folder myself:

root@tzlaptop:~# mkdir /sys/devices/system/cpu/cpu0/cpufreq
mkdir: cannot create directory `/sys/devices/system/cpu/cpu0/cpufreq': Operation not permitted
root@tzlaptop:~# 

I'm running Feisty 7.04:

terry@tzlaptop:~$ uname -a
Linux tzlaptop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux


root@tzlaptop:~# modprobe acpi-cpufreq
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device

But locate finds it:

root@tzlaptop:~# locate acpi-cpufreq.ko | grep generic
/lib/modules/2.6.20-15-generic/kernel/arch/i386/kernel/cpu/cpufreq/acpi-cpufreq.ko
/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/cpu/cpufreq/acpi-cpufreq.ko
root@tzlaptop:~# 



terry@tzlaptop:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 8
model name      : Pentium III (Coppermine)
stepping        : 1
cpu MHz         : 501.181
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
bogomips        : 1003.33
clflush size    : 32


modules loaded:

terry@tzlaptop:~$ lsmod
Module                  Size  Used by
speedstep_lib           6148  0 
ppdev                  10116  0 
savage                 34048  2 
drm                    81044  3 savage
sony_acpi               6284  0 
tc1100_wmi              8068  0 
dev_acpi               12292  0 
pcc_acpi               13184  0 
dock                   10268  0 
container               5248  0 
button                  8720  0 
video                  16388  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
battery                10756  0 
ac                      6020  0 
ipv6                  268960  8 
af_packet              23816  2 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8200  0 

ACPI messages:

terry@tzlaptop:~$ dmesg | grep ACPI
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001ffffc00 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ffffc00 - 0000000020000000 (ACPI NVS)
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6a90
[    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040001  LTP 0x00000000) @ 0x1fff9b81
[    0.000000] ACPI: FADT (v001 GATEWA SOLO5300 0x06040001 PTL  0x000f4240) @ 0x1ffffb65
[    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040001  LTP 0x00000001) @ 0x1ffffbd9
[    0.000000] ACPI: DSDT (v001 GATEWA SOLO5300 0x06040001 MSFT 0x0100000b) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[   17.160097] ACPI: Core revision 20060707
[   17.161337] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   17.168269] ACPI: setting ELCR to 0200 (from 0e00)
[   17.170877] ACPI: bus type pci registered
[   17.189927] ACPI: Interpreter enabled
[   17.189942] ACPI: Using PIC for interrupt routing
[   17.190812] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   17.190888] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   17.195703] PCI quirk: region 8000-803f claimed by PIIX4 ACPI
[   17.196578] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   17.207941] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[   17.208776] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[   17.209558] ACPI: PCI Interrupt Link [LNKC] (IRQs *11)
[   17.210364] ACPI: PCI Interrupt Link [LNKD] (IRQs 11) *9
[   17.372052] pnp: PnP ACPI init
[   17.489851] pnp: PnP ACPI: found 12 devices
[   17.489867] PnPBIOS: Disabled by ACPI PNP
[   17.490041] PCI: Using ACPI for IRQ routing
[   17.498812] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[   17.498834] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   17.499446] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[   17.499457] ACPI: PCI Interrupt 0000:00:08.1[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   20.312122] ACPI: (supports S0 S3 S4 S5)
[   22.213265] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   22.213285] ACPI: Processor [CPU0] (supports 8 throttling states)
[   10.648000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   10.648000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   24.460000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   24.460000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   25.128000] ACPI: PCI Interrupt 0000:06:00.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   38.480000] ACPI: AC Adapter [AC0] (on-line)
[   38.512000] ACPI: Battery Slot [BAT0] (battery present)
[   38.516000] ACPI: Battery Slot [BAT1] (battery absent)
[   38.748000] ibm_acpi: IBM ThinkPad ACPI Extras v0.13
[   38.848000] ACPI: Power Button (CM) [PWRB]
[   38.872000] ACPI: Sleep Button (CM) [SLPB]
[   39.308000] ACPI: ACPI Dock Station Driver 
[   73.172000] ACPI: EC: acpi_ec_wait timeout, status = 0, expect_event = 1



I could use some help here!

TIA

---

### Post by shame on 2007-07-14
I followed all the instructions and got no errors anywhere.
I tried setting everything to ondemand for both cpu0 and cpu1 and and according to boot messages, cpu frequency scaling was set to ondemand.

Next I tried setting everything (/etc/sysfs.conf, devices/system/cpu/cpu0/cpufreq/scaling_governor, devices/system/cpu/cpu1/cpufreq/scaling_governor) to performance to see if there was any difference in performance.
I've double checked it all but the boot message still says both cpu's are set to ondemand.

AMD 64 Athlon X2 3800+

---

### Post by clickwir on 2007-08-07
Hey this was a great post. I recently switched motherboards and went from an Intel P4 3ghz to AMD Athlon X2 4000. Didn't reinstall Kubuntu Feisty, just swapped motherboards and booted up. (Windows had a hissy fit, but that's why I rarely use it) But none of the power management functions were working.

It was just stuck at 2100MHz all the time. Followed the steps in the OP and it's working great now. Idles down to 1000MHz just like it should.

cat /proc/cpuinfo

```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 107
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
stepping        : 1
cpu MHz         : 1000.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc [6]
bogomips        : 2001.70
clflush size    : 64

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 107
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
stepping        : 1
cpu MHz         : 1000.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc [6]
bogomips        : 2001.70
clflush size    : 64
```

cat /etc/sysfs.conf

```
devices/system/cpu/cpu0/cpufreq/scaling_governor=ondemand
devices/system/cpu/cpu1/cpufreq/scaling_governor=ondemand
```

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors

```
userspace powersave ondemand conservative performance
```

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```
ondemand
```

cat /etc/modules

```
lp
fuse
cpufreq_conservative
cpufreq_ondemand
cpufreq_powersave
cpufreq_stats
cpufreq_userspace
powernow-k8

```

---

### Post by litemotiv on 2007-08-11
does anyone know how to use frequency scaling with an overclocked processor? my core2duo is clocked @ 3ghz, but with cpu scaling turned on it just varies between 1.6ghz and 2.4ghz (stock values).

i tested it on winxp too, cpu scaling there does use overclocked values of 2ghz and 3ghz.

thanks for any tips. ;)

---

### Post by Adahn on 2007-08-11
> **litemotiv said:**
> does anyone know how to use frequency scaling with an overclocked processor? my core2duo is clocked @ 3ghz, but with cpu scaling turned on it just varies between 1.6ghz and 2.4ghz (stock values).

i tested it on winxp too, cpu scaling there does use overclocked values of 2ghz and 3ghz.

thanks for any tips. ;)

I have this issue with my athlon 3600x2.  It scales down/up with powernowd normally but only to the stock speeds.

Installing cpufreq as per this thread gives the 'cpu scaling not supported' error.  Clock speed stays at the maximum (overclocked) speed of 2.95 GHz.  Strangely, system power usage (measured at the outlet with a kill-a-watt meter) is roughly the same idling at 2.95GHz in Ubuntu as it is downclocked/undervolted in Windows with rmclock.

I looked into editing the module files for cpufreq and powernow in Ubuntu to add the overclocked speeds but don't have permission to open the files.

---

### Post by cb474 on 2007-08-12
This guide says to use the speedstep-centrino module with Core Duo processors, but it doesn't work for me on my ThinkPad T60. Instead I have to use the acpi-cpufreq module.

Strangely, in Edgy I followed the same instructions on this laptop and the speedstep-centrino module worked. But not now in Feisty.

Is something wrong here?

---

### Post by litemotiv on 2007-08-14
> **Adahn said:**
> I have this issue with my athlon 3600x2.  It scales down/up with powernowd normally but only to the stock speeds.

Installing cpufreq as per this thread gives the 'cpu scaling not supported' error.  Clock speed stays at the maximum (overclocked) speed of 2.95 GHz.  Strangely, system power usage (measured at the outlet with a kill-a-watt meter) is roughly the same idling at 2.95GHz in Ubuntu as it is downclocked/undervolted in Windows with rmclock.

I looked into editing the module files for cpufreq and powernow in Ubuntu to add the overclocked speeds but don't have permission to open the files.

i submitted a launchpad entry for it:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/132403](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/132403)

---

### Post by BOBSONATOR on 2007-08-22
Guys, Check out my cpu-freq info

> cpufreq-infocpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  driver: centrino
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 600 MHz - 1.80 GHz
  available frequency steps: 600 MHz, 800 MHz, 1000 MHz, 1.20 GHz, 1.40 GHz, 1.60 GHz, 1.80 GHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 1.40 GHz and 1.40 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 1.40 GHz.


can someone help asap? its a  dothan centrino, and im going on a plane soon and need max batt.

THANKS IN ADVANCE!

---

### Post by Rhawi Dantas on 2007-08-25
Hi there, 

I have a Dell Inspiron 9400 Centrino Duo 1.6Ghz.

I followed the tutorial and ething was perfect till the time I rebooted.

The governor policy went back to performance instead of the one Ive set before, powersave.

Is there a way of me telling Ubuntu to every time on reboot set to powersave instead of performance ?

Thanks.

---

### Post by Rhawi Dantas on 2007-08-26
bump ?

---

### Post by foxy123 on 2007-08-27
> **Rhawi Dantas said:**
> bump ?

I wonder what ```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
``` gives you?

---

### Post by Rhawi Dantas on 2007-08-28
After rebooting performance.

But when i already configured everything its powersave. And everytime i need to reconfigure to be powersave and then after reboot it becomes performance.

---

### Post by foxy123 on 2007-08-28
> **Rhawi Dantas said:**
> After rebooting performance.

But when i already configured everything its powersave. And everytime i need to reconfigure to be powersave and then after reboot it becomes performance.

Do you manually edit /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor?

---

### Post by Rhawi Dantas on 2007-08-28
Well, just did and when i restarted the thing came back to the older configuration.

Maybe is something wrong with the script that initialize the stuff...

Any ideas

---

### Post by foxy123 on 2007-08-28
> **Rhawi Dantas said:**
> Well, just did and when i restarted the thing came back to the older configuration.

Maybe is something wrong with the script that initialize the stuff...

Any ideas

is powersave available at all? try
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
```

---

### Post by st33med on 2007-08-28
Need help. The directory cpufreq is missing. I couldn't make this work, so I rebooted, tried to reinstall powernowd, but it is not available, and, instead, installs powersaved. I found a powernowd package online, installed it, but it didn't run. It gives me error messages that directories and files inside cpufreq don't exist. Then, it runs slllllloooooooowwwwwwwww... reinstalled powersaved (since I had uninstalled it before I installed powernowd) and everything runs faster. However, I need powernowd to detect P states on powertop.

Can anybody help?

---

### Post by Rhawi Dantas on 2007-08-29
powersave is available just if i put the settings while im using the notebook. If i restart it i wont have powersave and no other options, just _ondemand_.

---

### Post by foxy123 on 2007-08-29
> **Rhawi Dantas said:**
> powersave is available just if i put the settings while im using the notebook. If i restart it i wont have powersave and no other options, just _ondemand_.

Have you put all the required modules in the /etc/modules?

---

### Post by Rhawi Dantas on 2007-08-30
Thats my /etc/modules
```

lp
sbp2
i8k force=1
fuse
cpufreq_conservative
cpufreq_ondemand
cpufreq_powersave
cpufreq_stats
cpufreq_userspace
acpi-cpufreq

```

Any ideas ?

---

### Post by Rhawi Dantas on 2007-09-01
bump bump bump :guitar:

---

### Post by tim202 on 2007-09-06
I'm having some trouble getting the instructions on the first page of this thread to work.  I've got a Toshiba laptop running a Celeron M processor, running Feisty 7.04 kernel vers. 2.6.20-16-generic.  None of the kernel module modprobe commands are able to find anything.  If anyone has any experience doing this on a Celeron M i'd really appreciate any input.

Thanks,
TIM

---

### Post by HangLoose on 2007-09-10
I'm also having problems with a Dell.
When I restart the notebook its not with the previous settings anymore. I need to edit again the scaling_max_freq to 10000 so its showing...

Weird thing though, is there anyone who's having the same stuff

---

### Post by rebelDNS on 2007-09-26
> **HangLoose said:**
> I'm also having problems with a Dell.
When I restart the notebook its not with the previous settings anymore. I need to edit again the scaling_max_freq to 10000 so its showing...

Weird thing though, is there anyone who's having the same stuff

I recently reinstalled my laptop and I've been having the same problem.  I didn't do anything different than the first time I installed cpufreq but it loses setting every time.

And the ondemand thing freezes up then suddenly skips ahead when I'm working on demanding programs, which is annoying when you work with video.

Has anyone found a workaround?

---

### Post by rebelDNS on 2007-09-26
> **rebelDNS said:**
> I recently reinstalled my laptop and I've been having the same problem.  I didn't do anything different than the first time I installed cpufreq but it loses setting every time.

And the ondemand thing freezes up then suddenly skips ahead when I'm working on demanding programs, which is annoying when you work with video.

Has anyone found a workaround?

Hey I figured it out!

after seeing this and editing the instructions for the latest version:
[http://ubuntuforums.org/showthread.php?t=541794](http://ubuntuforums.org/showthread.php?t=541794)

Do this:
Basically, hit alt + f2 and type in gconf-editor and run

click on "apps" then "gnome-power-management" and then "cpufreq"

right click on the "cpufreq_ac_policy" and "cpufreq_battery_policy" and select "edit key" then change it to whatever governor/setting you want to be default (as in whatever you type in after "cpufreq-set -g TYPE-THIS-PART-IN")

---

### Post by Linuturk on 2007-11-07
I attempted to enable cpufreqd, failed, and tried to revert back to powernowd.

Now, once I try to shutdown, reboot, or anything, my fan kicks on like a jet engine and the machine never turns off. 

Help?

---

### Post by boolat on 2007-11-22
Hello,

On my laptop I only 3 frequency setting cpu!

This:

[IMG]http://img212.imageshack.us/img212/4827/30screende7.jpg[/IMG]

How to add the optional 1200MHZ

Thanks

my laptop acer aspire 9300 model.

---

### Post by spotslayer on 2008-01-22
Scaling was working for me for quite a while. Somewhere it just quit. I think it was around the time I upgraded to 7.10. If you look at the output below everything looks good exept  for this.

 current policy: frequency should be within 1000 MHz and 1000 MHz

notice it is the same on each of the processors. 

How can I set this so it would be between 1000 Mhz and 1660 Mhz.

David

david@DsLNVO:~$ cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 1000 MHz - 1.67 GHz
  available frequency steps: 1.67 GHz, 1.33 GHz, 1000 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 1000 MHz and 1000 MHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 1000 MHz - 1.67 GHz
  available frequency steps: 1.67 GHz, 1.33 GHz, 1000 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 1000 MHz and 1000 MHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz.

---

### Post by insulae on 2008-01-25
great tuto!! work perfectly to me :D, i have a notebook with a sempron 3500+, i used powernow-k8 :D.

Grettings
insulae

---

### Post by Some_ux on 2008-02-29
The cpu frequency scaling worked perfectly well on my Sempron 3400+ until I chose to change it to Sempron LE-1250 (which I thought would be nice since it has lower power consumption).

I assumed all I needed to do was to plug the new processor and be done with it. As it turned out, I also needed to upgrade my BIOS to the latest version so that my ASUS m2npv-vm would recognize the chip. 

I made dead sure that Cool’n’quiet was enabled (I believe the BIOS setting is AUTO) and started business as usual.

Except that now I get:

$ sudo modprobe powernow-k8 ;dmesg | tail -n 4
FATAL: Error inserting powernow_k8 (/lib/modules/2.6.20-15-generic/kernel/arch/x86_64/kernel/cpufreq/powernow-k8.ko): No such device
[573997.121020] powernow-k8: Processor cpuid 70ff2 not supported
[574447.405193] powernow-k8: Processor cpuid 70ff2 not supported
[574937.680962] powernow-k8: Processor cpuid 70ff2 not supported
[575873.371938] powernow-k8: Processor cpuid 70ff2 not supported

Does that mean that powernow-k8 does not like my new processor? I know for a fact that it does have Cool’n’quiet and for all intents and purposes it is quite similar to the Sempron 3400+ (baring manufacturing technology, some cache size changes, modified voltages and frequencies)

What do I need to update so that powernow-k8 will recognize my Sempron LE-1250.

P.S. I’d like to avoid upgrading from 7.04 to 7.10 if possible; I have applications compiled on the old kernel.

---

### Post by brodiepearce on 2008-03-13
Hi,

I've tried a few different methods at getting this to work:  I have a 1.6GHz Pentium-M (unsure of core) (Toshiba Portege A200).

I get the following messages when trying to get speedstep-centrino or acpi-cpufreq etc. loaded:

```

FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.22-14-generic/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): No such device

```

```

FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.22-14-generic/kernel/arch/i386/kernel/cpu/cpufreq/acpi-cpufreq.ko): No neric/kernel/arch/i386/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device

```

I'm also getting error messages just after login telling me that frequency scaling is not supported.  The frequency also seems to be locked at 598MHz.  

/proc/cpuinfo:

```

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 13
model name	: Intel(R) Pentium(R) M processor 1.60GHz
stepping	: 6
cpu MHz		: 598.524
cache size	: 2048 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up est tm2
bogomips	: 1198.18
clflush size	: 64

```

Some searching revealed that particular Pentium-M processors didn't have frequency scaling support in the Linux kernel (not sure if this was a particular kernel version or a running issue), and require you to compile support in.  Other possibilities that I stumbled across are issues in the Toshiba BIOS, there is a patch to solve this very issue, but it's aimed specifically at M100/M200 Porteges and certain Tecra laptops.  It's likely that I'll update the BIOS regardless, and the patch doesn't include any warnings of the "Will rain fire and brimstone" ilk.

Has this been a common issue for anyone else?

---

### Post by regme on 2008-05-06
> **brodiepearce said:**
> 

Some searching revealed that particular Pentium-M processors didn't have frequency scaling support in the Linux kernel (not sure if this was a particular kernel version or a running issue), and require you to compile support in.  Other possibilities that I stumbled across are issues in the Toshiba BIOS, there is a patch to solve this very issue, but it's aimed specifically at M100/M200 Porteges and certain Tecra laptops.  It's likely that I'll update the BIOS regardless, and the patch doesn't include any warnings of the "Will rain fire and brimstone" ilk.

Has this been a common issue for anyone else?

I was in exactly the same pickle as you brodiepearce, with the same hardware and all.

A whole day of frustration mucking around with acpi-cpufreq and speedstep-centrino, updating the BIOS and all amounted to nothing. I had scaling working between 75MHz and 600Mhz using p4_clockmod (well below the 1.6GHz range), but this wasn't the solution. I thought I had tried everything.

As you mentioned, apparently it is a common issue with the Toshibas to get locked at low frequencies. This usually happens after changing processor or doing a BIOS update, stopping your speedstep and frequency tables from working, thus stopping you from using the maximum range of frequency scaling.

See [http://www.tabletpcbuzz.com/forum/topic.asp?TOPIC_ID=14562](http://www.tabletpcbuzz.com/forum/topic.asp?TOPIC_ID=14562) (edit: the previous link no longer works, but this one does [http://www.tabletpcbuzz.com/archive/index.php?t-31-p-2.html](http://www.tabletpcbuzz.com/archive/index.php?t-31-p-2.html)) It describes a patch to the BIOS to detect the processor and speedstepping correctly. I can confirm this solution works with the Toshiba Portege A200, and may work with other Toshibas having the same problem. As always with anything that touches the BIOS, proceed at your own risk.

---

### Post by rmtracey on 2008-10-25
I have been chasing this problem for weeks. my portege A200 is locked at 599 and I have so far tried everything I can find on the internet. Toshiba were less than helpful." never heard of this problem" But I have found numerous people out there with this exact same problem. Tried to access the website you mentioned but not there.Would appreciate any further referance. thanks . rmt

---

### Post by rmtracey on 2008-10-28
Thanks to regme. This fixed my problem. Toshiba still tell me they have not heard of this problem.rmt

---

### Post by dotmrt on 2008-12-07
Just for the information that I have a ThinkPad T60 with Core2Duo (with 2 cores) Intel(R) Core(TM)2 CPU T5600 @ 1.83GHz.
And I needed to use "sudo modprobe acpi-cpufreq", as speedstep-centrino didn't work. I guess Core Duo and Core 2 Duo are that different.

My Ubuntu kernel is 2.6.27-10-generic.

---

### Post by blakjesus on 2008-12-10
This is an excellent guide! My laptop used to run hot once i plugged it in to the AC adapter. Now if im only playing music and doing light web-browsing, it remains luke-warm no matter what; only gets hot when playing games. Looking forward to see how this affects my battery.

^^^ Oh and yea what the guy above me said. I had to use acpi-cpufreq for my Core 2 Duo ^^^

EDIT:
After rebooting, the frequency scaler says it is activated, but its not changing my cpu frequency anymore. I have an applet on my panel that tells me the state of my cpu. It used to change to reflect how demanding my programs were, but now it just stays at 2.53GHz even after doing "echo conservative > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
"

"cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor" says that my cpu frequency should be scaled but its not. Please help.

---

### Post by wolfshark on 2008-12-12
Hi guys! I've never been so lucky to enable cpu frequency scaling, but today i decided to try one more time. My CPU is Athlon X2 3600+ and Asrock Alive NF6G motherboard. My problem is that i can't load the powernow-k8 module

sudo modprobe powernow-k8
> FATAL: Error inserting powernow_k8 (/lib/modules/2.6.27-9-generic/kernel/arch/x86/kernel/cpu/cpufreq/powernow-k8.ko): No such device

I precompiled my kernel - same thing. The bios is fine - C&Q is enabled and Asrock's 12% blabla booster is disabled. Actually in "/sys/devices/system/cpu/cpu0" there is no cpufreq folder at all. I will be very happy if somebody help me to diagnose the problem and maybe fixing it. Thanks!

Ubuntu 8.10


Edit: 

This is the output of dmesg
> dmesg | grep powernow
[   17.351669] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 3600+ processors (2 cpu cores) (version 2.20.00)
[   17.352218] powernow-k8: ACPI Processor support is required for SMP systems but is absent. Please load the ACPI Processor module before starting this driver.
[   17.352480] powernow-k8: ACPI Processor support is required for SMP systems but is absent. Please load the ACPI Processor module before starting this driver.

But ACPI-freq doesn't want to modprobe either
> FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.27-9-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device


I tried to load powernow-k7 on my other pc with s.A Athlon processor and the result is the same. The Ubuntu installation is fresh.

---

### Post by graysky on 2008-12-13
The problem lies with Ubuntu's kernel or some config file that I can't find - see [this thread](http://ubuntuforums.org/showthread.php?t=1000132).  My X3360 machine is stuck in 'full speed' running Intrepid-amd64.  If I boot into Debian/Lenny, CPU scaling works just fine.

I think the cause of the problem is the fact that I can't modprobe acpi-cpufreq under Ubuntu.  See the post I linked above.


```
$ sudo modprobe acpi-cpufreq
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.27-9-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device
```

EDIT - I figured this out... see [my post here](http://ubuntuforums.org/showthread.php?p=6363028#post6363028) for the details.

---

### Post by blakjesus on 2008-12-15
Please help.

I had it all running perfectly, but after i rebooted it didn't work anymore. I tried following all the steps over again but it didnt work.

Everything is in place and it acts like it is scaling but my CPU frequency remains the same.

If i type 'cpufreq-info' it displays this:

```
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  **hardware limits: 800 MHz - 2.53 GHz**
  **available frequency steps: 2.53 GHz, 2.53 GHz, 1.60 GHz, 800 MHz**
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: **frequency should be within 2.53 GHz and 2.53 GHz**.
                  The governor "conservative" may decide which speed to use
                  within this range.
  current CPU frequency is 2.53 GHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  **hardware limits: 800 MHz - 2.53 GHz**
  **available frequency steps: 2.53 GHz, 2.53 GHz, 1.60 GHz, 800 MHz**
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: **frequency should be within 2.53 GHz and 2.53 GHz**.
                  The governor "conservative" may decide which speed to use
                  within this range.
  current CPU frequency is 2.53 GHz.
```

---

### Post by blakjesus on 2008-12-19
I found an entry at launchpad that relates to my problem, but it sticks me at the highest CPU frequency instead.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/138465]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/138465")

Is there a fix for this? :confused:

---

### Post by IndieRockSteve on 2009-02-19
I have a Intel Pentium E5200 Wolfdale chip
```
$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
stepping	: 6
cpu MHz		: 2499.921
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 4999.84
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
stepping	: 6
cpu MHz		: 2499.921
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 5000.04
clflush size	: 64
power management:

```

and I can't get speedstep-centrino or acpi-cpufreq to load:

```
$ sudo modprobe acpi-cpufreq 
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.27-11-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device

```

```
~$ sudo modprobe speedstep-centrino 
FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.27-11-generic/kernel/arch/x86/kernel/cpu/cpufreq/speedstep-centrino.ko): No such device
```

anyone know what's wrong?
thanks!

---

### Post by graysky on 2009-02-22
@IndieRockSteve and blakjesus - Read this thread a few pages back:

> **graysky said:**
> The problem lies with Ubuntu's kernel or some config file that I can't find - see [this thread](http://ubuntuforums.org/showthread.php?t=1000132).  My X3360 machine is stuck in 'full speed' running Intrepid-amd64.  If I boot into Debian/Lenny, CPU scaling works just fine.

I think the cause of the problem is the fact that I can't modprobe acpi-cpufreq under Ubuntu.  See the post I linked above.


```
$ sudo modprobe acpi-cpufreq
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.27-11-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device
```

EDIT - I figured this out... see [my post here](http://ubuntuforums.org/showthread.php?p=6363028#post6363028) for the details.

Anyway, before you compile your own kernel, can one or preferably both of you [file a bug report](https://wiki.ubuntu.com/KernelTeamBugPolicies) on this issue?  I just created a [new one](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/332846) as well - this is **the only way the kernel team will learn about it and hopefully fix it!**

---

### Post by piccobello on 2009-03-05
> **bodycoach2 said:**
> Ubuntu Document Storage Facility is back up. I found the answer:



Frequency scaling is working. Most excellent.

Thanks a lot! I also had the 'No such device' error, now that I loaded p4_clockmod scaling seems to work. I say "seems", as I also found this:

[http://www.codemonkey.org.uk/2009/01/18/forthcoming-p4clockmod/]("http://www.codemonkey.org.uk/2009/01/18/forthcoming-p4clockmod/")

so now I'm even more confused.. Generally speaking, I still have to find a good and complete tutorial about energy saving under linux. And this is not just about battery life, remember that computers all together have the same carbon footprint as airplanes..

---

### Post by afeasfaerw23231233 on 2009-03-16
> **piccobello said:**
> Thanks a lot! I also had the 'No such device' error, now that I loaded p4_clockmod scaling seems to work. I say "seems", as I also found this:

[http://www.codemonkey.org.uk/2009/01/18/forthcoming-p4clockmod/]("http://www.codemonkey.org.uk/2009/01/18/forthcoming-p4clockmod/")

so now I'm even more confused.. Generally speaking, I still have to find a good and complete tutorial about energy saving under linux. And this is not just about battery life, remember that computers all together have the same carbon footprint as airplanes..

Actually throttling is for preventing cpu from overheating. It has no actual use on saving power consumption. It just lowers the bus speed but not the voltage and multiplier. The run time of your battery will not increase if you are using a notebook. 

Please see these thread 
[http://ubuntuforums.org/showthread.php?t=309403](http://ubuntuforums.org/showthread.php?t=309403)
[http://ubuntuforums.org/showthread.php?t=1088427](http://ubuntuforums.org/showthread.php?t=1088427)

I cannot get my T1600 celeron dual-core to scale.

Modprobing acpi-cpufreq or speedstep-centrino got the similar result as above. 

According Intel's site it should have EIST. I don't know if that's a BIOS/OS/chipsets problem. My BIOS doesn't show any setting about EIST/speedstep at all. Cannot get EIST work in win xp too.

---

### Post by Moustacha on 2009-03-23
> **afeasfaerw23231233 said:**
> Actually throttling is for preventing cpu overheating. It has no actual use on saving power consumption. It just lowers the bus speed but not the voltage and multiplier. The run time of your battery will not increase if you are using a notebook. 

Please see these thread 
[http://ubuntuforums.org/showthread.php?t=309403](http://ubuntuforums.org/showthread.php?t=309403)
[http://ubuntuforums.org/showthread.php?t=1088427](http://ubuntuforums.org/showthread.php?t=1088427)

I cannot get my T1600 celeron dual-core to scale.

Modprobing acpi-cpufreq or speedstep-centrino got the similar result as above. 

According Intel's site it should have EIST. I don't know if that's a BIOS/OS/chipsets problem. My BIOS doesn't show any setting about EIST/speedstep at all. Cannot get EIST work in win xp too.

I've tried compiling 2.6.28.8 after reading graysky's post and still no dice for cpu scaling on the celeron. I think I'll try XP soon and see if the intel processor indentifier says if there's EIST or not.

---

### Post by afeasfaerw23231233 on 2009-03-23
The "Intel processor identifier" says our T1600 is an engineering sample. Strange.
This page of Intel says T1600 doesn't support EIST
[http://ark.intel.com/cpu.aspx?groupID=38979](http://ark.intel.com/cpu.aspx?groupID=38979)
but this Intel spec finder says it does support EIST
[http://processorfinder.intel.com/details.aspx?sSpec=SLB6J](http://processorfinder.intel.com/details.aspx?sSpec=SLB6J)

---

### Post by Moustacha on 2009-03-23
> **afeasfaerw23231233 said:**
> The "Intel processor identifier" says our T1600 is an engineering sample. Strange.
This page of Intel says T1600 doesn't support EIST
[http://ark.intel.com/cpu.aspx?groupID=38979](http://ark.intel.com/cpu.aspx?groupID=38979)
but this Intel spec finder says it does support EIST
[http://processorfinder.intel.com/details.aspx?sSpec=SLB6J](http://processorfinder.intel.com/details.aspx?sSpec=SLB6J)

Yeah, strange they both show the same CPUID (06FD)(0<cpu family><model><stepping> in hexadecimal) which is what my cpu is, and I'm guessing yours is too.

---

### Post by graysky on 2009-03-30
> **graysky said:**
> @IndieRockSteve and blakjesus - Read this thread a few pages back:

Anyway, before you compile your own kernel, can one or preferably both of you [file a bug report](https://wiki.ubuntu.com/KernelTeamBugPolicies) on this issue?  I just created a [new one](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/332846) as well - this is **the only way the kernel team will learn about it and hopefully fix it!**

I figured it out!  I took a clue from my /var/log/dmesg

```
[    4.633657] [Firmware Bug]: BIOS needs update for CPU frequency support
[    4.633718] ACPI Error (psloop-0136): Found unknown opcode 20 at AML address ffff88012d27c633 offset 4F, ignoring [20080926]
[    4.633722] ACPI Error (psloop-0136): Found unknown opcode 6F at AML address ffff88012d27c638 offset 54, ignoring [20080926]
[    4.633726] ACPI Error (psloop-0136): Found unknown opcode 20 at AML address ffff88012d27c63c offset 58, ignoring [20080926]
[    4.633729] ACPI Error (psloop-0136): Found unknown opcode 6F at AML address ffff88012d27c640 offset 5C, ignoring [20080926]
```

That line that reads, [color=red]Firmware Bug: BIOS needs update for CPU frequency support[/color] was really bugging me.  So I took a risk, d/l'ed the latest BIOS for my board, flashed, reset all my custom BIOS settings, and rebooted into my new kernel.  I'm now able to use acpi-cpufreq and scaling works smoothly :)

Thanks for all the advice.

---

### Post by madbot on 2009-05-13
Hi, I'm getting exactly the same issue here with the same CPU. I'm using a Shuttle K45 case & motherboard.

Any idea if anyone manage to get this working? ):P

> **IndieRockSteve said:**
> I have a Intel Pentium E5200 Wolfdale chip
```
$ cat /proc/cpuinfo 
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
stepping    : 6
cpu MHz        : 2499.921

```and I can't get speedstep-centrino or acpi-cpufreq to load:

```
$ sudo modprobe acpi-cpufreq 
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.27-11-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device

``````
~$ sudo modprobe speedstep-centrino 
FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.27-11-generic/kernel/arch/x86/kernel/cpu/cpufreq/speedstep-centrino.ko): No such device
```anyone know what's wrong?
thanks!

---

### Post by tristezo2k on 2009-08-16
I was getting errors when inserting the powernow_k8
module on my AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
It turned to be that I had to enable the Cool'n'Quiet option at BIOS.
After that it worked flawlessly.
seba@orion:~$ cpufreq-info 
cpufrequtils 004: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]cpufreq@lists.linux.org.uk[/email], please.
analyzing CPU 0:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 1000 MHz - 2.60 GHz
  available frequency steps: 2.60 GHz, 2.40 GHz, 2.20 GHz, 2.00 GHz, 1.80 GHz, 1000 MHz
  available cpufreq governors: powersave, ondemand, conservative, userspace, performance
  current policy: frequency should be within 1000 MHz and 2.60 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz.
  cpufreq stats: 2.60 GHz:5.77%, 2.40 GHz:0.69%, 2.20 GHz:0.12%, 2.00 GHz:0.48%, 1.80 GHz:1.63%, 1000 MHz:91.30%  (89)
analyzing CPU 1:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 1000 MHz - 2.60 GHz
  available frequency steps: 2.60 GHz, 2.40 GHz, 2.20 GHz, 2.00 GHz, 1.80 GHz, 1000 MHz
  available cpufreq governors: powersave, ondemand, conservative, userspace, performance
  current policy: frequency should be within 1000 MHz and 2.60 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz.
  cpufreq stats: 2.60 GHz:5.77%, 2.40 GHz:0.69%, 2.20 GHz:0.12%, 2.00 GHz:0.48%, 1.80 GHz:1.63%, 1000 MHz:91.30%  (89)
seba@orion:~$ lsmod|grep k8
powernow_k8            17156  1 
freq_table              9344  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
k8temp                  9216  0 
processor              42304  2 powernow_k8,thermal

Ahhh, the sound of silence...
Now The cpu fan is almost silent and my workstation is at 1GHz :P:P

Thanks!
Sebastian

---

### Post by Zyro71 on 2010-01-01
My cpu...Im not sure if it has speed step (or the old version of speed step) but it can be manually underclocked...in windows,
12.5%
25%
37.5%
50%
62.5%
75%
82.5%
100%
I havent found a program that will underclock this chip in linux, yet but im wondering if there is support on this cpu i got, or am i just screwed?

processor       : 0                                                                      
vendor_id       : GenuineIntel                                                           
cpu family      : 6                                                                      
model           : 23
model name      : Intel(R) Celeron(R) CPU          900  @ 2.20GHz
stepping        : 10
cpu MHz         : 2194.510
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx lm constant_tsc up arch_perfmon pebs bts pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm
bogomips        : 4389.02
clflush size    : 64
power management:

Windows says odd things about this cpu too, ocasionally it will underclock to half power which is 1.10GHZ but other times it will be 1.2GHZ or off by some ammount, saying that its half powered. And even underclocking sometimes makes me think that im not saving power either way so why even do it.

---

### Post by Moustacha on 2010-01-01
that manual underclocking is probably what that p4clockmod module does, where it limits the amount of work the processor does, but doesn't actually lower the clock frequency.
I'd say since you don't have the "est" or "eist" flag you're not going to get frequency scaling, unfortunately. I've given up on trying to get it to work, just have to upgrade the processor to a Pentium class or better.

---

### Post by slnkez on 2010-01-12
For me, the easiest way on Karmic (9.10) to boot with specific CPU frequency was to install sysfsutils.

sudo apt-get install sysfsutils

edit /etc/sysfs.conf and to the end:
devices/system/cpu/cpu0/cpufreq/scaling_governor = conservative

Remove /etc/init.d/ondemand so that it doesn't set the cpu frequency to ondemand after a minute or so:

sudo mv /etc/init.d/ondemand /etc/init.d/ondemand.bak

---

### Post by ronin510 on 2010-01-14
Thanks for the guide.  I've been able to run "sudo modprobe p4_clockmod" and the scaling works with "CPU Frequency Scaling Monitor" but I run into some problems.

I can do everything until:

**Step 4: Scaling Modules**
```
sudo modprobe cpufreq_conservative
sudo modprobe cpufreq_ondemand
sudo modprobe cpufreq_powersave
sudo modprobe cpufreq_stats
sudo modprobe cpufreq_userspace
```

I get this error:
```
FATAL: Module cpufreq_conservative not found.
```
(Each modprobe gets a similar error).

Where can I find or add these cpufreq_x modules?  I'm running Ubuntu 9.10 with an Intel Pentium 4 3.0ghz machine.

I then run these commands and receive this output
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
conservative ondemand userspace powersave performance 

sudo -s
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
performance
```

The system won't let me use the ondemand governor, but I can manually change the frequencies with the CPU applet.

Any ideas?

---

### Post by timc3 on 2010-01-25
I am trying to install some kind of freq. scaling on my AMD 3000+ system running Ubuntu 9.04 Server with 2.6.28-17 kernel.

However I am missing the powernow-k8 kernel module. Is there a way to build this?

---

### Post by dDaYb on 2010-02-17
$cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
conservative ondemand userspace powersave performance

$ sudo cpufreq-set -g ondemand
and in dmesg i have an error:
 **ondemand governor failed, too long transition latency of HW, fallback to performance governor**
why?

$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Celeron(R) CPU 2.66GHz
stepping        : 9
cpu MHz         : 2666.600
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc up pebs bts pni dtes64 monitor ds_cpl tm2 cid cx16 xtpr lahf_lm
bogomips        : 5320.06
clflush size    : 64
power management:

---

### Post by borabosna on 2010-03-23
I'm running UNR 9.10 on Asus Eee 1001p, Intel Atom N450 processor. I'm using the CPU frequency scaling applet in the panel. My available speeds are 1.66, 1.33 and 1.00 ghz. I select powersave on the applet, and it works fine, it doesn't jump back to ondemand or anything. Since 1.00 ghz is the lowest possible for me, I'm happy. But when I restart, it starts with ondemand again. I want to run it on powersave by default every time I boot. How do I do that? I checked gnome-conf editor but could not find a setting for it.

Sorry if this was asked earlier.

EDIT: found the answer:
[http://ubuntuforums.org/showthread.php?t=597998](http://ubuntuforums.org/showthread.php?t=597998)

---

### Post by wilsontp on 2010-03-28
I have ubuntu 9.10 on an hp tx2525nr.
 
It has an AMD 64-bit x2 processor (RM-70, 2.00GHz), and when I have it set for performance, when running on AC, it runs 2GHz, but on battery it drops to 1GHz.  If I tell it manually to run at 1GHz, it runs at 1GHz, but if I set it to manual 2GHz, it runs at 1GHz.
 
If I want to save battery I would've bought an intel.
 
How do I alter the cpu scaling kernel in ubuntu to run 2GHz on battery when I tell it to?

---

### Post by mikejeckson on 2010-03-29
Yes this is quit helpful.......

but i want to know that...How to check CPU health status and remain it good for good performance of the computer...

---

### Post by JohnnyC35 on 2010-05-26
borabosna how did you get your scaling to work?
I have an intel atom and it only tells me that scaling isn't available :S
... also Ubuntu thinks my dual-core has 4 cores ... :^)

> 
john@Mediabuntu:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 28
model name    : Intel(R) Atom(TM) CPU  330   @ 1.60GHz
stepping    : 2
cpu MHz        : 1999.942
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm
bogomips    : 3999.88
clflush size    : 64
cache_alignment    : 64
address sizes    : 32 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 28
model name    : Intel(R) Atom(TM) CPU  330   @ 1.60GHz
stepping    : 2
cpu MHz        : 1999.942
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 2
apicid        : 2
initial apicid    : 2
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm
bogomips    : 4000.02
clflush size    : 64
cache_alignment    : 64
address sizes    : 32 bits physical, 48 bits virtual
power management:

processor    : 2
vendor_id    : GenuineIntel
cpu family    : 6
model        : 28
model name    : Intel(R) Atom(TM) CPU  330   @ 1.60GHz
stepping    : 2
cpu MHz        : 1999.942
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm
bogomips    : 3999.96
clflush size    : 64
cache_alignment    : 64
address sizes    : 32 bits physical, 48 bits virtual
power management:

processor    : 3
vendor_id    : GenuineIntel
cpu family    : 6
model        : 28
model name    : Intel(R) Atom(TM) CPU  330   @ 1.60GHz
stepping    : 2
cpu MHz        : 1999.942
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 2
apicid        : 3
initial apicid    : 3
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm
bogomips    : 4000.00
clflush size    : 64
cache_alignment    : 64
address sizes    : 32 bits physical, 48 bits virtual
power management:


---

### Post by Belfry on 2010-05-31
> **JohnnyC35 said:**
> borabosna how did you get your scaling to work?
I have an intel atom and it only tells me that scaling isn't available :S
... also Ubuntu thinks my dual-core has 4 cores ... :^)

I believe that Atom 330 has hyperthreading, so a dual core should appear to the operating system as four cores.

Anyway I'm also trying to get scaling with Xubuntu 10.04 on an IBM Thinkpad A20m, 700MHz PIII.  It used to work well with the userspace governor under Hardy.  The big problem is there's no cpufreq directory under /sys/devices/system/cpu/cpu0/.  Does anyone have any ideas?

edit: Curiously. the directory is present when I boot the Xubuntu 10.04 live CD, and I can make frequency adjustments with the userspace governor.  I installed from the alternate CD, why would there be any difference?

---

### Post by Belfry on 2010-06-02
The plot thickens.  I  burned the kernel to a CD and booting it allows the cpufreq directory  and subfiles to appear :confused:.  Powernowd along with the userspace governor  then works normally (as it had in Hardy).

The CD drive sits on  the secondary channel (1:0) of the same disk controller as the hard  drive (0:0), so it seems strange that booting off one or the other would  produce such a divergence.  My disk is an old, rickety 12GB Travelstar,  so maybe I'll move my installation to a different disk and see what  happens.

---

### Post by Belfry on 2010-06-04
I have a workaround. Somehow Grub 2 interferes with the kernel creating the cpufreq files,  yet they appear with Grub legacy--at least with the Thinkpad A20m. Sometimes you can't teach an old laptop new tricks.  I didn't notice any other problems with the sysfs directory.

Backup your Grub 2 configuration files: /etc/default/grub and /etc/grub.d/*. Uninstall grub-pc and grub-common.  Delete all files in /boot/grub/. Then install Grub (the legacy version). Run update-grub and grub-install against your boot disk.

It is a strange problem.  I guess I should send a bug report to the Grub people (sounds kind of funny).  Could someone point me the direction to do that?

---

### Post by JamieKitson on 2010-08-14
Thanks very much for the tutorial, just one possible correction: the only speedstep module I had available was speedstep-lib, which I think worked.

---

