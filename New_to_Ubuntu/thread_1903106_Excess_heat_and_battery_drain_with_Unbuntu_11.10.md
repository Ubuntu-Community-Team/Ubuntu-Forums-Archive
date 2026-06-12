---
title: "Excess heat and battery drain with Unbuntu 11.10"
date: 2012-01-01
forum: New to Ubuntu
---

### Post by Expert Novice on 2012-01-01
Hi there, thanks for reading my first post :-)

Having grown tired of M****soft and their nonsense I decided I'd try Unbuntu 11.10 on my HP Pavilion g6 series laptop. I've installed and connected to the internet through my router without too much trouble and the initial impression is that everything is running reasonably well but am now experiencing a lot of heat and short battery life. This is with the machine sitting idling with nothing using any significant CPU in system monitor.

I did some googling and found a number of reports of similar behaviour and also a possible solution **[COLOR=Blue][here]("http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html")[/COLOR] **which I have followed. I've learned a few things about finding my way round Unbuntu but after an hour or so of idling I can see there has been no change t with the heat issue.

One thing I have noticed is that the heat seems to be concentrated in the same area that gets hotter when watching video for a while or some other graphics intensive task. This is to the bottom left of the keyboard seemingly centred around the ctrl key. I have no idea what's under there but would hazard a guess the graphics chip is round there somewhere so the issue may well be graphics related.

I've had no such issues while using windows, other than when the graphics have been working hard for a while so I don't think it's a hardware issue.

I did read somewhere of there being a graphics related bug that was causing similar behaviour but there was no solution given in that thread so any advice would be much appreciated.

---

### Post by LinuxFan999 on 2012-01-01
Do you have the proprietary video drivers installed? They usually have better power management then the open source drivers.
What video card is in your laptop?
By the way, you spelled Ubuntu wrong.

---

### Post by KdotJ on 2012-01-01
I had this issue with my laptop, which was running about 72C when just doing nothing... watching a video sent the temperature through the roof. I solved it by using CPU governors...

When you say idling, is the fan on the laptop constantly spinning at full speed? (Or seems louder than it should?)

Post the output of:
```
sudo cpufreq-info
```

If it's not installed, you can install it with:
```
sudo apt-get install cpufrequtils
```

---

### Post by Expert Novice on 2012-01-01
Thanks...

The video card is Intel(R) HD Graphics Family and was in the machine from new. The driver version is 8.15.10.2353 provided by Intel corporation. This is from looking at the Windows 7 installation. I presume this driver is not being used by Ubuntu and as I've not installed any other drivers in that O/S it'll be using the open source ones that come with the installation.
Looking in Ubuntu System Settings/System Info/Graphics I can see Driver - Unknown and Experience - Standard.

I only installed Ubuntu last night so I'm on something of a learning curve here. I presume I need to install the Intel video drivers to Ubuntu manually?

@KdotJ By idling I mean it's sitting with no programs running, doing nothing except making a lot more heat than usual with maybe 5%CPU usage. THe fan is maybe running a little faster than normal but I've heard it going faster still, say when saving a large chunk of newly edited video and the CPU usage shoots up for a short time the fan really spins up then. It's not as loud as that now but still louder than you'd expect. I've noticed the heat more through feeling the case of the laptop getting warmer than normal.

Will try the cpufreq idea and post back when I can. I'd do it now but Ubuntu has decided it doesn't want to connect through my router again. It was doing the same last night but connected no problem when I got home earlier. After shutting down and rebooting it would no longer connect so I can't d/l cpufrequtils. Wireles and ethernet are both the same.

It's getting late. I can sense another thread approaching :-)

---

### Post by KdotJ on 2012-01-01
> **Expert Novice said:**
> @KdotJ... Will try the cpufreq idea and post back when I can.

No worries. I'm not sure if will be the same for you, but the issue I had was that my CPU was always running at full speed (always at 2.8Ghz) even when it was doing nothing. Of course, this didn't show up as the CPU usage being high in the system monitor. This used to be an issue on laptops with various linux distributions, I've had the same trouble with others I've tried.

cpufrequtils will let you have more control over this (well, it will do it for you if you want) and control your CPU speeds dynamically. After doing this my CPU was idling at 1.05GHz and only worked harder when it needed to... my temperature dropped by around 20C and the battery lasted much longer. However, I've only just returned to Ubuntu so I'm not sure if all this comes as standard now.

Good luck with Ubuntu :D

---

### Post by Expert Novice on 2012-01-02
Ok, so I tried sudo cpufreq-info but as you can see below that prduced 'command not found'. So I went to install cpufreq. I have included here the output from the install because I noticed three fatal errors listed. Not sure if they're important or not but someone here will know.

And then below that is the output from sudo cpufreq-info as requested.

Will monitor how things go with cpufreq installed and report back  soon but still wondering about video drivers as mentioned earlier. Do I need to install them manually?

Thanks again

david@ubuntu:~$ sudo cpufreq-info
[sudo] password for david: 
sudo: cpufreq-info: command not found
david@ubuntu:~$ sudo apt-get install cpufrequtils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libcpufreq0
The following NEW packages will be installed
  cpufrequtils libcpufreq0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 51.9 kB of archives.
After this operation, 352 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric/universe libcpufreq0 i386 007-1 [13.6 kB]
Get:2 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric/universe cpufrequtils i386 007-1 [38.3 kB]
Fetched 51.9 kB in 0s (74.8 kB/s)    
Preconfiguring packages ...
Selecting previously deselected package libcpufreq0.
(Reading database ... 151758 files and directories currently installed.)
Unpacking libcpufreq0 (from .../libcpufreq0_007-1_i386.deb) ...
Selecting previously deselected package cpufrequtils.
Unpacking cpufrequtils (from .../cpufrequtils_007-1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up libcpufreq0 (007-1) ...
Setting up cpufrequtils (007-1) ...
 * Loading cpufreq kernel modules...                                            FATAL: Error inserting e_powersaver (/lib/modules/3.0.0-14-generic/kernel/drivers/cpufreq/e_powersaver.ko): No such device
FATAL: Error inserting p4_clockmod (/lib/modules/3.0.0-14-generic/kernel/drivers/cpufreq/p4-clockmod.ko): Device or resource busy
FATAL: Error inserting pcc_cpufreq (/lib/modules/3.0.0-14-generic/kernel/drivers/cpufreq/pcc-cpufreq.ko): No such device
                                                                         [ OK ]
 * CPUFreq Utilities: Setting ondemand CPUFreq governor...                       * CPU0...                                                                       * CPU1...                                                                       * CPU2...                                                                       * CPU3...                                                               [ OK ] 
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
david@ubuntu:~$ 


david@ubuntu:~$ sudo cpufreq-info
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [EMAIL="cpufreq@vger.kernel.org"]cpufreq@vger.kernel.org[/EMAIL], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1 2 3
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.30 GHz
  available frequency steps: 2.30 GHz, 2.30 GHz, 1.80 GHz, 1.60 GHz, 1.40 GHz, 1.20 GHz, 1000 MHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 2.30 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).
  cpufreq stats: 2.30 GHz:12.46%, 2.30 GHz:0.34%, 1.80 GHz:0.26%, 1.60 GHz:0.24%, 1.40 GHz:0.39%, 1.20 GHz:0.62%, 1000 MHz:0.56%, 800 MHz:85.14%  (2191)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1 2 3
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.30 GHz
  available frequency steps: 2.30 GHz, 2.30 GHz, 1.80 GHz, 1.60 GHz, 1.40 GHz, 1.20 GHz, 1000 MHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 2.30 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).
  cpufreq stats: 2.30 GHz:19.50%, 2.30 GHz:0.56%, 1.80 GHz:0.48%, 1.60 GHz:0.27%, 1.40 GHz:0.34%, 1.20 GHz:0.50%, 1000 MHz:0.75%, 800 MHz:77.59%  (3144)
analyzing CPU 2:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1 2 3
  CPUs which need to have their frequency coordinated by software: 2
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.30 GHz
  available frequency steps: 2.30 GHz, 2.30 GHz, 1.80 GHz, 1.60 GHz, 1.40 GHz, 1.20 GHz, 1000 MHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 2.30 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).
  cpufreq stats: 2.30 GHz:10.62%, 2.30 GHz:0.09%, 1.80 GHz:0.04%, 1.60 GHz:0.07%, 1.40 GHz:0.01%, 1.20 GHz:0.06%, 1000 MHz:0.13%, 800 MHz:88.98%  (349)
analyzing CPU 3:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1 2 3
  CPUs which need to have their frequency coordinated by software: 3
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.30 GHz
  available frequency steps: 2.30 GHz, 2.30 GHz, 1.80 GHz, 1.60 GHz, 1.40 GHz, 1.20 GHz, 1000 MHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 2.30 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).
  cpufreq stats: 2.30 GHz:11.04%, 2.30 GHz:0.07%, 1.80 GHz:0.10%, 1.60 GHz:0.06%, 1.40 GHz:0.08%, 1.20 GHz:0.15%, 1000 MHz:0.12%, 800 MHz:88.38%  (606)
david@ubuntu:~$

---

### Post by I_can_see_the_light on 2012-01-02
I see that the "fallback" driver acpi-cpufreq is used so I think that everything is in order. 

Just out of curiosity, what's the output if you run the following command in a terminal: ```
cat /proc/cpuinfo
```

---

### Post by Expert Novice on 2012-01-04
Ok, thanks for that reassurance. 

I have yet to make any changes to settings with cpufrequtils so don't know if that's going to make any difference.

Anyway here is the output for cat /proc/cpuinfo

Thanks


david@ubuntu:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
stepping    : 7
cpu MHz        : 800.000
cache size    : 3072 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt xsave avx lahf_lm ida arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 4589.59
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
stepping    : 7
cpu MHz        : 800.000
cache size    : 3072 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt xsave avx lahf_lm ida arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 4589.41
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 2
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
stepping    : 7
cpu MHz        : 800.000
cache size    : 3072 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 2
apicid        : 2
initial apicid    : 2
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt xsave avx lahf_lm ida arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 4589.43
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 3
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
stepping    : 7
cpu MHz        : 800.000
cache size    : 3072 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 2
apicid        : 3
initial apicid    : 3
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt xsave avx lahf_lm ida arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 4589.46
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

david@ubuntu:~$

---

### Post by KdotJ on 2012-01-04
Thanks for posting the cpufreq info, as you can see the cpu is showing running at 800Mhz. which is the lower end of the range. This means you don't have the same issue as I did.. Sorry for the false hope but at least its eliminated one possibility.

---

### Post by Expert Novice on 2012-01-04
Ok, so cpufrequtils is not worth playing with any more then. Thanks anyway :D

---

### Post by KdotJ on 2012-01-04
Yeah pretty much, these parts of the output explain that thnigs are working as you would want with regards from CPU scaling:

```

...
hardware limits: 800 MHz - 2.30 GHz
...
current CPU frequency is 800 MHz (asserted by call to hardware)
...

```

---

### Post by Expert Novice on 2012-01-04
Ok, Thank you. It's good to at least eliminate one possibility. Also good to find helpful people when you feel out of your depth with new stuff :)

I was looking at powertop. I will try using that. Maybe that'll show where all the power is going. I'll make another thread for that if necessary.

Thanks again ):P

---

### Post by KdotJ on 2012-01-04
No worries. Powertop is a good useful program. I used it on my netbook to stop various running processes (such as bluetooth stuff) that I wasn't using. It did increase my battery life for sure.

Good luck!

---

### Post by Expert Novice on 2012-01-04
Yes, battery life... Seems to be an issue with laptops from what I've read. There seems to be a lack of compatibility with some functions which have a detrimental effect on power usage and battery drain. For example I don't seem to be able to turn down the screen brightness on here which is obviously going to affect battery life. Doubt that'd make the internals under the keyboard get so hot though so I wonder if there's something else going crazy in there, eating up lot of power for no reason because there's some incompatibility going on.

BTW I installed Xsensors to keep an eye on CPU temp and it shows minimum 55-65c all the time with maybe 5%cpu load. Windows would be 35c.

---

### Post by I_can_see_the_light on 2012-01-04
You could try installing the package ```
lm-sensors
```
Then run ```
sudo sensors-detect
```in a terminal window. If you're lucky it will detect a thermal sensor that could help.

For tips on how to tweak power savings on battery (and also on AC) you can visit [this thread]("http://crunchbanglinux.org/forums/topic/11954/laptop-power-saving-script-for-debian/") on crunchbanglinux forums. Ubuntu 11.10 uses a later version of pm-utils than crunchbang though so you need to check your scripts in **/usr/lib/pm-utils/power.d/**. Some of them contain similar settings to the proposed powersavings script. In my case I deleted this bit
```
# Enable laptop mode
echo 5 > /proc/sys/vm/laptop_mode
# Less VM disk activity. Suggested by powertop
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
# Intel power saving
echo Y > /sys/module/snd_hda_intel/parameters/power_save_controller
echo 1 > /sys/module/snd_hda_intel/parameters/power_save
```
since it's already handled by default in Ubuntu. Also, don't install **laptop-mode-tools** like the author of that script did, it's not needed in Ubuntu.

---

### Post by Expert Novice on 2012-01-04
Yes, I've been looking at lm sensors too. Tried installing it but couldn't get it to work. Will go back and try it now and post the output. Will have a look at that link later. I can feel my head starting to fry again. Glad to have made some progress though.

---

### Post by Expert Novice on 2012-01-04
Hmm, it doesn't seem to have detected much. I think this may be the one I need though...?

Intel digital thermal sensor...                             Success!
    (driver `coretemp')

Full output below...

david@ubuntu:~$ sudo sensors-detect
[sudo] password for david: 
# sensors-detect revision 5946 (2011-03-23 11:54:44 +0100)
# System: Hewlett-Packard HP Pavilion g6 Notebook PC (laptop)
# Board: Hewlett-Packard 166F

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): yes
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
Intel digital thermal sensor...                             Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): yes
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): yes
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): ye
Using driver `i2c-i801' for device 0000:00:1f.3: Intel Cougar Point (PCH)
Module i2c-i801 loaded successfully.
Module i2c-dev loaded successfully.

Next adapter: i915 gmbus disabled (i2c-0)
Do you want to scan it? (YES/no/selectively): yes

Next adapter: i915 gmbus ssc (i2c-1)
Do you want to scan it? (YES/no/selectively): yes

Next adapter: i915 GPIOB (i2c-2)
Do you want to scan it? (YES/no/selectively): yes

Next adapter: i915 gmbus vga (i2c-3)
Do you want to scan it? (YES/no/selectively): yes

Next adapter: i915 GPIOA (i2c-4)
Do you want to scan it? (YES/no/selectively): yes

Next adapter: i915 gmbus panel (i2c-5)
Do you want to scan it? (YES/no/selectively): yes
Client found at address 0x28
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                No
Probing for `Winbond W83781D'...                            No
Probing for `Winbond W83782D'...                            No
Probing for `Winbond W83627HF'...                           No
Probing for `Winbond W83627EHF'...                          No
Probing for `Winbond W83627DHG/W83667HG/W83677HG'...        No
Probing for `Asus AS99127F (rev.1)'...                      No
Probing for `Asus AS99127F (rev.2)'...                      No
Probing for `Asus ASB100 Bach'...                           No
Probing for `Analog Devices ADM1029'...                     No
Probing for `ITE IT8712F'...                                No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: i915 GPIOC (i2c-6)
Do you want to scan it? (YES/no/selectively): yes
Client found at address 0x28
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                No
Probing for `Winbond W83781D'...                            No
Probing for `Winbond W83782D'...                            No
Probing for `Winbond W83627HF'...                           No
Probing for `Winbond W83627EHF'...                          No
Probing for `Winbond W83627DHG/W83667HG/W83677HG'...        No
Probing for `Asus AS99127F (rev.1)'...                      No
Probing for `Asus AS99127F (rev.2)'...                      No
Probing for `Asus ASB100 Bach'...                           No
Probing for `Analog Devices ADM1029'...                     No
Probing for `ITE IT8712F'...                                No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: i915 gmbus dpc (i2c-7)
Do you want to scan it? (YES/no/selectively): yes

Next adapter: i915 GPIOD (i2c-8)
Do you want to scan it? (YES/no/selectively): yes

Next adapter: i915 gmbus dpb (i2c-9)
Do you want to scan it? (YES/no/selectively): yes

Next adapter: i915 GPIOE (i2c-10)
Do you want to scan it? (YES/no/selectively): yes

Next adapter: i915 gmbus reserved (i2c-11)
Do you want to scan it? (YES/no/selectively): yes
yes
Next adapter: i915 gmbus dpd (i2c-12)
Do you want to scan it? (YES/no/selectively): 

Next adapter: i915 GPIOF (i2c-13)
Do you want to scan it? (YES/no/selectively): yes

Next adapter: DPDDC-B (i2c-14)
Do you want to scan it? (YES/no/selectively): yes

Next adapter: SMBus I801 adapter at 4040 (i2c-15)
Do you want to scan it? (YES/no/selectively): yes
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: yes

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)yes
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run 'service module-init-tools start'
to load them.

Unloading i2c-dev... OK
Unloading i2c-i801... OK
Unloading cpuid... OK

david@ubuntu:~$

---

### Post by Expert Novice on 2012-01-04
david@ubuntu:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +57.0°C  

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +57.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +49.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +51.0°C  (high = +86.0°C, crit = +100.0°C)

david@ubuntu:~$

---

### Post by I_can_see_the_light on 2012-01-04
Well, I can't think of anything else right now. Let's see if that will make any change - along with lm-sensors there should have been another package automatically installed called **fancontrol**. Hopefully it will work out right.

But when you find the time I suggest you look at the link to crunchbang forums, that script extended my battery life a bit at least but for others it made a huge difference.

---

### Post by blackbird34 on 2012-01-04
The Jupiter applet may help you here. More info at [http://shuffleos.com/3009/jupiter-a-light-weight-power-hardware-control-applet-for-linux/](http://shuffleos.com/3009/jupiter-a-light-weight-power-hardware-control-applet-for-linux/)  which is a little article explaining how it functions: 
```
Jupiter is a simple and easy to use hardware and power management applet designed for [Linux]("http://shuffleos.com/tag/linux").
  The Jupiter applet improves the battery life of the portable Linux computers by 
getting integrated with the operating system and changing  parameters of the
 computer based on battery or powered connection.  

```...and how to install:

```
sudo add-apt-repository ppa:webupd8team/jupiter

``````
sudo apt-get update

``````
sudo apt-get install jupiter

```...and here, the thread where i first found out about it: [http://ubuntuforums.org/showthread.php?t=1854019](http://ubuntuforums.org/showthread.php?t=1854019) (I use Jupiter too, it added a fair amount of battery time to my computer).

PS (Anyone more experienced, please tell me if you think this is irrelevant, I seem to be posting about Jupiter it an awful lot :D)

---

### Post by I_can_see_the_light on 2012-01-04
> **blackbird34 said:**
> please tell me if you think this is irrelevant, I seem to be posting about Jupiter it an awful lot :D)

Nah, I don't think it's irrelevant. I had Jupiter installed in 10.10 but for me it didn't make much of a difference, but there are many success stories. 

@Expert Novice:
I suggest you try Jupiter before you try my earlier suggestion regarding the power savings script from crunchbang forums.

---

### Post by Expert Novice on 2012-01-04
Ok, thanks, I will, and thanks blackbird for the tip. Will look into that tomorrow. For now I am definitely getting off the laptop :-)

---

### Post by Expert Novice on 2012-01-08
After the suggestion this may be a driver issue causing the power loss and heat I remembered I had not installed and proprietory drivers when installing Uubuntu. I restored a previous back up of my hard disc as an alternative to a full uninstall of Ubuntu and then reinstalled it allowing it to download and install all third party sofware needed.

I presume I should now have all the correct drivers for my hardware but am still getting the same issues.  

I did try using Jupiter befroe re installing Ubuntu. It didn't give me many options I can remember other than adjusting screen res, switching off touchpad and selecting internal or external display. There were performance options availabe but selecting the powersaving mode seemed to have the effect of inducing peaks of high CPU usage which made the machine slow to the point of being more or less unusable. At least this was my experience of Jupiter and as such it was difficult to to notice any improvement. Indeed, when left to sit and idle there was still the same amount of heat being generated so I assume the power draw would be siimilar too.

I will have a go with Powertop and see what that shows.

---

### Post by I_can_see_the_light on 2012-01-08
> **Expert Novice said:**
> I will have a go with Powertop and see what that shows.
Good idea. You can enable many power tweaks from within powertop but they don't survive reboots.

---

### Post by I_can_see_the_light on 2012-01-08
Have you tried logging in to Unity 2D by the way? My laptop runs a lot cooler when not using a 3D window manager. If that does the trick for you it might be something to consider using, and with the help of [xcompmgr]("http://packages.ubuntu.com/oneiric/xcompmgr") or [cairo-compmgr]("http://cairo-compmgr.tuxfamily.org/") you can get some basic desktop effects like shadows which, in my opinion, improves the desktop experience.

---

### Post by Expert Novice on 2012-01-08
No, I hadn't thought of the 2d possibility but I'll give it a go, thanks.

I ran Powertop which seems to be showing some issues. Not that you can really compare two machines very accurately of course, different hardware/software etc but I wondered how my readings compare to those you've seen. From what I've read 3 wake up calls a minute is considered very good so at a guess 100 might be just about acceptable? As you can see from the overview readout below my machine is showing rather more than that.  This was after sitting for twenty mins after a reboot with only powertop running in terminal and Jupiter running so I could see CPU temp (55-58c). The figure for battery drain seems high too.

Also posted device stats screen. What are all those 100%s?

I've been searching for some guidance on interpreting Powertops readings but can't seem to find anything. Lots on what it does but little on interpreting and acting on the results.

Can you help me make any more sense of this?

Overview...

The battery reports a discharge rate of 18.8 W
The estimated remaining time is 123 minutes

Summary: 425.4 wakeups/second,  0.0 GPU ops/second and 0.0 VFS ops/sec

                Usage Events/s Category Description
            100.0%                      Device         Audio codec hwC0D3: Intel
            100.0%                      Device         Audio codec hwC0D0: IDT
              2.5 ms/s     133.8        Interrupt      PS/2 Touchpad / Keyboard / Mouse
            100.0%                      Device         Display backlight
            100.0%                      Device         Display backlight
             19.6 ms/s      61.4        Process        compiz
             17.8 ms/s      60.1        Process        /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
              0.8 ms/s      53.0        Timer          hrtimer_wakeup
              9.7 ms/s      32.6        Process        /usr/lib/firefox-9.0.1/firefox
            465.9 µs/s      19.9        Interrupt      [42] i915
            571.7 µs/s      18.9        Timer          tick_sched_timer
              7.3 ms/s      15.1        Process        gnome-terminal
              1.0 ms/s       5.9        Process        /usr/bin/mono --runtime=v4.0.30319 /usr/bin/jupiter.exe
            262.0 µs/s       4.8        Process        syndaemon -i 0.5 -K -R
             56.7 µs/s       2.9        Process        [rtsx-polling]
              1.7 ms/s       1.6        Process        //bin/dbus-daemon --fork --print-pid 8 --print-address 10 --session
             35.9 µs/s       1.2        kWork          ieee80211_iface_work
            426.4 µs/s       1.1        Process        /usr/lib/bamf/bamfdaemon
              8.1 ms/s       0.8        kWork          ieee80211_dynamic_ps_enable_wor
              1.2 ms/s       0.9        kWork          disk_events_workfn
              6.5 µs/s       0.9        kWork          wq_barrier_func
             97.2 µs/s       0.8        Interrupt      [6] tasklet(softirq)
            214.0 µs/s       0.8        Process        /usr/lib/gnome-settings-daemon/gnome-settings-daemon
             12.4 µs/s       0.6        Process        [ksoftirqd/1]
            316.6 µs/s       0.6        Process        /usr/lib/unity/unity-panel-service
            249.9 µs/s       0.6        Interrupt      [7] sched(softirq)
             18.7 µs/s       0.5        Process        [ksoftirqd/0]
              8.9 µs/s       0.5        Process        [rts_pstor]
             73.5 µs/s       0.4        Process        udisks-daemon: polling /dev/sr0 /dev/sdb
             34.8 µs/s       0.4        Interrupt      [4] block(softirq)
             18.8 µs/s       0.4        Interrupt      [41] SATA controller


Device Stats...

The battery reports a discharge rate of 18.4 W

              Usage     Device name
            100.0%        Audio codec hwC0D3: Intel
            100.0%        Audio codec hwC0D0: IDT
              7.1%        CPU use
            100.0%        Display backlight
            100.0%        Display backlight
            100.0%        PCI Device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller
            100.0%        PCI Device: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1
            100.0%        Radio device: rt2800pci
            100.0%        PCI Device: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller
            100.0%        PCI Device: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1
            100.0%        PCI Device: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
            100.0%        PCI Device: Intel Corporation 2nd Generation Core Processor Family DRAM Controller
            100.0%        PCI Device: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2
            100.0%        PCI Device: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe
            100.0%        PCI Device: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
            100.0%        PCI Device: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller
            100.0%        PCI Device: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3
            100.0%        PCI Device: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller
            100.0%        PCI Device: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader
             11.5 pkts/s  Network interface: wlan0 (rt2800pci)
              0.0 pkts/s  Network interface: eth0 (r8169)
              0.0%        USB device: HP Webcam-101 (DC01702LAAHGLP)
              0.0%        USB Device: usb-device-8087-0024
              0.0%        USB Device: usb-device-8087-0024
              0.0%        USB device: EHCI Host Controller
              0.0%        USB device: EHCI Host Controller

---

### Post by Expert Novice on 2012-01-08
The 2d suggestion now has wake ups hovering around 130 so that's a real improvement, thanks.

Still got more or less the same battery drain though. I have some other things to try. Will see how they go.

Cheers

---

### Post by Flynsarmy on 2012-01-08
I have an nvidia optimus machine (Dell 15z) which has a discrete nvidia with on board intel. Disabling the nvidia took care of most of my heat issues - but I still had some with the intel which I also managed to solve.

Check the Minor *Intel GPU Tweaks* section of my blog post [here]("http://www.flynsarmy.com/2012/01/lower-heat-power-consumption-on-dell-15z-in-ubuntu/"). Hope it helps!

EDIT: With regards to your battery life issues - they could be caused by the linux power regression bug that's been plaguing us for a while now. Ubuntu 11.10 [is affected]("http://www.phoronix.com/scan.php?page=news_item&px=OTg2Mg") and there's apparently no fix until 12.04.

---

### Post by Expert Novice on 2012-01-08
Ok, thanks. I'll have a look at those. Anything's better than the current situation (pun only half intended).

Re the power regression in the later Kernels, perhaps I'd do better looking for a pre 2.6.38 version to use for the time being. Sounds like that's going to be the only way to get an improvement before 12.04. Still new to all this though so some more research into swapping Kernels will be in order first :-)

---

### Post by Expert Novice on 2012-01-08
@Flynsarmy Ok, so your mod is similar to the one I've tried from this post...

[http://ubuntuforums.org/showthread.php?t=1874306&page=4](http://ubuntuforums.org/showthread.php?t=1874306&page=4)

That line in my file now reads...

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force acpi_osi=Linux i915.lvds_downclock=1 i915.i915_enable_fbc=1 i915.i915_enable_rc6=1"

It doesn't seem to have made a huge difference.

How does that look to you? Should I add the missing parts from yours as well? How would the line read then? I mean does it matter which order in the line you place each option?

---

### Post by KdotJ on 2012-01-08
> **I_can_see_the_light said:**
> Good idea. You can enable many power tweaks from within powertop but they don't survive reboots.

Maybe I was just doing it wrong, but I remember having to keep running powertop every now and then to tweak stuff (during one login session) as some services had started again. This was probably how my installation was configured though.

---

### Post by I_can_see_the_light on 2012-01-09
> **KdotJ said:**
> Maybe I was just doing it wrong, but I remember having to keep running powertop every now and then to tweak stuff (during one login session) as some services had started again. This was probably how my installation was configured though.

Hmm, I haven't done extensive testing with powertop so that may well be true on some setups. On my laptop though, the tweaks seem to "stick" as long as I'm logged on.

---

### Post by Expert Novice on 2012-01-11
@I_can_see_the_light  Ok, so I tried the mods you recommended the other day from the crunchbanglinux.org forum.

Initial results from looking at Powertop are favourable with the battery drain having gone from an average of 18w down to 12.5 or so. I need to charge the battery and see what happens with a full charge but that's bound to make some difference. Thanks for the tip.

I still need to get to grips with Powertop. Still not sure how to use it for maximum power savings. If I could find out how to turn down the screen brightness as well, that would help a lot.

---

### Post by I_can_see_the_light on 2012-01-12
> **Expert Novice said:**
> @I_can_see_the_light  Ok, so I tried the mods you recommended the other day from the crunchbanglinux.org forum.

Initial results from looking at Powertop are favourable with the battery drain having gone from an average of 18w down to 12.5 or so. I need to charge the battery and see what happens with a full charge but that's bound to make some difference. Thanks for the tip.

I still need to get to grips with Powertop. Still not sure how to use it for maximum power savings. If I could find out how to turn down the screen brightness as well, that would help a lot.That's good news :)


Have a look at that powersave script again. There's two lines for changing the brightness.

For battery:
```
# Set backlight brightness to 50%
echo 5 > /sys/devices/virtual/backlight/acpi_video0/brightness
```
and AC:
```
echo 10 > /sys/devices/virtual/backlight/acpi_video0/brightness
```

The path to the brightness setting can be different on your machine, mine is /sys/devices/virtual/backlight**/fujitsu-laptop/**brightness.
To find out your brightness level you need to browse to the folder /sys/devices/virtual/backlight**/xxx/** and look for a file called *max_brightness* and then adjust the values in the powersave script accordingly. But remember, you can't set any **.5** values.

---

### Post by Expert Novice on 2012-01-13
I had another look at the powersave script. The brightness is already set to 50. I changed it to 10 to see what would happen but there was no effect.

There's no max_brightness file where you suggested but I did a search for any other with that name. I found 5 with various values but I wasn't able to save any changes in them. I tried sudo nautilus but was still getting the 'You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.' message.

The AC line was the same as you posted.

Otherwise the machine seems to be doing a lot better. After powering on and leaving the machine to settle for a few minutes with the screen closed, on opening it I saw projected battery life of over 6 hours. This soon drops when the backlight starts up at 100% but was still over 4 for a time. Previously it was showing me just over 2 hours after a full charge so that's a good improvement with the Crunchbang mod but the screen brightness is still eating the battery rather quickly. Still runs hot but from what I've read that seems to be a feature of 11.10. How thoughtful of the developers to give us laptop users a way of keeping warm through the winter months :p

Despite persisting issues you've been a big help. Thank you!!

---

### Post by I_can_see_the_light on 2012-01-13
> **Expert Novice said:**
> Still runs hot but from what I've read that seems to be a feature of 11.10. How thoughtful of the developers to give us laptop users a way of keeping warm through the winter months :p :D  Yeah I've read a lot about that too. 

Could you unplug the power cord for 10 seconds and then plug it back in, then run the following command in a terminal: ```
cat /var/log/pm-powersave.log | grep -i aspm
``` and post the output here.

> **Expert Novice said:**
> Despite persisting issues you've been a big help. Thank you!!You're welcome.

---

### Post by Expert Novice on 2012-01-13
Ok, what does this tell us?

david@david-Laptop:~$ cat /var/log/pm-powersave.log | grep -i aspm
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:
/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:
/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:
/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:
/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:
/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:
/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:
/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:
/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:
/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:
/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:
/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:
/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:
/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:
/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:
/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:
/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:
/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:
/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:
/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:
/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:
/usr/lib/pm-utils/power.d/pcie_aspm false: success.

---

### Post by I_can_see_the_light on 2012-01-14
> **Expert Novice said:**
> Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:
/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:
/usr/lib/pm-utils/power.d/pcie_aspm false: success.
This part tells me that the script successfully enabled and disabled the power saving for the pcie_aspm module. 


That should reduce the heat a lot but just to double check this, unplug the cord again and post the output of this command: ```
cat /sys/module/pcie_aspm/parameters/policy
```


The brightness setting not working was strange. According to a post in the thread on crunchbang forums this command will find the file that should be modified by the script: ```
find /sys -iname brightness
```
And this command should tell you where the max_brigtness file resides: ```
find /sys -iname max_brightness
```

---

### Post by Expert Novice on 2012-01-14
Ok...

cat /sys/module/pcie_aspm/parameters/policy gives us

default performance [powersave]

I wasn't sure if you meant to leave the power unplugged or not so that is with the power unplugged and below is the output after unplugging and reconnecting again after 10 seconds...

[default] performance powersave

Output from the other two codes below...

david@david-Laptop:~$ find /sys -iname brightness
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/brightness
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/brightness
/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/leds/rt2800pci-phy0::radio/brightness
/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/leds/rt2800pci-phy0::assoc/brightness
/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/leds/rt2800pci-phy0::quality/brightness
find: `/sys/kernel/debug': Permission denied
david@david-Laptop:~$ find /sys -iname max_brightness
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/max_brightness
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/max_brightness
/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/leds/rt2800pci-phy0::radio/max_brightness
/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/leds/rt2800pci-phy0::assoc/max_brightness
/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/leds/rt2800pci-phy0::quality/max_brightness
find: `/sys/kernel/debug': Permission denied

These are the files I was talking about in post 35. If I understand correctly Nautilus over rides the protection given to certain system files allowing us to change them but even accessing these files through Nautilus I still get the perrmision denied message when trying to save changes.

/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/max_brightness contains only the number 4882 as do the files 

 /sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/actual_brightness 

and 

 /sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/brightness

Perhaps if these could be changed it would make some difference but as I say, permission seems to be denied.

---

### Post by I_can_see_the_light on 2012-01-14
> **Expert Novice said:**
> cat /sys/module/pcie_aspm/parameters/policy gives us

default performance [powersave]

[default] performance powersaveOk, then it's working as it should.


> **Expert Novice said:**
> david@david-Laptop:~$ find /sys -iname brightness
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/brightness
**/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/brightness**
david@david-Laptop:~$ find /sys -iname max_brightness
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/max_brightness
**/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/max_brightness**

/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/max_brightness contains only the number 4882

try this: ```
sudo echo 2441 > /sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/brightness
```This should set the backlight brightness to 50%

---

### Post by Expert Novice on 2012-01-14
david@david-Laptop:~$ sudo echo 2441 > /sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/brightness
bash: /sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/brightness: Permission denied
david@david-Laptop:~$

---

### Post by I_can_see_the_light on 2012-01-14
> **Expert Novice said:**
> Looking in Ubuntu System Settings/System Info/Graphics I can see **Driver - Unknown** and Experience - Standard.I can't believe I missed this, please post the output of these commands: ```
glxinfo | grep -i direct
```and ```
glxinfo | grep -i opengl
```

> **Expert Novice said:**
> david@david-Laptop:~$ sudo echo 2441 > /sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/brightness
bash: /sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/brightness: Permission denied
david@david-Laptop:~$Well, I don't really know what to do now. There has to be another way to change the screen brightness. Have you tried changing any settings for this from the *Screen* property in System Settings?

---

### Post by Expert Novice on 2012-01-14
[QUOTE= Have you tried changing any settings for this from the *Screen* property in System Settings?[/QUOTE]

Yes, in 'screen'  I can move the slider that controls brightness but the brightness doesn't change and when I leave 'screen and reopen it the slider has returned to it's original position, about 90% of full on.
There are keys on the keyboard that adjust brightness. If I try these the slider will not move below 90%. It will move to 100% but the brightness remains the same.

I had to install glxinfo. Here are the output...

david@david-Laptop:~$ glxinfo | grep -i direct
The program 'glxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install mesa-utils
david@david-Laptop:~$ sudo apt-get install mesa-utils
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  mesa-utils
0 upgraded, 1 newly installed, 0 to remove and 296 not upgraded.
Need to get 27.6 kB of archives.
After this operation, 135 kB of additional disk space will be used.
Get:1 [http://gg.archive.ubuntu.com/ubuntu/](http://gg.archive.ubuntu.com/ubuntu/) oneiric/universe mesa-utils i386 8.0.1+git20110129+d8f7d6b-0ubuntu2 [27.6 kB]
Fetched 27.6 kB in 0s (74.0 kB/s)   
Selecting previously deselected package mesa-utils.
(Reading database ... 128584 files and directories currently installed.)
Unpacking mesa-utils (from .../mesa-utils_8.0.1+git20110129+d8f7d6b-0ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up mesa-utils (8.0.1+git20110129+d8f7d6b-0ubuntu2) ...
david@david-Laptop:~$ glxinfo | grep -i direct
direct rendering: Yes

david@david-Laptop:~$ glxinfo | grep -i opengl
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile x86/MMX/SSE2
OpenGL version string: 2.1 Mesa 7.11
OpenGL shading language version string: 1.20
OpenGL extensions:
david@david-Laptop:~$

---

### Post by I_can_see_the_light on 2012-01-14
The Sandybridge chip sets are known to behave badly, the only thing I have left to suggest (at the moment at least) is to create a Live USB stick and download [this file]("http://bazaar.launchpad.net/~xorg-edgers/xorg-server/xorg-pkg-tools/view/head:/xorg-edgers-live-test") to the root directory of the newly created Live USB. Then boot your live USB and run the script.

Here's the source of my suggestion: [mesa libraries, drm modules, xserver]("https://wiki.ubuntu.com/XorgOnTheEdge")
The [xorg-edgers launchpad site]("https://launchpad.net/~xorg-edgers/+archive/ppa") tells me that I have to link to their page if I publish instructions on how to install from their archive.

When the script has finished you'll get an error saying something about GDM, but that's because GDM is no longer present in a stock Ubuntu install. To start the graphical shell again you need to run ```
sudo service lightdm start
```

But it seems like xorg-edgers is updating their packages right now so it might be better to wait until everything is updated.

Another thing would be to try a newer kernel, try searching the forums for this. And to find out your kernel version either open up System Monitor or enter this in a terminal: ```
uname -r -m
```

---

### Post by Expert Novice on 2012-01-14
My kernel is 3.0.0-12-generic i686

From looking [here]("http://www.kernel.org/") see the latest version is 3.2.1 but I have no idea how to go about installing and using this after downloading.

Is it something you can do with a few terminal commands or more complicated?

Thanks

---

### Post by Expert Novice on 2012-01-14
Running sudo apt-get uprade now :-)

---

### Post by I_can_see_the_light on 2012-01-14
First of all, apply all available updates. Then go [here]("https://launchpad.net/ubuntu/+source/linux/3.2.0-9.16/+build/3092079") and download the latest Ubuntu 12.04 kernel or use these three direct links: [one]("https://launchpad.net/ubuntu/+source/linux/3.2.0-9.16/+build/3092079/+files/linux-headers-3.2.0-9_3.2.0-9.16_all.deb"), [two]("https://launchpad.net/ubuntu/+source/linux/3.2.0-9.16/+build/3092079/+files/linux-headers-3.2.0-9-generic_3.2.0-9.16_i386.deb"), [three]("https://launchpad.net/ubuntu/+source/linux/3.2.0-9.16/+build/3092079/+files/linux-image-3.2.0-9-generic_3.2.0-9.16_i386.deb")

Save them to a new folder with nothing else inside, then open up a terminal and cd to the directory containing the three files. Enter ```
sudo dpkg -i *.deb
```
It shouldn't be necessary but run this command afterwards anyway: ```
sudo update-grub
```
Now reboot. Your new kernel should be booting automatically since its version is higher than the one you have right now. 

If the OS doesn't boot or if you experience problems then reboot and after the [POST screen]("http://en.wikipedia.org/wiki/Power-on_self-test") hold shift (I think) to get the Grub menu to appear and boot the kernel you are using right now. The easiest way to uninstall the new kernel is to first install [Synaptic]("apt://synaptic") from the Software Center and then, from inside Synaptic click the button *Status* and then in the list to the left click *Installed (local or obsolete)*. The three packages you installed should be visible on the right and just right click them and choose *Mark for complete removal*, then click *Apply*.

---

### Post by Expert Novice on 2012-01-14
Also ran sudo apt-get dist upgrade and am now on 3.0.0-14-generic i686.

How would I go about installing 3.2.1 from [www.kernel.org?](www.kernel.org?)

Why is it the newest kernel I seem to be able to get is 3.0.0-14? Do the upgrade/update commands I used not install the latest available versions?

Thanks again

---

### Post by Expert Novice on 2012-01-14
Ah, ok, just saw your most recent post. Will have to have a look at that tomorrow. Got to go for now.

Appreciating all your help :-)

---

### Post by I_can_see_the_light on 2012-01-14
> **Expert Novice said:**
> Why is it the newest kernel I seem to be able to get is 3.0.0-14? Do the upgrade/update commands I used not install the latest available versions?

Those commands will only install the latest updates that has been made available for your Ubuntu release. We normally only get "minor version" updates (e.g. 3.0.0-12 -> 3.0.0-14) except for Firefox, Thunderbird, Chromium and possibly some other programs that use a rapid release cycle. In other words, those commands will do the exact same thing as the Update Manager does :)

---

### Post by Expert Novice on 2012-01-16
Ok, that's great, thanks. Now running 12.04 3.2.0-9-generic i686 but still getting the same issues sadly. CPU possibly running a little cooler but if so only by a couple of degrees so it's difficult to tell for sure. On the positive side though I did briefly see a projected 4h25m of battery shortly after booting earlier and I've learned some more useful knowledge. 

I downloaded kernel 3.2.1 from [http://www.kernel.org/](http://www.kernel.org/) so might get round to installing that soon but this is in a different format to what came from the direct links you gave me so I think I'll need some different commands. There is a read me in the folder but still I think I'll have some more learning to do.

---

### Post by sonicsackboyver.25.04 on 2012-01-16
i used to have an issue like that but it dosent seem to be happening anymore

---

### Post by Expert Novice on 2012-01-16
Glad to hear it :-) Was that with 11.10? Did you find a solution?

---

### Post by I_can_see_the_light on 2012-01-16
@ Expert Novice
The kernels from kernel.org are not compiled, you have to do that yourself and that's something I haven't done myself so I can't give you any guidance. But If you want to try the 3.2.1 kernel you can try this link:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2.1-precise/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2.1-precise/")

Download the *linux-headers generic i386*, *linux headers all* and *linux-image generic i386*

---

### Post by sonicsackboyver.25.04 on 2012-01-16
> **Expert Novice said:**
> Glad to hear it :-) Was that with 11.10? Did you find a solution?

idk it just stopped

---

### Post by Expert Novice on 2012-01-16
I'll keep my fingers crossed for a similar recovery then.

@I_can_see_the_light Ok, I think compiling kernels at this stage might be considered trying to run prior to acquiring the skill of walking so yes, I'll try 3.2.1. via your link. That looks like a useful index to keep an eye on... Thanks again :-)

---

### Post by Expert Novice on 2012-01-16
I recall reading somewhere recently how the power management used by HP, Dell etc is often (understandably I suppose) optimised for Windows and often over rides anything else so trying to use anything else with it just doesn't work. I wonder if there are settings in my laptops BIOS that can be changed, or maybe just switch off the power management altogether and allow Ubuntu to look after it own settings. Will try to remember to have a look when booting next time.

---

### Post by tkabir11 on 2012-01-17
> **KdotJ said:**
> No worries. I'm not sure if will be the same for you, but the issue I had was that my CPU was always running at full speed (always at 2.8Ghz) even when it was doing nothing. Of course, this didn't show up as the CPU usage being high in the system monitor. This used to be an issue on laptops with various linux distributions, I've had the same trouble with others I've tried.

cpufrequtils will let you have more control over this (well, it will do it for you if you want) and control your CPU speeds dynamically. After doing this my CPU was idling at 1.05GHz and only worked harder when it needed to... my temperature dropped by around 20C and the battery lasted much longer. However, I've only just returned to Ubuntu so I'm not sure if all this comes as standard now.

Good luck with Ubuntu :D

Hi- I was just reading through this thread as I've been having the same overheating problem as the OP. From reading your posts- I installed cpufrequtils- and in the output of cpufreq-info I get the following: 

```
analyzing CPU 0:
  driver: p4-clockmod
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.00 ms.
  hardware limits: 208 MHz - 1.67 GHz
  available frequency steps: 208 MHz, 417 MHz, 625 MHz, 833 MHz, 1.04 GHz, 1.25 GHz, 1.46 GHz, 1.67 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 208 MHz and 1.67 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 1.67 GHz (asserted by call to hardware).
  cpufreq stats: 208 MHz:0.00%, 417 MHz:0.00%, 625 MHz:0.00%, 833 MHz:0.00%, 1.04 GHz:0.00%, 1.25 GHz:0.00%, 1.46 GHz:0.00%, 1.67 GHz:100.00%
analyzing CPU 1:
  driver: p4-clockmod
  CPUs which run at the same hardware frequency: 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 10.00 ms.
  hardware limits: 208 MHz - 1.67 GHz
  available frequency steps: 208 MHz, 417 MHz, 625 MHz, 833 MHz, 1.04 GHz, 1.25 GHz, 1.46 GHz, 1.67 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 208 MHz and 1.67 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 1.67 GHz (asserted by call to hardware).
  cpufreq stats: 208 MHz:0.00%, 417 MHz:0.00%, 625 MHz:0.00%, 833 MHz:0.00%, 1.04 GHz:0.00%, 1.25 GHz:0.00%, 1.46 GHz:0.00%, 1.67 GHz:100.00%
```

As you can see- the governer 'performance' is being used- which I believe is making my cpu run at fullspeed (1.67 GHz) at all times.So I just need to know how can I change the settings of cpufreq governer?? Currently my laptop is heating up quite a bit and the fan is spinning fast even when idle. 
Thanks.

---

### Post by Expert Novice on 2012-01-17
@tkabir11  That's odd. I just looked at cpufreq-info again and it's showing my CPU running full speed at 2.3GHz but if I look at System Monitor it's nowhere near that. Something is getting confused, as well as me. The other day cpufreq-info showed only 800MHz. I have changed kernel since then though so maybe that has something to do with it. Which version/kernel are you using now?

---

### Post by Expert Novice on 2012-01-17
I just did cpufreq-info again and now it's showing 800MHz

---

### Post by tkabir11 on 2012-01-17
> **Expert Novice said:**
> @tkabir11  That's odd. I just looked at cpufreq-info again and it's showing my CPU running full speed at 2.3GHz but if I look at System Monitor it's nowhere near that. Something is getting confused, as well as me. The other day cpufreq-info showed only 800MHz. I have changed kernel since then though so maybe that has something to do with it. Which version/kernel are you using now?

I'm using Ubuntu 11.10 3.0.0-12-generic.
When I check system monitor, cpu usage is showing at around 5-15% on idle; but on cpufreq-info its always showing as 1.67Ghz.

---

### Post by Expert Novice on 2012-01-17
Well, I'm no expert but something seems to be getting confused.

I running kernel 3.2.1 but still getting the same issues as I've had with the previous ones. If you look back in the thread you'll see the possible solutions I've tried, the most helpful of which were the one in post 37 [here]("http://ubuntuforums.org/showthread.php?t=1874306&page=4"), and there's a link to crunchbanglinux forums in post 15 on this thread with a mod that made a big difference to the projected battery life. Maybe you could try that.

---

