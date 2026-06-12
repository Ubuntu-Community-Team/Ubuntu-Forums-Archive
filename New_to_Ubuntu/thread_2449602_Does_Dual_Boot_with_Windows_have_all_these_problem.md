---
title: "Does Dual Boot with Windows have all these problems? (with Youtube links)"
date: 2020-08-30
forum: New to Ubuntu
---

### Post by j2ee on 2020-08-30
[https://www.youtube.com/watch?v=_JeP5wGd6wk](https://www.youtube.com/watch?v=_JeP5wGd6wk)
I thought about dual boot then found out this video. Sound like very bad. I am having Windows 10 in multiple computers and I don't need a pure Ubuntu machine. Install full Ubuntu in an USB stick is a good idea for my case?

---

### Post by VMC on 2020-08-30
I have zero problems dual(triple) booting Windows, Linux. I use separate partitions. Then again everyone has their own experience.
Have you heard about using Windows [WSL]("https://docs.microsoft.com/en-us/windows/wsl/install-win10")?

---

### Post by oldfred on 2020-08-30
Video is just discussing the advantages of a virtual install of Windows, if you do not game.

Windows is not particularly dual boot friendly. It does its own updates and may also update UEFI reseting system to defaults. So after Windows updates, you may have to change some settings again.
And regular Windows updates turn fast start up back on, which prevents grub from booting Windows. With UEFI it is just boot Windows directly from UEFI and resolve any issue. But with BIOS, you have to temporarily install a Windows boot loader to boot into Windows.

I have multiple full installs on flash drives. Primarily used for emergency boot. Once booted they are just as fast as programs are in RAM. But writes are terribly slow, even after some settings to improve read/write.
But I just used an old SSD with an USB3 to SATA adapter and it was as fast or faster than HDD and almost as fast as internal SSD. Decided to update a system with M.2 SATA SSD to NVMe drive and put M.2 into USB adapter and it was very fast.  

Some flash drives are faster than others, but I suggest using a SSD, if you can afford it. They are a lot lower in cost now. If you prefer HDD, only use an adapter with external power as USB power is often not enough for HDDs. My adapter for SSD worked great, but with HDD would not work at all.

---

### Post by j2ee on 2020-08-30
> **oldfred said:**
> Video is just discussing the advantages of a virtual install of Windows, if you do not game.

Windows is not particularly dual boot friendly. It does its own updates and may also update UEFI reseting system to defaults. So after Windows updates, you may have to change some settings again.
And regular Windows updates turn fast start up back on, which prevents grub from booting Windows. With UEFI it is just boot Windows directly from UEFI and resolve any issue. But with BIOS, you have to temporarily install a Windows boot loader to boot into Windows.

I have multiple full installs on flash drives. Primarily used for emergency boot. Once booted they are just as fast as programs are in RAM. But writes are terribly slow, even after some settings to improve read/write.
But I just used an old SSD with an USB3 to SATA adapter and it was as fast or faster than HDD and almost as fast as internal SSD. Decided to update a system with M.2 SATA SSD to NVMe drive and put M.2 into USB adapter and it was very fast.  

Some flash drives are faster than others, but I suggest using a SSD, if you can afford it. They are a lot lower in cost now. If you prefer HDD, only use an adapter with external power as USB power is often not enough for HDDs. My adapter for SSD worked great, but with HDD would not work at all.

Thx for sharing. Is there security concern if I install a full version of Ubuntu in a flash drive then using it in a computer with harddisk having Windows 10 in it? If Windows 10 is infected, may be it would infect the Ubuntu in flash drive as well?

---

### Post by SeijiSensei on 2020-08-30
> **j2ee said:**
> Thx for sharing. Is there security concern if I install a full version of Ubuntu in a flash drive then using it in a computer with harddisk having Windows 10 in it? If Windows 10 is infected, may be it would infect the Ubuntu in flash drive as well?
The chances of that happening are infinitesimally small. A Windows virus won't know what to do with Linux.  

After 25 years of using Linux, I never think about infections at all.  It's just not a concern.

---

### Post by j2ee on 2020-08-30
> **SeijiSensei said:**
> The chances of that happening are infinitesimally small. A Windows virus won't know what to do with Linux.  

After 25 years of using Linux, I never think about infections at all.  It's just not a concern.

Unbuntu in USB stick with a window harddisk is still much safer to access bank website comparing to Windows with antivirus? LOL

I read old post saying no one would write an virus to attack Linux from Windows so it is not something to worry in practical point of view

---

### Post by grahammechanical on 2020-08-31
Apparently it is a matter of cost effectiveness. As there are more Windows machines around the crooks can make more money out of Windows users than Linux users.

It might be true to say that there are few virus in Linux but that does not mean that are not any vulnerabilities. Here is a list of detected and fixed vulnerabilities in Linux

[https://ubuntu.com/security/notices](https://ubuntu.com/security/notices)

Regards

---

### Post by monkeybrain20122 on 2020-08-31
Installing Ubuntu on a usb stick is not going to be very performant. It is not a medium meant for serious use. If you are serious about using Ubuntu but don't want dualboot or give it its own machine install in an external hd.

---

### Post by j2ee on 2020-09-01
> **monkeybrain20122 said:**
> Installing Ubuntu on a usb stick is not going to be very performant. It is not a medium meant for serious use. If you are serious about using Ubuntu but don't want dualboot or give it its own machine install in an external hd.

I just use it for easy tasks, should not feel big speed different.

---

### Post by Quarkrad on 2020-09-01
You have posted on a forum where many long standing Ubuntu users have dual booted with Windows for many years - through win7 to win10.  May do not dual boot because they have no need for Windows but I have not read any posts where people do not dual boot because of any inherent problems.  Where problems do occur, e.g. due to a Windows update, people on this forum quickly offer a solution - having dual booted for about 9years I have only experienced one issue where I've had to come to this forum.  So .... it is potentially difficult for people here to advise you other than positively as dual booting works.

---

### Post by monkeybrain20122 on 2020-09-01
> **j2ee said:**
> I just use it for easy tasks, should not feel big speed different.

In that case you may as well use a live usb (with persistence if desired). I would be easier and run faster than installing into a usb thumb since the live usb runs in ram.

---

### Post by j2ee on 2020-09-01
> **monkeybrain20122 said:**
> In that case you may as well use a live usb (with persistence if desired). I would be easier and run faster than installing into a usb thumb since the live usb runs in ram.

Any security concern since I cannot update/patch OS/Browser/Program with live usb with persistence?

---

### Post by monkeybrain20122 on 2020-09-01
> **j2ee said:**
> Any security concern since I cannot update/patch OS/Browser/Program with live usb with persistence?

If you worry then don't use persistence, it then just runs in ram and everytime you unplugged you have a fresh start. But you should be  able to update the browser with persistence. You can install things and keep them, just need to enable the repositories.

---

### Post by mastablasta on 2020-09-02
if you just plan to toy around with linux, then install it to virtualbox. no need to reboot and all that when going to linux. you just launch kt and pick up form where you left (virtualbox will save the state) or boot fresh.

for example one of the guides with pics: [https://automaticaddison.com/how-to-install-ubuntu-20-04-and-virtualbox-on-your-computer/](https://automaticaddison.com/how-to-install-ubuntu-20-04-and-virtualbox-on-your-computer/)

you can use another one.

all you need is 4 GB ram (well you should give at least 2 GB to ubuntu OS) and about 8-10 Gb free hard disk.

i did this on old single core CPU and windows XP (with PAE kernel so it sort of supported 4 GB ram) and it worked perfectly. i used Xubuntu (or rather pure XFCE) because it was lighter on resources. i gave the OS only 1 GB ram. i later moved to bare metal (HDD) install.

on low powered AMD E450 (dual core) i could give it one core and i used 512 MB for  the setup (i had only 2 GB ram in total), but there i used it only for server.

---

### Post by j2ee on 2020-09-02
> **mastablasta said:**
> if you just plan to toy around with linux, then install it to virtualbox. no need to reboot and all that when going to linux. you just launch kt and pick up form where you left (virtualbox will save the state) or boot fresh.

for example one of the guides with pics: [https://automaticaddison.com/how-to-install-ubuntu-20-04-and-virtualbox-on-your-computer/](https://automaticaddison.com/how-to-install-ubuntu-20-04-and-virtualbox-on-your-computer/)

you can use another one.

all you need is 4 GB ram (well you should give at least 2 GB to ubuntu OS) and about 8-10 Gb free hard disk.

i did this on old single core CPU and windows XP (with PAE kernel so it sort of supported 4 GB ram) and it worked perfectly. i used Xubuntu (or rather pure XFCE) because it was lighter on resources. i gave the OS only 1 GB ram. i later moved to bare metal (HDD) install.

on low powered AMD E450 (dual core) i could give it one core and i used 512 MB for  the setup (i had only 2 GB ram in total), but there i used it only for server.

I would do something like ebanking, virualbox in windows is too risky.

---

### Post by TheFu on 2020-09-02
> **j2ee said:**
> I would do something like ebanking, virualbox in windows is too risky.

That's a matter of opinion.
Windows is too risky to be allowed on the internet, IMHO.

I haven't dual booted in a very long time, but still use Windows almost daily for a few things that just aren't there on Linux. Mainly financial tools and video editing (certain types only). My Windows video editing machine is a laptop from 2011-ish. For financial stuff, I have Windows running inside a VM.  Two different systems, but I'd prefer to run Windows in the VM for a number of reasons mainly related to snapshots, backups, and nearly instant restores when something bad happens.  The VM host is Linux (Ubuntu 16.04 server). When that laptop dies, I probably won't replace it.  If the VM host dies, I have a failover system that can be running in about 45 minutes for all the VMs.  Some of the VMs have been migrated forward since 2008 from machine to machine. Each time, gaining a performance boost.  Virtual machines move between different hardware pretty easily in the Linux world.
I started with VMs on a PentiumM CPU --> Core2Dou E6600 --> Core2Dou X8600 --> Core i5-750 --> Ryzen 5 2600.  That's a huge jump in performance with each move. Also, the amount of RAM has gone up. Initially, the box barely had enough to support virtual machines at all.  Then I ran with 8G and about 10 VMs, then 16G and about 20 VMs with plenty of extra RAM for a few play VMs.  Until just this June, 16G was fine.  After installing 20.04 into a VM, the RAM needs seemed to increase. I think it was snap packages. I was exceeding the 16G a few times a week, so another 16G was added to provide headroom.
```
$ free -h
              total        used        free      shared  buff/cache   available
Mem:            31G         16G        733M        454M         13G         12G
Swap:          4.3G        2.1G        2.1G
```

There are few good reasons to dual boot at all anymore, but we each have our own reasons.

If I were going to do on-line banking, then I'd use a new TinyCore desktop every week. TinyCore with a modern browser is about 64MB in size - a trivial download. That's the complete, Linux, OS.  Less code means more secure, fewer attack vectors.  When I was a CFO handling bank stuff for the company, I'd create a bootable flash with the latest TinyCore and boot that from one of the computers here, do my stuff, then reboot. Extremely tiny chance of being hacked or having a keylogger.  Bank accounts for businesses don't get the same protections where I live that bank accounts for individuals get. For a business, once the account is hacked, that money is gone. So much for paying everyone or paying bills. Imagine even a tiny company with just 5 well-paid employees having the money to make payroll in the account every month. Poof - that money could be gone.

---

### Post by j2ee on 2020-09-03
> **TheFu said:**
> That's a matter of opinion.
Windows is too risky to be allowed on the internet, IMHO.

I haven't dual booted in a very long time, but still use Windows almost daily for a few things that just aren't there on Linux. Mainly financial tools and video editing (certain types only). My Windows video editing machine is a laptop from 2011-ish. For financial stuff, I have Windows running inside a VM.  Two different systems, but I'd prefer to run Windows in the VM for a number of reasons mainly related to snapshots, backups, and nearly instant restores when something bad happens.  The VM host is Linux (Ubuntu 16.04 server). When that laptop dies, I probably won't replace it.  If the VM host dies, I have a failover system that can be running in about 45 minutes for all the VMs.  Some of the VMs have been migrated forward since 2008 from machine to machine. Each time, gaining a performance boost.  Virtual machines move between different hardware pretty easily in the Linux world.
I started with VMs on a PentiumM CPU --> Core2Dou E6600 --> Core2Dou X8600 --> Core i5-750 --> Ryzen 5 2600.  That's a huge jump in performance with each move. Also, the amount of RAM has gone up. Initially, the box barely had enough to support virtual machines at all.  Then I ran with 8G and about 10 VMs, then 16G and about 20 VMs with plenty of extra RAM for a few play VMs.  Until just this June, 16G was fine.  After installing 20.04 into a VM, the RAM needs seemed to increase. I think it was snap packages. I was exceeding the 16G a few times a week, so another 16G was added to provide headroom.
```
$ free -h
              total        used        free      shared  buff/cache   available
Mem:            31G         16G        733M        454M         13G         12G
Swap:          4.3G        2.1G        2.1G
```

There are few good reasons to dual boot at all anymore, but we each have our own reasons.

If I were going to do on-line banking, then I'd use a new TinyCore desktop every week. TinyCore with a modern browser is about 64MB in size - a trivial download. That's the complete, Linux, OS.  Less code means more secure, fewer attack vectors.  When I was a CFO handling bank stuff for the company, I'd create a bootable flash with the latest TinyCore and boot that from one of the computers here, do my stuff, then reboot. Extremely tiny chance of being hacked or having a keylogger.  Bank accounts for businesses don't get the same protections where I live that bank accounts for individuals get. For a business, once the account is hacked, that money is gone. So much for paying everyone or paying bills. Imagine even a tiny company with just 5 well-paid employees having the money to make payroll in the account every month. Poof - that money could be gone.


Thx for sharing. Ubuntu live usb (not full install) is not safe?

---

### Post by TheFu on 2020-09-03
> **j2ee said:**
> Thx for sharing. Ubuntu live usb (not full install) is not safe?

It is too hard to keep current.  Any Linux that hasn't been patched in the last week isn't safe. Will you pull a new "daily" ISO build every week to use? That's a huge amount of download that something like 65MB TinyCore can easily fill if used in the same way just for web surfing/banking.  
Only use the ISO for one purpose - either online banking OR normal surfing.  Banking always, always, gets a special ISO.

Whether any distro is safe or not cannot be said. It is about limiting attack vectors. Less code means a smaller attack surface and fewer bugs.  Is a 65MB distro less code than a 1.3GB distro?  YES!  Will you be hacked using one or the other for the 15 minutes you need it every week?  Nobody can say, but it is less code.  Are both teams making up to date tools and packages with all the latest known patches?  I don't know in every case.  Canonical certainly has 20x more people on the job, but they have 20x more code to deal with too.

Only you can decide.

---

### Post by j2ee on 2020-09-03
> **TheFu said:**
> That's a matter of opinion.
Windows is too risky to be allowed on the internet, IMHO.

I haven't dual booted in a very long time, but still use Windows almost daily for a few things that just aren't there on Linux. Mainly financial tools and video editing (certain types only). My Windows video editing machine is a laptop from 2011-ish. For financial stuff, I have Windows running inside a VM.  Two different systems, but I'd prefer to run Windows in the VM for a number of reasons mainly related to snapshots, backups, and nearly instant restores when something bad happens.  The VM host is Linux (Ubuntu 16.04 server). When that laptop dies, I probably won't replace it.  If the VM host dies, I have a failover system that can be running in about 45 minutes for all the VMs.  Some of the VMs have been migrated forward since 2008 from machine to machine. Each time, gaining a performance boost.  Virtual machines move between different hardware pretty easily in the Linux world.
I started with VMs on a PentiumM CPU --> Core2Dou E6600 --> Core2Dou X8600 --> Core i5-750 --> Ryzen 5 2600.  That's a huge jump in performance with each move. Also, the amount of RAM has gone up. Initially, the box barely had enough to support virtual machines at all.  Then I ran with 8G and about 10 VMs, then 16G and about 20 VMs with plenty of extra RAM for a few play VMs.  Until just this June, 16G was fine.  After installing 20.04 into a VM, the RAM needs seemed to increase. I think it was snap packages. I was exceeding the 16G a few times a week, so another 16G was added to provide headroom.
```
$ free -h
              total        used        free      shared  buff/cache   available
Mem:            31G         16G        733M        454M         13G         12G
Swap:          4.3G        2.1G        2.1G
```

There are few good reasons to dual boot at all anymore, but we each have our own reasons.

If I were going to do on-line banking, then I'd use a new TinyCore desktop every week. TinyCore with a modern browser is about 64MB in size - a trivial download. That's the complete, Linux, OS.  Less code means more secure, fewer attack vectors.  When I was a CFO handling bank stuff for the company, I'd create a bootable flash with the latest TinyCore and boot that from one of the computers here, do my stuff, then reboot. Extremely tiny chance of being hacked or having a keylogger.  Bank accounts for businesses don't get the same protections where I live that bank accounts for individuals get. For a business, once the account is hacked, that money is gone. So much for paying everyone or paying bills. Imagine even a tiny company with just 5 well-paid employees having the money to make payroll in the account every month. Poof - that money could be gone.

> **TheFu said:**
> It is too hard to keep current.  Any Linux that hasn't been patched in the last week isn't safe. Will you pull a new "daily" ISO build every week to use? That's a huge amount of download that something like 65MB TinyCore can easily fill if used in the same way just for web surfing/banking.  
Only use the ISO for one purpose - either online banking OR normal surfing.  Banking always, always, gets a special ISO.

Whether any distro is safe or not cannot be said. It is about limiting attack vectors. Less code means a smaller attack surface and fewer bugs.  Is a 65MB distro less code than a 1.3GB distro?  YES!  Will you be hacked using one or the other for the 15 minutes you need it every week?  Nobody can say, but it is less code.  Are both teams making up to date tools and packages with all the latest known patches?  I don't know in every case.  Canonical certainly has 20x more people on the job, but they have 20x more code to deal with too.

Only you can decide.

Do you install browser everytime for banking? I see download option and it is 16mb

[http://tinycorelinux.net/downloads.html](http://tinycorelinux.net/downloads.html)

---

### Post by mastablasta on 2020-09-04
if you browse only to your bank page (so one page/website only) then the only way to get infected via browser would be if the bank site was infected with malware. now if that happens, then you have bigger problem than your PC. well actually the bank has it and through it their users.

you could update it every time or use persistance. or you could just use the live version.

again many people just use virtualbox for that, in virtualbox you can also boot just a live session (no need to actually install).

ventoy, yumi, multibootUSB for multi OS booting form ISO images on one USB.

---

### Post by TheFu on 2020-09-04
DNS can be taken over, so we never know which banking site we are actually hitting, unless the bank requires x.509 certs for authentication.  In the USA, I've not seen that, but I heard it was common in Germany.  

DNS settings can be taken over by having a hacked router, which is always a concern.  
[LIST]
[*][https://arstechnica.com/information-technology/2018/06/vpnfilter-malware-infecting-50000-devices-is-worse-than-we-thought/](https://arstechnica.com/information-technology/2018/06/vpnfilter-malware-infecting-50000-devices-is-worse-than-we-thought/)
[*][https://www.fkie.fraunhofer.de/en/press-releases/Home-Router.html](https://www.fkie.fraunhofer.de/en/press-releases/Home-Router.html)
[/LIST]

Banking best practices from Security Reporter Brian Krebs: 
  [https://krebsonsecurity.com/online-banking-best-practices-for-businesses/](https://krebsonsecurity.com/online-banking-best-practices-for-businesses/)

Brian is in the middle of all sorts of online criminal activities, so much so that the criminal organizations have tried to make his life hard by
[LIST]
[*]SWATting 
[*]getting him arrested for illegal drugs (they mailed him drugs and called the cops)
[*]DDoS'd his website with 665 Gbps of traffic
[*]Repeated attempts to hack his online accounts; Paypal failed and got socially engineered, BTW. Do you use paypal?
[*]He's shown the insides of ATM skimmers, organized criminals operating hundreds of ATMs around the world.
[*]Inside stories from ID theives
[*]many more ...
[/LIST]
His multi-part articles read like a spy novel.

Anyways, try to follow his banking advice, the best you can.

---

