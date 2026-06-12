---
title: "Change Resolution of Ubuntu 22.04 on Hyper V"
date: 2023-07-17
forum: New to Ubuntu
---

### Post by hanayamahn on 2023-07-17
Hello friends, I am having some problems in Hyper V with Ubuntu 22.04, I cannot change the resolution of the machine, I have seen various tutorials and they all say to change the configuration in the file:

```
[FONT=var(--ff-mono)]sudo nano /etc/default/grub[/FONT]
```
But this does not work when I change it ubuntu lets it work does anyone know how to solve this problem it's been a couple of hours and I'm really getting desperate

---

### Post by TheFu on 2023-07-17
I don't know anything about hyper-v, but with other hypervisors, we have to change the fake hardware in teh VM setup, then inside the VM, let the OS know you want a different resolution. If running a GUI with Xorg as the display server, lxrandr is the bonehead tool to use.  I can't help with Wayland. Don't/Can't use it for my needs.

Different DEs will have different GUI methods to change screen resolution. The "Desktop Guide" for that DE will always have a page about that.

Settings in grub are only for grub and non-GUI logins, like Ubuntu Server would have.

None of this says that Hyper-V will support these things, but I can say that VMware Workstation, Player, VirtualBox, KVM/QEMU via virt-viewer, all work this way.  A few weeks ago, someone joined our LUG meeting for the same issue and we really couldn't help because nobody uses Hyper-V.  That's not unexpected for Linux people NOT use use MSFT as their base OS. We just don't do that.

The easy answer is to uninstall Hyper-V and install Virtualbox where many more people will have experience.  The only places I know that use Hyper-V are MSFT in Azure and 100% MSFT small/medium companies.

---

### Post by hanayamahn on 2023-07-17
I understand what really annoys me is that a month ago I installed the same problem and I solved it but I don't remember what the solution was.

---

### Post by TheFu on 2023-07-17
> **hanayamahn said:**
> I understand what really annoys me is that a month ago I installed the same problem and I solved it but I don't remember what the solution was.

OT:  I have a personal wiki for that sort of stuff and for web pages with good information, I use wallabag.  Not that any of this help, but it is a common problem.  

My tech wiki has nearly 400 pages.  My wallabag server has ... er ... 1252 saved websites.  Both can be searched to find exactly the information I need.  Wallabag gets cloned to my tablet and phone, so there's always something to read when I'm disconnected or in a waiting room.

Additionally, since I'm a Unix person, I have hundreds of scripts that I've written over the decades which solve specific problems and can be used as example code to build new solutions as needed.

Text is the universal way to store information. I don't get too hung up about formatting beyond comments/code.

---

### Post by hanayamahn on 2023-07-18
I finally found the solution in my case with Ubuntu 22.04 LTS "Jammy"


No, in my case it was not necessary to enter:

```
[FONT=var(--ff-mono)]sudo nano /etc/default/grub[/FONT]
```

And then change the following line to the resolution we want:

```
[COLOR=var(--black-800)][FONT=var(--ff-mono)]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video=hyperv_fb:3840x2160"[/FONT][/COLOR]
```

A solution that I think is easier and better is the following:
1- First of all we are going to enter the following route:


 ```
[COLOR=#232629][FONT=-apple-system]sudo nano /etc/modprobe.d/blacklist.conf[/FONT][/COLOR]
```[COLOR=#232629][FONT=-apple-system]

[/FONT][/COLOR]And we will add the following parameter to the list:
```
blacklist hyperv_fb
```

After this we save in the file we turn off the machine and from powershell we execute the following command:

```
set-vmvideo "Machine Name" -horizontalresolution::1920 -verticalresolution:1080 -resolutiontype single
```

With this we start the machine and it should work without problems.

---

### Post by TheFu on 2023-07-18
"fb" means frame buffer and is from the old, old, old, VGA days.  640x480.  Almost nobody uses FB anymore and hasn't in 15+ yrs, except when no other video driver works. Blacklisting a fb isn't a bad idea.

The rest is all MS-Windows specific and should help others.  There are a few people here who use hyperV at their $day_job, so perhaps they can confirm?  I suspect not, since most people using remote VPS don't run desktops, just servers which need no GUI.

Regardless, thanks for posting a possible solution.  A few weeks ago, someone joined my LUG with a similar GUI issue for HyperV. If they join again, I'll point them here.  I suspect they've switched to running Linux and are using KVM/QEMU as their hypervisor now, which doesn't have this issue.

---

### Post by MAFoElffen on 2023-07-20
Framebuffer still takes affect until the Graphics Engine (Xorg or Wayland) starts after the DM. He did the right thing in the grub2 cmdline argument... Setting "video=" in the kernel boot line is a common way, that still works to tell the kernel to use KMS setting to set the resolution until the graphics engine and graphics drivers take over.

Note mine:
```

mafoelffen@Mikes-B460M:~$ grep 'GRUB_CMDLINE_LINUX_DEFAULT=' /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="-- splash kvm-intel.nested=1 intel_idle.max_cstate=4 [COLOR=#ff0000]video=uvesafb:mode_option=1920x1080-32,mtrr=3,scroll=ywrap,noedid[/COLOR] intel_iommu=on iommu=pt i915.enable_gvt=1 i915.enable_guc=2 i915.enable_fbc=0 systemd.unified_cgroup_hierarchy=0 libata.force=noncq"

```
This machine comes up with the Grub2 menu in 1920x1080, shows the boot process messages in that mode, and stays in that mode throughout (even in XServer).

BUT-- By adding "blacklist hyperv_fb" to the blacklist, he just nulified that setting by telling Linux that is should prevent that framebuffer from loading at all. LOL. If he had left it alone at that point, it would have worked, just from that parameter.

The later command for Hyper-V then took over and reset the VM Guest Session into a Hyper-V specific guest graphics mode (Telling Hyper-V to start the guest in that graphics mode). Which is the one it is really using currently.

I do  Windows Server Insider testing and Hyper-V, and Linux Dev Testing and KVM... I'm not 100% sure, but I think he looked things up on the internet and mixed / combined answers into one solution, but didn't understand what each really meant.

---

### Post by TheFu on 2023-07-21
> **MAFoElffen said:**
>  'm not 100% sure, but I think he looked things up on the internet and mixed / combined answers into one solution, but didn't understand what each really meant.

That's completely understandable. It is very difficult for someone new to understand that different fixes can undo things prior fixes claim to work.  There are lots of blog posts by people who think they have a solution, but they really don't.  There are lots of moving parts in a Linux OS and things that work for 1 system don't always work for others.

I suspect we've all been there.  Linux moves pretty fast.  Only experience will help someone know when a particular subsystem in undergoing rapid changes or when commands have been stable for 20+ yrs and work exactly the same all that time.

---

### Post by MAFoElffen on 2023-07-25
I just migrated my old laptop to ZFS to maximize it for KVM snapshots and backups of my changed priorities on it... And I found an old xorg.conf file I wrote over 13 years ago, that I used to transfer to & use just for Linux VM Guest's. I originally wrote it for OpenSolaris. That worked for over a decade for KVM, MS Virtual Machine, MS Hyper-V, XEN Server, Citrix, VMware vSphere, VMware ESXi, VMware Workstation, VirtualBox, etc.

I forgot about it. I transferred it to an Ubuntu VM, switched it over to Xorg, and it still works. LOL. Some things never change.

---

