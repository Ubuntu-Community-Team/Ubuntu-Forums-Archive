---
title: "Does upgrading Ubuntu versions upgrade kernel versions?"
date: 2014-04-19
forum: New to Ubuntu
---

### Post by Gnawnsense on 2014-04-19
Was just browsing around on Reddit and seen a thread about Radeon drivers, so I took a look. I noticed that the discussion was about the kernel version 14.04 was using which looked to be 3.13.

I recently upgraded my 13.10 installation to 14.04 and went to check my kernel version because I had been contemplating installing the AMD proprietary drivers. I'm not much of a technical user, so kernel upgrades and issues are usually over my head. When I went to terminal to check, this is what I got:

```
uname -r
3.11.0-19-generic
```

I was just wondering if upgrading the distribution was the reason I was still on 3.11 or not?

---

### Post by wildmanne39 on 2014-04-19
When you upgrade it also upgrades the kernel, if it did not you most likely had upgraded the kernel at some point before you did an version upgrade. You may have a lock on your kernel to prevent it from being upgraded.

---

### Post by grahammechanical on 2014-04-19
This is what uname -r gives me

> 3.13.0-24-generic

Have you re-booted? Have you ran an update since the upgrade? One reason for having a new version of Ubuntu every six months is to bring in newer Linux kernels and the latest Linux hardware stack = the hardware Linux works with.

If you run this command the output should show all the Linux kernels on your system. It should show the 14.04 kernel and also your old 13.10 kernels

```
sudo update-grub
```

If you run this command it will list the proprietary video drivers available for your graphic card

```
ubuntu-drivers list
```

this command will give information about your card + all drivers available including the open source driver.

```
ubuntu-drivers devices
```

Regards.

---

### Post by Gnawnsense on 2014-04-19
Thanks for the responses!

> **Wild Man said:**
> When you upgrade it also upgrades the kernel, if it did not you most likely had upgraded the kernel at some point before you did an version upgrade. You may have a lock on your kernel to prevent it from being upgraded.

I originally was running Windows 7 on this machine. A few months ago with the 14.04 release looming, I decided to install 13.10, but after installation, I hardly ever booted into the system, and never did any manual upgrades.

On 14.04 release day my software updater said there was a new release available so I accepted it. Everything seems to of updated (to my limited knowledge) except the kernel.

> **grahammechanical said:**
> Have you re-booted? Have you ran an update since the upgrade?

Yes, I have rebooted multiple times, but definitely once the initial update was completed. I also haven't had any prompts for any additional updates required since upgrading to 14.04 and haven't done any manual updates or modifications to the system myself. Everything is still pretty much stock.

I suppose my next question is: is there a safe way to upgrade my kernel version to the current 14.04 without having to do something like a reinstall?

---

### Post by SeijiSensei on 2014-04-19
Run "sudo apt-get update; sudo apt-get upgrade" from a command prompt.  Do you see any items that are "held back?"  If so, run "sudo apt-get dist-upgrade" and those will be installed as well.

---

### Post by Gnawnsense on 2014-04-19
> **SeijiSensei said:**
> Run "sudo apt-get update; sudo apt-get upgrade" from a command prompt.  Do you see any items that are "held back?"  If so, run "sudo apt-get dist-upgrade" and those will be installed as well.

Hi,

Thanks for the response.

Doesn't look like update/upgrade think there is anything to update. This is what I got:

```
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by Gnawnsense on 2014-04-20
At this point, I think just upgrading my kernel is probably necessary. Still unsure to why the kernel didn't follow along when I did the 14.04 update, though.

And shouldn't Software Updater be catching the downgraded kernel at this point and be prompting an update?

---

### Post by Gnawnsense on 2014-04-20
Just upgraded my kernel manually and it seems to be working OK, regardless of a few errors I seen during the installation process.

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install linux-generic[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]

[/FONT][/COLOR]The above seemed to take care of the kernel version:

```
uname -r
3.13.0-24-generic
```

---

