---
title: "VMware, VirtualBox, Xen, KVM... which is best?"
date: 2009-05-01
forum: Recurring Discussions
---

### Post by expelledboy on 2009-05-01
I just wanted to find out which was the most popular virtualization software out there.. 

I picking up that VirtualBox is winning that race at the moment with KVM becoming a stronger contender.

Please leave your experiences, pros and cons of the software you prefer.

---

### Post by garythegoth on 2009-05-01
> **expelledboy said:**
> I just wanted to find out which was the most popular virtualization software out there.. 

I picking up that VirtualBox is winning that race at the moment with KVM becoming a stronger contender.

Please leave your experiences, pros and cons of the software you prefer.

Each have their advantages. Personally I prefer VirtualBox.

---

### Post by expelledboy on 2009-05-01
> **garythegoth said:**
> Each have their advantages. Personally I prefer VirtualBox.

I prefer vbox at the moment, but I have been reading up and it seems that KVM has more features and runs just as fast.. not only that but it is what ubuntu recommends!

---

### Post by kk0sse54 on 2009-05-01
I want to virtualize all types of OSs not just mainly linux OSs therefore I much prefer Vmware over Vbox.

---

### Post by expelledboy on 2009-05-01
> **C!oud said:**
> I want to virtualize all types of OSs not just mainly linux OSs therefore I much prefer Vmware over Vbox.

VirtualBox runs all types of OSs! Are you saying that it does do as well as VMware?

---

### Post by HavocXphere on 2009-05-01
VB its smaller & simpler than VMware and still does exactly what I need.

That might all change though depending on which one pushes the 3d/DirectX angle the hardest.

---

### Post by kk0sse54 on 2009-05-01
> **expelledboy said:**
> VirtualBox runs all types of OSs! Are you saying that it does do as well as VMware?

No it does not, ever try using NetBSD in Vbox?

---

### Post by expelledboy on 2009-05-01
I must say I havent.. have you tried anything other that Vbox or VMware?

---

### Post by StOoZ on 2009-05-01
experienced with both vmware & vbox , and I prefer vbox...

---

### Post by kk0sse54 on 2009-05-01
> **expelledboy said:**
> I must say I havent.. have you tried anything other that Vbox or VMware?

Yes I have, including Qemu and KVM

---

### Post by smbm on 2009-05-01
OpenVZ

---

### Post by clhsharky on 2009-05-01
KVM    - Seems fast enough, fairly easy to set up, and has done what I need.

---

### Post by Eisenwinter on 2009-05-01
> **expelledboy said:**
> VirtualBox runs all types of OSs! Are you saying that it does do as well as VMware?
Can vbox virtualize 64-bit OSes?

---

### Post by Paqman on 2009-05-01
> **Eisenwinter said:**
> Can vbox virtualize 64-bit OSes?

The crippled OSE version that's in the repos can't, but if you get the full-caliber version from their site it can.

---

### Post by AndyCooll on 2009-05-01
My preference is for VirtualbBox because there are open-source versions available (and those are personally important principles for me). However when I've tried VMWare in the past I've found this to be slightly more compatible with Windows applications than VirtualBox.

cool:

---

### Post by Steve McDermott on 2009-05-01
I'm currently using VMware & have no experience of the others.

Essentially, I use a Windows system for developing websites (Dreamweaver, Fireworks, etc). I have installed VMware to run Ubuntu server in a virtual machine, to aid testing my website work without having to upload to a remote server.

---

### Post by expelledboy on 2009-05-01
> **smbm said:**
> OpenVZ

hmm.. I forgot about that one.
Now how do I add to a poll? :confused:

---

### Post by Delever on 2009-05-01
Migrated from VMware to VirtualBox and I am very happy with it.

---

### Post by samjh on 2009-05-01
VirtualBox by a long shot.  I've been using it for the past year to run Windows XP and try other operating systems.  It's easy to use, has good community support, and works well. :)

---

### Post by expelledboy on 2009-05-02
I guess virtualbox is the winna!

---

### Post by expelledboy on 2009-05-02
KVM doesnt even feature? Even though it supports 64bit OSs and vbox (free) doesnt.. something must be really wrong with it that I am just not picking up! Or is it just that vbox got there first?

---

### Post by wmcbrine on 2009-05-02
My processor is too old to support true hardware virtualization, which realistically limits me to VMware or VirtualBox. Between them, VBox wins because it's open source, and I can install it from the repos.

---

### Post by 123Mike on 2009-05-11
> **expelledboy said:**
> I just wanted to find out which was the most popular virtualization software out there.. 

I picking up that VirtualBox is winning that race at the moment with KVM becoming a stronger contender.

Please leave your experiences, pros and cons of the software you prefer.

I don't like VirtualBox anymore because it doesn't provide SMP. I just bought this quad core system, and the VM only gets to utilize one single core. I'm highly disappointed as well as the resistance and protests from the VirtualBox creators when they get confronted with others requesting this features. Anywhere from "you don't need it" to "it doesn't make sense to need it".

Zzo, if you have a hardware virtualization enabled cpu (eg. not the Q8000 series), go for KVM.

---

### Post by swoll1980 on 2009-05-11
> **C!oud said:**
> No it does not, ever try using NetBSD in Vbox?

What good would it do you, running BSD in a Virtual Machine?

---

### Post by expelledboy on 2009-05-24
> **123Mike said:**
> Zzo, if you have a hardware virtualization enabled cpu (eg. not the Q8000 series), go for KVM.

Hmm.. that is interesting. No has brought this up as an argument against vbox. I have already installed virtualbox thou :-k I have a core2duo and I did notice it was slow, but I just thought that was the speed virtual machines ran?

I looked at KVM for ages and thought it looked better.. but as you can see people steered to using vbox?

---

### Post by kk0sse54 on 2009-05-24
> **swoll1980 said:**
> What good would it do you, running BSD in a Virtual Machine?

What good would it do you, running linux in a Virtual Machine?

---

### Post by Simian Man on 2009-05-24
For running a few OSes at home?  VirtualBox.
For running a grid of virtualized machines in an enterprise situation?  KVM.

The two use cases are so different, yet your poll fails to address that.

---

### Post by expelledboy on 2009-05-24
> **Simian Man said:**
> For running a few OSes at home?  VirtualBox.
For running a grid of virtualized machines in an enterprise situation?  KVM.

The two use cases are so different, yet your poll fails to address that.

Ya.. I guess it does #-oTo tell the truth I did not know anything about either of them when I started the poll.

You dont think that you could use KVM for running a few OS's at home though, just as well as vbox?

---

### Post by kc3 on 2009-05-24
I say VirtualBox all the way :D

---

### Post by Simian Man on 2009-05-24
> **expelledboy said:**
> You dont think that you could use KVM for running a few OS's at home though, just as well as vbox?

You could, but it would be more work for features you wouldn't need.  Virtualbox's easy to use interface makes it perfect for home use.

---

### Post by egon1987 on 2009-05-26
My vote for XEN (source, not XenExpress). The best free virtualization platform for corporate usage... lots of features (for example.. try to virtualize 64bit 4Gb ram and 8core VM with other 0$ virtual software).

KVM does CPU and Memory virtualization for Windows Guests a bit worse than XEN. And it was too unstable (1y back) for production HVM (Windows VM).

So why so many votes for VirtualBox ?
Well.. you can install it for ubuntu with 3 clicks :) .. no hassle with filling out "trial" request forms, compiling or setting up. And it aint bad for testing some new OS-s.

---

### Post by aeiah on 2009-05-26
i tested xen at work and its fantastic at certain things. i could ping a virtual machine from another part of the office and live migrate the virtual machine from one physical machine to another simply by shutting the first physical machine off. it dropped just 1 packet in the ping test, sometimes not even that.

it is however, rubbish at windows, so we couldnt use it in the end. it was also a bit hardcore and intimidating for other people in the office because the VMs tend to just be cli.

we went with KVM in the end, because it integrates better with the virtual machine manager than virtualbox does and i didnt like the commercial aspect of virtual box.

i use virtualbox at home to try out livecds and stuff though. its great for casual use.

---

### Post by aeiah on 2009-05-26
> **egon1987 said:**
> 
KVM does CPU and Memory virtualization for Windows Guests a bit worse than XEN. And it was too unstable (1y back) for production HVM (Windows VM).


perhaps i was too hasty in my conclusions with xen. i should never have trusted my manager to test the windows virtualisation side of things :mad:


but in kvm we have 64bit 4GB VMs running quite nicely. only with 4 cores though.

---

### Post by expelledboy on 2009-06-04
I have now tried virtualbox and kvm and I have to say I am equally impressed.

Simian Man was very right however in saying that they each have their own use.
[LIST]
[*]Vbox - for the average user who would like to run separate OS's, for whatever reasons, without actually interfering with the current system
[*]kvm - as a solution to run a multitude of systems all on one base OS instead of installing each to a separate hardware platform
[/LIST]
I have also tried OpenVZ.. the great advantage of this setup is the virtual machines run at native speed! The problem though is only virtual machines that can share the kernel with the host OS can be run on the system. No m$. Boo-hoo ;)

One other thing to mention is you must install Vbox PUEL edition. Why? Because you agree to the PUEL licence when you use the guest addition anyway! :o And you dont even get to use the all the feature of the proprietary version.. sneaky bastards hey :popcorn:

Just follow the instructions as the bottom of [this]("http://www.virtualbox.org/wiki/Linux_Downloads") link to add VboxPUEL to your repos so you can update through synaptic.

---

### Post by praveesh on 2009-06-07
> **123Mike said:**
> I don't like VirtualBox anymore because it doesn't provide SMP. I just bought this quad core system, and the VM only gets to utilize one single core. I'm highly disappointed as well as the resistance and protests from the VirtualBox creators when they get confronted with others requesting this features. Anywhere from "you don't need it" to "it doesn't make sense to need it".
Zzo, if you have a hardware virtualization enabled cpu (eg. not the Q8000 series), go for KVM.
Which series of cpu support hardware based virtualisation? . I have intel Core2Duo E4600 but when I tries to run kvm , it replies that "Ubuntu does not support running Kvm without hardware based virtualisation" . I ran the command to know whether cpu support intel vt, it didnt give any output(indicates that vt not supported)

---

### Post by zeny on 2009-06-17
At work I use KVM to host a Windows box, and all our servers are KVM. IMO I don't think anything can touch its performance.

---

### Post by mecat on 2009-06-19
I use kvm on my servers. kvm can use internal storage very well (i tested both on dell r710, 4X2,8GHz, 4x1BG nic broadcom, 2x300G SAS 15k raid-1, lvm [guest as lvm lv] and kvm-072 was 2 times faster than vmvare esx 4), but has slower network implementation (vmware up800/down400mbit/s, kvm up450/down300mbit/s). I would like to compare it to xen.
I use it also on my notebook, but it is very tircky (wifi and bridging do not fit well). For normal people vbox is much better ;-)

---

### Post by thisllub on 2009-06-19
One thing VirtualBox has going for it is compatibility.
I can use my VirtualBox machines in a Linux, Solaris or Windows host.
VMWare appears to support BSD as well.

I think on a single machine with a single VM VirtualBox outperforms VMWare.
That may have changed since I last compared them 6 months ago.

---

### Post by maurizio.omissoni on 2009-06-23
I have to evaluate neu Virtualizations Systems as we are not happy with the VMWare Server 2.0... compilation at every update (Tools also), and there is no mac-plugin to use the webinterface.
I discovered proxmox that uses webinterface and java and can be administrated from every platform. proxmox uses openVZ and KVM/qemu as virtualization system. So you have all the technology: content, full and para-virtualization. I tested with a 400$ amd phenom triple-core machine.
proxmox will use the whole machine and installation lasts 15 minutes.
u can download templates directli from the webinterface. VM can be created mannually, from templates or from iso-files or cd/dvd, simply great and smart.
Reccomandations are: 4 linux server -> openVZ, 4linux-desktop and Win -> KVM.
My results:
installing a debian 5.0 (lenny) throug openVZ templates within 2 minutes.
boot that machine: 1 second!!!!!!!!!!!!!!
installing xp pro from iso-file through KVM within 6 minutes
booting xp in 12 seconds !!!!!
I am impressed.

---

### Post by JedMeister on 2009-08-07
I haven't voted yet and won't until I have done some testing....

I have used VirtualBox the most (mostly on Windows Host). At this point I would say:
[LIST]
[*]_VirtualBox_
[LIST]
[*]Pros - easy setup (in Ubuntu repos), easy to use, not a steep learning curve, great in a desktop environment.
[*]Cons - system intensive when mulitple VMs running, poor guest OS performance, difficult to run headless or in a server environment.
[/LIST]
[*]_VMWare_ (I haven't tried VM ESXi - only used VMServer on a Windows Host - so may not be relevant to Linux version)
[LIST]
[*]Pros - easy setup, easy to use, easy to set up for use in server environment.
[*]Cons - system intensive when mulitple VMs running, poor guest OS performance.
[/LIST]
[*]_KVM_ (I haven't used this yet so only theoretical)
[LIST]
[*]Pros - easy setup (in Ubuntu repos), easy setup for use in server environment, supports paravirtualisation (I think?).
[*]Cons - not sure?
[/LIST]
[*]_Xen (Source)_ (I haven't used this yet so only theoretical)
[LIST]
[*]Pros - works well in server environment, supports paravirtualisation.
[*]Cons - requires custom kernel for paravirtualisation.
[/LIST]
[/LIST]

I am in the process of setting up a headless server with multiple guest VMs (7-10) running, most will be Linux (Ubuntu probably) but I will be running a couple of Windows guests so paravirtualisation is a must. I was originally planning to use Xen as it seems to be the favourite in the commercial world. I was disappointed when I discovered that Ubuntu only (officially) supports running as a Xen guest (rather than a guest & host) but I still planned to persevere as I wasn't aware that KVM supported paravirtualisation (it does now right?). Now I'm leaning toward KVM (assuming it supports paravirtualisation - due to simpler install and setup). Any opinions on that?

[edit] I've just found and installed [Proxmox VE]("http://pve.proxmox.com/wiki/Main_Page") (Virtual Environment) on my server. Its a bare-metal Debian based Virtual Machine Server that utilises OpenVZ (for Container Virtualisation) and KVM (for Full Virtualisation & Paravirtualisation). It has a web interface so is ideal for a headless server. You can install it on a pre-existing Debian install too so probably could install on Ubuntu if you so wanted to. I haven't been testing long but it looks brilliant and is exactly what I was after.
PS I've voted for KVM :)

---

### Post by merlinv12 on 2009-09-02
Thought I would throw my 2.5 cents in to the mix.

About 1 years ago, I looked into virtualization for my business. I played around with nearly all of them. I had a 4 cpu xeon server. Unfortunately, my server did not have the necessary cpu extensions (I think svt) to use kvm, so that was out. I tried vmware, xen and openvz. Virtualbox seemed to much of a hobbists VM to consider seriously. After testing the three above, here was our conclusion.

VMware: Big overhead, but truely isolated unmodified OSes can be run. You can virtually use any OS, windows or otherwise. The overhead hit was really high for our liking, and since we were only running linux servers we decided against it.

Xen: Xen was our favourite choice at the time, except for the fact that the OSes had to be modified b/c xen is paravirtualization. The overhead hit is not big. And we could run any linux OS we wanted. Its only major issue it has issues using default tls. Either have to disable tls support, or compile friendly version. We were planning on using it, until we tried a little gem called openvz.

OpenVZ: We ended up using it b/c there was very little overhead, superfast, smp support like Xen and VMware, backup and restore of VE's was as simple as Xen, and almost anyone, including a monkey, could manage it. So we used it. No hard limits, so systems use as much resources as they need and nothing more. Note: the VE OSes must be of similar kind. Essentially only linux.

For almost a year we were happy with OpenVZ, it is truely awesome, until we hit its deep and dirty problem. It has to do with how it and java communicate with each other. If you have a 2 gig system with 4 VE's and say the java VE is allowed 500 megs, when java checks memory it sees 4 gigs not 500 soft limit that is set. Since we started hosting java based web apps, this began to be a huge headache as we were having major memory issues, program malfunctions and so. So, now we are using Xen, and have been pretty happy with, though we miss the fact that we can set soft limits like that in OpenVZ.

So if you are not running any major java programs and only using linux, I highly recommend openvz, otherwise use xen for production environments.

Cheers

---

### Post by kandresen on 2009-12-19
WMware is proprietary and cost money for commercial and non-commercial use alike. It is a great solution, especially when ran from a Windows host - on a Linux host it requires a specially build kernel with proprietary extensions - not sure if this cause any limits today, but I did run into some problems with this several years ago... 

Xen has been an on/off project for me. It requires a Linux kernel and is system specific. Unfortunately I bought a quad Intel machine, not an AMD and found out the hard way that Intel only offered virualization in "protected mode" unlike AMD... This was a major issue as it only officially supported kernel 2.6.18, which did not have the work around for Intel processors built into later versions of the kernel. Though crippled a bit by Intel CPU's, virualization work ok as long as you don't try to give dedicated resources such as a network card or hard disk to a client system. 

VirtualBox is proprietary and only free for non-commercial use! It is a great solution from within OpenSolaris, Windows and Linux alike. I have mostly used it to run OpenSolaris from within Linux - apparently OpenSolaris no longer runs as easy on KVM as Sun stopped working on that project after Redhat bought it. VirtualBox, just as WMware require a priprietary kernel module, and notice that the kernel module cannot be loaded at the same time as the kernel module of KVM. 

KVM is GPL and an extension of the Qemu framework. KVM is essentially only available within Linux, however the system may be ran from any other system that can run Qemu! KVM is my solution of choice! You can give dedicated hardware to a guest system (i.e "-hdd /dev/sdX"). There are graphical frontends for Linux, Windows, and Mac. On linux they are not usually setup by defualt - I have mostly used "qemu-launcher" but there is also "qtemu". There is still more control by using command line, but these parameters may usually be added to the configuration files for the graphical ones...

---

### Post by chrisinspace on 2010-01-13
I'm going through this exercise now as I set up a virtual environment for my house.  I want to reduce the number of computers I have and dig deeper into virtualization to brush up my skills.  

I have been evaluating my choices, but I think I'm a bit limited by some constraints, mainly my processor.  I inherited an old server from a previous job.  It's been sitting in my basement for a few months, but I decided to put it to use for this project.  It's an IBM x306 with a 2.8GHz P4.  The problem is I don't think it supports Intel VT-x.  So, if I understand correctly, KVM is out.

I decided to give Xen a try.  It runs Linux machines just fine, but after a failed attempt and some research, it seems that without Intel VT-x, I can't set up a Windows guest.

Can anyone confirm my suspicions about Intel VT-x?  If I can't run KVM at all and can't set up a Windows guest in Xen, then I guess I'll go with VirtualBox.  I have been using it for years on my laptop to run a virtual copy of XP and play with other Linux distros.  I love it.  It's so easy to use and I think performance is generally good.  I was hoping to learn something new and geared more towards the enterprise, but for my personal home VM environment, I think a headless VirtualBox server will suit my needs just fine.  I plan to host a couple Linux guests and one or two Windows guests (no more than 5 servers total).  They need to have 24/7 availability, but they will only be serving a few client computers.  I have installed a 4-port NIC for a total of 6 network interfaces.  I'd like each guest to have it's own dedicated NIC.  Do you think VirtualBox is up to the task?

---

### Post by chrisinspace on 2010-01-15
Well, a couple of days into my setup and it's working great.  I found [these instructions]("http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-3.0-on-a-headless-ubuntu-9.04-server") on running VirtualBox in a headless mode and some thorough [documentation about VBoxManage]("http://www.virtualbox.org/manual/UserManual.html#vboxmanage") on the VirtualBox site.  So far, everything is going pretty smoothly.  I installed an Ubuntu guest, configured ssh, and set up some port forwarding in my router.  Using VBoxManage, I can start up the guest without opening a GUI console and then from a remote computer, ssh into it (via CLI or sftp using Filezilla).  I'm really happy with this setup and can't wait to get a couple more guests in place.  I doubt this solution would be robust enough for an enterprise implementation, but it works great for a home or small business scenario.

---

