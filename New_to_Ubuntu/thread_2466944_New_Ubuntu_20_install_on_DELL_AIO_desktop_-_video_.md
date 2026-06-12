---
title: "New Ubuntu 20 install on DELL AIO desktop - video problems"
date: 2021-09-10
forum: New to Ubuntu
---

### Post by symicron on 2021-09-10
Hey Everyone,

I'm new to the forum and I just installed Ubuntu 20 on my old desktop computer. I'm using Dell all-in-one hardware. I tried figuring this out on my own first... so here's the problem and here's what I've done to try to fix it:

When I login to Ubuntu my display is blurry and (for lack of a better description) it vibrates. I set up the hardware as a dual boot with a Windows 10 partition and the Windows OS is working fine. So this is only on the Ubuntu side.

Some of the troubleshooting recommendations I've tried included:


[LIST]
[*]Using Wayland at the login screen -- didn't help... still fuzzy
[*]Use "sudo ubuntu-drivers autoinstall" -- also didn't seem to help
[*]Open Software & Updates and look under the "additional drivers" tab -- there are no drivers there to select
[*]Add the ppa:ubuntu-x-swat/updates repository and then apt get && upgrade -- didn't help
[*]Search the manufacturer's website for drivers -- apparently there was an intel graphics update tool for this hardware but it's gone now
[/LIST]

Here's the hardware information from lshw:

  *-display                 
       description: VGA compatible controller
       product: Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:35 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64) memory:c0000-dffff

And now for the interesting part (and for my question):

In my troubleshooting I navigated through GRUB to the "advanced options" section where I booted Ubuntu with the Linux 5.8.0-43-generic kernel and the video works perfectly! So, what is the difference between this environment and the default boot environment? I've also booted to Ubuntu's Linux 5.11.0-34-generic kernel and get the same vibrating fuzziness. 

I'm just not sure what's different between these 2 environments or what to change. Any suggestions?

Thanks for your time!

---

### Post by Dennis N on 2021-09-10
Since the new 5.11 kernel appears suspect and your install is new,  it might be easiest to just install Ubuntu 20.04.1, which has the 5.4 kernel.
 Download and install from this iso:
[http://old-releases.ubuntu.com/releases/focal/ubuntu-20.04.1-desktop-amd64.iso](http://old-releases.ubuntu.com/releases/focal/ubuntu-20.04.1-desktop-amd64.iso)

Or, wait and see if a better answer comes along.

---

### Post by guiverc on 2021-09-11
I suggest you try and be precise with details.

Ubuntu 20?  No such release; do you mean Ubuntu Core 20, as the **20** or ***year*** format is used only by Ubuntu products that are ***snap* only**.

Ubuntu products using ***deb*** packages (but can use *snap* packages too) use the ***year.month* **format, eg. Ubuntu 20.04 LTS Desktop.

Desktop releases are all *deb* based thus are *year.month* in format, yes you can throw some *desktop* features on a *snap* only 20 product, but it's not the full experience of a 20.04 desktop system.

Ubuntu offers two kernel stack choices for LTS releases; GA is 5.4 for Ubuntu 20.04 LTS, and the HWE changes during the first two years of it's life, (5.4 *bumped* to 5.8 at 20.04.2, and is currently at 5.11 as upgrade it'll be at 20.04.3 currently).

You select the kernel stack at install time on a Server product, with Ubuntu *flavors* you select by ISO (eg. Lubuntu 20.04 & 20.04.1 media use the GA stack, 20.04.2 & later media default to HWE using Lubuntu as an example) - but Ubuntu 20.04 LTS desktop defaulted to HWE.

For more details you can see - [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

(you'll also find details on how to downgrade from HWE to GA; you can have both installed; they don't take up much extra disk space, but it will upgrades will be slightly more as both will get upgraded)

---

### Post by Dennis N on 2021-09-11
Only if you install 20.04 or 20.04.1 do you keep the 5.4 kernel. Otherwise, you have what is called the Hardware Enablement Stack (HWE) with kernel changing as your system reaches each new point version. 20.04.2 initially has the 5.8 kernel, but when your OS version becomes 20.04.3 through the normal update process, you get 5.11 kernel installed. It will happen again when it becomes 20.04.4 and you get whatever kernel is used in the 21.10 release.

HWE is to give system compatability with newer hardware. If yours works fine with the 5.4 kernel, you are set for 5 years with that by installing the 20.04.1 release.

---

### Post by guiverc on 2021-09-11
> **Dennis N said:**
> Only if you install 20.04 or 20.04.1 do you keep the 5.4 kernel. Otherwise, you have what is called the Hardware Enablement Stack (HWE) with kernel changing as your system reaches each new point version. 

That was the case with releases from 10.04 through to 18.04, but not Ubuntu 20.04 LTS Desktop.

In the [link I provided]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") you'll note

> All Ubuntu Desktop 20.04 LTS will ship with an updated kernel by  default. Also Ubuntu Desktop certified hardware may use OEM kernel  flavour, where required. Server installations will default to the GA kernel and provide the enablement kernel as optional. 

ie. **HWE is now the default for 20.04 Desktop installs **too (inc. 20.04 & 20.04.1 media).  `ubiquity` was modified to make it *smarter* and include other kernel options, from OEM to HWE by default.

Server installs use the GA yes.  Lubuntu uses `calamares` as it's installer, so it provided the GA stack with 20.04 & 20.04.1; as did some other *flavors* as well, but those using `ubiquity` can find other kernels installed; only `subiquity` lets the user decide at install time.

fyi:  I QA-tested Xubuntu 20.04 & 20.04.1 and on my *test* boxes I got the GA kernel, but my boxes are old and newer kernels maybe installed on different hardware; the new feature of `ubiquity`. Ubuntu 20.04 LTS Desktop installed the HWE kernel though on all my boxes.  ([I]I can't recall the results for Kubuntu & others I tested sorry).
[/I]

---

### Post by tea for one on 2021-09-11
> **symicron said:**
> I'm new to the forum and I just installed Ubuntu 20 on my old desktop computer. I'm using Dell all-in-one hardware
> **symicron said:**
> I booted Ubuntu with the Linux 5.8.0-43-generic kernel and the video works perfectly!
> **symicron said:**
> I'm just not sure what's different between these 2 environments or what to change.

Old hardware and now you have booted with a working kernel - looks like a good result to me.

I would not change anything or even try to figure out why one kernel is fine and the other one is troublesome.

Why not take some time and just explore the OS, see if you like it, test other devices (speakers, usb sticks etc), change the theme, add some new software, create some data and then back it up.

If you want a bit of terminal fun, you could edit grub to always boot into your newly discovered working kernel?

---

### Post by Dennis N on 2021-09-11
> ie. HWE is now the default for 20.04 Desktop installs too (inc. 20.04 & 20.04.1 media). 

If so, how would you explain this? 

```
dmn@Sydney:~$ neofetch --stdout
dmn@Sydney 
---------- 
OS: Ubuntu 20.04.3 LTS x86_64 
Host: MS-7B53 1.0 
[COLOR="#FF0000"]**Kernel: 5.4.0-81-generic**[/COLOR] 
```

---

### Post by grahammechanical on 2021-09-11
I would like to add something that I think might be useful for the Original Poster of this thread.

The system is arranged so that we always have an alternative Linux kernel to boot into. If you use Software Updater to update and it installs a newer kernel it will remove the oldest kernel and leave you with two newer kernels. So, be careful that you do not lose the 5.8 kernel.

If we use the terminal commands of update & upgrade to update newer kernels are installed but older kernels are not removed unless we run the autoremove command. So, I suggest using the terminal to update until you can trust the 5.11 kernel.

Regards

---

### Post by symicron on 2021-09-12
Thank you Dennis N! I'll keep in mind the idea of installing 20.04.1 with the 5.4 kernel. That may be a good solution.

I also noticed I could edit Grub to default to the older 5.8 version instead of having to manually select the advanced options and then select 5.8 from the sub-menu.

---

### Post by symicron on 2021-09-12
I definitely like the OS. I've used other flavors of Linux before. Just new here.

And yes... my plan for now is to use the older kernel. The problem is with future updates and eventually having to "fix" the problem. I don't understand why there would be a difference between the two kernels and am hoping someone might teach me something. :)

---

### Post by symicron on 2021-09-12
Thanks grahammechanical... you expressed my concern exactly!

Now seems like the best time to figure this out (and get involved in the community as well) while I use the older kernel.

---

### Post by symicron on 2021-09-12
Hello guiverc, 

I downloaded and installed the latest desktop ISO from the Ubuntu website. During installation I checked the box to update third party drivers. I also ran an update && upgrade after.

I'm running Ubuntu 20.04 LTS Desktop.

Thanks!

---

### Post by symicron on 2021-09-12
PS. I appreciate the helpful comments. 

Also, I thought I'd research the documentation for Linux kernels at Kernel.org to see if there was any mention. To be honest, it is difficult reading and I didn't find anything specific. I did notice that the kernel 5.11 released in February this year has already been marked EoL and replaced with 5.12. The latest kernel is 5.14.3 stable.

Does it make sense to attempt to update the kernel? [This website]("https://www.thomas-krenn.com/en/wiki/Ubuntu_LTS_Hardware_Enablement_Stack_information") seems to indicate that 5.8 is the current kernel version. Also, [Ubuntu's documentation]("https://wiki.ubuntu.com/FocalFossa/ReleaseNotes") says Focal Fossa (what I'm running) Ubuntu 20.04 uses HWE stack 5.8.

[This website]("https://www.omgubuntu.co.uk/2021/02/new-linux-5-11-kernel-features") indicates 5.11 was released to mainline distribution in April 2021 and rolled out this summer (which is probably why I have it in my install). They mention some graphics card updates but those are mostly newer cards (like Radeon) and wouldn't apply to my situation.

I did take a quick look at the [mainline distribution here]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.11/"). There are also folders for 5.12, 5.13 and 5.14 on that web server, so although I couldn't find any official kernel releases past 5.11 by the Ubuntu team it appears they're testing the later versions. 

To be honest, I think I'll just stick with 5.8 for now. I wish there were any easy way to see the differences between 5.8 and 5.11 to figure out why one works on my hardware and the other doesn't.

---

### Post by psychohermit on 2021-09-23
If I were you I would make a copy of the 5.8 kernel and stash it in my home directory. Just a little CYA in case the 5.8 kernel gets deleted.

You'll want to copy System-map, initrd.img and config for the 5.8 kernel.

--glenn

---

### Post by psychohermit on 2021-09-24
If I were you I would make a copy of the 5.8 kernel just to CYA.  You'll want to copy Config, initrd.img, and System.map and put them in a safe place, just in case the 5.8 kernel gets deleted.

Just my $0.02
--glenn

Damn my previous reply hadn't shown up yet

---

### Post by symicron on 2021-09-25
> **psychohermit said:**
> If I were you I would make a copy of the 5.8 kernel just to CYA.

Makes total sense. Thank you, Glenn!

---

