---
title: "HDD swap of Ubuntu Instalation 12.10x64"
date: 2013-01-09
forum: New to Ubuntu
---

### Post by 90Ninety on 2013-01-09
Two (more) challenges I have pit myself against (last one has nearly beat me ..) 

Summary :  My first intention was to run Ubuntu as a server and have since set  it up on old hardware . However since using Ubuntu, I decided I want to keep it for desktop use as-well , while keeping server features .  Though as I'm using old hardware , I am wanting to tinker ( see below) 

 1st Hurdle : So to achieve this, could I simply take the HDD from the excising 'old' hardware/rig into my High-End  Windows rig ? Hypothetically I would like to dual boot and use Linux and windows 50:50 but wait , there added features I'd like . 

 2nd Hurdle : Assuming a dual boot feature would work,even with a new install(If I must) , could I use Virtual software while using window to Boot the Ubuntu 12.10 Installation ?  This would save time re-booting and  loading   back into Ubuntu


Am I asking too much , would this be difficult , would I need a fresh Install of Ubuntu , would the virtual desktop load the excising Ubuntu installation ? 


Please comment

---

### Post by TheFu on 2013-01-09
> **90Ninety said:**
> Two (more) challenges I have pit myself against (last one has nearly beat me ..) 

Summary :  My first intention was to run Ubuntu as a server and have since set  it up on old hardware . However since using Ubuntu, I decided I want to keep it for desktop use as-well , while keeping server features .  Though as I'm using old hardware , I am wanting to tinker ( see below) 

 1st Hurdle : So to achieve this, could I simply take the HDD from the excising 'old' hardware/rig into my High-End  Windows rig ? Hypothetically I would like to dual boot and use Linux and windows 50:50 but wait , there added features I'd like . 

 2nd Hurdle : Assuming a dual boot feature would work,even with a new install(If I must) , could I use Virtual software while using window to Boot the Ubuntu 12.10 Installation ?  This would save time re-booting and  loading   back into Ubuntu


Am I asking too much , would this be difficult , would I need a fresh Install of Ubuntu , would the virtual desktop load the excising Ubuntu installation ? 


Please comment

This can all be achieved with a little know how.  

Putting multiple HDDs inside a single PC works.  Just run boot-repair after you get them installed.  I'd recommend that the Linux HDD be added second, to avoid screwing the Windows install.

Or 

You could create a similar-sized partition on the 1st disk in the Windows PC and use something like **dd** to mirror all the contents from the 2nd disk over.

It is possible to run (windows or linux) under either (windows or linux) virtualization servers. Both work well provided you are smart with the virtual hardware that each client OS is provided. However, it generally is **NOT possible** to use the same windows or Linux installation for both hardware and virtual installations. **I don't know anyone that has that working.**

If you are interested in virtualization and you have enough RAM, CPU, and disk, this is a great way.  It works best with Core2Duo or better CPUs - basically, you want a CPU with vt-x support.

When you virtualize an OS, it doesn't see any of your real hardware, only the virtual hardware that the hypervisor shows. That means your high-end GPU doesn't matter to the VM at all. Same for any physical audio cards and disk controllers - it doesn't matter to the virtual machines - those will only see virtual devices.

Check out** virtualbox** for beginning-level virtualization, though I would not recommend it for servers. It is pretty great for desktop on desktop virtualization.

---

### Post by 90Ninety on 2013-01-15
Have ran into a few hurdles ( maybe I shouldn't tinker so much ) 

 I put my 1.5 TB HDD (with working Linux 12.10x64 installation) from my low range rig to my High range Rig . Now I have a HD7770 and Phenom x2 3.0 Ghz , so should be much better (in theory) 
 However the OS seems unstable , I keep getting black screens and my monitor cannot handle the signal from the GPU 

 I will try a DVI/VGA cable instead of the HDMI to see if this is a solution 

 This issue is intermittent however when the OS does work , some programs fail to launch ( Steam for example ) 

 Also tried Shank , which in theory should work , however it looks horrible and runs dog slow 

Any suggestions , I believe it to be driver issues 

New Rig 
Phenom x2 2.8 BE 
Asus Mobo  
8 Gig Corsair Ram

---

### Post by TheFu on 2013-01-16
> **90Ninety said:**
> Have ran into a few hurdles ( maybe I shouldn't tinker so much ) 

 I put my 1.5 TB HDD (with working Linux 12.10x64 installation) from my low range rig to my High range Rig . Now I have a HD7770 and Phenom x2 3.0 Ghz , so should be much better (in theory) 
 However the OS seems unstable , I keep getting black screens and my monitor cannot handle the signal from the GPU 

 I will try a DVI/VGA cable instead of the HDMI to see if this is a solution 

 This issue is intermittent however when the OS does work , some programs fail to launch ( Steam for example ) 

 Also tried Shank , which in theory should work , however it looks horrible and runs dog slow 

Any suggestions , I believe it to be driver issues 

New Rig 
Phenom x2 2.8 BE 
Asus Mobo  
8 Gig Corsair Ram

Well, if both those boxes didn't use the same GPU driver, you could be screwing the monitor.  It is best to disable/remove any GPU drivers **before** moving 1 install into a new box unless you know it has an identical GPU.  I think video over HDMI sorta just works, it is only the audio+video that needs the specific GPU drivers.

If that doesn't solve the issue, you'll want to search for "ubuntu install {insert-motherboard-model}" on google. That should provide any necessary installation tips needed. If that doesn't find anything, start looking up all the chips used in the system on a LHC - **Linux Hardware Compatibility List**.  If you find that a specific component isn't supported, either search for a close driver or swap it out.

Forget about Steam for the time being. That program is too new to worry about. It is just for gaming anyway.  What programs do you really need to work on the PC to make money? Those are your priorities.

---

