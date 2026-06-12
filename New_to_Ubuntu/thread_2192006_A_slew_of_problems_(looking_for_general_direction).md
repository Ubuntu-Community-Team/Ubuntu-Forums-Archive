---
title: "A slew of problems (looking for general direction)"
date: 2013-12-05
forum: New to Ubuntu
---

### Post by hopobyrne on 2013-12-05
Hi everyone,

I am, most unfortunately, back in Windows 7. I love love love Ubuntu but am an absolute beginner and am having problems. Here are just a few:

1. Unity will not load anything other than background screen. Only shell I can use is gnome-fallback.
2. Software center and other things like DebiG almost immediately stop responding and close down.
3. Apt-get does not work well. Unless I sudo apt-get update every login, it will get stuck at 50% building the dependency tree for everything.
4. Power options do not change. In Windows I set it to suspend after 5 minutes, in Ubuntu  I changed it for 30 minutes, but always suspends after 5 minutes nonetheless.

I'm sure this is all very vague, and I'm sorry for that. I was wondering if installing the 32-bit rather than the 64-bit may alleviate some of these ailments? Or if anyone could just point me in the right direction I would be so grateful.

Lenovo B570 laptop
4GB RAM
Intel Pentium 2.0 Ghz processor
64-bit operating system.
Graphics: Sandy Bridge something or other.

---

### Post by newb85 on 2013-12-05
Let's try to be more specific on some specs.   Please run
```
 sudo lshw -C video
```
```
 sudo lshw -C processor
```
Individually and post the outputs.

---

### Post by oldos2er on 2013-12-05
If you can get to gnome-fallback, please run the following command and copy/paste all the output here ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by hopobyrne on 2013-12-05
> **newb85 said:**
> Let's try to be more specific on some specs.   Please run
```
 sudo lshw -C video
```
```
 sudo lshw -C processor
```
Individually and post the outputs.
```

*-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:42 memory:d0000000-d03fffff memory:c0000000-c
*-cpu                   
       description: CPU
       product: Intel(R) Pentium(R) CPU B940 @ 2.00GHz
       vendor: Intel Corp.
       physical id: 30
       bus info: cpu@0
       version: Intel(R) Pentium(R) CPU B940 @ 2.00GHz
       serial: Not Supported by CPU
       slot: CPU
       size: 1900MHz
       capacity: 2GHz
       width: 64 bits
       clock: 100MHz
       capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer xsave lahf_lm arat epb xsaveopt pln pts dtherm cpufreq
       configuration: cores=2 enabledcores=2 threads=2

``````

sudo apt-get update && sudo apt-get upgrade
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                   
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy InRelease                                   
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release.gpg                       
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                         
Ign [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy InRelease                                 
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Sources                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                       
Ign [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-updates InRelease                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main amd64 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main i386 Packages                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                       
Ign [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-backports InRelease             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                       
Ign [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-security InRelease              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release                                     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release                                     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-proposed InRelease                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release                                     
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy Release.gpg                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main amd64 Packages                
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-updates Release.gpg             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-backports Release.gpg
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main amd64 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-security Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-proposed Release.gpg
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main amd64 Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-updates Release
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-backports Release                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main amd64 Packages                
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-security Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages                 
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-proposed Release
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy/main Sources                     
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy/restricted Sources
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy/universe Sources
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy/multiverse Sources
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy/main amd64 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy/restricted amd64 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy/universe amd64 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy/multiverse amd64 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy/main i386 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy/restricted i386 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy/universe i386 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy/multiverse i386 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en_US
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy/multiverse Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en_US
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy/restricted Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy/universe Translation-en
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-updates/main Sources
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-updates/restricted Sources
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-updates/universe Sources
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-updates/multiverse Sources
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-updates/main amd64 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-updates/restricted amd64 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-updates/universe amd64 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-updates/multiverse amd64 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-updates/main i386 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-updates/restricted i386 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-updates/universe i386 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-updates/multiverse i386 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-updates/main Translation-en
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-updates/multiverse Translation-en
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-updates/restricted Translation-en
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-updates/universe Translation-en
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-backports/main Sources
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-backports/restricted Sources
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-backports/universe Sources
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-backports/multiverse Sources
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-backports/main amd64 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-backports/restricted amd64 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-backports/universe amd64 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-backports/multiverse amd64 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-backports/main i386 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-backports/restricted i386 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-backports/universe i386 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-backports/multiverse i386 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-backports/main Translation-en
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-backports/multiverse Translation-en
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-backports/restricted Translation-en
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-backports/universe Translation-en
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-security/main Sources
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-security/restricted Sources
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-security/universe Sources
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-security/multiverse Sources
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-security/main amd64 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-security/restricted amd64 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-security/universe amd64 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-security/multiverse amd64 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-security/main i386 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-security/restricted i386 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-security/universe i386 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-security/multiverse i386 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-security/main Translation-en
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-security/multiverse Translation-en
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-security/restricted Translation-en
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-security/universe Translation-en
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-proposed/universe amd64 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-proposed/restricted amd64 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-proposed/main amd64 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-proposed/multiverse amd64 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-proposed/universe i386 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-proposed/restricted i386 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-proposed/main i386 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-proposed/multiverse i386 Packages
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-proposed/main Translation-en
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-proposed/multiverse Translation-en
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-proposed/restricted Translation-en
Hit [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-proposed/universe Translation-en
Ign [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy/main Translation-en_US
Ign [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy/multiverse Translation-en_US
Ign [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy/restricted Translation-en_US
Ign [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy/universe Translation-en_US
Ign [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-updates/main Translation-en_US
Ign [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-updates/multiverse Translation-en_US
Ign [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-updates/restricted Translation-en_US
Ign [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-updates/universe Translation-en_US
Ign [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-backports/main Translation-en_US
Ign [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-backports/multiverse Translation-en_US
Ign [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-backports/restricted Translation-en_US
Ign [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-backports/universe Translation-en_US
Ign [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-security/main Translation-en_US
Ign [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-security/multiverse Translation-en_US
Ign [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-security/restricted Translation-en_US
Ign [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-security/universe Translation-en_US
Ign [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-proposed/main Translation-en_US
Ign [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-proposed/multiverse Translation-en_US
Ign [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-proposed/restricted Translation-en_US
Ign [http://mirrors.gigenet.com](http://mirrors.gigenet.com) saucy-proposed/universe Translation-en_US
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic linux-signed-generic
  linux-signed-image-generic
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
```

---

### Post by oldos2er on 2013-12-06
I don't see anything wrong there, but I'm not familiar with the gigenet mirror you're using. I wonder if switching to the main server would help with apt-get getting "stuck" problem.

To upgrade the packages that have been kept back, run ```
sudo apt-get dist-upgrade
```

---

### Post by hopobyrne on 2013-12-06
Possibly it's my fault. When I entered sudo apt-get update && sudo apt-get upgrade into the terminal the first time, it went on for a lot longer, but my backscroll was set to 300 or 500, so I could not copy it all. I set backscroll to unlimited, re-entered the command, and what you saw in the last post was all that came up. It was way less lines than the first time.

Should I log in again and try again, this time copying everything?

I'll also switch my current mirror to the main server and see if that helps.

---

### Post by oldos2er on 2013-12-06
Are you still having a problem opening Software Center? If so, it might be helpful to rerun the commands to see if there are any errors. Also if you run Software Center in terminal it may show where the problem is. ```
software-center
```

---

### Post by stinkeye on 2013-12-06
I noticed you have the proposed repositories enabled which is not default.
> "Pre-released Updates (saucy-proposed)". The testing area for updates. This repository is recommended only to those interested in helping to test updates and provide feedback.

---

### Post by buzzingrobot on 2013-12-06
> **stinkeye said:**
> I noticed you have the proposed repositories enabled which is not default.

Yep. Disable that first and then do the update, upgrade, dist-upgrade dance.

---

### Post by hopobyrne on 2013-12-06
I have done so, and for the first time ever, I logged in and it doesn't say "System Program Problem Detected."

Software center is going just fine, it hasn't closed out. However when I run it from the terminal it does give me warnings and errors. I wish I knew what an insecure string pickle is...it certainly sounds interesting.

---

### Post by hopobyrne on 2013-12-07
I do hate to be a terrible bother. I had everything working much better, but then I entered this command and everything went very, very south.

dconf reset -f /org/compiz/

After that nothing would even load and I couldn't even power down or log out. I rebooted using the power button and when I did, I had to press "f" to fix something or other, at which point it rebooted automatically to Ubuntu.

When I logged in again, it told me that I was logging in with a different language and asked me politely if I would like to keep all my files in their original language. I chose yes.

And then I could get into gnome, but again could not open a single thing. Couldn't even alt+ctrl up or down to different work stations.

Would I be better off just re-installing, and if so to try the 32-bit version? I refuse to give up on Linux. It's just way too cool.

By the way, Ubuntu is booting from my SSD and Windows from my HDD. Not sure if that's relevant.

---

