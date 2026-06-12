---
title: "VmWare Player multi-boot fun."
date: 2007-07-23
forum: Other OS Talk
---

### Post by Shazaam on 2007-07-23
If you have been a little hesitant about running a dual/multi boot system I might have found the answer.
My system setup:
PuppyLinux, SimplyMepis and Ubuntu Dapper on a 320gig sata drive.
I use Ubuntu the most so I chose it for my Host.

Tools needed: VmWare Player( or Server, etc), installable livecd/dvd distro disks, and a gparted livecd.
Go here: [http://www.easyvmx.com/](http://www.easyvmx.com/) and make your virtual machine. NOTE: If you are going to install Mandriva use Mandrake as your guest OS instead of Mandriva as it's not supported with easyvmx (don't worry Mandriva works fine with this). I called my virtual machine "Massive Multi-Boot" but you can name it anything.  Memory size: 768 works ok. For networks I left it default. Under Disk Configuration I chose both cdroms, 2 IDE hard disk drives (one 80gig and the other 100gig). Sound and I/O Ports you can choose what you want. Same with experimental 3d. Click create virtual machine and you will be able to download your virtual machine in a zip file. Create a folder in your home directory called "My Virtual Machines" and extract the files from the zip you downloaded to there.

Now for the fun part! Insert the gparted livecd in your drive, start VmWare, make sure you click in the player window so you can use your mouse and keyboard (don't panic just press "Control+Alt" to release focus), and as it starts to run press F2 (you will see a promt)  to get to the player boot menu. Change the first boot to CDROM, save and exit and restart the player. The gparted livecd should boot, when it's finished booting partition your VIRTUAL disks as you want.
I want to stress that AT NO TIME, if you are running gparted in a VIRTUAL machine are you affecting ANY of your physical (real) drives.
When you are done partitioning your virtual drives reboot (through the gparted livecd right click menu) and shutdown VmWare. Gather up your installable livecd/dvds, restart VmWare and install the distro's on the VIRTUAL drives.
I have 1gig of real ram in my pc and sometimes VmWare player locks up my pc booting the VmWare distros so if you want a smoother experience you might want at least 2 gigs of real memory.
 My virtual multiboot:
Swap, damnsmalllinux, PuppyLinux, Knoppix and SimplyMepis on one virtual drive, Mandriva 2007 and Ubuntu on the other virtual drive. Total real folder size is 9.2 gigs. This will enlarge when you install anything in your virtual os's such as updates, apps etc.
Grub is installed and works fine, the only problems I have had are the memory ones listed earlier and I had to do a little virtual grub editing to to make it work (grub gets confused in a virtual multi-boot). Now on to getting them networked with my Ubuntu Dapper host!.

---

### Post by ryanVickers on 2007-07-23
I don't know how the rest of you have found it, but on my very fast machine, VMware (even with the tools) is quite slow, but **innotek VirtualBox** runs at a speed (even doing 3D) at about 95% of normal I think!  Consider this alternative to VMware - it's got more or comparable features and it works way better in my opinion!

I don't know why you would want a multi-booting virtual machine though! It defeats the purpose of the VM in the first place - so you don't have to reboot ever!

---

### Post by Gary.M on 2007-07-23
> **ryanVickers said:**
> I don't know how the rest of you have found it, but on my very fast machine, VMware (even with the tools) is quite slow, but **innotek VirtualBox** runs at a speed (even doing 3D) at about 95% of normal I think!  Consider this alternative to VMware - it's got more or comparable features and it works way better in my opinion!

I have tried both, Virtualbox first. I agree there are things to like about Virtualbox, BUT I experienced random aborts where my WinXP guest would vapourise in the blink of an eye, often at the most frustrating times. I couldn't live with that unreliability, so I installed the Vmware player, and I am happy. Rock stable, which is what counts first. I turn off anything in XP that eats CPU and I have an XP guest that is fast and stable.

By the way, I did quite a bit of forum reading on the Virtualbox problem. There are plenty of reports of these random aborts, but no solutions. Questions about it on the Virtualbox forum or mailing list go unanswered.

---

### Post by ryanVickers on 2007-07-23
Odd, I've never had that happen.  I just couldn't stand that moving a stupid scroll bar or dragging an icon took about 1 or 2 seconds to begin and then ran at ~3 fps!

---

### Post by Gary.M on 2007-07-23
> **ryanVickers said:**
> Odd, I've never had that happen.  I just couldn't stand that moving a stupid scroll bar or dragging an icon took about 1 or 2 seconds to begin and then ran at ~3 fps!

Did you install the Vmware Windows Tools? Once they're installed the Player runs fast.

---

### Post by ryanVickers on 2007-07-23
I did, and it was faster.  I tried even building a special VM with a bunch of acceleration enabled and stuff and what I posted above was about average.  At best, moving a window, lets say, would go about 4 to 10 fps!

---

### Post by swoll1980 on 2007-07-24
> **ryanVickers said:**
> I don't know how the rest of you have found it, but on my very fast machine, VMware (even with the tools) is quite slow, but **innotek VirtualBox** runs at a speed (even doing 3D) at about 95% of normal I think!  Consider this alternative to VMware - it's got more or comparable features and it works way better in my opinion!

I don't know why you would want a multi-booting virtual machine though! It defeats the purpose of the VM in the first place - so you don't have to reboot ever!

I spent $180 on vmware work station to find out a month later that innotek was free. I gave it  a shot and could not believe how fast my vms' were running. The difference is amazing. I uninstalled vmware and through it in the closet. I would throw it away, but then I would feel like even more of an idiot. I wouldn't even call it an alternitive, but rather the standard in virtualization software. You can use vmware as an alternative in case the world ever ends and vmware is the only virtualization software that survived.

---

### Post by Gary.M on 2007-07-24
> **swoll1980 said:**
> I spent $180 on vmware work station to find out a month later that innotek was free. I gave it  a shot and could not believe how fast my vms' were running. The difference is amazing. I uninstalled vmware and through it in the closet.

I truly wish that Virtualbox had done it for me... the stability problem was the killer. Vmware doesn't seem slower on my machine, which is fast but not the latest. In fact with my experience, I'm thinking that sometime I might actually pay my money and buy Vmware workstation!

---

### Post by ryanVickers on 2007-07-24
You may as well just use VMware Player - there's no features lost in my opinion because you just create the Vms on [easyvmx.com]("http://www.easyvmx.com/") anyways!

---

### Post by dmitrijledkov on 2007-07-24
I'm one of those Apple people and VMWare and Parallels Desktop both eat up all of my 1GB memory and I have to close every single app, therefore I'm going to do multiboot soon =)

---

### Post by ryanVickers on 2007-07-24
I've got 1Gb of memory and it works fine!  I also have a multi-boot (as well as the VM).  Depends on what I'm doing - VM for work (like flash) and the "real" boot for games! :)

---

