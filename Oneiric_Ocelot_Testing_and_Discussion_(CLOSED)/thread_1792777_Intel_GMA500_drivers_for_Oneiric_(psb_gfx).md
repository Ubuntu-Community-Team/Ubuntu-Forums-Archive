---
title: "Intel GMA500 drivers for Oneiric (psb_gfx)"
date: 2011-06-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lucazade on 2011-06-28
New release, new work to make this graphic chipset working!
There are some good and bad news...

The new 'psb_gfx' driver is included by default in kernel 3.0.x, shipped by default in OO, unfortunately the version included is outdated and doesn't work properly (white screen of death!).

So I've update the DKMS package taking the sources of the drivers from staging kernel tree and uploaded in a PPA.
KMS is working good so the resolution is auto-detected, 2D is enough fast enough for the netbook.

To make it working there are some steps to do, at least at the moment.
A bug reported should be opened and maybe some talk to kernel and X devs could help to fix it permanently for OO release.



To make the livecd startup we have to unload a couple of drivers adding some parameters to kernel, otherwise it ends up in a white screen.

add 'poulsbo.dummy=1 psb_gfx.dummy=1' to kernel params at grub time (hit F6 when livecd starts)
this way the 2 kernel modules are not loaded, because of wrong options enabled, and livecd could use vesa as X driver.

once installed, reboot with fake kernel params and add ppa:
```
sudo add-apt-repository ppa:gma500/psb-gfx
sudo apt-get update
sudo apt-get install psb-dkms

```

necessary workarounds:
```
echo 'blacklist poulsbo' | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo mv /etc/init/plymouth.conf /etc/init/plymouth.conf.disable
sudo sed -i 's/vt.handoff=7//g' /etc/grub.d/10_linux
sudo update-grub
```

fix for backlight hotkeys on acer751h (please report for other netbooks):
```

echo 'blacklist acer_wmi' | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo sed -i 's/GRUB_CMDLINE_LINUX=""/GRUB_CMDLINE_LINUX="acpi_backlight=vendor"/g' /etc/default/grub
sudo update-grub

```

reboot again and it should work.

---

Notes: netbook can suspend but doesn't resume, nice!

---

### Post by jbernardo on 2011-06-28
Hey Luca!
Nice to see you're keeping the flame for our neglected GMA500!
The psb_gfx driver is 2D only in the foreseeable future, right? So no vaapi, no opengl, nothing like that is in the horizon?

---

### Post by lucazade on 2011-06-28
> **jbernardo said:**
> Hey Luca!
Nice to see you're keeping the flame for our neglected GMA500!
The psb_gfx driver is 2D only in the foreseeable future, right? So no vaapi, no opengl, nothing like that is in the horizon?

Hey José!
Difficult to see vaapi and opengl coming, even if the other project driven by oss foundation aim to implement these and had already reverse eng them. Maybe with a join venture of efforts, who knows!
Also the user space X driver exa or uxa is still missing but fbdev seems enough atm.

---

### Post by fjgaude on 2011-06-28
This is important news for me and my Dell 10n netbook! Keep it coming and thanks to all who do the work.

---

### Post by tista on 2011-06-28
Hi guys. ;)

OK... I would keep my eyes open for this thread!
and a couple of patchworks we've done must be ported to upstream ubuntu kernel, right?

cheers.

---

### Post by lucazade on 2011-06-28
> **tista said:**
> Hi guys. ;)

OK... I would keep my eyes open for this thread!
and a couple of patchworks we've done must be ported to upstream ubuntu kernel, right?

cheers.

Hi Tista!

Yep, some patchwork is missing at the moment, you're right.
Screen dithering and acpi register for sure, should be added as patches to package and hopefully also upstream.

---

### Post by tista on 2011-07-01
Hi Luca.

I've seen the issues in psb-dkms 0.2.26 on Natty:
[http://ubuntuforums.org/showpost.php?p=10993178&postcount=4274]("http://ubuntuforums.org/showpost.php?p=10993178&postcount=4274")

is that really? :(
and I won't recommend that "everything given in errors must be commented out"... in this case, that functions would be very important. so the current 0.2.26 has what the differences are from my bzr branch? any new stuff had been employed? 

if you had, let me know the sources of 0.2.26!! :)
I would help you guys to track this issue down...

Ciao.

---

### Post by lucazade on 2011-07-01
> **tista said:**
> Hi Luca.

I've seen the issues in psb-dkms 0.2.26 on Natty:
[http://ubuntuforums.org/showpost.php?p=10993178&postcount=4274]("http://ubuntuforums.org/showpost.php?p=10993178&postcount=4274")

is that really? :(
and I won't recommend that "everything given in errors must be commented out"... in this case, that functions would be very important. so the current 0.2.26 has what the differences are from my bzr branch? any new stuff had been employed? 

if you had, let me know the sources of 0.2.26!! :)
I would help you guys to track this issue down...

Ciao.

Ciao Tista

The sources of 0.2.27 come directly from Alan Cox tree, updated some days ago:
[http://git.kernel.org/?p=linux/kernel/git/alan/linux-3.0-mid-ref.git;a=tree;f=drivers/staging/gma500;h=011c08eaa49485fa60e7e567e0d0bb57602eec96;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/alan/linux-3.0-mid-ref.git;a=tree;f=drivers/staging/gma500;h=011c08eaa49485fa60e7e567e0d0bb57602eec96;hb=HEAD)

I haven't updated psb_gfx bzr branch on my launchpad yet but sources are anyway  available from the ppa itself:
[https://launchpad.net/~gma500/+archive/psb-gfx/+files/psb-dkms_0.2.27.tar.gz](https://launchpad.net/~gma500/+archive/psb-gfx/+files/psb-dkms_0.2.27.tar.gz)

This time I used only the original sources without employing stuff from your branch because I wanted to find why it was broken in OO. Now that it is working good (also plymouth, vt.handoff are ok now!) it is time to merge with dithering and acpi_register patches ( don't remember if there are other things).

What do you suggest?

edit... 0.2.26 was a copy of your branch and I never had that issue

---

### Post by tista on 2011-07-01
> **lucazade said:**
> Ciao Tista

The sources of 0.2.27 come directly from Alan Cox tree, updated some days ago:
[http://git.kernel.org/?p=linux/kernel/git/alan/linux-3.0-mid-ref.git;a=tree;f=drivers/staging/gma500;h=011c08eaa49485fa60e7e567e0d0bb57602eec96;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/alan/linux-3.0-mid-ref.git;a=tree;f=drivers/staging/gma500;h=011c08eaa49485fa60e7e567e0d0bb57602eec96;hb=HEAD)

I haven't updated psb_gfx bzr branch on my launchpad yet but sources are anyway  available from the ppa itself:
[https://launchpad.net/~gma500/+archive/psb-gfx/+files/psb-dkms_0.2.27.tar.gz](https://launchpad.net/~gma500/+archive/psb-gfx/+files/psb-dkms_0.2.27.tar.gz)

This time I used only the original sources without employing stuff from your branch because I wanted to find why it was broken in OO. Now that it is working good (also plymouth, vt.handoff are ok now!) it is time to merge with dithering and acpi_register patches ( don't remember if there are other things).

What do you suggest?

edit... 0.2.26 was a copy of your branch and I never had that issue

Ciao Luca. ;)

Grazie mille!!

OK.. I would sync the latest Alan's codes on my PPA!!
[https://launchpad.net/~tista/+archive/psb-gfx-daily]("https://launchpad.net/~tista/+archive/psb-gfx-daily")

just now I'm updating package to be improved my latest bzr branch (it would be the very similar to your 0.2.26). and then, I would give it a try to sync Alan's latest, you know?

Ciao! :)

---

### Post by lucazade on 2011-07-01
@Tista

Tried your new package with dithering enabled... woohoo!
Finally a good rendering, i'm still wondering why this is not enabled by default in alan's tree.
Anyway your package is for natty but I tried only in Oneiric, i'm going to copy the package in the official ppa just to make the original info in this thread still relevant.

thanks again for your special efforts :)

---

### Post by speculatrix on 2011-07-01
am looking forward to getting beyond maverick, I have held back due to power problems documented at Phoronix, and also until gma500 driver is solid, so thanks for the efforts. :popcorn:

---

### Post by fjgaude on 2011-07-01
> **lucazade said:**
> @Tista

Tried your new package with dithering enabled... woohoo!
Finally a good rendering, i'm still wondering why this is not enabled by default in alan's tree.
Anyway your package is for natty but I tried only in Oneiric, i'm going to copy the package in the official ppa just to make the original info in this thread still relevant.

thanks again for your special efforts :)

Will all this be reflected on this link:

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

I'm running 1366x768 with 10.04 and fbdev driver. I'm happy with it but would like to go with 11.04 or 11.10 when it's released.

Thank you, all of you, for supporting the little netbooks.

---

### Post by lucazade on 2011-07-01
> **fjgaude said:**
> Will all this be reflected on this link:

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

I'm running 1366x768 with 10.04 and fbdev driver. I'm happy with it but would like to go with 11.04 or 11.10 when it's released.

Thank you, all of you, for supporting the little netbooks.

Yep, it will be added soon.
Anyway this driver in natty required more steps to install, now it is really simple.. hope won't change before OO release.

---

### Post by mikewhatever on 2011-07-01
> **speculatrix said:**
> am looking forward to getting beyond maverick, I have held back due to power problems documented at Phoronix, and also until gma500 driver is solid, so thanks for the efforts. :popcorn:

A workaround for one of the power regressions has been published on Phoronix (pcie_aspm=force - my laptop wouldn't boot with it, you might have better luck), but if you wait for the host of gma500 drivers (or one of them) to become stable, chances are you will die of old age before that happens. :p

Both Maverick and Lucid work well with the psb driver, so, unless you have desire and knowledge to hack the new driver, I'd suggest using one of those.

PS: Hi everyone.O:)

---

### Post by tista on 2011-07-01
Hi guys.

I'm just now uploading dkms package for oneiric with same codes on natty. ;)

and the next would be embedded acpi_register coding onto psb_drv.c or somewhere...
so I also would do to contact linux-next team to manage our workarounds!! :)

then may I contact to ubuntu-kernel team, too? ;)
or hopefully linux-next team especially Alan, right?

ciao.

---

### Post by lucazade on 2011-07-01
> **tista said:**
> Hi guys.

I'm just now uploading dkms package for oneiric with same codes on natty. ;)

and the next would be embedded acpi_register coding onto psb_drv.c or somewhere...
so I also would do to contact linux-next team to manage our workarounds!! :)

then may I contact to ubuntu-kernel team, too? ;)
or hopefully linux-next team especially Alan, right?

ciao.

simply great :)
I agree to contact linux-next team and to propose your patches, it would be nice addition.

We should also contact the Ubuntu-kernel team asking them to update psb_gfx driver shipped with stock kernel and to not include the 'poulsbo' backlight kernel module, that creates only problems and never worked properly (your acpi_register is better).

Then if we really want to be goodfellas we have to investigate why netbook won't resume from suspend.
All this stuff will make OO a good experience for gma500 guys.

Ciao!!

---

### Post by fjgaude on 2011-07-01
> Then if we really want to be goodfellas we have to investigate why netbook won't resume from suspend.
All this stuff will make OO a good experience for gma500 guys.

Hey, you guys are already declared 'good guys'. <smile>

---

### Post by tista on 2011-07-01
Hi all. ;)

Just now I've updated psb-dkms as the version 0.2.34~bzr~rev59~oneiric1!!
[https://launchpad.net/~tista/+archive/psb-gfx-daily]("https://launchpad.net/~tista/+archive/psb-gfx-daily")

[summary]
* Fixed to revive acpi_register as external option for its module. see details in the output of modinfo...

[usage]
* If set 1 like "psb_gfx.acpi_register=1" in grub, psb_gfx could run to be forced acpi_video_register ON. so you could see the backlight controller in /sys/class/backliht/...
* If set nothing, psb_gfx would run without any own backlight controller. it sometimes would help the machine like SONY VAIO, and some more... that means these machines had some stock platform module in kernel.

[other notes]
* this feature should be depended on the option "acpi_backlight" on grub. yep. that's the combinations with them. still I couldn't track the all PC down, so you might give some "trial and error" for it.

Best Regards.

P.S:
the next is umm... would be suspend/resume?
yeah but this wall might be too hard to break through... ;)

---

### Post by NormanFLinux on 2011-07-02
Mandriva based distros have supported GMA 500 out of the box for awhile now. With Ubuntu, it takes some confuguring to get GMA 500 drivers installed and working.

---

### Post by lucazade on 2011-07-02
@Tista 
A big thanks for your work :)
Going to try acpi_register in OO and report back results... for resume/suspend it is a big issue because when it doesn't resume (always) I've to remove the battery because the power led is always blinking.

@NormanFLinux
Beside a huge work from a Mandriva user to port Psb driver to Xorg 1.7, so some year ago, all the other distro during these years have used the drivers cooked for Ubuntu and adapted to other distro.

---

### Post by fjgaude on 2011-07-02
Suspend/resume is a big issue with netbooks and the like. I will have to stick with either 10.10 or 10.04 LTS if 11.04 or 11.10 don't do it reliably.

Thanks Luca and Tista for getting us this far with GMA500.

---

### Post by lucazade on 2011-07-02
> **fjgaude said:**
> Suspend/resume is a big issue with netbooks and the like. I will have to stick with either 10.10 or 10.04 LTS if 11.04 or 11.10 don't do it reliably.

Thanks Luca and Testa for getting us this far with GMA500.

oh yes.. really annoying and difficult to debug.

maybe this project for oneiric will help:
[https://launchpad.net/ubuntu/+spec/hwe-o-improved-s3-s4-debug](https://launchpad.net/ubuntu/+spec/hwe-o-improved-s3-s4-debug)

---

### Post by fjgaude on 2011-07-02
> **lucazade said:**
> oh yes.. really annoying and difficult to debug.

maybe this project for oneiric will help:
[https://launchpad.net/ubuntu/+spec/hwe-o-improved-s3-s4-debug](https://launchpad.net/ubuntu/+spec/hwe-o-improved-s3-s4-debug)

I subscribed the the link. Thanks for the info.

---

### Post by tista on 2011-07-02
Hi Luca. ;)

today I'm tracking resume issues down...
yeah my friends had accepted for my remote access via ssh, and then I'm draining log from his machine! :)

...OMG...

psb_gfx might give us the kernel bug.  lol

here is the description of kernel log...
```
PM: Finishing wakeup.
 ------------[ cut here ]------------
kernel BUG at /var/lib/dkms/psb/0.2.34~bzr~rev59~oneiric1/build/psb_intel_lvds.c:151!
invalid opcode: 0000 [#1] SMP
last sysfs file: /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0/uevent
~~~
EIP: 0060:[<f80f4ce3>] EFLAGS: 00210246 CPU: 1
EIP is at psb_intel_lvds_set_brightness+0x143/0x150 [psb_gfx]
Process Xorg (pid: 653, ti=f35ec000 task=f35e0ca0 task.ti=f35ec000)
Stack:
~~~
EIP: [<f80f4ce3>] psb_intel_lvds_set_brightness+0x143/0x150 [psb_gfx] SS:ESP 0068:f35edd5c
```

so I'm going to fix the sources!! :)

Ciao.

---

### Post by lucazade on 2011-07-03
Hey!
Nice find, hope you can find the culprit ;)

tried acpi_register yesterday but didn't work, dunno, today I'll try again and 
check what's broken.
/sys/class/backlight seems the same of natty.

See you

---

### Post by lucazade on 2011-07-03
oh.. found why brightness hotkeys were not working :)

I've to use as kernel params for my acer751/gma500
"acpi_backlight=vendor psb_gfx.acpi_register=1"

and i've also to blacklist these kernel modules in /etc/modprobe.d/blacklist.conf
blacklist poulsbo
blacklist acer_wmi

---

### Post by tista on 2011-07-03
> **lucazade said:**
> oh.. found why brightness hotkeys were not working :)

I've to use as kernel params for my acer751/gma500
"acpi_backlight=vendor psb_gfx.acpi_register=1"

and i've also to blacklist these kernel modules in /etc/modprobe.d/blacklist.conf
blacklist poulsbo
blacklist acer_wmi

OK... so finally it works well?

then me?
no... it didn't fix yet. :(
because some gma_backlight* functions didn't work properly on dev_priv... damned.
and this rev has already pm_runtime on kernel directly, so the codes of power-management, yeah power.c is now quite small and tiny, as far as I know whether it works well on the RAM register to be saved pm configurations... in fact, it seems to fail resuming on VT, too. yeah that's purely kernel problems especially on psb_gfx. 
well umm... I might have to salvage some stuff from deadly old-psb or Intel drivers.

anyway, I hope Linux-MID team could solve this first.

ciao.

---

### Post by lucazade on 2011-07-03
> **tista said:**
> OK... so finally it works well?

then me?
no... it didn't fix yet. :(
because some gma_backlight* functions didn't work properly on dev_priv... damned.
and this rev has already pm_runtime on kernel directly, so the codes of power-management, yeah power.c is now quite small and tiny, as far as I know whether it works well on the RAM register to be saved pm configurations... in fact, it seems to fail resuming on VT, too. yeah that's purely kernel problems especially on psb_gfx. 
well umm... I might have to salvage some stuff from deadly old-psb or Intel drivers.

anyway, I hope Linux-MID team could solve this first.

ciao.

ah, what a pity..
yes, here is working well backlight.
(i've only psb-bl interface in /sys/class/backlight)

about resuming i dunno if is related to vt wakeup because, at least here, it does nothing when i press the power button to resume from suspend, so it seems a step before.
the power amber led is still blinking and doesn't seem to like the power button to resume at all. (sorry, don't know how to say this better in english!)

EDIT: another annoying thing is the mouse pointer that often disappear.

---

### Post by tista on 2011-07-04
> **lucazade said:**
> 
EDIT: another annoying thing is the mouse pointer that often disappear.

OMG.... that issues had still been remained?! :sad:
I'm afraid that it might be caused wrong vsync or something like that on psb_gfx's auto configurations for LVDS... so could you try any external LCD via VGA? and also try to compare the Xorg.0.log between psb_gfx and emgd. I wanna know where the differences appeared in modelines auto-generated. because some type of machine, like VAIO P, it already seems to be fixed naturally...:P yep that would be hardware-dependencies.

even if we couldn't notice any hints, I have some ideas. yeah I might force pointer to render like HWcursor by patching to psb_gem.c and/or psb_gtt.c... I suppose 2D accel is the key!

ciao.

---

### Post by lucazade on 2011-07-04
> **tista said:**
> OMG.... that issues had still been remained?! :sad:
I'm afraid that it might be caused wrong vsync or something like that on psb_gfx's auto configurations for LVDS... so could you try any external LCD via VGA? and also try to compare the Xorg.0.log between psb_gfx and emgd. I wanna know where the differences appeared in modelines auto-generated. because some type of machine, like VAIO P, it already seems to be fixed naturally...:P yep that would be hardware-dependencies.

even if we couldn't notice any hints, I have some ideas. yeah I might force pointer to render like HWcursor by patching to psb_gem.c and/or psb_gtt.c... I suppose 2D accel is the key!

ciao.

Tista this issue is present also using vesa and fbdev (without psb_gfx) and I have tried Hwcursor as xorg option but without luck.
I'll try to use an external display to see if it helps and report to you.


I was trying to figure out what's broken in suspend and why it doesn't wakeup from suspend. Tried all pm-suspend quirks and uswsusp but no luck.

right now i've found this:
```
Jul  3 10:14:21 one kernel: [    0.958057] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Jul  3 10:14:21 one kernel: [    0.958077] ACPI: Power Button [PWRB]
Jul  3 10:14:21 one kernel: [    0.958259] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
Jul  3 10:14:21 one kernel: [    0.958276] ACPI: Sleep Button [SLPB]
Jul  3 10:14:21 one kernel: [    0.958507] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Jul  3 10:14:21 one kernel: [    0.958525] ACPI: Power Button [PWRF]
Jul  3 10:14:21 one kernel: [    0.958542] ACPI Error: Could not enable PowerButton event (20110413/evxfevnt-198)
Jul  3 10:14:21 one kernel: [    0.958560] ACPI Warning: Could not enable fixed event 0x2 (20110413/evxface-197)
Jul  3 10:14:21 one kernel: [    0.976262] button: probe of LNXPWRBN:00 failed with error -22
```

When I press the power button the netbook doesn't resume, maybe it is related to this.

---

### Post by tista on 2011-07-04
> **lucazade said:**
> Tista this issue is present also using vesa and fbdev (without psb_gfx) and I have tried Hwcursor as xorg option but without luck.
I'll try to use an external display to see if it helps and report to you.

alright.
so I gotta do checking whether fbdev Xorg driver still had such options... ;)

> I was trying to figure out what's broken in suspend and why it doesn't wakeup from suspend. Tried all pm-suspend quirks and uswsusp but no luck.

right now i've found this:
```
Jul  3 10:14:21 one kernel: [    0.958057] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Jul  3 10:14:21 one kernel: [    0.958077] ACPI: Power Button [PWRB]
Jul  3 10:14:21 one kernel: [    0.958259] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
Jul  3 10:14:21 one kernel: [    0.958276] ACPI: Sleep Button [SLPB]
Jul  3 10:14:21 one kernel: [    0.958507] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Jul  3 10:14:21 one kernel: [    0.958525] ACPI: Power Button [PWRF]
Jul  3 10:14:21 one kernel: [    0.958542] ACPI Error: Could not enable PowerButton event (20110413/evxfevnt-198)
Jul  3 10:14:21 one kernel: [    0.958560] ACPI Warning: Could not enable fixed event 0x2 (20110413/evxface-197)
Jul  3 10:14:21 one kernel: [    0.976262] button: probe of LNXPWRBN:00 failed with error -22
```

When I press the power button the netbook doesn't resume, maybe it is related to this.

OK... yeah evil inside! XD
I also do googling how the fact that the other  intel driver did.

cheers. ;)

**P.S:**
I've created patched fbdev driver here:
[http://www.2shared.com/file/Bh6K2tv9/fbdev_HW_Cursor_patchedtar.html]("http://www.2shared.com/file/Bh6K2tv9/fbdev_HW_Cursor_patchedtar.html")
yeah HWcorsor option would be enabled by default and SWcursor were killed.
if you could, give it a try... ;) you know I didn't know whether it works or not, so you should be ready for rollback!! :)
yep you might have better to download original package from main repos manually to prepare for rollback...

ciao.

**P.S #2:**
Also uploaded to PPA for use of experimental trials...

---

### Post by lucazade on 2011-07-04
> **tista said:**
> alright.
so I gotta do checking whether fbdev Xorg driver still had such options... ;)



OK... yeah evil inside! XD
I also do googling how the fact that the other  intel driver did.

cheers. ;)

**P.S:**
I've created patched fbdev driver here:
[http://www.2shared.com/file/Bh6K2tv9/fbdev_HW_Cursor_patchedtar.html]("http://www.2shared.com/file/Bh6K2tv9/fbdev_HW_Cursor_patchedtar.html")
yeah HWcorsor option would be enabled by default and SWcursor were killed.
if you could, give it a try... ;) you know I didn't know whether it works or not, so you should be ready for rollback!! :)
yep you might have better to download original package from main repos manually to prepare for rollback...

ciao.

**P.S #2:**
Also uploaded to PPA for use of experimental trials...

Hi Tista

tried your patched fbdev, unfortunately it doesn't solve the issue.
pointer still disappear when left clicking.

anyway your patch seems to be implemented correctly:
(**) FBDEV(0): Option "HW Cursor" "true"

thanks anyway for your trial :D

side note: some new code is going to land in psb_gfx tree:
Cedar Trail Coming Soon To Open GMA500 Driver
[http://www.phoronix.com/scan.php?page=news_item&px=OTYyNw](http://www.phoronix.com/scan.php?page=news_item&px=OTYyNw)

---

### Post by tista on 2011-07-04
> **lucazade said:**
> Hi Tista

tried your patched fbdev, unfortunately it doesn't solve the issue.
pointer still disappear when left clicking.

anyway your patch seems to be implemented correctly:
(**) FBDEV(0): Option "HW Cursor" "true"

thanks anyway for your trial :D

side note: some new code is going to land in psb_gfx tree:
Cedar Trail Coming Soon To Open GMA500 Driver
[http://www.phoronix.com/scan.php?page=news_item&px=OTYyNw](http://www.phoronix.com/scan.php?page=news_item&px=OTYyNw)

Ciao Luca.

yeah it didn't make any success... even on my X120e.
Intel driver had some more codes to improve HW cursor like agp/dri/gtt and more.
I suppose it might be caused DRI2 implementations or something like that...

in case, on X120e had been forced to boot with fbdev, DRI/DRI2 were avoided, then pointer had been flickered whenever tooltip showed, left-click, and more cases..
If remembered well, I had created some libdrm for gfx, you remember that?
if could, give it a try... yeah userspace handler would be needed. I might install it in past... but today some headers had been updated, so I might have to update to sync it...

cheers. ;)

---

### Post by lucazade on 2011-07-10
@ Tista

Updated psb_gfx driver to latest staging snapshot (ppa:lucazade/testing)
Now backlight patch is no more needed, i think acpi_register has been added directly to source (only acpi_backlight=vendor is needed for acer).

Updated package lacks anyway dithering patch (i've seen your patch also for 60hz, what is it about?), so needs to be updated again.

Testing now on natty and seems to work well.

---

### Post by lucazade on 2011-07-10
i've reported present issues and tista's patches upstream.
hope to see these bugs ironed out or at least understand if are well-known issues.

---

### Post by tista on 2011-07-10
> **lucazade said:**
> @ Tista

Updated psb_gfx driver to latest staging snapshot (ppa:lucazade/testing)
Now backlight patch is no more needed, i think acpi_register has been added directly to source (only acpi_backlight=vendor is needed for acer).

Updated package lacks anyway dithering patch (i've seen your patch also for 60hz, what is it about?), so needs to be updated again.

Testing now on natty and seems to work well.

@Luca

OK. let's explain.
the default psb_gfx was fitted to 50Hz LVDS vblank. but almost panel must have nearly 60Hz, so I've decreased values of "mdelay". but its function might be better to use "msleep" to wait for the cycle of vblank. ;)

anyway, I'm searching for the solutions to fix mouse pointer flickering.

ciao.

---

### Post by lucazade on 2011-07-10
> **tista said:**
> @Luca

OK. let's explain.
the default psb_gfx was fitted to 50Hz LVDS vblank. but almost panel must have nearly 60Hz, so I've decreased values of "mdelay". but its function might be better to use "msleep" to wait for the cycle of vblank. ;)

anyway, I'm searching for the solutions to fix mouse pointer flickering.

ciao.

@all

yep, 60hz seems a saner refresh for a lcd panel :)
and i believe mouse pointer issue is due to fbdev because kernel module has mouse support but no X support for it.

Got in touch with AlanCox (intel dev for psb_gfx) today and the issues i told him are now investigated.


I'd be nice to provide some good feedback to devs if testing this new driver.
so what devices people are using and whether the internal/external
video on them works and if there are any problems eg the
suspend/resume, dither, vt.handoff blank screen, plymouth cut/half screen (probably libdrm related), backlight hotkeys support.

Ciaooo!

---

### Post by fjgaude on 2011-07-10
> **lucazade said:**
> @all

yep, 60hz seems a saner refresh for a lcd panel :)
and i believe mouse pointer issue is due to fbdev because kernel module has mouse support but no X support for it.

Got in touch with AlanCox (intel dev for psb_gfx) today and the issues i told him are now investigated.


I'd be nice to provide some good feedback to devs if testing this new driver.
so what devices people are using and whether the internal/external
video on them works and if there are any problems eg the
suspend/resume, dither, vt.handoff blank screen, plymouth cut/half screen (probably libdrm related), backlight hotkeys support.

Ciaooo!

I have a Dell 10n with 1366 x 768 screen... I will consider installing the new driver, psb-gfx, presently have fbdev with all the workarounds, which work perfectly, suspend, etc., if you tell me how to do it. <smile>

Thanks for all your work, you and Tista.

---

### Post by lucazade on 2011-07-11
> **fjgaude said:**
> I have a Dell 10n with 1366 x 768 screen... I will consider installing the new driver, psb-gfx, presently have fbdev with all the workarounds, which work perfectly, suspend, etc., if you tell me how to do it. <smile>

Thanks for all your work, you and Tista.

You're welcome!

If you want to try in psb_gfx in Oneiric you can follow instructions on my first post.
Psb_gfx uses fbdev as well but it add also nice features like KMS to detect resolution automatically at boot stage (without using grub hack or xorg.conf), a proper memory management, a brightness support out-of-the-box and other nice thing.
Try it on a spare partition if you don't want to mess with your installation.

I had issue with suspending also with fbdev, which workaournd are you using?
I believe I've tried every possible combination :)

---

### Post by fjgaude on 2011-07-11
I did what was suggested on your link:

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsboAlternatives](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsboAlternatives)

and added this:

Suspend by using uswsusp (alternative)

sudo apt-get purge vbetool && sudo apt-get install uswsusp
and suspend using:

sudo s2ram --force
to make this permanent, run:

sudo gedit /etc/pm/config.d/00sleep_module

and set in the file:

SLEEP_MODULE="uswsusp"
and run:

sudo gedit /etc/pm/config/defaults
and add in the file:

S2RAM_OPTS="--force"
QUIRK_NONE="true"
---

Never had an issue with brightness or any thing else.

Will see if I understand your first post, then think about what to do to keep my present install.

Thanks once again.

---

### Post by lucazade on 2011-07-11
"Medfield PVR driver

Import of known good and working tree for the **2D/3D** non free driver

NOT FOR UPSTREAM [requires non-free userspace]"

[http://git.kernel.org/?p=linux/kernel/git/alan/linux-3.0-mid-ref.git;a=commit;h=a84320e73d98f3acff2e84fd718069249c4fc9d6](http://git.kernel.org/?p=linux/kernel/git/alan/linux-3.0-mid-ref.git;a=commit;h=a84320e73d98f3acff2e84fd718069249c4fc9d6)

:guitar:

---

### Post by lucazade on 2011-07-11
From readme:
```
SOURCE

This driver is a forward port of the Poulsbo/Langwell/Penwell SGX graphics and
display controller drivers from 2.6.37 to 3.0-rc-something.

The starting point was the meego-kernel-branch-mrst-k37 branch on [1]. The
commits touching drivers/staging/mrst directory were exported to patches using:

$ git format-patch -1000 meego-kernel-branch-mrst-k37 -- drivers/staging/mrst

Note that the above filters out the changes outside drivers/staging/mrst.

The patches were then applied on top of the MID repository [2]. Possibly due to
rebases in the original tree [1] there were some conflicts that were
resolved. In the end, this did not report any diff:

$ git diff meego-kernel-branch-mrst-k37 -- drivers/staging/mrst

After this, the build problems were fixed one by one.


TODO

* Make it work.

* Continuous: Merge [2] (and thus Linus' tree) here as it is updated.

* Review the hacked up quick fixes to build problems.

* Possibly update the DDK version.

[B]* Merge the diverged and polished drivers/staging/gma500 back with this driver.
[/B]
* Finally: Backport the combined drivers and hardware adaptation to desired
  kernel version.


NOTES

There is arch/x86/configs/medfield_pvr_defconfig known to work. It excludes the
drivers/staging/gma500 driver as long as the drivers have not been merged.


REFERENCES

[1] git://gfx-build.fm.intel.com/kernel.git
[2] git://git.kernel.org/pub/scm/linux/kernel/git/alan/linux-3.0-mid-ref.git
```


A list of devices with SGX535/540 on board (known as intel gma500), I didn't know was so long!
```

Series5 (SGX)

PowerVR SGX (pixel, vertex, and geometry shader hardware)
next generation fully programmable universal scalable shader architecture
exceeding requirements of OpenGL 2.0 and up to DirectX 10.1 Shader Model 4.1
licensed to Apple Inc, Sony, Intel, Nokia, Renesas, NEC, TI, MediaTek, NXP Semiconductors, Realtek, Samsung, Sigma Designs, SigmaTel, SiRF, SiS and others
size from 2.6 mm² to 12.5 mm² (@65 nm)
6 variants announced (realistic, sustainable, less than 50% shader load, real-world performance listed at 200 MHz; peak performance significantly higher dependent on content and operating conditions) —
SGX520 (7 mil Triangles/sec, 250Mpx/s@200 MHz) for the handheld mobile market[1]
SGX530 (14 mil Triangles/sec, 500Mpx/s@200 MHz)for the handheld mobile market
SGX535 (14 M Triangles/s, 1Gpx/s@200 MHz, Max Memory Band 4.2GB/s), For handheld high-end mobile, portable, MID, UMPC, consumer, and automotive devices.licensed by NEC.[2][3] Intel calls it the GMA 500.
SGX540 (20M Triangles/s(Built-in Samsung S5PC110-111) 1Gpx/s@200 MHz,Built-in SOC.[4]
SGX545 (40 M Triangles/s, 1Gpx/s@200 MHz)[5]
Products that include the SGX:
Ambarella iOne SoC-SGX540 + Cortex-A9 Dual
Apple A4—SGX535 + VXD375 + Cortex-A8
Apple iPad
Apple iPhone 4
Apple iPod Touch 4th gen
Apple TV (2010)
Samsung—SGX540(S5PC110-111) + Cortex-A8
Samsung Galaxy S
Samsung Samsung Galaxy Tab
Samsung Vibrant, i997 Infuse 4G, Galaxy S 4G, Samsung Google Nexus S, i897 Captivate, S8530 Wave II
Intel CE 3100 (Canmore)—SGX535 (Intel GMA500) + Pentium M
Conceptronic YUIXX
Gigabyte GN-MD300-RH
Metrological's Mediaconnect TV
Routon H3
Samsung STB-HDDVR
Toshiba Connected TVs
Toshiba Network Player
TCL IPTV
Fujitsu
Intel CE4100 (Sodaville) family—SGX535 + Atom-based CPU
Orange Orange Box
Sony Bravia Internet TV
Intel CE4110 (Sodaville)—SGX535 at 200MHz + Atom-based CPU at 1.2GHz[6]
D-Link Boxee Box
Intel CE4130 (Sodaville)—SGX535 at 200MHz + Atom-based CPU at 1.2GHz
Intel CE4150 (Sodaville)—SGX535 at 400MHz + Atom-based CPU at 1.2GHz
Logitech Revue (970-000001)
Iliad Freebox Revolution
Intel CE4170 (Sodaville)—SGX535 at 400MHz + Atom-based CPU at 1.6GHz
Intel CE4200 (Groveland) family—SGX535 + [[Intel Atom|
Bouygues Telecom BBox
Intel SCH US15/W/L (Poulsbo)—SGX535 (Intel GMA500) + VXD370
Abit (USI) MID-100
Abit (USI) MID-150, MID-200
Acer Aspire One AO751h
Advantech MICA-101
Aigo MID P8860, P8880, P8888
Arbor Gladius G0710
Archos 9
ASUS EeePC T91
ASUS EeePC S121, EeePC 1101HGO/HA/HAB
ASUS R50A, R70A
Averatec (TriGem) MID
BenQ Aries2
Bandai Namco Rilakkuma
BenQ S6
Clarion MiND
CLEVO TN70M, TN71M, T89xM
Colmek Stinger
Compal jAX10
CompuLab Fit-PC2
Cowon W2
Dell Inspiron Mini 12, Inspiron Mini 10, Inspiron Mini 1010 Tiger
Digifriends WiMAX MID
DT Research DT312
DUX HFBX-3800
EB mobile internet device
FMV-BIBLO LOOX U/C40, LOOX U/C30
Fujitsu UMPC U2010
Fujitsu LifeBook U2020
Fujitsu LifeBook U820, UH900
Fujitsu FMV-BIBLO LOOX U
Gigabyte M528
Hanbit Pepper Pad 3
HP Slate
Kohjinsha/Inventec S32, SC3
Kohjinsha W130, SX3KP06MS, SC3KX06A
Kohjinsha/Inventec X5
Kohjinsha PM series
Lenovo IdeaPad U8
LG XNote B831, LGX30
MaxID BHC-100, iDLMax
mis MP084T-001G
MSI Wind U115, U110
MSI X-Slim 320
NEC VersaPro UltraLite type VS
NEXCOM MRC 2100, MTC 2100, MTC 2100-MD
Nokia Booklet 3G
NOVA SideArm2 SA2I
OMRON Panel PC
Onkyo NX707
OQO Model 2+
Panasonic Toughbook CF-U1
Panasonic CF-H1 Mobile Clinical Assistant
Portwell Japan UMPC-2711
Quanta mobile internet device
Sony Vaio P series, Vaio X series
TCS-003-01595 — Intel Atom Rugged Tablet PC 8.4"
Terralogic Toughnote DB06-I Intel Atom Industrial Grade Rugged UMPC
Terralogic Toughnote DB06-M Intel Atom Military Grade Rugged UMPC
Toshiba mobile internet device
Trigem LLUON Mobbit PS400
UMID Clamshell
Viliv (YuKyung) S5, S7, X70
WiBrain i1, M1
WILLCOM D4 (Sharp WS016SH)
Intel Z6xx (Lincroft)—SGX535+VXD+VXE (Intel GMA600) + Atom-based CPU
LG GW990 (Concept device)
OpenPeak OpenTablet 7
Aava Mobile (Concept device)
Wistron W1
Quanta Redvale
CZC P10T
NEC EMMA Mobile/EV2—SGX530 + Cortex-A9 MPCore (Dual)
NEC NaviEngine EC-4270, EC-4260—SGX535 + ARM11 MPCore (Quad)
Alpine Car Information Systems (Spring 2010)
NEC Unidentified —SGX + PowerVR video & display
NEC Medity M2 —SGX + PowerVR video & display
NEC N-01A, N-02A, N-03A, N-04A, N-05A, N-06A, NEC N-07A, NEC N-08A, N-09A
Renesas SH-Mobile G3—SGX530 + SH-4
Fujitsu F-01A , F-02A, F-03A, F-04A, F-08A, F-09A
Sharp SH-01A, SH-02A, SH-03A, SH-05A, SH-06A, SH-07A, SH-06A NERV
Renesas SH-Mobile G4(in development)—SGX540 + SH-4
Fujitsu (in development)
Sharp (in development)
Renesas SH-Mobile APE4 (R8A73720)—SGX540 + Cortex-A8
Renesas SH-Navi3 (SH7776)—SGX530 + SH-X3(SH-4A (Dual)) Samsung APL0298C05—SGX535 + VXD370 + Cortex-A8
Apple iPod Touch 3rd Gen (32GB/64GB)
Apple iPhone 3GS
Samsung S5PC110—SGX540 + Cortex-A8
Meizu M9
Samsung S5PC111 (Hummingbird)—SGX540 + Cortex-A8
Samsung Vibrant
Samsung Epic 4G
Samsung Fascinate
Samsung Captivate
Samsung Galaxy S
Samsung P1000/P1000T Galaxy Tab
Samsung Yepp PMP
Google Nexus S
Samsung S5PV210—SGX540 + Cortex-A8
Sigma Designs SMP8656—SGX530 + MIPS
Sigma Designs SMP8910-SGX530 + MIPS
Texas Instruments OMAP3420—SGX530 + Cortex-A8
Texas Instruments OMAP3430—SGX530 + Cortex-A8
Nokia N900
Emblaze ELSE
Palm Pre
Palm Pre Plus
Samsung i8910, i8320
Samsung (Vodafone) 360 H1, 360 M1
Sony Ericsson Satio
Motorola Droid / Milestone
Motorola MOTOROI
Motorola XT800
HTC Qilin/Dopod T8388
Texas Instruments OMAP3440—SGX530 + Cortex-A8
ARCHOS Android IMT
ECS T800 800MHz
Motorola Milestone XT720
Texas Instruments OMAP3450—SGX530 + Cortex-A8
ECS T800 1GHz
Texas Instruments OMAP3515—SGX530 + Cortex-A8
Texas Instruments AM3517—SGX530 + Cortex-A8
Embest SOC8200
DAVE Embedded Systems Lizard (SOM)
Texas Instruments OMAP3530—SGX530 + Cortex-A8
Embest DevKit8000
OpenSourceMID.org K7 MID
Always Innovating Touch Book
Beagle Board
Beagle MID
Gumstix Overo — Water, Fire
ICETEK-OMAP3530-MINI
Pandora (console)
OMAP35x EVM Mistral Solutions
ISB Corp. Android STB
Kopin Golden-i
GDA Technologies' OMAP3530-based PMP
Texas Instruments OMAP3620—SGX530 + Cortex-A8
Motorola Droid 2
Texas Instruments OMAP3621—SGX530 + Cortex-A8
Barnes & Noble Nook Color
Texas Instruments OMAP3630—SGX530 + Cortex-A8
Archos 28, Archos 32, Archos 43, Archos 70, Archos 101
Synaptics Fuse
Sony Ericsson U5i "Vivaz" , Sony Ericsson U8i "Vivaz pro"
Motorola Droid X (Shadow)
Motorola Milestone 2
Palm Pre2
LG Optimus Black
Samsung Galaxy SL
Samsung P1010 Galaxy Tab Wi-Fi
Texas Instruments OMAP3640—SGX530 + Cortex-A8
Motorola Droid 2 R2D2 special edition
Motorola Droid 2 Global
Texas Instruments Sitara AM3715—SGX530 + Cortex-A8
Psion Omnii EP10
Texas Instruments DaVinci DM3730—SGX530 + Cortex-A8
InHand Fury
Beagleboard-xM
Texas Instruments Sitara AM3891—SGX530 + Cortex-A8
Texas Instruments Integra C6A8168—SGX530 + Cortex-A8
Texas Instruments OMAP4430—SGX540 + Cortex-A9 MPCore (dual)
Pandaboard
RIM Playbook
Texas Instruments OMAP4440—SGX540 + Cortex-A9 MPCore (dual)
Trident PNX8481—SGX531
Trident PNX8491—SGX531
Trident HiDTV PRO-SX5_SGX531
```

---

### Post by fjgaude on 2011-07-11
Thanks, Luca, for all the info. Considering the state of OO I think I'll wait for its release before I spend time with my netbook, upgrading it with psb-gfx driver. Simply don't have the time to work out the bugs. But will continue to watch what you guys are doing for GMA500 boxes.

Okay, maybe I'll install 11.04 on a separate partition, and then psb-gfx. Would that work, Luca?

---

### Post by lucazade on 2011-07-11
> **fjgaude said:**
> Thanks, Luca, for all the info. Considering the state of OO I think I'll wait for its release before I spend time with my netbook, upgrading it with psb-gfx driver. Simply don't have the time to work out the bugs. But will continue to watch what you guys are doing for GMA500 boxes.

Okay, maybe I'll install 11.04 on a separate partition, and then psb-gfx. Would that work, Luca?

You can try psb-gfx on 11.04, follow this post by tista.
[http://ubuntuforums.org/showpost.php?p=10766450&postcount=3866](http://ubuntuforums.org/showpost.php?p=10766450&postcount=3866)

Drivers Update.. dither has been fixed upstream, no more need of patch :)

---

### Post by fjgaude on 2011-07-11
> **lucazade said:**
> You can try psb-gfx on 11.04, follow this post by tista.
[http://ubuntuforums.org/showpost.php?p=10766450&postcount=3866](http://ubuntuforums.org/showpost.php?p=10766450&postcount=3866)

Drivers Update.. dither has been fixed upstream, no more need of patch :)

Oh boy! Will get to it in a few days... will let you know if I need help. <smile>

---

### Post by tista on 2011-07-11
Hi guys.

OK. Alan had done!! :)

so I'm happy with that I didn't have to do any cody/patchworks for it... :P
if you guys had some issues, should contact to linux-MID team, and they fix it. that's all.

now I'm supporting some other distributions instead of Ubuntu. so my works didn't seems to be needed for Ubuntu, right?

cheers.

---

### Post by lucazade on 2011-07-12
> **tista said:**
> Hi guys.

OK. Alan had done!! :)

so I'm happy with that I didn't have to do any cody/patchworks for it... :P
if you guys had some issues, should contact to linux-MID team, and they fix it. that's all.

now I'm supporting some other distributions instead of Ubuntu. so my works didn't seems to be needed for Ubuntu, right?

cheers.

\\:D/

Alan had done.

If I have understand well he added some bits in order to glue 2D X driver and PVR binary stuff for both opengl and vaapi.
Not an easy road but surely impressive!

Did you switch to another distro? Arch? Elementary? :)

---

### Post by tista on 2011-07-12
> **lucazade said:**
> \\:D/

Alan had done.

If I have understand well he added some bits in order to glue 2D X driver and PVR binary stuff for both opengl and vaapi.
Not an easy road but surely impressive!

Did you switch to another distro? Arch? Elementary? :)

ahaha. ;)

No I didn't. yeah I prefer to the combination of Ubuntu/Elementary!
but... Ubuntu had a lot of great talents like you!! :P in opposite, the others how? and Ubuntu might be soooo lucky to be announced by who develops in future works. 
I believe that we and all linux users must share the "same sources" to develop/contribute as "same time". 
although I didn't have any ideas how the other distro had contributed the package system, but at least I could announce the future news to the others. if they might need some tiny patchworks, yeah I wanna support them. I think the power of contributers would be the almost same within all of distros. why? yep because we know the men "true gutu" working for the future.  even if we had some troubles, the developers would track them down and fix them quickly.

I also like Arch, Meego, Gentoo, Slackware, and even LFS, too!! but many people had to choose Ubuntu to employ the newest gma500 drivers. oh god, I don't like such situations.... so I wanna support the others, too.

ciao.

---

### Post by lucazade on 2011-07-12
> **tista said:**
> 
I also like Arch, Meego, Gentoo, Slackware, and even LFS, too!! but many people had to choose Ubuntu to employ the newest gma500 drivers. oh god, I don't like such situations.... so I wanna support the others, too.


nuff respect! ;)

---

### Post by tista on 2011-07-12
Hi Luca.

Just now I'm updating "mrst-dkms" packaging to my PPA...
[https://launchpad.net/~tista/+archive/psb-gfx-daily]("https://launchpad.net/~tista/+archive/psb-gfx-daily")

yeah that's the newest mrst/medfield combo drivers included SGX sources!!
but I didn't know how it works... :P

stay tuned!!

ciao.

P.S:
now I have to polish dkms installer/builder... so wait a moment... :sad:

---

### Post by lucazade on 2011-07-12
so cool, i'll stay tuned for testing this driver (which should be developed from PowerVR itself, so should be well done)

I'm wondering what are the non-free user space packages of pvr needed to have the whole working.. beside your dkms kernel modules.

any of these?
[http://repo.meego.com/MeeGo/snapshots/testing/1.2.80/latest/repos/non-oss/source/](http://repo.meego.com/MeeGo/snapshots/testing/1.2.80/latest/repos/non-oss/source/)
[http://repo.meego.com/MeeGo/snapshots/testing/1.2.80/latest/repos/non-oss/ia32/packages/i586/](http://repo.meego.com/MeeGo/snapshots/testing/1.2.80/latest/repos/non-oss/ia32/packages/i586/)

i'm bit lost through packages :)

---

### Post by tista on 2011-07-12
> **lucazade said:**
> so cool, i'll stay tuned for testing this driver (which should be developed from PowerVR itself, so should be well done)

I'm wondering what are the non-free user space packages of pvr needed to have the whole working.. beside your dkms kernel modules.

any of these?
[http://repo.meego.com/MeeGo/snapshots/testing/1.2.80/latest/repos/non-oss/source/](http://repo.meego.com/MeeGo/snapshots/testing/1.2.80/latest/repos/non-oss/source/)
[http://repo.meego.com/MeeGo/snapshots/testing/1.2.80/latest/repos/non-oss/ia32/packages/i586/](http://repo.meego.com/MeeGo/snapshots/testing/1.2.80/latest/repos/non-oss/ia32/packages/i586/)

i'm bit lost through packages :)

I'm using here:
[http://git.kernel.org/?p=linux/kernel/git/alan/linux-3.0-mid-ref.git;a=commit;h=a84320e73d98f3acff2e84fd718069249c4fc9d6]("http://git.kernel.org/?p=linux/kernel/git/alan/linux-3.0-mid-ref.git;a=commit;h=a84320e73d98f3acff2e84fd718069249c4fc9d6")

yeah I usually use git... maybe here would be newer than meego repository... or Alan might port them from meego sources? anyway, it would be better to divide the package to each drivers... ;)

combo modules builder/installer system sometimes grows the size up and makes it harder to maintain.

ciao.

---

### Post by lucazade on 2011-07-12
> **tista said:**
> I'm using here:
[http://git.kernel.org/?p=linux/kernel/git/alan/linux-3.0-mid-ref.git;a=commit;h=a84320e73d98f3acff2e84fd718069249c4fc9d6]("http://git.kernel.org/?p=linux/kernel/git/alan/linux-3.0-mid-ref.git;a=commit;h=a84320e73d98f3acff2e84fd718069249c4fc9d6")

yeah I usually use git... maybe here would be newer than meego repository... or Alan might port them from meego sources? anyway, it would be better to divide the package to each drivers... ;)

combo modules builder/installer system sometimes grows the size up and makes it harder to maintain.

ciao.

yes, i use the same git kernel repo.

I thought there were necessary also some binary blobs for firmware/opengl/vaapi. Am I wrong?
Do we have sources for everything? and everything needed is inside mrst tree?

---

### Post by tista on 2011-07-12
> **lucazade said:**
> yes, i use the same git kernel repo.

I thought there were necessary also some binary blobs for firmware/opengl/vaapi. Am I wrong?
Do we have sources for everything? and everything needed is inside mrst tree?

there were some lack of headers to build. not binaries. ;)
so I would drain them from meego tree to build pvr drivers sections of mrst/medfield... or Luca could drain headers from src.rpm?

---

### Post by lucazade on 2011-07-12
> **tista said:**
> there were some lack of headers to build. not binaries. ;)
so I would drain them from meego tree to build pvr drivers sections of mrst/medfield... or Luca could drain headers from src.rpm?

I would drain them for you but, you know, with my C knowledge I could take ages to find which headers to get and which not :)
Anyway I'm going to look at src.rpm files and confrontate with alan tree.

---

### Post by tista on 2011-07-12
> **lucazade said:**
> I would drain them for you but, you know, with my C knowledge I could take ages to find which headers to get and which not :)
Anyway I'm going to look at src.rpm files and confrontate with alan tree.

So sorry Luca.
I've found headers to be needed to build for... yeah that's my mistakes of making dkms packages.
now I'm re-polishing some Makefile up and if I could build manually on local, ASAP I would upload it.

ciao.

---

### Post by fanum on 2011-07-12
> **lucazade said:**
> "Medfield PVR driver

Import of known good and working tree for the **2D/3D** non free driver

NOT FOR UPSTREAM [requires non-free userspace]"

[http://git.kernel.org/?p=linux/kernel/git/alan/linux-3.0-mid-ref.git;a=commit;h=a84320e73d98f3acff2e84fd718069249c4fc9d6](http://git.kernel.org/?p=linux/kernel/git/alan/linux-3.0-mid-ref.git;a=commit;h=a84320e73d98f3acff2e84fd718069249c4fc9d6)

:guitar:

Is this an all new driver? Any details or documentation (other than provided already)?

---

### Post by lucazade on 2011-07-12
> **fanum said:**
> Is this an all new driver? Any details or documentation (other than provided already)?

It is based on an existing driver called pvr made by PowerVR/IMG, which I never tried before and from what I recall should provide both 2d/3d accel.. this will also merge with the new driver psb_gfx (really a kernel module) in the future.

Maybe this article could help:
[http://www.phoronix.com/scan.php?page=news_item&px=OTY2Mg](http://www.phoronix.com/scan.php?page=news_item&px=OTY2Mg)

really, really interesting.. hope to test soon to understand better the situation.
Way toooo much drivers for this chipset but this seems the best :)

---

### Post by fjgaude on 2011-07-12
Luca, gosh it is truly interesting... please keep us informed as you have already done. And when it is time, update your Poulsbo page. It was that page that got me to 10.04 from 7.10 with my Dell 10n.

---

### Post by tista on 2011-07-12
@Luca

yeah I've got almost there (make.log):
[http://paste.ubuntu.com/643024/]("http://paste.ubuntu.com/643024/")

Soon I would fix remained compilation errors in both medfield and moorestown!!
Wait a moment pls... ;)

ciao.

**P.S:**
I've uploaded current mrst-dkms-0.1.1~oneiric4...
but unfortunately it still has dkms installation errors. after compilations, dkms didn't start to install 2 mdules into updates/dkms/ directory.... today I didn't have any ideas why it fails....

so here is the workarounds.
copy 2modules named "mrst_gfx.ko" and "medfield_gfx.ko" into /lib/modules/YOUR_KERNEL/updates/dkms/ manually, right? these modules would stay in /var/lib/dkms/mrst/0.1.1~oneiric4/build/medfield and /var/lib/dkms/mrst/0.1.1~oneiric4/build/moorestown.

I'm tracking this dkms errors down... ;)

---

### Post by lucazade on 2011-07-13
@great tista

i'm looking forward to hearing from you soon.

I was searching some info about this pvr driver and found an old article on Phoronix:
> AFAICS, there are up to 6 (yes, six) drivers for Intel products based on SGX535.
- 1 driver for Canmore/Sodaville
- 1 driver for US15W (from UMG)
- 1 driver for MRST (DRI2 capable), that also includes support for older US15W
- 1 driver for US15W (IEGD 10.x)
- 1 driver for MRST/US15W with support for Android (OpenGL ES)
- 1 driver for MRST/US15W. That new EMGD that looks derived from IEGD.

The "psb" drivers have two branches. What people have for US15W + some updates to Intel customers. The newer branch, that supports dri2 and other features for VA-API, is targetted to Moorestown users, but it could also work with older Poulsbo. This is not publicly available because the platforms are not publicly available either... Thinking about it further, there might be three branches actually: the one with support for Android platforms.

[http://phoronix.com/forums/showthread.php?24142-Even-With-MeeGo-Poulsbo-amp-Moorestown-Are-Crap#post131854](http://phoronix.com/forums/showthread.php?24142-Even-With-MeeGo-Poulsbo-amp-Moorestown-Are-Crap#post131854)

pvr should be that one with dri2, if i'm not wrong. what a mess!

---

### Post by tista on 2011-07-13
> **lucazade said:**
> @great tista

i'm looking forward to hearing from you soon.

I was searching some info about this pvr driver and found an old article on Phoronix:


[http://phoronix.com/forums/showthread.php?24142-Even-With-MeeGo-Poulsbo-amp-Moorestown-Are-Crap#post131854](http://phoronix.com/forums/showthread.php?24142-Even-With-MeeGo-Poulsbo-amp-Moorestown-Are-Crap#post131854)

pvr should be that one with dri2, if i'm not wrong. what a mess!

Nice info Luca!! ;)

and I've found some headers in Meego repos  to develop Mesa drivers!
what's mean? yeah the Wayland... today we've got KMS driver, and what were remained things? yep open-sourced GLES to kick wayland!! if I had a hint to make new GLES, I would contact wayland team again...

and then, we also prepare for xorg drivers, the first, Meego has patched fbdev. so we might port it to our Ubuntu. OK. I would try it soon...

ciao. :)

---

### Post by lucazade on 2011-07-13
> **tista said:**
> Nice info Luca!! ;)

and I've found some headers in Meego repos  to develop Mesa drivers!
what's mean? yeah the Wayland... today we've got KMS driver, and what were remained things? yep open-sourced GLES to kick wayland!! if I had a hint to make new GLES, I would contact wayland team again...

and then, we also prepare for xorg drivers, the first, Meego has patched fbdev. so we might port it to our Ubuntu. OK. I would try it soon...

ciao. :)

Crossing fingers!

yep, this is the correct combo for Wayland, or at least it looks like. :)

---

### Post by tista on 2011-07-13
> **lucazade said:**
> Crossing fingers!

yep, this is the correct combo for Wayland, or at least it looks like. :)

@Luca

the SGX fbdev driver is coming soooooon !!
xserver-xorg-video-fbdev_1:0.4.99-232+0m6~sgx~oneiric2

just now building....
this package has a lot of pvr headers to improve pvr2d, xv, and more.... :)

---

### Post by jbernardo on 2011-07-13
> **tista said:**
> @Luca

the SGX fbdev driver is coming soooooon !!
xserver-xorg-video-fbdev_1:0.4.99-232+0m6~sgx~oneiric2

just now building....
this package has a lot of pvr headers to improve pvr2d, xv, and more.... :)

Guys,
Thank you for everything... Seems like it is time to start tinkering with my 1101HA again!
Looks like I'll have to install oneiric to test this...

---

### Post by lucazade on 2011-07-13
@jbernardo
great, your efforts are always precious!

I've updated instructions for installing psb_gfx drivers on Oneiric.
A couple of tricks are necessary also to start the livecd.



To make the livecd startup we have to unload a couple of drivers adding some parameters to kernel, otherwise it ends up in a white screen.

add 'poulsbo.dummy=1 psb_gfx.dummy=1' to kernel params at grub time (hit F6 when livecd starts)
this way the 2 kernel modules are not loaded, because of wrong options enabled, and livecd could use vesa as X driver.

once installed, reboot with fake kernel params and add ppa:
```
sudo add-apt-repository ppa:gma500/psb-gfx
sudo apt-get update
sudo apt-get install psb-dkms

```

necessary workarounds:
```
echo 'blacklist poulsbo' | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo mv /etc/init/plymouth.conf /etc/init/plymouth.conf.disable
sudo sed -i 's/vt.handoff=7//g' /etc/grub.d/10_linux
sudo update-grub
```

fix for backlight hotkeys on acer751h (please report for other netbooks):
```

echo 'blacklist acer_wmi' | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo sed -i 's/GRUB_CMDLINE_LINUX=""/GRUB_CMDLINE_LINUX="acpi_backlight=vendor"/g' /etc/default/grub
sudo update-grub

```

reboot again and it should work.

---

### Post by jbernardo on 2011-07-13
Thanks Luca,
I'll try it this week!

---

### Post by tista on 2011-07-13
Hi guys.

I've uploaded pvr specified fbdev SGX driver for Oneiric. ;)
[https://launchpad.net/~tista/+archive/psb-gfx-daily]("https://launchpad.net/~tista/+archive/psb-gfx-daily")

this driver had improved many features, especially pvr2d. so it didn't have any compatibilities for any other KMS driver instead of pvr/psb_gfx/mrst_gfx/medfield_gfx drivers, maybe.

seen from sources, it also improves xv video playback, too. and hopefully PVR 3D!! but at least now we had to port some binaries for PVR 3D from Meego repository... I didn't do that yet.

well... what is the next guys want me to do? porting PVR Xorg driver? mrst-dkms fixing up? or something else? :)
let me know! ohh forgot to mention, did anybody maintain EMGD today? should it be continued to Oneiric? I didn't think that because of its binary crap of Xorg driver... otherwise the kernelspace would be OK to do patchworks similar to 2.6.39 or so...

ciao.

---

### Post by lucazade on 2011-07-13
> **tista said:**
> Hi guys.

I've uploaded pvr specified fbdev SGX driver for Oneiric. ;)
[https://launchpad.net/~tista/+archive/psb-gfx-daily]("https://launchpad.net/~tista/+archive/psb-gfx-daily")

this driver had improved many features, especially pvr2d. so it didn't have any compatibilities for any other KMS driver instead of pvr/psb_gfx/mrst_gfx/medfield_gfx drivers, maybe.

seen from sources, it also improves xv video playback, too. and hopefully PVR 3D!! but at least now we had to port some binaries for PVR 3D from Meego repository... I didn't do that yet.

woohooo!! 

> well... what is the next guys want me to do? porting PVR Xorg driver? mrst-dkms fixing up? or something else? :)

what to do? what you enjoy most... :F

> let me know! ohh forgot to mention, did anybody maintain EMGD today? should it be continued to Oneiric? I didn't think that because of its binary crap of Xorg driver... otherwise the kernelspace would be OK to do patchworks similar to 2.6.39 or so...

ciao.

Yep, sometime some fix to emgd is necessary, other day I've applied a patch for dkms against new kernel, a guy sent me.
emgd xorg is slow and binary so nothing to play with, kernel space could be useful.

ah, wait
How to test new fbdev sgx?? just install?

ciao!

---

### Post by tista on 2011-07-13
> **lucazade said:**
> woohooo!! 
ah, wait
How to test new fbdev sgx?? just install?

ciao!

@Luca

Yep.
I think it needs just installing... but I don't know how it works on psb_gfx... :P

cheers.

---

### Post by lucazade on 2011-07-13
Ok.. tried sgx.

unfortunately X doesn't start, also blacklisting psb_gfx.
It ends up flickering in virtualterminals. :)

```

[   126.929] 
X.Org X Server 1.10.2.902 (1.10.3 RC 2)
Release Date: 2011-07-01
[   126.930] X Protocol Version 11, Revision 0
[   126.930] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[   126.930] Current Operating System: Linux ao751h 3.0.0-5-generic #6-Ubuntu SMP Tue Jul 12 05:14:17 UTC 2011 i686
[   126.931] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-5-generic root=UUID=b51999e8-641f-453a-9ef0-8b69851cf059 ro quiet splash
[   126.931] Build Date: 13 July 2011  12:18:21AM
[   126.931] xorg-server 2:1.10.2.902-1ubuntu3 (For technical support please see http://www.ubuntu.com/support) 
[   126.932] Current version of pixman: 0.22.2
[   126.932] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   126.932] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   126.934] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jul 13 15:38:03 2011
[   126.935] (==) Using config file: "/etc/X11/xorg.conf"
[   126.935] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   126.937] (==) No Layout section.  Using the first Screen section.
[   126.937] (**) |-->Screen "Default Screen" (0)
[   126.937] (**) |   |-->Monitor "<default monitor>"
[   126.938] (**) |   |-->Device "Configured Video Device"
[   126.938] (==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
[   126.938] (==) Automatically adding devices
[   126.938] (==) Automatically enabling devices
[   126.938] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   126.938] 	Entry deleted from font path.
[   126.938] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   126.938] 	Entry deleted from font path.
[   126.938] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   126.938] 	Entry deleted from font path.
[   126.938] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   126.938] 	Entry deleted from font path.
[   126.938] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   126.938] 	Entry deleted from font path.
[   126.938] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   126.939] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   126.939] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   126.939] (II) Loader magic: 0x8239da0
[   126.939] (II) Module ABI versions:
[   126.939] 	X.Org ANSI C Emulation: 0.4
[   126.939] 	X.Org Video Driver: 10.0
[   126.939] 	X.Org XInput driver : 12.3
[   126.939] 	X.Org Server Extension : 5.0
[   126.940] (--) PCI:*(0:0:2:0) 8086:8108:1025:0244 rev 7, Mem @ 0xb0080000/524288, 0xc0000000/268435456, 0xb0000000/262144, I/O @ 0x00001800/8
[   126.941] (II) Open ACPI successful (/var/run/acpid.socket)
[   126.941] (II) LoadModule: "extmod"
[   126.943] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   126.943] (II) Module extmod: vendor="X.Org Foundation"
[   126.943] 	compiled for 1.10.2.902, module version = 1.0.0
[   126.943] 	Module class: X.Org Server Extension
[   126.943] 	ABI class: X.Org Server Extension, version 5.0
[   126.943] (II) Loading extension MIT-SCREEN-SAVER
[   126.943] (II) Loading extension XFree86-VidModeExtension
[   126.943] (II) Loading extension XFree86-DGA
[   126.943] (II) Loading extension DPMS
[   126.943] (II) Loading extension XVideo
[   126.943] (II) Loading extension XVideo-MotionCompensation
[   126.944] (II) Loading extension X-Resource
[   126.944] (II) LoadModule: "dbe"
[   126.945] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   126.945] (II) Module dbe: vendor="X.Org Foundation"
[   126.945] 	compiled for 1.10.2.902, module version = 1.0.0
[   126.945] 	Module class: X.Org Server Extension
[   126.945] 	ABI class: X.Org Server Extension, version 5.0
[   126.945] (II) Loading extension DOUBLE-BUFFER
[   126.945] (II) LoadModule: "glx"
[   126.946] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   126.947] (II) Module glx: vendor="X.Org Foundation"
[   126.947] 	compiled for 1.10.2.902, module version = 1.0.0
[   126.947] 	ABI class: X.Org Server Extension, version 5.0
[   126.947] (==) AIGLX enabled
[   126.947] (II) Loading extension GLX
[   126.947] (II) LoadModule: "record"
[   126.948] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   126.948] (II) Module record: vendor="X.Org Foundation"
[   126.948] 	compiled for 1.10.2.902, module version = 1.13.0
[   126.948] 	Module class: X.Org Server Extension
[   126.948] 	ABI class: X.Org Server Extension, version 5.0
[   126.949] (II) Loading extension RECORD
[   126.949] (II) LoadModule: "dri"
[   126.950] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   126.950] (II) Module dri: vendor="X.Org Foundation"
[   126.950] 	compiled for 1.10.2.902, module version = 1.0.0
[   126.950] 	ABI class: X.Org Server Extension, version 5.0
[   126.950] (II) Loading extension XFree86-DRI
[   126.950] (II) LoadModule: "dri2"
[   126.951] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   126.952] (II) Module dri2: vendor="X.Org Foundation"
[   126.952] 	compiled for 1.10.2.902, module version = 1.2.0
[   126.952] 	ABI class: X.Org Server Extension, version 5.0
[   126.952] (II) Loading extension DRI2
[   126.952] (II) LoadModule: "fbdev"
[   126.953] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   126.953] (II) Module fbdev: vendor="X.Org Foundation"
[   126.953] 	compiled for 1.10.2.902, module version = 0.4.0
[   126.953] 	Module class: X.Org Video Driver
[   126.953] 	ABI class: X.Org Video Driver, version 10.0
[   126.953] (II) FBDEV: driver for framebuffer: fbdev
[   126.953] (--) using VT number 7

[   126.958] (WW) Falling back to old probe method for fbdev
[   126.958] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   126.958] (II) FBDEV(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 16/16
[   126.958] (==) FBDEV(0): Depth 16, (==) framebuffer bpp 16
[   126.958] (==) FBDEV(0): RGB weight 565
[   126.959] (==) FBDEV(0): Default visual is TrueColor
[   126.959] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[   126.959] (==) FBDEV(0): SwapMethod is flip
[   126.959] (==) FBDEV(0): Disabling vblank synchronization
[   126.959] (==) FBDEV(0): Enabling synchronous rendering
[   126.959] (==) FBDEV(0): Using 3 page flip buffers.
[   126.959] (==) FBDEV(0): Screen size can't be changed
[   126.959] omap/sysfs: can't open '/sys/devices/platform/omapdss/overlay0/name' for reading: 2:No such file or directory
[   126.959] (EE) FBDEV(0): Unable to open overlay /dev/fb0/gfx
[   126.959] (II) UnloadModule: "fbdev"
[   126.960] (II) Unloading fbdev
[   126.960] (EE) Screen(s) found, but none have a usable configuration.
[   126.960] 
Fatal server error:
[   126.960] no screens found
[   126.960] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[   126.960] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   126.960] 
[   126.964]  ddxSigGiveUp: Closing log

```

well, first trial... it was expected :D

EDIT: mrst-dkms failed to build, attached dkms make.log

---

### Post by tista on 2011-07-13
@Luca.

Thanks for your trials! :)

yeah fbdev seems to be fitted to omap3... so it might need some special fb like "omap1fb". I'm trying to force it to use psbfb.

and then, mrst-dkms would be the same results on my X120e. but modules were already built. so you could cp modules to update/dkms. module path were showed in the last part of log.
```
LD [M]  /var/lib/dkms/mrst/0.1.1~oneiric4/build/medfield/medfield_gfx.ko
LD [M]  /var/lib/dkms/mrst/0.1.1~oneiric4/build/moorestown/mrst_gfx.ko
```

could you copy them into updates/dkms manually? ;)

cheers.

---

### Post by lucazade on 2011-07-13
You're right mrst and midfield are built. Copied both in /lib/modules/.../updates/dkms
but I can't find a way to load them.. tried modprobe and modinfo but can't find the module.

> what i'm missing?
probably a coffee..


```
luca@ao751h:~/Scrivania$ sudo insmod /lib/modules/3.0.0-5-generic/updates/dkms/mrst_gfx.ko
insmod: error inserting '/lib/modules/3.0.0-5-generic/updates/dkms/mrst_gfx.ko': -1 Unknown symbol in module
luca@ao751h:~/Scrivania$ sudo insmod /lib/modules/3.0.0-5-generic/updates/dkms/medfield_gfx.ko 
insmod: error inserting '/lib/modules/3.0.0-5-generic/updates/dkms/medfield_gfx.ko': -1 Unknown symbol in module

luca@ao751h:~/Scrivania$ sudo modprobe /lib/modules/3.0.0-5-generic/updates/dkms/medfield_gfx.ko 
FATAL: Module /lib/modules/3.0.0_5_generic/updates/dkms/medfield_gfx.ko not found.
luca@ao751h:~/Scrivania$ sudo modprobe /lib/modules/3.0.0-5-generic/updates/dkms/mrst_gfx.ko 
FATAL: Module /lib/modules/3.0.0_5_generic/updates/dkms/mrst_gfx.ko not found.
```

---

### Post by tista on 2011-07-13
> **lucazade said:**
> Ciao Tista

The sources of 0.2.27 come directly from Alan Cox tree, updated some days ago:
[http://git.kernel.org/?p=linux/kernel/git/alan/linux-3.0-mid-ref.git;a=tree;f=drivers/staging/gma500;h=011c08eaa49485fa60e7e567e0d0bb57602eec96;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/alan/linux-3.0-mid-ref.git;a=tree;f=drivers/staging/gma500;h=011c08eaa49485fa60e7e567e0d0bb57602eec96;hb=HEAD)

I haven't updated psb_gfx bzr branch on my launchpad yet but sources are anyway  available from the ppa itself:
[https://launchpad.net/~gma500/+archive/psb-gfx/+files/psb-dkms_0.2.27.tar.gz](https://launchpad.net/~gma500/+archive/psb-gfx/+files/psb-dkms_0.2.27.tar.gz)

This time I used only the original sources without employing stuff from your branch because I wanted to find why it was broken in OO. Now that it is working good (also plymouth, vt.handoff are ok now!) it is time to merge with dithering and acpi_register patches ( don't remember if there are other things).

What do you suggest?

edit... 0.2.26 was a copy of your branch and I never had that issue

OK... exactly it's around the time to merge...
but one thing.

if acpi_register is embedded like "hard-coded", VAIO PC might be failed to control via any backlight hotkeys. I was afraid that "we had no choice"... :sad: so I coded it like "side by side" external option.

and then, now I've found the errors on mrst-dkms. so I've uploaded newer one to fix modprobing error. ;)

cheers.

---

### Post by lucazade on 2011-07-13
> **tista said:**
> OK... exactly it's around the time to merge...
but one thing.

if acpi_register is embedded like "hard-coded", VAIO PC might be failed to control via any backlight hotkeys. I was afraid that "we had no choice"... :sad: so I coded it like "side by side" external option.

and then, now I've found the errors on mrst-dkms. so I've uploaded newer one to fix modprobing error. ;)

cheers.

right, vaio doesn't need acpi_register and now is hardcoded. External option +1

in the messagge you quoted I was wrong when saying plymouth and vt.handoff were ok.. are still broken and Alan is aware of these.
Dither instead has been merged is surely no necessary.

great for mrst-dkms.. i'll take a look at your ppa, obviously no hurry.

---

### Post by tista on 2011-07-13
> **lucazade said:**
> right, vaio doesn't need acpi_register and now is hardcoded. External option +1

in the messagge you quoted I was wrong when saying plymouth and vt.handoff were ok.. are still broken and Alan is aware of these.
Dither instead has been merged is surely no necessary.

great for mrst-dkms.. i'll take a look at your ppa, obviously no hurry.

ehehehe ;)

mrst had come !!!
[http://paste.ubuntu.com/643372/]("http://paste.ubuntu.com/643372/")
my friend had tested it on natty... it seems to scceed to load. :)
as far as I know mrst still uses ttm??

anyway, we've got to add new KMS driver for GMA500!!

cheers.

---

### Post by lucazade on 2011-07-13
> **tista said:**
> ehehehe ;)

mrst had come !!!
[http://paste.ubuntu.com/643372/]("http://paste.ubuntu.com/643372/")
my friend had tested it on natty... it seems to scceed to load. :)
as far as I know mrst still uses ttm??

anyway, we've got to add new KMS driver for GMA500!!

cheers.

ahhaha you were fast!
how many options mrst have? :O cool!

yep it uses ttm (no gtt) and no kms.. this is why alan diverged psb_gfx tree, i suppose, to merge again after adding these feature..

nice time are comings... 2nd life for poulsbo!

---

### Post by lucazade on 2011-07-14
Tista
looking again at mrst module you posted I've seen it support only a small
part of pciid.

My card is VGA compatible controller [0300]: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller [8086:8108]

mrst support only:
alias:          pci:v00008086d00004107sv*sd*bc*sc*i*
alias:          pci:v00008086d00004106sv*sd*bc*sc*i*
alias:          pci:v00008086d00004105sv*sd*bc*sc*i*
alias:          pci:v00008086d00004104sv*sd*bc*sc*i*
alias:          pci:v00008086d00004103sv*sd*bc*sc*i*
alias:          pci:v00008086d00004102sv*sd*bc*sc*i*
alias:          pci:v00008086d00004101sv*sd*bc*sc*i*
alias:          pci:v00008086d00004100sv*sd*bc*sc*i*

while psb_gfx supports:
alias:          pci:v00008086d00000137sv*sd*bc*sc*i*
alias:          pci:v00008086d00000136sv*sd*bc*sc*i*
alias:          pci:v00008086d00000135sv*sd*bc*sc*i*
alias:          pci:v00008086d00000134sv*sd*bc*sc*i*
alias:          pci:v00008086d00000133sv*sd*bc*sc*i*
alias:          pci:v00008086d00000132sv*sd*bc*sc*i*
alias:          pci:v00008086d00000131sv*sd*bc*sc*i*
alias:          pci:v00008086d00000130sv*sd*bc*sc*i*
alias:          pci:v00008086d00004107sv*sd*bc*sc*i*
alias:          pci:v00008086d00004106sv*sd*bc*sc*i*
alias:          pci:v00008086d00004105sv*sd*bc*sc*i*
alias:          pci:v00008086d00004104sv*sd*bc*sc*i*
alias:          pci:v00008086d00004103sv*sd*bc*sc*i*
alias:          pci:v00008086d00004102sv*sd*bc*sc*i*
alias:          pci:v00008086d00004101sv*sd*bc*sc*i*
alias:          pci:v00008086d00004100sv*sd*bc*sc*i*
alias:          pci:v00008086d00008109sv*sd*bc*sc*i*
alias:          pci:v00008086d00008108sv*sd*bc*sc*i*

so doesn't seem no good.. what about medfield?

---

### Post by tista on 2011-07-14
> **lucazade said:**
> Tista
looking again at mrst module you posted I've seen it support only a small
part of pciid.

My card is VGA compatible controller [0300]: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller [8086:8108]

mrst support only:
alias:          pci:v00008086d00004107sv*sd*bc*sc*i*
alias:          pci:v00008086d00004106sv*sd*bc*sc*i*
alias:          pci:v00008086d00004105sv*sd*bc*sc*i*
alias:          pci:v00008086d00004104sv*sd*bc*sc*i*
alias:          pci:v00008086d00004103sv*sd*bc*sc*i*
alias:          pci:v00008086d00004102sv*sd*bc*sc*i*
alias:          pci:v00008086d00004101sv*sd*bc*sc*i*
alias:          pci:v00008086d00004100sv*sd*bc*sc*i*

while psb_gfx supports:
alias:          pci:v00008086d00000137sv*sd*bc*sc*i*
alias:          pci:v00008086d00000136sv*sd*bc*sc*i*
alias:          pci:v00008086d00000135sv*sd*bc*sc*i*
alias:          pci:v00008086d00000134sv*sd*bc*sc*i*
alias:          pci:v00008086d00000133sv*sd*bc*sc*i*
alias:          pci:v00008086d00000132sv*sd*bc*sc*i*
alias:          pci:v00008086d00000131sv*sd*bc*sc*i*
alias:          pci:v00008086d00000130sv*sd*bc*sc*i*
alias:          pci:v00008086d00004107sv*sd*bc*sc*i*
alias:          pci:v00008086d00004106sv*sd*bc*sc*i*
alias:          pci:v00008086d00004105sv*sd*bc*sc*i*
alias:          pci:v00008086d00004104sv*sd*bc*sc*i*
alias:          pci:v00008086d00004103sv*sd*bc*sc*i*
alias:          pci:v00008086d00004102sv*sd*bc*sc*i*
alias:          pci:v00008086d00004101sv*sd*bc*sc*i*
alias:          pci:v00008086d00004100sv*sd*bc*sc*i*
alias:          pci:v00008086d00008109sv*sd*bc*sc*i*
alias:          pci:v00008086d00008108sv*sd*bc*sc*i*

so doesn't seem no good.. what about medfield?

@Luca

yeah that's right.
medfield had similar support lists:
[http://paste.ubuntu.com/643857/]("http://paste.ubuntu.com/643857/")

today I've uploaded latest mrst-dkms to be fixed dkms installation error... ;)
well... if you guys let me cody to enlarge the support lists included around the old poulsbo machies, I might do that...

anyway, mrst and medfield could be OK to load on old poulsbo machine. I think that because of sources.

ciao.

**P.S:**
I've now uploaded 8108/8109 included version of mrst!!
yeah named mrst-dkms_0.1.1~oneiric8.
soon it would be built on PPA. ;)
but medfield must be specified to SGX540, so I only added old psb's pciid to mrst, right?
and I'm afraid that 8108/8109 was defied as PSB equal to "True KMS GEM" driver, otherwise mrst is now still in stack with ttm, so I really don't know how modded mrst works on old psb machines... :sad:
anyway, let it try Luca!

here is the latest modinfo of mrst included 8108/8109!! :)
[http://paste.ubuntu.com/643963/]("http://paste.ubuntu.com/643963/")

---

### Post by lucazade on 2011-07-16
> **tista said:**
> @Luca

**P.S:**
I've now uploaded 8108/8109 included version of mrst!!
yeah named mrst-dkms_0.1.1~oneiric8.
soon it would be built on PPA. ;)
but medfield must be specified to SGX540, so I only added old psb's pciid to mrst, right?
and I'm afraid that 8108/8109 was defied as PSB equal to "True KMS GEM" driver, otherwise mrst is now still in stack with ttm, so I really don't know how modded mrst works on old psb machines... :sad:
anyway, let it try Luca!

here is the latest modinfo of mrst included 8108/8109!! :)
[http://paste.ubuntu.com/643963/]("http://paste.ubuntu.com/643963/")

I've seen your message only now :)
Yep, I've tried rev8 of mrst-dkms, it compiles correctly and the module mrst_gfx is loaded auto at startup, so pciid seems ok.
I still have to try it alongside the fbdev-sgx to see if framebuffer of mrst is used by fbdev. Right? Otherwise mrst_gfx could talk to binary pvr X driver?

Other thing.. Was trying emgd 1.6 in Oneiric.. xorg 1.9 backport seems to be installed ok.. kernel module is obviously broken against kernel 3.x.
](*,)

```
cat /var/lib/dkms/emgd/1.6.0.1922/build/make.log
DKMS make.log for emgd-1.6.0.1922 for kernel 3.0.0-5-generic (i686)
sab 16 lug 2011, 12.17.38, CEST
/var/lib/dkms/emgd/1.6.0.1922/build -- release
make -C /lib/modules/3.0.0-5-generic/build M=/var/lib/dkms/emgd/1.6.0.1922/build modules
make[1]: ingresso nella directory "/usr/src/linux-headers-3.0.0-5-generic"
  CC [M]  /var/lib/dkms/emgd/1.6.0.1922/build/pvr/services4/3rdparty/emgd_displayclass/emgd_dc.o
  CC [M]  /var/lib/dkms/emgd/1.6.0.1922/build/pvr/services4/3rdparty/emgd_displayclass/emgd_dc_linux.o
  CC [M]  /var/lib/dkms/emgd/1.6.0.1922/build/emgd/drm/emgd_fb.o
  CC [M]  /var/lib/dkms/emgd/1.6.0.1922/build/emgd/drm/emgd_mmap.o
  CC [M]  /var/lib/dkms/emgd/1.6.0.1922/build/emgd/drm/emgd_drv.o
/var/lib/dkms/emgd/1.6.0.1922/build/emgd/drm/emgd_drv.c:1974:2: error: unknown field &#8216;pci_driver&#8217; specified in initializer
/var/lib/dkms/emgd/1.6.0.1922/build/emgd/drm/emgd_drv.c:1975:3: error: unknown field &#8216;name&#8217; specified in initializer
/var/lib/dkms/emgd/1.6.0.1922/build/emgd/drm/emgd_drv.c:1975:3: warning: initialization from incompatible pointer type [enabled by default]
/var/lib/dkms/emgd/1.6.0.1922/build/emgd/drm/emgd_drv.c:1975:3: warning: (near initialization for &#8216;driver.kdriver.pci&#8217;) [enabled by default]
/var/lib/dkms/emgd/1.6.0.1922/build/emgd/drm/emgd_drv.c:1976:3: error: unknown field &#8216;id_table&#8217; specified in initializer
/var/lib/dkms/emgd/1.6.0.1922/build/emgd/drm/emgd_drv.c:1976:3: warning: excess elements in union initializer [enabled by default]
/var/lib/dkms/emgd/1.6.0.1922/build/emgd/drm/emgd_drv.c:1976:3: warning: (near initialization for &#8216;driver.kdriver&#8217;) [enabled by default]
/var/lib/dkms/emgd/1.6.0.1922/build/emgd/drm/emgd_drv.c: In function &#8216;emgd_init&#8217;:
/var/lib/dkms/emgd/1.6.0.1922/build/emgd/drm/emgd_drv.c:1994:2: error: implicit declaration of function &#8216;drm_init&#8217; [-Werror=implicit-function-declaration]
/var/lib/dkms/emgd/1.6.0.1922/build/emgd/drm/emgd_drv.c: In function &#8216;emgd_exit&#8217;:
/var/lib/dkms/emgd/1.6.0.1922/build/emgd/drm/emgd_drv.c:2006:2: error: implicit declaration of function &#8216;drm_exit&#8217; [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors

make[2]: *** [/var/lib/dkms/emgd/1.6.0.1922/build/emgd/drm/emgd_drv.o] Errore 1
make[1]: *** [_module_/var/lib/dkms/emgd/1.6.0.1922/build] Errore 2
make[1]: uscita dalla directory "/usr/src/linux-headers-3.0.0-5-generic"
make: *** [modules] Errore 2

```

---

### Post by tista on 2011-07-16
> **lucazade said:**
> I've seen your message only now :)
Yep, I've tried rev8 of mrst-dkms, it compiles correctly and the module mrst_gfx is loaded auto at startup, so pciid seems ok.
I still have to try it alongside the fbdev-sgx to see if framebuffer of mrst is used by fbdev. Right? Otherwise mrst_gfx could talk to binary pvr X driver?

Other thing.. Was trying emgd 1.6 in Oneiric.. xorg 1.9 backport seems to be installed ok.. kernel module is obviously broken against kernel 3.x.
](*,)

```
cat /var/lib/dkms/emgd/1.6.0.1922/build/make.log
DKMS make.log for emgd-1.6.0.1922 for kernel 3.0.0-5-generic (i686)
sab 16 lug 2011, 12.17.38, CEST
/var/lib/dkms/emgd/1.6.0.1922/build -- release
make -C /lib/modules/3.0.0-5-generic/build M=/var/lib/dkms/emgd/1.6.0.1922/build modules
make[1]: ingresso nella directory "/usr/src/linux-headers-3.0.0-5-generic"
  CC [M]  /var/lib/dkms/emgd/1.6.0.1922/build/pvr/services4/3rdparty/emgd_displayclass/emgd_dc.o
  CC [M]  /var/lib/dkms/emgd/1.6.0.1922/build/pvr/services4/3rdparty/emgd_displayclass/emgd_dc_linux.o
  CC [M]  /var/lib/dkms/emgd/1.6.0.1922/build/emgd/drm/emgd_fb.o
  CC [M]  /var/lib/dkms/emgd/1.6.0.1922/build/emgd/drm/emgd_mmap.o
  CC [M]  /var/lib/dkms/emgd/1.6.0.1922/build/emgd/drm/emgd_drv.o
/var/lib/dkms/emgd/1.6.0.1922/build/emgd/drm/emgd_drv.c:1974:2: error: unknown field &#8216;pci_driver&#8217; specified in initializer
/var/lib/dkms/emgd/1.6.0.1922/build/emgd/drm/emgd_drv.c:1975:3: error: unknown field &#8216;name&#8217; specified in initializer
/var/lib/dkms/emgd/1.6.0.1922/build/emgd/drm/emgd_drv.c:1975:3: warning: initialization from incompatible pointer type [enabled by default]
/var/lib/dkms/emgd/1.6.0.1922/build/emgd/drm/emgd_drv.c:1975:3: warning: (near initialization for &#8216;driver.kdriver.pci&#8217;) [enabled by default]
/var/lib/dkms/emgd/1.6.0.1922/build/emgd/drm/emgd_drv.c:1976:3: error: unknown field &#8216;id_table&#8217; specified in initializer
/var/lib/dkms/emgd/1.6.0.1922/build/emgd/drm/emgd_drv.c:1976:3: warning: excess elements in union initializer [enabled by default]
/var/lib/dkms/emgd/1.6.0.1922/build/emgd/drm/emgd_drv.c:1976:3: warning: (near initialization for &#8216;driver.kdriver&#8217;) [enabled by default]
/var/lib/dkms/emgd/1.6.0.1922/build/emgd/drm/emgd_drv.c: In function &#8216;emgd_init&#8217;:
/var/lib/dkms/emgd/1.6.0.1922/build/emgd/drm/emgd_drv.c:1994:2: error: implicit declaration of function &#8216;drm_init&#8217; [-Werror=implicit-function-declaration]
/var/lib/dkms/emgd/1.6.0.1922/build/emgd/drm/emgd_drv.c: In function &#8216;emgd_exit&#8217;:
/var/lib/dkms/emgd/1.6.0.1922/build/emgd/drm/emgd_drv.c:2006:2: error: implicit declaration of function &#8216;drm_exit&#8217; [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors

make[2]: *** [/var/lib/dkms/emgd/1.6.0.1922/build/emgd/drm/emgd_drv.o] Errore 1
make[1]: *** [_module_/var/lib/dkms/emgd/1.6.0.1922/build] Errore 2
make[1]: uscita dalla directory "/usr/src/linux-headers-3.0.0-5-generic"
make: *** [modules] Errore 2

```

Hi Luca.

I've just got home...

I suppose mrst_gfx is the kernelspace of pvr-bin binaries. :) so we might have to port some binaries from Meego:
[http://repo.meego.com/MeeGo/snapshots/testing/1.2.80/latest/repos/non-oss/source/pvr-bin-mrst-5.3.0.0046-11.1.src.rpm]("http://repo.meego.com/MeeGo/snapshots/testing/1.2.80/latest/repos/non-oss/source/pvr-bin-mrst-5.3.0.0046-11.1.src.rpm")
yesterday I've tried making packages but it didn't succeeded.. :sad: or you could do that like EMGD? I'm happy if you could...

fbdev-sgx must be freezing for a while because of its dependencies on OMAP platform. now I'm trying to purge some omap codes, but it seems to be failed to load... anyway 1st choice would be the binaries like pvr-bin-mrst, and 2nd, if could, modded fbdev, OK? :)
I believe fully open-sourced fbdev must be the best... but the big problem stayed. yeah where we should define the overlay for framebuffer except for omap codes.... maybe I might have to cody a bit on mrst_gfx to make overlay sysfs platform... OMG. :P you saw intel_overlay.c already? yep. that's huuuuuge cody! :sad: or I'm searching for somehow we could make overlay without any omap sysfs.

ciao.

**O.T**
emgd-dkms seems to be needed 2.6.39 patch. you had? I would search it, too.

---

### Post by tista on 2011-07-16
@Luca

here is the patches for emgd-dkms to be fiited 2.6.39 or higher:
[http://paste.ubuntu.com/645393/]("http://paste.ubuntu.com/645393/")
[http://paste.ubuntu.com/645394/]("http://paste.ubuntu.com/645394/")
[http://paste.ubuntu.com/645395/]("http://paste.ubuntu.com/645395/")
[http://paste.ubuntu.com/645396/]("http://paste.ubuntu.com/645396/")
[http://paste.ubuntu.com/645397/]("http://paste.ubuntu.com/645397/")

above 5 patches would be all... but I didn't have any convictions. :P
if you had failed to build, let me know your make.log...

cheers.

---

### Post by lucazade on 2011-07-16
Thanks for pointing these patches out.. I totaly forgot them..
They were already applied in emgd-testing ppa. 

Now both emgd-dkms and emgd-xorg are installed in OO, but only in virtualmachine...
Now I've to try to find the courage to install them on the netbook.
At least if it works there is another working driver beside psb_gfx/mrst_gfx and friends!

Agree as well with priorities pvr-bin on top of fbdev, I've seen binary package in meego repo and your in ppa,I'll try to fix (crossing fingers)!

I imagined you used OMAP template but I haven't investigated to much in code, to be sincere.

Happy we!

EDIT: copied all emgd stuff in testing ppa for oneiric.
So if anyone want to try it follow the instruction written here:
[https://launchpad.net/~gma500/+archive/emgd](https://launchpad.net/~gma500/+archive/emgd)
and change first line into:
sudo add-apt-repository ppa:gma500/emgd-fix

---

### Post by lucazade on 2011-07-16
Was looking at xserver-xorg-video-pvr failed build, unfortunately is a bit different from xserver-xorg-video-emgd because of all those symlinks.

like:
```
dpkg-shlibdeps: warning: couldn't find library libpvr2d.so needed by debian/xserver-xorg-video-pvr/usr/lib/pvr/mrst/libpvrPVR2D_LINUXFBWSEGL.so.1.1.16.4043 (ELF format: 'elf32-i386'; RPATH: '/lib:/usr/lib').
```

dpkg-shlibdeps so needs some tuning to find these libs, maybe in substvars.
I need to read some documentation about this, because I don't know how it works..

OT: anyway googling I've found the non-oss repo of meego (where I believe you took the pvr-bin) and there is an updated emgd-bin2027, I'll update our package afterwards.
[http://build.meego.com/project/monitor?arch_i586=1&defaults=0&project=MeeGo%3A1.2%3Anon-oss%3ATesting&repo_MeeGo_1_2=1&succeeded=1](http://build.meego.com/project/monitor?arch_i586=1&defaults=0&project=MeeGo%3A1.2%3Anon-oss%3ATesting&repo_MeeGo_1_2=1&succeeded=1)

---

### Post by lucazade on 2011-07-16
Built xserver-xorg-video-pvr.. yeah!

in debian/rules i've uncommented:
#DEB_DH_SHLIBDEPS_ARGS_ALL=-X*

and removed from binary-arch section:
dh_shlibdeps

hope the .deb works, i've only installed in virtualbox.. there also some warning or errors during package building

```

$ debuild -i -us -uc -b 
dpkg-buildpackage -rfakeroot -D -us -uc -i -b
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package xserver-xorg-video-pvr
dpkg-buildpackage: source version 5.3.0-11.1~oneiric2
dpkg-buildpackage: source changed by tista <t.com>
 dpkg-source -i --before-build xserver-xorg-video-pvr
dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
test -x debian/rules
dh_testroot
dh_clean 
 debian/rules build
test -x debian/rules
mkdir -p "."
 fakeroot debian/rules binary
test -x debian/rules
mkdir -p "."
dh_testdir
dh_testroot
touch install-stamp
dh_testroot
dh_prep 
dh_installdirs -A 
Adding cdbs dependencies to debian/xserver-xorg-video-pvr.substvars
dh_installdirs -pxserver-xorg-video-pvr 
dh_installdocs -pxserver-xorg-video-pvr 
dh_installexamples -pxserver-xorg-video-pvr 
dh_installman -pxserver-xorg-video-pvr  
dh_installinfo -pxserver-xorg-video-pvr  
dh_installmenu -pxserver-xorg-video-pvr 
dh_installcron -pxserver-xorg-video-pvr 
dh_installinit -pxserver-xorg-video-pvr  
dh_installdebconf -pxserver-xorg-video-pvr 
dh_installemacsen -pxserver-xorg-video-pvr   
dh_installcatalogs -pxserver-xorg-video-pvr 
dh_installpam -pxserver-xorg-video-pvr 
dh_installlogrotate -pxserver-xorg-video-pvr 
dh_installlogcheck -pxserver-xorg-video-pvr 
dh_installchangelogs -pxserver-xorg-video-pvr  
dh_installudev -pxserver-xorg-video-pvr 
dh_lintian -pxserver-xorg-video-pvr 
dh_bugfiles -pxserver-xorg-video-pvr 
dh_install -pxserver-xorg-video-pvr  
dh_link -pxserver-xorg-video-pvr  
dh_installmime -pxserver-xorg-video-pvr 
dh_strip -pxserver-xorg-video-pvr  
dh_compress -pxserver-xorg-video-pvr  
dh_fixperms -pxserver-xorg-video-pvr  
dh_makeshlibs -pxserver-xorg-video-pvr  
dh_installdeb -pxserver-xorg-video-pvr 
dh_perl -pxserver-xorg-video-pvr 
dh_shlibdeps -pxserver-xorg-video-pvr   -X* 
dh_gencontrol -pxserver-xorg-video-pvr  
dpkg-gencontrol: warning: Depends field of package xserver-xorg-video-pvr: unknown substitution variable ${shlibs:Depends}
# only call dh_scour for packages in main
if grep -q '^Component:[[:space:]]*main' /CurrentlyBuilding 2>/dev/null; then dh_scour -pxserver-xorg-video-pvr ; fi
# symlink identical documentation to depending packages
[ -n "$CDBS_NO_DOC_SYMLINKING" ] || \
	[ -h debian/xserver-xorg-video-pvr/usr/share/doc ] || \
	[ -h debian/xserver-xorg-video-pvr/usr/share/doc/xserver-xorg-video-pvr ] || \
	[ ! -d debian/xserver-xorg-video-pvr/usr/share/doc ] || \
	myarch=$(sed -n -e's/^Architecture: *//p' debian/xserver-xorg-video-pvr/DEBIAN/control); \
	for dep in `perl -ne 'if (/^(Pre-)?Depends:/) {s/^\w+://; foreach (split /,/) { split; print($_[0], "\n"); } }' debian/xserver-xorg-video-pvr/DEBIAN/control`; do \
	    if [ -d debian/$dep/usr/share/doc ]; then \
	        thisarch=$(sed -n -e's/^Architecture: *//p' debian/$dep/DEBIAN/control 2>/dev/null); \
	        if [ "x$myarch" != "x$thisarch" ] && [ "x$thisarch" = xall ]; then \
	            continue; \
	        fi; \
	        if [ -L debian/xserver-xorg-video-pvr/usr/share/doc/xserver-xorg-video-pvr ]; then \
	            continue; \
	        fi; \
                echo "Searching for duplicated docs in dependency $dep..."; \
                rootdir=`pwd`; \
                (cd debian/xserver-xorg-video-pvr/usr/share/doc/xserver-xorg-video-pvr; find -type f ! -name copyright | while read f; do \
                    thisfile="$rootdir/debian/xserver-xorg-video-pvr/usr/share/doc/xserver-xorg-video-pvr/$f"; \
                    depfile="$rootdir/debian/$dep/usr/share/doc/$dep/$f"; \
                    if [ -f $depfile -o -L $depfile ] && zcmp $thisfile $depfile >/dev/null; then \
                        echo "  symlinking $f in xserver-xorg-video-pvr to file in $dep"; \
                        rm $thisfile; ln -s /usr/share/doc/$dep/$f $thisfile; \
                    fi; \
                done ); \
            fi; \
	done
# symlink identical Gnome help files within packages
if [ -z "$CDBS_NO_GNOME_HELP_SYMLINKING" ] && [ -d debian/xserver-xorg-video-pvr/usr/share/gnome/help ]; then \
            cd debian/xserver-xorg-video-pvr && LC_ALL=C fdupes -r1nq usr/share/gnome/help | while read s; do \
                set -- $(echo $s | tr ' ' '\n' | sort); \
                f=$1; shift; \
                for d; do \
                    echo "symlinking duplicate Gnome help file $d to $f"; \
                    rm $d; ln -s /$f $d; \
                done; \
            done; \
	fi
dh_link -p xserver-xorg-video-pvr
dh_md5sums -pxserver-xorg-video-pvr 
dh_builddeb -pxserver-xorg-video-pvr 
dpkg-deb: attenzione: "debian/xserver-xorg-video-pvr/DEBIAN/control" contiene il campo "Original-Maintainer" definito dall'utente
dpkg-deb: attenzione: 1 avviso relativo ai file di controllo viene ignorato

dpkg-deb: generazione del pacchetto "xserver-xorg-video-pvr" in "../xserver-xorg-video-pvr_5.3.0-11.1~oneiric2_i386.deb".
dh_testdir
dh_testroot
dh_installdirs
dh_installchangelogs
dh_installdocs
dh_installexamples
dh install --sourcedir=debian/tmp/ --fail-missing
   dh_installifupdown -O--sourcedir=debian/tmp/ -O--fail-missing
   dh_pysupport -O--sourcedir=debian/tmp/ -O--fail-missing
   dh_installmodules -O--sourcedir=debian/tmp/ -O--fail-missing
   dh_installppp -O--sourcedir=debian/tmp/ -O--fail-missing
   dh_installwm -O--sourcedir=debian/tmp/ -O--fail-missing
   dh_installxfonts -O--sourcedir=debian/tmp/ -O--fail-missing
   dh_installgsettings -O--sourcedir=debian/tmp/ -O--fail-missing
   dh_ucf -O--sourcedir=debian/tmp/ -O--fail-missing
   dh_gconf -O--sourcedir=debian/tmp/ -O--fail-missing
   dh_icons -O--sourcedir=debian/tmp/ -O--fail-missing
   dh_usrlocal -O--sourcedir=debian/tmp/ -O--fail-missing
dh_link
dh_strip
dh_compress
dh_fixperms
dh_makeshlibs
dh_installdeb
dh_gencontrol
dpkg-gencontrol: warning: Depends field of package xserver-xorg-video-pvr: unknown substitution variable ${shlibs:Depends}
dh_md5sums
dh_builddeb
dpkg-deb: attenzione: "debian/xserver-xorg-video-pvr/DEBIAN/control" contiene il campo "Original-Maintainer" definito dall'utente
dpkg-deb: attenzione: il file di configurazione "/etc/powervr.ini" è duplicato
dpkg-deb: attenzione: 2 avvisi relativi ai file di controllo vengono ignorati

dpkg-deb: generazione del pacchetto "xserver-xorg-video-pvr" in "../xserver-xorg-video-pvr_5.3.0-11.1~oneiric2_i386.deb".
 dpkg-genchanges -b >../xserver-xorg-video-pvr_5.3.0-11.1~oneiric2_i386.changes
dpkg-genchanges: warning: duplicate files list entry for file xserver-xorg-video-pvr_5.3.0-11.1~oneiric2_i386.deb (line 2)
dpkg-genchanges: binary-only upload - not including any source code
 dpkg-source -i --after-build xserver-xorg-video-pvr
dpkg-buildpackage: binary only upload (no source included)
Now running lintian...
E: xserver-xorg-video-pvr: duplicate-conffile etc/powervr.ini
E: xserver-xorg-video-pvr: helper-templates-in-copyright
W: xserver-xorg-video-pvr: maintainer-not-full-name tista
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/dri/pvr_dri.so /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/dri/pvr_dri.so /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libEGL.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libEGL.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libGLES_CM.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libGLES_CM.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libGLESv2.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libGLESv2.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libIMGegl.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libIMGegl.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libOpenVG.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libOpenVG.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libOpenVGU.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libOpenVGU.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libPVROGL.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libPVROGL.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libPVRScopeServices.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libPVRScopeServices.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libglslcompiler.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libglslcompiler.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libpvr2d.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libpvr2d.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libpvrPVR2D_BLITWSEGL.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libpvrPVR2D_BLITWSEGL.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libpvrPVR2D_DRIWSEGL.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libpvrPVR2D_DRIWSEGL.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libpvrPVR2D_FLIPWSEGL.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libpvrPVR2D_FLIPWSEGL.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libpvrPVR2D_LINUXFBWSEGL.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libpvrPVR2D_LINUXFBWSEGL.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libsrv_init.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libsrv_init.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libsrv_um.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libsrv_um.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libusc.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libusc.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: missing-dependency-on-libc needed by usr/lib/pvr/mrst/dri/pvr_dri.so and 18 others
Finished running lintian.

```

---

### Post by tista on 2011-07-16
> **lucazade said:**
> Built xserver-xorg-video-pvr.. yeah!

in debian/rules i've uncommented:
#DEB_DH_SHLIBDEPS_ARGS_ALL=-X*

and removed from binary-arch section:
dh_shlibdeps

hope the .deb works, i've only installed in virtualbox.. there also some warning or errors during package building

```

$ debuild -i -us -uc -b 
dpkg-buildpackage -rfakeroot -D -us -uc -i -b
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package xserver-xorg-video-pvr
dpkg-buildpackage: source version 5.3.0-11.1~oneiric2
dpkg-buildpackage: source changed by tista <t.com>
 dpkg-source -i --before-build xserver-xorg-video-pvr
dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
test -x debian/rules
dh_testroot
dh_clean 
 debian/rules build
test -x debian/rules
mkdir -p "."
 fakeroot debian/rules binary
test -x debian/rules
mkdir -p "."
dh_testdir
dh_testroot
touch install-stamp
dh_testroot
dh_prep 
dh_installdirs -A 
Adding cdbs dependencies to debian/xserver-xorg-video-pvr.substvars
dh_installdirs -pxserver-xorg-video-pvr 
dh_installdocs -pxserver-xorg-video-pvr 
dh_installexamples -pxserver-xorg-video-pvr 
dh_installman -pxserver-xorg-video-pvr  
dh_installinfo -pxserver-xorg-video-pvr  
dh_installmenu -pxserver-xorg-video-pvr 
dh_installcron -pxserver-xorg-video-pvr 
dh_installinit -pxserver-xorg-video-pvr  
dh_installdebconf -pxserver-xorg-video-pvr 
dh_installemacsen -pxserver-xorg-video-pvr   
dh_installcatalogs -pxserver-xorg-video-pvr 
dh_installpam -pxserver-xorg-video-pvr 
dh_installlogrotate -pxserver-xorg-video-pvr 
dh_installlogcheck -pxserver-xorg-video-pvr 
dh_installchangelogs -pxserver-xorg-video-pvr  
dh_installudev -pxserver-xorg-video-pvr 
dh_lintian -pxserver-xorg-video-pvr 
dh_bugfiles -pxserver-xorg-video-pvr 
dh_install -pxserver-xorg-video-pvr  
dh_link -pxserver-xorg-video-pvr  
dh_installmime -pxserver-xorg-video-pvr 
dh_strip -pxserver-xorg-video-pvr  
dh_compress -pxserver-xorg-video-pvr  
dh_fixperms -pxserver-xorg-video-pvr  
dh_makeshlibs -pxserver-xorg-video-pvr  
dh_installdeb -pxserver-xorg-video-pvr 
dh_perl -pxserver-xorg-video-pvr 
dh_shlibdeps -pxserver-xorg-video-pvr   -X* 
dh_gencontrol -pxserver-xorg-video-pvr  
dpkg-gencontrol: warning: Depends field of package xserver-xorg-video-pvr: unknown substitution variable ${shlibs:Depends}
# only call dh_scour for packages in main
if grep -q '^Component:[[:space:]]*main' /CurrentlyBuilding 2>/dev/null; then dh_scour -pxserver-xorg-video-pvr ; fi
# symlink identical documentation to depending packages
[ -n "$CDBS_NO_DOC_SYMLINKING" ] || \
	[ -h debian/xserver-xorg-video-pvr/usr/share/doc ] || \
	[ -h debian/xserver-xorg-video-pvr/usr/share/doc/xserver-xorg-video-pvr ] || \
	[ ! -d debian/xserver-xorg-video-pvr/usr/share/doc ] || \
	myarch=$(sed -n -e's/^Architecture: *//p' debian/xserver-xorg-video-pvr/DEBIAN/control); \
	for dep in `perl -ne 'if (/^(Pre-)?Depends:/) {s/^\w+://; foreach (split /,/) { split; print($_[0], "\n"); } }' debian/xserver-xorg-video-pvr/DEBIAN/control`; do \
	    if [ -d debian/$dep/usr/share/doc ]; then \
	        thisarch=$(sed -n -e's/^Architecture: *//p' debian/$dep/DEBIAN/control 2>/dev/null); \
	        if [ "x$myarch" != "x$thisarch" ] && [ "x$thisarch" = xall ]; then \
	            continue; \
	        fi; \
	        if [ -L debian/xserver-xorg-video-pvr/usr/share/doc/xserver-xorg-video-pvr ]; then \
	            continue; \
	        fi; \
                echo "Searching for duplicated docs in dependency $dep..."; \
                rootdir=`pwd`; \
                (cd debian/xserver-xorg-video-pvr/usr/share/doc/xserver-xorg-video-pvr; find -type f ! -name copyright | while read f; do \
                    thisfile="$rootdir/debian/xserver-xorg-video-pvr/usr/share/doc/xserver-xorg-video-pvr/$f"; \
                    depfile="$rootdir/debian/$dep/usr/share/doc/$dep/$f"; \
                    if [ -f $depfile -o -L $depfile ] && zcmp $thisfile $depfile >/dev/null; then \
                        echo "  symlinking $f in xserver-xorg-video-pvr to file in $dep"; \
                        rm $thisfile; ln -s /usr/share/doc/$dep/$f $thisfile; \
                    fi; \
                done ); \
            fi; \
	done
# symlink identical Gnome help files within packages
if [ -z "$CDBS_NO_GNOME_HELP_SYMLINKING" ] && [ -d debian/xserver-xorg-video-pvr/usr/share/gnome/help ]; then \
            cd debian/xserver-xorg-video-pvr && LC_ALL=C fdupes -r1nq usr/share/gnome/help | while read s; do \
                set -- $(echo $s | tr ' ' '\n' | sort); \
                f=$1; shift; \
                for d; do \
                    echo "symlinking duplicate Gnome help file $d to $f"; \
                    rm $d; ln -s /$f $d; \
                done; \
            done; \
	fi
dh_link -p xserver-xorg-video-pvr
dh_md5sums -pxserver-xorg-video-pvr 
dh_builddeb -pxserver-xorg-video-pvr 
dpkg-deb: attenzione: "debian/xserver-xorg-video-pvr/DEBIAN/control" contiene il campo "Original-Maintainer" definito dall'utente
dpkg-deb: attenzione: 1 avviso relativo ai file di controllo viene ignorato

dpkg-deb: generazione del pacchetto "xserver-xorg-video-pvr" in "../xserver-xorg-video-pvr_5.3.0-11.1~oneiric2_i386.deb".
dh_testdir
dh_testroot
dh_installdirs
dh_installchangelogs
dh_installdocs
dh_installexamples
dh install --sourcedir=debian/tmp/ --fail-missing
   dh_installifupdown -O--sourcedir=debian/tmp/ -O--fail-missing
   dh_pysupport -O--sourcedir=debian/tmp/ -O--fail-missing
   dh_installmodules -O--sourcedir=debian/tmp/ -O--fail-missing
   dh_installppp -O--sourcedir=debian/tmp/ -O--fail-missing
   dh_installwm -O--sourcedir=debian/tmp/ -O--fail-missing
   dh_installxfonts -O--sourcedir=debian/tmp/ -O--fail-missing
   dh_installgsettings -O--sourcedir=debian/tmp/ -O--fail-missing
   dh_ucf -O--sourcedir=debian/tmp/ -O--fail-missing
   dh_gconf -O--sourcedir=debian/tmp/ -O--fail-missing
   dh_icons -O--sourcedir=debian/tmp/ -O--fail-missing
   dh_usrlocal -O--sourcedir=debian/tmp/ -O--fail-missing
dh_link
dh_strip
dh_compress
dh_fixperms
dh_makeshlibs
dh_installdeb
dh_gencontrol
dpkg-gencontrol: warning: Depends field of package xserver-xorg-video-pvr: unknown substitution variable ${shlibs:Depends}
dh_md5sums
dh_builddeb
dpkg-deb: attenzione: "debian/xserver-xorg-video-pvr/DEBIAN/control" contiene il campo "Original-Maintainer" definito dall'utente
dpkg-deb: attenzione: il file di configurazione "/etc/powervr.ini" è duplicato
dpkg-deb: attenzione: 2 avvisi relativi ai file di controllo vengono ignorati

dpkg-deb: generazione del pacchetto "xserver-xorg-video-pvr" in "../xserver-xorg-video-pvr_5.3.0-11.1~oneiric2_i386.deb".
 dpkg-genchanges -b >../xserver-xorg-video-pvr_5.3.0-11.1~oneiric2_i386.changes
dpkg-genchanges: warning: duplicate files list entry for file xserver-xorg-video-pvr_5.3.0-11.1~oneiric2_i386.deb (line 2)
dpkg-genchanges: binary-only upload - not including any source code
 dpkg-source -i --after-build xserver-xorg-video-pvr
dpkg-buildpackage: binary only upload (no source included)
Now running lintian...
E: xserver-xorg-video-pvr: duplicate-conffile etc/powervr.ini
E: xserver-xorg-video-pvr: helper-templates-in-copyright
W: xserver-xorg-video-pvr: maintainer-not-full-name tista
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/dri/pvr_dri.so /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/dri/pvr_dri.so /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libEGL.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libEGL.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libGLES_CM.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libGLES_CM.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libGLESv2.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libGLESv2.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libIMGegl.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libIMGegl.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libOpenVG.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libOpenVG.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libOpenVGU.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libOpenVGU.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libPVROGL.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libPVROGL.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libPVRScopeServices.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libPVRScopeServices.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libglslcompiler.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libglslcompiler.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libpvr2d.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libpvr2d.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libpvrPVR2D_BLITWSEGL.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libpvrPVR2D_BLITWSEGL.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libpvrPVR2D_DRIWSEGL.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libpvrPVR2D_DRIWSEGL.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libpvrPVR2D_FLIPWSEGL.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libpvrPVR2D_FLIPWSEGL.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libpvrPVR2D_LINUXFBWSEGL.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libpvrPVR2D_LINUXFBWSEGL.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libsrv_init.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libsrv_init.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libsrv_um.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libsrv_um.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libusc.so.1.1.16.4043 /usr/lib
E: xserver-xorg-video-pvr: binary-or-shlib-defines-rpath usr/lib/pvr/mrst/libusc.so.1.1.16.4043 /lib
E: xserver-xorg-video-pvr: missing-dependency-on-libc needed by usr/lib/pvr/mrst/dri/pvr_dri.so and 18 others
Finished running lintian.

```

Wooo!!

Nice Luca. :)

if remembered well, pvr backend services might need "wsbm" shlibs... but it includes only Meego, so we also might have to add pre-built binaries into xserver-xorg-video-pvr to solve shared libs dependencies... 

grazie.

**P.S**
I've found libswbm from SuSE... see attached tarball. ;)
and it's already built on Oneiric, so you could see prebuilt binaries in libswbm/src/.libs
should we make packaging it? or embed these binaries into xserver-xorg-video-pvr? I think it's better to embed it because ubuntu main repository might not have this package ever...

I gotta also include it to polish pvr driver up... ;)

**P.S #2**
OMG... pvr-bin binaries seem to need kernelspace named "pvrsrvkm"... :sad:
yeah that's old name of psb_gfx. today it names "psb" or so, unfortunately psb_gfx might not be success to run with it. damned.
so we have to salvage pvr-dkms from meego kernel. yep Alan had purged pvr compatibilities from his git tree... 

today I've uploaded xserver-xorg-video-pvr and pvr-va-driver on my PPA!! :)
[https://launchpad.net/~tista/+archive/psb-gfx-daily]("https://launchpad.net/~tista/+archive/psb-gfx-daily")
and now I'm working for pvr-dkms to be loaded as pvr kernelspace...

---

### Post by lucazade on 2011-07-17
> **tista said:**
> Wooo!!

Nice Luca. :)

if remembered well, pvr backend services might need "wsbm" shlibs... but it includes only Meego, so we also might have to add pre-built binaries into xserver-xorg-video-pvr to solve shared libs dependencies... 

grazie.

**P.S**
I've found libswbm from SuSE... see attached tarball. ;)
and it's already built on Oneiric, so you could see prebuilt binaries in libswbm/src/.libs
should we make packaging it? or embed these binaries into xserver-xorg-video-pvr? I think it's better to embed it because ubuntu main repository might not have this package ever...

I gotta also include it to polish pvr driver up... ;)

**P.S #2**
OMG... pvr-bin binaries seem to need kernelspace named "pvrsrvkm"... :sad:
yeah that's old name of psb_gfx. today it names "psb" or so, unfortunately psb_gfx might not be success to run with it. damned.
so we have to salvage pvr-dkms from meego kernel. yep Alan had purged pvr compatibilities from his git tree... 

today I've uploaded xserver-xorg-video-pvr and pvr-va-driver on my PPA!! :)
[https://launchpad.net/~tista/+archive/psb-gfx-daily]("https://launchpad.net/~tista/+archive/psb-gfx-daily")
and now I'm working for pvr-dkms to be loaded as pvr kernelspace...

OMG!
What an amazing work amico! It is really a mess but I'm confident you are close to put all the pieces together. 

When Alan opened the git tree he said he would removed hooks to binary libraries (which I think is what you are referring to when saying he purged pvr compatibilities).
But when some days ago he said both 2D/3D support with non free stuff I thought he would use those pvr-bin. So i'm a bit confused on this thing, you probably know it better looking at the code.

I hope these pvr-bin are compiled against xorg 1.10 otherwise we need some "backport" of 1.9 like it was in natty when using emgd.
I hope as well pciid are good inside pvr-bin/xserver-xorg-video-pvr otherwise we're out (anyone said hexeditor!??).

so the situation could be:
pvr-dkms/pvrsrvkm: kernel module, non KMS
pvr-bin/xserver-xorg-video-pvr: 2D exa, 3D opengl, firmware bits
pvr-va: vaapi HD videoplayback

(and psb_gfx and mrst_gfx cannot be used with these pvr stuff, correct me if wrong)

when the dream comes true...

---

### Post by tista on 2011-07-17
> **lucazade said:**
> OMG!
What an amazing work amico! It is really a mess but I'm confident you are close to put all the pieces together. 

Thanks. yeah I'm really excited!! :)

> When Alan opened the git tree he said he would removed hooks to binary libraries (which I think is what you are referring to when saying he purged pvr compatibilities).

that's correct.
the first trial had done with pvr hooks. so the name of drm driver was "pvrsrvkm".

> But when some days ago he said both 2D/3D support with non free stuff I thought he would use those pvr-bin. So i'm a bit confused on this thing, you probably know it better looking at the code.

Alan had opened mrst/medfield combo kernelspace exactly. but I suppose now these works are NOT completed. because this method would make an "anomaly" since these are based on the current psb_gfx's codes what improves GEM, KMS and some new technique. yep even though mrst/medfield didn't do yet. 

> I hope these pvr-bin are compiled against xorg 1.10 otherwise we need some "backport" of 1.9 like it was in natty when using emgd.
I hope as well pciid are good inside pvr-bin/xserver-xorg-video-pvr otherwise we're out (anyone said hexeditor!??).

Yeah I also hope that. so which the Meego 1.2 had employed xorg ver? I didn't check it out yet...

> so the situation could be:
pvr-dkms/pvrsrvkm: kernel module, non KMS
pvr-bin/xserver-xorg-video-pvr: 2D exa, 3D opengl, firmware bits
pvr-va: vaapi HD videoplayback

(and psb_gfx and mrst_gfx cannot be used with these pvr stuff, correct me if wrong)

that's perfect! exactly. but one thing. mrst_gfx has a name of drm kernelspace "pvrsrvkm". so the closest is now mrst-dkms to kick pvr-bin properly.  but as far as I know mrst_gfx didn't handle fb0 properly... :sad: yeah my friend said "it named vesafb" except "psbfb", "mrstfb" or so... I suppose Alan's work might cause it.

> when the dream comes true...

the last 4Q 2010, we might talk about this pvr driver on mega thread, at that time we didn't make any possibilities. 
but now we might get new PVR!! yeah exciting news are always come from Meego... :)

cheers.

---

### Post by tista on 2011-07-17
> **tista said:**
> Thanks. yeah I'm really excited!! :)



that's correct.
the first trial had done with pvr hooks. so the name of drm driver was "pvrsrvkm".



Alan had opened mrst/medfield combo kernelspace exactly. but I suppose now these works are NOT completed. because this method would make an "anomaly" since these are based on the current psb_gfx's codes what improves GEM, KMS and some new technique. yep even though mrst/medfield didn't do yet. 



Yeah I also hope that. so which the Meego 1.2 had employed xorg ver? I didn't check it out yet...



that's perfect! exactly. but one thing. mrst_gfx has a name of drm kernelspace "pvrsrvkm". so the closest is now mrst-dkms to kick pvr-bin properly.  but as far as I know mrst_gfx didn't handle fb0 properly... :sad: yeah my friend said "it named vesafb" except "psbfb", "mrstfb" or so... I suppose Alan's work might cause it.



the last 4Q 2010, we might talk about this pvr driver on mega thread, at that time we didn't make any possibilities. 
but now we might get new PVR!! yeah exciting news are always come from Meego... :)

cheers.

**ADD**
I've found these differences between ours(Alan released) and Meego:
[http://paste.ubuntu.com/645776/]("http://paste.ubuntu.com/645776/")

OK. Let's dive into patchworks!! :)

ciao.

**P.S:**
today I've bought used VAIO P again!! :P
and now I'm reverting psb_gfx to very early stage and it shows that:
[http://paste.ubuntu.com/645857/]("http://paste.ubuntu.com/645857/")

..damned. :sad:

I think the key is **"(EE) Couldn't get PVR Services status"**. so Meego might have some daemon or so to start PVR backends?? well I also should search this error on googling...

---

### Post by lucazade on 2011-07-17
> **tista said:**
> **ADD**
I've found these differences between ours(Alan released) and Meego:
[http://paste.ubuntu.com/645776/]("http://paste.ubuntu.com/645776/")

OK. Let's dive into patchworks!! :)

ciao.

**P.S:**
today I've bought used VAIO P again!! :P
and now I'm reverting psb_gfx to very early stage and it shows that:
[http://paste.ubuntu.com/645857/]("http://paste.ubuntu.com/645857/")

..damned. :sad:

I think the key is **"(EE) Couldn't get PVR Services status"**. so Meego might have some daemon or so to start PVR backends?? well I also should search this error on googling...

Dunno, I'll search as well.

---

### Post by tista on 2011-07-17
> **lucazade said:**
> Dunno, I'll search as well.

I've found this init script and modded:
[http://paste.ubuntu.com/645920/]("http://paste.ubuntu.com/645920/")

but principal last part of it, binary named pvrsrvinit_r$SGX_CORE_REV is now not working on psb_gfx/mrst_gfx.... damned... :sad:

because I've never seen /proc/pvr/* directory. how do that?? or may I install Meego 1.2.80 testing release?

getting greeeen like hulk... grrrrrrrrr

ciao.

---

### Post by lucazade on 2011-07-17
never seen this kind of script.. ugly..
yep, maybe from meego we can track down this /proc/pvr and generally how pvr works.
Meego IVI ships EMGD so no good.. maybe the UX version + manual install of pvr from non-oss repo.

---

### Post by tista on 2011-07-20
Hi guys.

did you see git tree updated already?
[http://git.kernel.org/?p=linux/kernel/git/sfr/linux-next.git;a=history;f=drivers/staging/gma500;hb=HEAD]("http://git.kernel.org/?p=linux/kernel/git/sfr/linux-next.git;a=history;f=drivers/staging/gma500;hb=HEAD")

it seems to fix mouse pointer flickering... how about that? or Luca had synced it into offcial PPA? :)

ciao.

---

### Post by lucazade on 2011-07-20
> **tista said:**
> Hi guys.

did you see git tree updated already?
[http://git.kernel.org/?p=linux/kernel/git/sfr/linux-next.git;a=history;f=drivers/staging/gma500;hb=HEAD]("http://git.kernel.org/?p=linux/kernel/git/sfr/linux-next.git;a=history;f=drivers/staging/gma500;hb=HEAD")

it seems to fix mouse pointer flickering... how about that? or Luca had synced it into offcial PPA? :)

ciao.

Hey Tista

PPA is not updated yet.. 
I thought the tree still lacks all this 15 patches:
[https://lkml.org/lkml/2011/7/15/236](https://lkml.org/lkml/2011/7/15/236)

correct?

---

### Post by tista on 2011-07-20
> **lucazade said:**
> Hey Tista

PPA is not updated yet.. 
I thought the tree still lacks all this 15 patches:
[https://lkml.org/lkml/2011/7/15/236](https://lkml.org/lkml/2011/7/15/236)

correct?

I suppose current tree were "patched".... ?? yeah using these patches posted lkml...
and it's around the time to final polish of psb_gfx.

and then I'm willing to salvage some stuff from SGX SDK... yep shlibs, init scripts, and development headers whatever we're needing.. and soon I would refresh PPA!! :)

EDIT:

OK. I've found the original init script for pvr services on OMAP:
[http://paste.ubuntu.com/648141/]("http://paste.ubuntu.com/648141/")

---

### Post by lucazade on 2011-07-20
> **tista said:**
> I suppose current tree were "patched".... ?? yeah using these patches posted lkml...
and it's around the time to final polish of psb_gfx.

and then I'm willing to salvage some stuff from SGX SDK... yep shlibs, init scripts, and development headers whatever we're needing.. and soon I would refresh PPA!! :)

EDIT:

OK. I've found the original init script for pvr services on OMAP:
[http://paste.ubuntu.com/648141/]("http://paste.ubuntu.com/648141/")

You're right patches are already applied to tree, I didn't notice.
Today landed also dependecies and vblank fixes.

Great find about pvr service script. If you are on init I'll wait for your ppa update.

EDIT: updated ppa with latest changes from tree but pointer issue is still here.
for the rest everything look the same.

---

### Post by tista on 2011-07-28
Hi guys. ;)

Just now I'm uploading latest xserver-xorg-video-pvr...
[https://launchpad.net/~tista/+archive/psb-gfx-daily]("https://launchpad.net/~tista/+archive/psb-gfx-daily")
current is named xserver-xorg-video-pvr_5.3.0-11.1~oneiric7. ASAP build would finish on Launchpad!!

yeah I've polished some init scripts and fixed some installation paths. so tonight I would run it on my VAIO P to test it! ;) if other guys might give it a try before my trials, please let me know how the results.

cheers.

---

### Post by lucazade on 2011-07-28
> **tista said:**
> Hi guys. ;)

Just now I'm uploading latest xserver-xorg-video-pvr...
[https://launchpad.net/~tista/+archive/psb-gfx-daily]("https://launchpad.net/~tista/+archive/psb-gfx-daily")
current is named xserver-xorg-video-pvr_5.3.0-11.1~oneiric7. ASAP build would finish on Launchpad!!

yeah I've polished some init scripts and fixed some installation paths. so tonight I would run it on my VAIO P to test it! ;) if other guys might give it a try before my trials, please let me know how the results.

cheers.

Hi tista!
Going to try it on my netbook, I'll see what will happen and report here experience.
Thanks for sharing it :)

---

### Post by tista on 2011-07-28
> **lucazade said:**
> Hi tista!
Going to try it on my netbook, I'll see what will happen and report here experience.
Thanks for sharing it :)

Ciao Luca.

oh forgot to mention... it might need Xorg 1.9 or so maybe... :sad: so we could use such packages via emgd repos. yeah "downgrading" is needed...
then you go!! :)

ciao.

---

### Post by lucazade on 2011-07-28
> **tista said:**
> Ciao Luca.

oh forgot to mention... it might need Xorg 1.9 or so maybe... :sad: so we could use such packages via emgd repos. yeah "downgrading" is needed...
then you go!! :)

ciao.

good to know, I'll try also with xorg 1.9
crossing fingers.

---

### Post by tista on 2011-07-28
> **lucazade said:**
> good to know, I'll try also with xorg 1.9
crossing fingers.

@Luca

...damned. it didn't work still.... :sad:
and I've noticed and forgot at all. yeah Alan has mrst platform driver in MID kernel. so we might need it, too. because init script named "pvr-bin" seems to check platform driver....

OK.. never ending story had begun? ;)
yep, I would try to make mrst platform driver as dkms from now!!

cheers.

---

### Post by lucazade on 2011-07-28
> **tista said:**
> @Luca

...damned. it didn't work still.... :sad:
and I've noticed and forgot at all. yeah Alan has mrst platform driver in MID kernel. so we might need it, too. because init script named "pvr-bin" seems to check platform driver....

OK.. never ending story had begun? ;)
yep, I would try to make mrst platform driver as dkms from now!!

cheers.

I was trying it right now.
I've installed xserver-xorg-video-pvr, xorg 1.9 from emgd-fix ppa (with 1.10 there was a version mismatch and forgot to try ignoreabi), and mrst-dkms (hoping this could provide pvrsrvkm module to kick X).

this is what I get at the moment:
```
[  1008.502] 
X.Org X Server 1.9.2.901 (1.9.3 RC 1)
Release Date: 2010-11-13
[  1008.502] X Protocol Version 11, Revision 0
[  1008.503] Build Operating System: Linux 2.6.24-28-xen i686 Ubuntu
[  1008.503] Current Operating System: Linux ao751h 3.0.0-7-generic #8-Ubuntu SMP Fri Jul 22 20:24:22 UTC 2011 i686
[  1008.503] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-7-generic root=UUID=b51999e8-641f-453a-9ef0-8b69851cf059 ro quiet splash
[  1008.503] Build Date: 02 May 2011  11:16:09AM
[  1008.504] xorg-server 3:1.10.9-down1.9.2.901.2+git20101129+server-1.9-branch.65f2ab20-0ubuntu0sarvatt2~natty (For technical support please see http://www.ubuntu.com/support) 
[  1008.504] Current version of pixman: 0.22.2
[  1008.504] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[  1008.505] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  1008.506] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jul 28 15:57:40 2011
[  1008.507] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  1008.508] (==) No Layout section.  Using the first Screen section.
[  1008.508] (==) No screen section available. Using defaults.
[  1008.508] (**) |-->Screen "Default Screen Section" (0)
[  1008.508] (**) |   |-->Monitor "<default monitor>"
[  1008.509] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[  1008.509] (**) |   |-->Device "Card0"
[  1008.509] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[  1008.509] (==) Automatically adding devices
[  1008.509] (==) Automatically enabling devices
[  1008.509] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  1008.509] 	Entry deleted from font path.
[  1008.509] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  1008.509] 	Entry deleted from font path.
[  1008.509] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  1008.509] 	Entry deleted from font path.
[  1008.509] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  1008.510] 	Entry deleted from font path.
[  1008.510] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  1008.510] 	Entry deleted from font path.
[  1008.510] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  1008.510] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  1008.510] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[  1008.510] (II) Loader magic: 0x81f9960
[  1008.510] (II) Module ABI versions:
[  1008.510] 	X.Org ANSI C Emulation: 0.4
[  1008.510] 	X.Org Video Driver: 8.0
[  1008.510] 	X.Org XInput driver : 11.0
[  1008.510] 	X.Org Server Extension : 4.0
[  1008.512] (--) PCI:*(0:0:2:0) 8086:8108:1025:0244 rev 7, Mem @ 0xb0080000/524288, 0xc0000000/268435456, 0xb0000000/262144, I/O @ 0x00001800/8
[  1008.512] (II) Open ACPI successful (/var/run/acpid.socket)
[  1008.512] (II) LoadModule: "extmod"
[  1008.514] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  1008.514] (II) Module extmod: vendor="X.Org Foundation"
[  1008.514] 	compiled for 1.9.2.901, module version = 1.0.0
[  1008.514] 	Module class: X.Org Server Extension
[  1008.514] 	ABI class: X.Org Server Extension, version 4.0
[  1008.514] (II) Loading extension MIT-SCREEN-SAVER
[  1008.514] (II) Loading extension XFree86-VidModeExtension
[  1008.514] (II) Loading extension XFree86-DGA
[  1008.514] (II) Loading extension DPMS
[  1008.515] (II) Loading extension XVideo
[  1008.515] (II) Loading extension XVideo-MotionCompensation
[  1008.515] (II) Loading extension X-Resource
[  1008.515] (II) LoadModule: "dbe"
[  1008.515] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  1008.516] (II) Module dbe: vendor="X.Org Foundation"
[  1008.516] 	compiled for 1.9.2.901, module version = 1.0.0
[  1008.516] 	Module class: X.Org Server Extension
[  1008.516] 	ABI class: X.Org Server Extension, version 4.0
[  1008.516] (II) Loading extension DOUBLE-BUFFER
[  1008.516] (II) LoadModule: "glx"
[  1008.517] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  1008.517] (II) Module glx: vendor="X.Org Foundation"
[  1008.517] 	compiled for 1.9.2.901, module version = 1.0.0
[  1008.517] 	ABI class: X.Org Server Extension, version 4.0
[  1008.517] (==) AIGLX enabled
[  1008.518] (II) Loading extension GLX
[  1008.518] (II) LoadModule: "record"
[  1008.518] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  1008.519] (II) Module record: vendor="X.Org Foundation"
[  1008.519] 	compiled for 1.9.2.901, module version = 1.13.0
[  1008.519] 	Module class: X.Org Server Extension
[  1008.519] 	ABI class: X.Org Server Extension, version 4.0
[  1008.519] (II) Loading extension RECORD
[  1008.519] (II) LoadModule: "dri"
[  1008.520] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  1008.520] (II) Module dri: vendor="X.Org Foundation"
[  1008.520] 	compiled for 1.9.2.901, module version = 1.0.0
[  1008.520] 	ABI class: X.Org Server Extension, version 4.0
[  1008.521] (II) Loading extension XFree86-DRI
[  1008.521] (II) LoadModule: "dri2"
[  1008.521] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  1008.522] (II) Module dri2: vendor="X.Org Foundation"
[  1008.522] 	compiled for 1.9.2.901, module version = 1.2.0
[  1008.522] 	ABI class: X.Org Server Extension, version 4.0
[  1008.522] (II) Loading extension DRI2
[  1008.522] (II) LoadModule: "pvr"
[  1008.522] (II) Loading /usr/lib/xorg/modules/drivers/pvr_drv.so
[  1008.523] (II) Module PVR: vendor="X.Org Foundation"
[  1008.524] 	compiled for 1.9.0, module version = 1.6.4043
[  1008.524] 	Module class: X.Org Video Driver
[  1008.524] 	ABI class: X.Org Video Driver, version 8.0
[  1008.524] (II) pvr: Driver for PowerVR chipsets: PowerVR SGX
[  1008.524] (--) using VT number 7

[  1008.528] drmOpenDevice: node name is /dev/dri/card0
[  1008.548] [drm] failed to load kernel module "pvrsrvkm"
[  1008.549] (EE) Couldn't get PVR Services status
[  1008.549] (WW) Falling back to old probe method for pvr
[  1008.549] (EE) No devices detected.
[  1008.549] 
Fatal server error:
[  1008.549] no screens found
[  1008.549] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[  1008.549] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  1008.549] 
```

---

### Post by lucazade on 2011-07-28
in the meantime I tried emgd in oneriric with xorg 1.9.. it works and also unity-3d can start  but with some artefacts :D :D :D

```
luca@ao751h:~$ glxgears 
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
1187 frames in 5.0 seconds = 237.320 FPS
1274 frames in 5.0 seconds = 254.647 FPS
1298 frames in 5.0 seconds = 259.545 FPS
1302 frames in 5.0 seconds = 260.363 FPS
1300 frames in 5.0 seconds = 259.757 FPS
^C


luca@ao751h:~$ glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_multithread_makecurrent, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap, 
    GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
OpenGL vendor string: Intel Corporation
OpenGL renderer string: EMGD on PowerVR SGX535
OpenGL version string: 2.1
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_matrix_palette, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shader_objects, GL_ARB_shading_language_100, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_NV_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_blend, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_IMG_texture_compression_pvrtc, GL_NV_blend_square, 
    GL_NV_texgen_reflection, GL_S3_s3tc, GL_SGIS_generate_mipmap

24 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x05d 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x05e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x05f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x060 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x061 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x062 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x063 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x064 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x065 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x066 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x067 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x068 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x069 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x06b 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x06c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x06d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x06e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x06f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x070 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x071 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x044 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None

24 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x045 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x046 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x047 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x048 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x049 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x04a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x04b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x04c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x04d 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x04e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x04f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x050 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x051 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x052 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x053 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x054 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x055 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x056 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x057 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x058 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x059 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x05a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x05b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x05c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None



luca@ao751h:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Intel Corporation
OpenGL renderer string: EMGD on PowerVR SGX535
OpenGL version string:  2.1

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes



luca@ao751h:~$ vainfo 
libva: libva version 0.32.0
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/emgd_drv_video.so
Intel(R) Embedded Media and Graphics Driver 1.6 Build 1952
Using XCB based dispatch table.
libva: va_openDriver() returns 0
vainfo: VA API version: 0.32
vainfo: Driver version: Intel(R) Embedded Media and Graphics Driver 1.6 Build 1952
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Main              :	VAEntrypointVLD
      VAProfileMPEG4Simple            :	VAEntrypointVLD
      VAProfileMPEG4AdvancedSimple    :	VAEntrypointVLD
      VAProfileH264Baseline           :	VAEntrypointVLD
      VAProfileH264Main               :	VAEntrypointVLD
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Simple              :	VAEntrypointVLD
      VAProfileVC1Simple              :	VAEntrypointMoComp
      VAProfileVC1Main                :	VAEntrypointVLD
      VAProfileVC1Main                :	VAEntrypointMoComp
      VAProfileVC1Advanced            :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointMoComp
```

gtkperf obviously is still slow, but unity-2d is faster than using only psb_gfx

---

### Post by tista on 2011-07-28
> **lucazade said:**
> in the meantime I tried emgd in oneriric with xorg 1.9.. it works and also unity-3d can start  but with some artefacts :D :D :D

```
luca@ao751h:~$ glxgears 
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
1187 frames in 5.0 seconds = 237.320 FPS
1274 frames in 5.0 seconds = 254.647 FPS
1298 frames in 5.0 seconds = 259.545 FPS
1302 frames in 5.0 seconds = 260.363 FPS
1300 frames in 5.0 seconds = 259.757 FPS
^C


luca@ao751h:~$ glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_multithread_makecurrent, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap, 
    GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
OpenGL vendor string: Intel Corporation
OpenGL renderer string: EMGD on PowerVR SGX535
OpenGL version string: 2.1
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_matrix_palette, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shader_objects, GL_ARB_shading_language_100, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_NV_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_blend, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_IMG_texture_compression_pvrtc, GL_NV_blend_square, 
    GL_NV_texgen_reflection, GL_S3_s3tc, GL_SGIS_generate_mipmap

24 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x05d 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x05e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x05f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x060 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x061 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x062 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x063 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x064 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x065 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x066 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x067 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x068 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x069 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x06b 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x06c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x06d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x06e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x06f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x070 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x071 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x044 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None

24 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x045 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x046 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x047 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x048 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x049 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x04a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x04b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x04c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x04d 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x04e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x04f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x050 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x051 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x052 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x053 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x054 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x055 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x056 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x057 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x058 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x059 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x05a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x05b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x05c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None



luca@ao751h:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Intel Corporation
OpenGL renderer string: EMGD on PowerVR SGX535
OpenGL version string:  2.1

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes



luca@ao751h:~$ vainfo 
libva: libva version 0.32.0
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/emgd_drv_video.so
Intel(R) Embedded Media and Graphics Driver 1.6 Build 1952
Using XCB based dispatch table.
libva: va_openDriver() returns 0
vainfo: VA API version: 0.32
vainfo: Driver version: Intel(R) Embedded Media and Graphics Driver 1.6 Build 1952
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Main              :	VAEntrypointVLD
      VAProfileMPEG4Simple            :	VAEntrypointVLD
      VAProfileMPEG4AdvancedSimple    :	VAEntrypointVLD
      VAProfileH264Baseline           :	VAEntrypointVLD
      VAProfileH264Main               :	VAEntrypointVLD
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Simple              :	VAEntrypointVLD
      VAProfileVC1Simple              :	VAEntrypointMoComp
      VAProfileVC1Main                :	VAEntrypointVLD
      VAProfileVC1Main                :	VAEntrypointMoComp
      VAProfileVC1Advanced            :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointMoComp
```

gtkperf obviously is still slow, but unity-2d is faster than using only psb_gfx

Wow!! nice trial!! :)
now I'm fighting against mrst platform driver... yeah already failed to build 30 times over... grrrrrr

today would be an unlucky day for me!! ;)
so if I couldn't, I have to make ubuntu patched MID kernel on my PPA?!
...OMG XD it's the biggest work than ubuntu kernel team, right? :P

ciao.

---

### Post by lucazade on 2011-07-28
> **tista said:**
> Wow!! nice trial!! :)
now I'm fighting against mrst platform driver... yeah already failed to build 30 times over... grrrrrr

today would be an unlucky day for me!! ;)
so if I couldn't, I have to make ubuntu patched MID kernel on my PPA?!
...OMG XD it's the biggest work than ubuntu kernel team, right? :P

ciao.

wish you good luck, for sure not an easy road.
i'm ready to test anything you'll cook for us ;)

ciao!

---

### Post by lucazade on 2011-07-28
New EMGD release

Version: 1.8	Release date: July 2011	File Size: 70MB - 98MB
[http://edc.intel.com/Software/Downloads/EMGD/](http://edc.intel.com/Software/Downloads/EMGD/)

Also a new Meego IVI release 1.2.0.1 with emgd on board.
[http://wiki.meego.com/index.php?title=Quality/IVI_1.2_Update&oldid=44617](http://wiki.meego.com/index.php?title=Quality/IVI_1.2_Update&oldid=44617)
[https://meego.com/downloads/releases/updates/meego-v1.2.0.1-ivi-update](https://meego.com/downloads/releases/updates/meego-v1.2.0.1-ivi-update)

going to update packages in ppa

---

### Post by lucazade on 2011-07-28
nv..

---

### Post by lucazade on 2011-07-29
[B]Updated EMGD PPA up to 1.8-2032 version for Oneiric and Natty
[/B][https://launchpad.net/~gma500/+archive/emgd-1.8](https://launchpad.net/~gma500/+archive/emgd-1.8)


Applied patch for kernels 2.6.39/3.0.x (Oneiric only)
Backported a function in osfunc.c (Oneiric only)
Fixed some includes .h


Doing some tests at the moment, seems a bit faster. 2D/3D/vaapi are ok.
probably libva and mplayer vaapi needs an update, 
flashplayer with hw accel should be tested (there is a specs doc inside driver megapackage)
also emgdui config tool and emgdbl should be tested.

;)

---

### Post by lucazade on 2011-07-30
I was trying Hardware Accelerated Adobe Flash 10.1/10.2 for Linux onEmbedded Devices (gma500)
[http://edc.intel.com/Link.aspx?id=5291](http://edc.intel.com/Link.aspx?id=5291)

I've downloaded modded libflashplayer.so from:
[https://registrationcenter.intel.com/RegCenter/AutoGen.aspx?ProductID=1618&AccountID=&EmailID=&ProgramID=&RequestDt=&rm=COM&lang=](https://registrationcenter.intel.com/RegCenter/AutoGen.aspx?ProductID=1618&AccountID=&EmailID=&ProgramID=&RequestDt=&rm=COM&lang=)

copied the library in /usr/lib/chromium-browser/plugins and/or in firefox plugins dir
but both browsers crashes at launching.
Probably because I'm using different version of Chromium and Firefox, dunno :S

This is a part of the FAQ:
> Question 2: Which operating systems are supported?
Answer: MeeGo 1.2 IVI and Fedora 14 (Timesys)

Question 3: Which web browsers are supported?
Answer: Chromium* 11.0 for MeeGo 1.2 and Firefox* 3.6.x for Fedora 14.

Question 4: Which graphics drivers are supported?
Answer: Intel® Embedded Media and Graphics Driver (Intel® EMGD) v1.8


If anyone want to try.. let me know if it works for you.

---

### Post by fjgaude on 2011-07-30
> If anyone wants to try.. let me know if it works for you.


I install OO on my Dell mini 10n next Thursday, Alpha3, and let you know how it goes.

Thanks once again for keeping the flame alive.

---

### Post by lucazade on 2011-07-30
> **fjgaude said:**
> I install OO on my Dell mini 10n next Thursday, Alpha3, and let you know how it goes.

Thanks once again for keeping the flame alive.

[CENTER]*Gma500 Olympic Torch is still alive* :)

[IMG]http://i.imgur.com/0RORJ.jpg[/IMG] [/CENTER]

---

### Post by lucazade on 2011-08-01
Unity3D has some visual glitches using an Intel GMA500 gfx card and Intel EMGD drivers.
Unity interface (panel, launcher and dash) seems to use a wrong resolution and everything is badly scaled.

please guys, add "affect to me" / subscribe to the report 
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/818778](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/818778)

---

### Post by fjgaude on 2011-08-01
> **lucazade said:**
> Unity3D has some visual glitches using an Intel GMA500 gfx card and Intel EMGD drivers.
Unity interface (panel, launcher and dash) seems to use a wrong resolution and everything is badly scaled.

please guys, add "affect to me" / subscribe to the report 
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/818778](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/818778)

What is the resolution of your monitor... your attachment didn't look far off, but the panel was bad, bad.

---

### Post by lucazade on 2011-08-01
> **fjgaude said:**
> What is the resolution of your monitor... your attachment didn't look far off, but the panel was bad, bad.

the resolution is wrong only in the panel/launcher/dash, the rest of the desktop uses the correct resolution (1366x768 ).
speaking about resolution could confuse a bit.. in reality the unity stuff are painted wrongly and badly scaled.

---

### Post by fjgaude on 2011-08-01
Okay, and thanks for the explanation... have subscribed and will get it a try this coming Thursday, Alpha3 install.

---

### Post by lucazade on 2011-08-01
> **fjgaude said:**
> Okay, and thanks for the explanation... have subscribed and will get it a try this coming Thursday, Alpha3 install.

If you have a better and saner way to explain this in english I'll update bug description, unfortunately is not a common issue and quite difficult to express it!

---

### Post by fjgaude on 2011-08-01
> **lucazade said:**
> If you have a better and saner way to explain this in english I'll update bug description, unfortunately is not a common issue and quite difficult to express it!

Your English is as good as any native speaker. I don't think I can do any better: The screen resolution is labeled wrongly, but the desktop shows correctly, only the Unity aspect is crafted wrong with unstable rendering of the images and typefaces.

---

### Post by tista on 2011-08-02
Guys.

I've uploaded the initial prototype mrst platform driver as dkms!!:
[https://launchpad.net/~tista/+archive/psb-gfx-daily]("https://launchpad.net/~tista/+archive/psb-gfx-daily")

tonight I would give it a try on local machine... this module had been salvaged from Alan's git tree, but it has the trick!! yep, he used some minor init function as "multiple init" in 1 platform source... OMG... so the default were never succeeded to build against oneiric kernel. :sad: however I didn't have any choice to keep 2 inits alive, so I had purged one of them...

finally, because this driver is now very experimental stuff, please be carefully to deal with it... ;)

Ciao!

P.S
I spoke more horrible English! :P

---

### Post by lucazade on 2011-08-02
> **tista said:**
> Guys.

I've uploaded the initial prototype mrst platform driver as dkms!!:
[https://launchpad.net/~tista/+archive/psb-gfx-daily]("https://launchpad.net/~tista/+archive/psb-gfx-daily")

tonight I would give it a try on local machine... this module had been salvaged from Alan's git tree, but it has the trick!! yep, he used some minor init function as "multiple init" in 1 platform source... OMG... so the default were never succeeded to build against oneiric kernel. :sad: however I didn't have any choice to keep 2 inits alive, so I had purged one of them...

finally, because this driver is now very experimental stuff, please be carefully to deal with it... ;)

Ciao!

P.S
I spoke more horrible English! :P

LOL
I'll give it a look... hope nothing will explode ;)

Yep, our English should look really elementary for a native speaker.. but at the end we can communicate!
Unfortunately I can't gesticulate, like every italians usually do, when writing in forum.
[http://www.youtube.com/watch?v=9JhuOicPFZY](http://www.youtube.com/watch?v=9JhuOicPFZY)
:)

---

### Post by lucazade on 2011-08-02
@Tista

tried mrst-platform but dkms building fails
```
DKMS make.log for mrst-platform-0.1alpha1~oneiric3 for kernel 3.0.0-7-generic (i686)
mar  2 ago 2011, 13.17.43, CEST
make -C /lib/modules/3.0.0-7-generic/build SUBDIRS=/var/lib/dkms/mrst-platform/0.1alpha1~oneiric3/build modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-7-generic'
  CC [M]  /var/lib/dkms/mrst-platform/0.1alpha1~oneiric3/build/mrst.o
/var/lib/dkms/mrst-platform/0.1alpha1~oneiric3/build/mrst.c:295:13: error: redefinition of ‘x86_mrst_early_setup’
/usr/src/linux-headers-3.0.0-7-generic/arch/x86/include/asm/setup.h:53:20: note: previous definition of ‘x86_mrst_early_setup’ was here
/var/lib/dkms/mrst-platform/0.1alpha1~oneiric3/build/mrst.c:1599:19: warning: ‘mrst_platform_init’ defined but not used [-Wunused-function]
make[2]: *** [/var/lib/dkms/mrst-platform/0.1alpha1~oneiric3/build/mrst.o] Error 1
make[1]: *** [_module_/var/lib/dkms/mrst-platform/0.1alpha1~oneiric3/build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-7-generic'
make: *** [default] Error 2
```

just to understand situation better: are these the modules included in meego kernel?

so, when it will build, we need mrst-platform + mrst-dkms or new psb_gfx with mrst inside + xserver-xorg-video-pvr to get it working?

where is pvrsrvkm module?

what the hell is pvr-va-driver?

too much questions in a row, I know, but following all these things it is a giant effort (and I could immagine your huge effort).. at least I can follow your development more closely.

Konnichiwa :)

---

### Post by tista on 2011-08-02
> **lucazade said:**
> @Tista

tried mrst-platform but dkms building fails
```
DKMS make.log for mrst-platform-0.1alpha1~oneiric3 for kernel 3.0.0-7-generic (i686)
mar  2 ago 2011, 13.17.43, CEST
make -C /lib/modules/3.0.0-7-generic/build SUBDIRS=/var/lib/dkms/mrst-platform/0.1alpha1~oneiric3/build modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-7-generic'
  CC [M]  /var/lib/dkms/mrst-platform/0.1alpha1~oneiric3/build/mrst.o
/var/lib/dkms/mrst-platform/0.1alpha1~oneiric3/build/mrst.c:295:13: error: redefinition of ‘x86_mrst_early_setup’
/usr/src/linux-headers-3.0.0-7-generic/arch/x86/include/asm/setup.h:53:20: note: previous definition of ‘x86_mrst_early_setup’ was here
/var/lib/dkms/mrst-platform/0.1alpha1~oneiric3/build/mrst.c:1599:19: warning: ‘mrst_platform_init’ defined but not used [-Wunused-function]
make[2]: *** [/var/lib/dkms/mrst-platform/0.1alpha1~oneiric3/build/mrst.o] Error 1
make[1]: *** [_module_/var/lib/dkms/mrst-platform/0.1alpha1~oneiric3/build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-7-generic'
make: *** [default] Error 2
```

just to understand situation better: are these the modules included in meego kernel?

so, when it will build, we need mrst-platform + mrst-dkms or new psb_gfx with mrst inside + xserver-xorg-video-pvr to get it working?

where is pvrsrvkm module?

what the hell is pvr-va-driver?

too much questions in a row, I know, but following all these things it is a giant effort (and I could immagine your huge effort).. at least I can follow your development more closely.

Konnichiwa :)

Hi Luca. ;)

yeah I've experienced some build error, so tomorrow I would polish it more and more...

and OK. let's explain for that. :-)

first, my modules are almost inspired from Meego, you're right. but in this method, we had some problems.
1. Meego is still stack with "old-fashion" resources. yeah for example, Meego UX kernel is under .37?! could you believe that! and Xorg are 1.9... that's speechless...
2. Meego are designed something like "embedded linux". yep, specialized kernel, specialized xorg driver, and minimum packaging design. so it has various remix, UX, IVI, nebook, mobile phone, and more.
3. most re-usable remix seems UX for us I think. IVI is keeping EMGD, so it's never be exciting us all, you know.
4. Moorestown and Medfield would be the next target of Meego today. NOT only poulsbo. but mrst/mdfld is quite different platform compared with poulsbo. so these need some external platform driver I suppose. and already you knew, these would be running with SGX540 or higher version.
5. however today we have psb_gfx, but Alan seems to purge almost sgx stuff from it. I think he might scratch new xorg driver based on Intel i9xx driver family... otherwise, mrst/mdfld are still keeping pipes to sgx because Meego would keep these drivers alive on their distributions. then Alan had forked these kernel module into his git tree, and applied a lot of patches to be built against 3.0 or higher kernel as "linux-next" development. I also used Alan's one instead of Meego's one because actually Meego  is ugly old.
6. pvrsrvkm module could be defined softly "mrst/mdfld" today. but don't forget the early psb_gfx, too. so I usually take that early gfx to check xorg driver testing... I think in past Meego used such gfx as "pvr kernel module" on gma500.  but today, Meego is no more supported poulsbo xorg-driver using pvr, after mrst/mdfld are appeared on our sights. at least EMGD has only approved poulsbo.
7. pvr-va-driver is the video driver and firmware as well. I think it didn't so matter when we try to run as graphic display driver. and it strongly was binary crapped.

and then my TODO are something like below:
* wait until Alan or someone released xorg driver running with current psb_gfx.
* scratch omap-fbdev driver to get compatibilities with psb_gfx.
* analyze and study uncleared pvr services to run on Ubuntu
* fix dkms and follow the latest kernel

umm... that's all. :)

ciao.

---

### Post by lucazade on 2011-08-02
Tista

well, well.. thanks for such all-comprehensive and articulated answer.
Now it is clear, or better is clear you know what you are doing ;)

Yep, it is a pity that Meego always employs old tech and it is a pity as well that 
Linux Foundation supports Meego but doesn't do anything for the binary drivers included in this distro.

let me know when you need help or test..

C U in the next episode of this endless soap-opera!

---

### Post by lucazade on 2011-08-05
@Tista

I'm trying to fix emgdbl kernel module for brightness hotkeys control in Oneiric.

Installing this module without any changes from Natty version I get this
```

[ 1485.660175] ------------[ cut here ]------------
[ 1485.660207] WARNING: at /build/buildd/linux-3.0.0/drivers/video/backlight/backlight.c:314 backlight_device_register+0x193/0x1c0()
[ 1485.660220] Hardware name: AO751h           
[ 1485.660228] emgd_psb: invalid backlight type
[ 1485.660235] Modules linked in: emgdbl(+) cryptd aes_i586 aes_generic rfcomm bnep emgd drm_kms_helper drm parport_pc ppdev binfmt_misc vesafb snd_hda_codec_realtek joydev snd_hda_intel snd_hda_codec snd_hwdep snd_pcm uvcvideo videodev snd_seq_midi i2c_isch sch_gpio btusb snd_rawmidi arc4 psmouse serio_raw bluetooth snd_seq_midi_event lpc_sch snd_seq ath5k ath mac80211 cfg80211 snd_timer snd_seq_device snd soundcore snd_page_alloc poulsbo wmi video lp parport pata_sch r8169
[ 1485.660386] Pid: 5512, comm: modprobe Not tainted 3.0.0-7-generic #8-Ubuntu
[ 1485.660395] Call Trace:
[ 1485.660416]  [<c1047832>] warn_slowpath_common+0x72/0xa0
[ 1485.660432]  [<c12c72f3>] ? backlight_device_register+0x193/0x1c0
[ 1485.660448]  [<c12c72f3>] ? backlight_device_register+0x193/0x1c0
[ 1485.660463]  [<c1047903>] warn_slowpath_fmt+0x33/0x40
[ 1485.660479]  [<c12c72f3>] backlight_device_register+0x193/0x1c0
[ 1485.660499]  [<f98fe15a>] emgdbl_probe+0x6a/0xac [emgdbl]
[ 1485.660517]  [<c133c951>] platform_drv_probe+0x11/0x20
[ 1485.660531]  [<c133b4ed>] really_probe+0x4d/0x150
[ 1485.660546]  [<c1343959>] ? pm_runtime_barrier+0x49/0xb0
[ 1485.660561]  [<c133b72a>] driver_probe_device+0x3a/0x60
[ 1485.660575]  [<c133b831>] __device_attach+0x41/0x50
[ 1485.660589]  [<c133b7f0>] ? __driver_attach+0xa0/0xa0
[ 1485.660603]  [<c133a5b9>] bus_for_each_drv+0x49/0x70
[ 1485.660617]  [<c133b6ba>] device_attach+0x8a/0xa0
[ 1485.660630]  [<c133b7f0>] ? __driver_attach+0xa0/0xa0
[ 1485.660644]  [<c133ade5>] bus_probe_device+0x25/0x40
[ 1485.660657]  [<c13393fc>] device_add+0x28c/0x380
[ 1485.660672]  [<c1280b63>] ? kvasprintf+0x43/0x60
[ 1485.660686]  [<c1276e1a>] ? kobject_set_name_vargs+0x4a/0x60
[ 1485.660701]  [<c1276e1a>] ? kobject_set_name_vargs+0x4a/0x60
[ 1485.660717]  [<c133d067>] platform_device_add+0xd7/0x1b0
[ 1485.660734]  [<c133d40a>] platform_device_register_resndata+0x5a/0x80
[ 1485.660753]  [<f9903045>] emgdbl_init+0x45/0x1000 [emgdbl]
[ 1485.660769]  [<c1001125>] do_one_initcall+0x35/0x170
[ 1485.660794]  [<f9903000>] ? 0xf9902fff
[ 1485.660812]  [<c108262d>] sys_init_module+0xad/0x210
[ 1485.660829]  [<c1125395>] ? sys_close+0x75/0xd0
[ 1485.660846]  [<c152bc14>] syscall_call+0x7/0xb
[ 1485.660857] ---[ end trace 7c4cf105e762c0c4 ]---

```

Investigating a bit I found the commit in 2.6.39 that changed sysfs/class/backlight implementation for >.39 kernels:
[http://lwn.net/Articles/423170/](http://lwn.net/Articles/423170/)

this requires, at least I suppose, a change in all backlight modules for video drivers and a single line patch should fix it:
props.type = BACKLIGHT_RAW;
or 
props.type = BACKLIGHT_PLATFORM;

> BACKLIGHT_RAW it's hitting the control registers directly rather than going via a platform interface.

Platform is intended for cases where the platform (ie, the specific 
instance of a GMA500-based system) provides its own mechanism, rather 
than falling through to the raw register access. The idea is that 
platform interfaces may keep track of other platform-level policy such 
as ALS. Opregion potentially mitigates these problems, but I've still 
seen some cases where the distinction matters.
[https://lkml.org/lkml/2011/4/13/144](https://lkml.org/lkml/2011/4/13/144)

tried both and now module doesn't crash anymore, is loaded at startup correctly but still not able to change brightness level.


Other things I've checked that are needed for backlight:
"ls /sys/class/backlight" shows emgd_psb backlight support module available (like it was in natty)

"poulsbo" module is modprobbed and this allow acpi to see key events (acpi_listen confims it and looks like natty)

"acpi_backlight=vendor" is added as kernel params to use emgd_psb


what else am I missing?

---

### Post by lucazade on 2011-08-05
...another issue probably related to brightness is suspend which is broken in Oneiric using every kind of video drivers so it seems an acpi error..

if I make a diff of "dmesg | grep ACPI" in both natty and Oneiric I get these lines present in natty only:
```

[   17.874117] ACPI: resource (null) [io  0x1180-0x11bf] conflicts with ACPI region GPIO [io 0x1180-0x11bf]
[   17.874132] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.966852] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)

```


and this in Oneiric only:
```
[    0.164670] PM: Registering ACPI NVS region at 7f6bc000 (12288 bytes)

[    0.265837]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d

[    0.265846] ACPI _OSC control for PCIe not granted, disabling ASPM

[    0.956233] ACPI: AC Adapter [ACAD] (off-line)
```


this requires an acpi guru to figure it out.. i've tried adding "acpi_sleep=nonvs" but obviously didn't help.
:-k

---

### Post by tista on 2011-08-07
> **lucazade said:**
> @Tista

I'm trying to fix emgdbl kernel module for brightness hotkeys control in Oneiric.

Installing this module without any changes from Natty version I get this
```

[ 1485.660175] ------------[ cut here ]------------
[ 1485.660207] WARNING: at /build/buildd/linux-3.0.0/drivers/video/backlight/backlight.c:314 backlight_device_register+0x193/0x1c0()
[ 1485.660220] Hardware name: AO751h           
[ 1485.660228] emgd_psb: invalid backlight type
[ 1485.660235] Modules linked in: emgdbl(+) cryptd aes_i586 aes_generic rfcomm bnep emgd drm_kms_helper drm parport_pc ppdev binfmt_misc vesafb snd_hda_codec_realtek joydev snd_hda_intel snd_hda_codec snd_hwdep snd_pcm uvcvideo videodev snd_seq_midi i2c_isch sch_gpio btusb snd_rawmidi arc4 psmouse serio_raw bluetooth snd_seq_midi_event lpc_sch snd_seq ath5k ath mac80211 cfg80211 snd_timer snd_seq_device snd soundcore snd_page_alloc poulsbo wmi video lp parport pata_sch r8169
[ 1485.660386] Pid: 5512, comm: modprobe Not tainted 3.0.0-7-generic #8-Ubuntu
[ 1485.660395] Call Trace:
[ 1485.660416]  [<c1047832>] warn_slowpath_common+0x72/0xa0
[ 1485.660432]  [<c12c72f3>] ? backlight_device_register+0x193/0x1c0
[ 1485.660448]  [<c12c72f3>] ? backlight_device_register+0x193/0x1c0
[ 1485.660463]  [<c1047903>] warn_slowpath_fmt+0x33/0x40
[ 1485.660479]  [<c12c72f3>] backlight_device_register+0x193/0x1c0
[ 1485.660499]  [<f98fe15a>] emgdbl_probe+0x6a/0xac [emgdbl]
[ 1485.660517]  [<c133c951>] platform_drv_probe+0x11/0x20
[ 1485.660531]  [<c133b4ed>] really_probe+0x4d/0x150
[ 1485.660546]  [<c1343959>] ? pm_runtime_barrier+0x49/0xb0
[ 1485.660561]  [<c133b72a>] driver_probe_device+0x3a/0x60
[ 1485.660575]  [<c133b831>] __device_attach+0x41/0x50
[ 1485.660589]  [<c133b7f0>] ? __driver_attach+0xa0/0xa0
[ 1485.660603]  [<c133a5b9>] bus_for_each_drv+0x49/0x70
[ 1485.660617]  [<c133b6ba>] device_attach+0x8a/0xa0
[ 1485.660630]  [<c133b7f0>] ? __driver_attach+0xa0/0xa0
[ 1485.660644]  [<c133ade5>] bus_probe_device+0x25/0x40
[ 1485.660657]  [<c13393fc>] device_add+0x28c/0x380
[ 1485.660672]  [<c1280b63>] ? kvasprintf+0x43/0x60
[ 1485.660686]  [<c1276e1a>] ? kobject_set_name_vargs+0x4a/0x60
[ 1485.660701]  [<c1276e1a>] ? kobject_set_name_vargs+0x4a/0x60
[ 1485.660717]  [<c133d067>] platform_device_add+0xd7/0x1b0
[ 1485.660734]  [<c133d40a>] platform_device_register_resndata+0x5a/0x80
[ 1485.660753]  [<f9903045>] emgdbl_init+0x45/0x1000 [emgdbl]
[ 1485.660769]  [<c1001125>] do_one_initcall+0x35/0x170
[ 1485.660794]  [<f9903000>] ? 0xf9902fff
[ 1485.660812]  [<c108262d>] sys_init_module+0xad/0x210
[ 1485.660829]  [<c1125395>] ? sys_close+0x75/0xd0
[ 1485.660846]  [<c152bc14>] syscall_call+0x7/0xb
[ 1485.660857] ---[ end trace 7c4cf105e762c0c4 ]---

```

Investigating a bit I found the commit in 2.6.39 that changed sysfs/class/backlight implementation for >.39 kernels:
[http://lwn.net/Articles/423170/](http://lwn.net/Articles/423170/)

this requires, at least I suppose, a change in all backlight modules for video drivers and a single line patch should fix it:
props.type = BACKLIGHT_RAW;
or 
props.type = BACKLIGHT_PLATFORM;


[https://lkml.org/lkml/2011/4/13/144](https://lkml.org/lkml/2011/4/13/144)

tried both and now module doesn't crash anymore, is loaded at startup correctly but still not able to change brightness level.


Other things I've checked that are needed for backlight:
"ls /sys/class/backlight" shows emgd_psb backlight support module available (like it was in natty)

"poulsbo" module is modprobbed and this allow acpi to see key events (acpi_listen confims it and looks like natty)

"acpi_backlight=vendor" is added as kernel params to use emgd_psb


what else am I missing?

So sorry for delayed reply...
umm... yep, such "one make patch" would be OK to fix this issues. and I think that would be enough to apply "BACKLIGHT_PLATFORM" instead of "RAW". finally I could confirm this patch.

and then almost fully what you pointed out. ;) 

ciao.

---

### Post by tista on 2011-08-07
> **lucazade said:**
> ...another issue probably related to brightness is suspend which is broken in Oneiric using every kind of video drivers so it seems an acpi error..

if I make a diff of "dmesg | grep ACPI" in both natty and Oneiric I get these lines present in natty only:
```

[   17.874117] ACPI: resource (null) [io  0x1180-0x11bf] conflicts with ACPI region GPIO [io 0x1180-0x11bf]
[   17.874132] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.966852] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)

```


and this in Oneiric only:
```
[    0.164670] PM: Registering ACPI NVS region at 7f6bc000 (12288 bytes)

[    0.265837]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d

[    0.265846] ACPI _OSC control for PCIe not granted, disabling ASPM

[    0.956233] ACPI: AC Adapter [ACAD] (off-line)
```


this requires an acpi guru to figure it out.. i've tried adding "acpi_sleep=nonvs" but obviously didn't help.
:-k

@Luca 
above differences made from same kernel? or different kernels?
seems Oneiric logs appears in the very early stage of boot, but so far I know... :sad:
and see carefully, who is the "pci0000:00"? SCH Poulsbo VGA must be pci:00.02.00, right? she is chipset? unfortunately I'm using Thinkpad now, so I couldn't check it out right now...

cheers.

---

### Post by lucazade on 2011-08-08
Hey Tista!

It looks like there is something wrong with ACPI because that patch for backlight support doesn't help (and it should) and suspend as well doesn't work.

Not a great issue, in the meantime i'm trying older kernels to see where the issue rely.. 2.6.39 in Oneiric doesn't help, now i'll try 2.6.38 (the same of natty).. who knows!

ciao

---

### Post by tista on 2011-08-08
> **lucazade said:**
> Hey Tista!

It looks like there is something wrong with ACPI because that patch for backlight support doesn't help (and it should) and suspend as well doesn't work.

Not a great issue, in the meantime i'm trying older kernels to see where the issue rely.. 2.6.39 in Oneiric doesn't help, now i'll try 2.6.38 (the same of natty).. who knows!

ciao

Hi Luca!!

OK... but my radeon runs well on oneiric even suspend/resume, backlight and almost same as on Natty... :sad: how your nvidia goes? and then, I would also track the emgdbl issues down soon!! ;)

P.S
What a nice avatar?! :P I like it!!

---

### Post by lucazade on 2011-08-08
> **tista said:**
> Hi Luca!!

OK... but my radeon runs well on oneiric even suspend/resume, backlight and almost same as on Natty... :sad: how your nvidia goes? and then, I would also track the emgdbl issues down soon!! ;)

P.S
What a nice avatar?! :P I like it!!

Bingo!

with 2.6.38 suspend and resume works!!! :popcorn:
2.6.39 and 3.0.x broke it, not able to resume pressing power button. 
now finding out what's wrong in these new kernels requires some magic ^^ skills.


about backlight and emgdbl, the module with that patch is correctly installed and in use, but level of brightness in /sys/class/backlight/emgd_psb/brightness is always at 16.. doesn't decrease.
poulsbo module with acpi_register() inside make fn keys working correctly (at least acpi_listen show them) and acpi_backlight=vendor set emgd_psb as current platform, so these seems ok to me.. is the level of brightness that probably is not changed in pci register. do you agree with me? :)

ps.. ahahha, thanks for the comment bout avatar :P lol

---

### Post by lucazade on 2011-08-08
tried "old" emgdbl with .38 (without the latest patch "props.type = BACKLIGHT_PLATFORM;" because .38 doesn't require this) but brightness level doesn't change, always at 16.

so, it seems it is not related to emgdbl but to something Oneiric specific.

---

### Post by tista on 2011-08-08
> **lucazade said:**
> Bingo!

with 2.6.38 suspend and resume works!!! :popcorn:
2.6.39 and 3.0.x broke it, not able to resume pressing power button. 
now finding out what's wrong in these new kernels requires some magic ^^ skills.


about backlight and emgdbl, the module with that patch is correctly installed and in use, but level of brightness in /sys/class/backlight/emgd_psb/brightness is always at 16.. doesn't decrease.
poulsbo module with acpi_register() inside make fn keys working correctly (at least acpi_listen show them) and acpi_backlight=vendor set emgd_psb as current platform, so these seems ok to me.. is the level of brightness that probably is not changed in pci register. do you agree with me? :)

ps.. ahahha, thanks for the comment bout avatar :P lol

Yeah Bingo!! ;)

and if I remembered well, this period of releasing .39 is the day we've experienced newer drm_pci_init functions in kernel. in previous, we usually used such initializations as apart each. but from .39, we runs init such as "combo" init functions, right? so I suppose that's the reason why pci_register had got something wrong... 

yeah it seems to be needed some help from guru of kernel!! or it might be better to report the bug to ubuntu kernel maintainers...

ciao.

P.S
I'm drinking now too much!! so it means "tista seems to be useless", right? :P:P:P
[IMG]http://i55.tinypic.com/105483t.jpg[/IMG]

---

### Post by lucazade on 2011-08-08
i'll look at pci_register stuff and to open a bug report. Btw now i'm useless as well..posting from the seaside!

---

### Post by lucazade on 2011-08-09
```
sudo su
echo "5" > /sys/class/backlight/emgd_psb/brightness
```

this way I can change brightness (from 1 to 16)
wondering why doesn't work from hotkeys.
:-k

---

### Post by fjgaude on 2011-08-09
> **lucazade said:**
> ```
sudo su
echo "5" > /sys/class/backlight/emgd_psb/brightness
```

this way I can change brightness (from 1 to 16)
wondering why doesn't work from hotkeys.
:-k

This did nothing on my Dell mini. I then went in and changed the "0" that was there to "5" to see what would happen and I couldn't save the file, system wouldn't let me. Strange!

After the latest massive Oneiric update system stills works fine under Unity 2D.

---

### Post by lucazade on 2011-08-09
> **fjgaude said:**
> This did nothing on my Dell mini. I then went in and changed the "0" that was there to "5" to see what would happen and I couldn't save the file, system wouldn't let me. Strange!

After the latest massive Oneiric update system stills works fine under Unity 2D.

Backlight support is quite different from netbook to netbook, even if they share same gfx chipset, because every brand (asus, dell, acer, sony..) come with a "special" acpi kernel module that usually manage these things.

In my case I should use "acer_wmi" kernel module to handle brightness support and to enable fn keys but *obviously* acer stopped to develop this acpi module and don't support aspire series at all.

So I need to use generic "poulsbo" kernel module (included in the kernel itself) to enable fn keys, employ "emgd_psb" backlight platform by installing "emgdbl" package and adding "acpi_backlight=vendor" as kernel param.. yes, tricky!

IIRC dell and asus have good module that support these features out of the box, sony maybe a little different (tista knows this).

You can't directly write in that file because is "special" and created on the fly when the kernel is working (both /sys/* and /proc/* stuff).

you should try to see in gma500 mega-thread if there were some user experiences with dell and emgd backlight, these should probably work in the same way in both natty and oneiric... otherwise change brightness at grub screen and live happy ;)

---

### Post by fjgaude on 2011-08-09
Okay, and thanks for the knowledge!

I see a dell_backlight folder in /class/backlight... but I like the full brightness the way it is, LED backlight set to "7" max. <smile>

"The best is yet to come."

Oneiric is just about there and will likely be in Beta1. The only thing left for me is when I mount a drive on the same box its files end up being marked as "1001 - user #1001" and I can't write to them even using root. Hmmm... sure this will be fixed soon.

---

### Post by tista on 2011-08-09
> **lucazade said:**
> ```
sudo su
echo "5" > /sys/class/backlight/emgd_psb/brightness
```

this way I can change brightness (from 1 to 16)
wondering why doesn't work from hotkeys.
:-k

Buona sera Luca. ;)

yeah it seems to be caused acpi event handling, right? then did you already try embedding emgdbl into initramfs? it could come with earliest registrations than any other platform modules.

and I gonna see diff-ing the sources about poulsbo stub between .38 and 3.0.0.... ;)

P.S
sony should be loaded the machine-specified platform "sony-laptop".  and "acpi_backlight=video" in grub as well...

---

### Post by lucazade on 2011-08-10
> **tista said:**
> Buona sera Luca. ;)

yeah it seems to be caused acpi event handling, right? then did you already try embedding emgdbl into initramfs? it could come with earliest registrations than any other platform modules.

and I gonna see diff-ing the sources about poulsbo stub between .38 and 3.0.0.... ;)

P.S
sony should be loaded the machine-specified platform "sony-laptop".  and "acpi_backlight=video" in grub as well...

I've tried to embed emgdbl in initramfs but no luck. yep, it should register the platform earlier, i've also blacklisted acer_wmi that creates a dummy entry as backlight platform but nothing.
If you have time it would be great!

---

### Post by stevensj on 2011-08-26
Hi,

Just wondering what you guys think that state of the drivers will be once OO lands.  Which do you think will be better, psb_gfx or emgd?  It seems like there is more work happening with emgd at the moment.  At the moment the wiki says that psb-gfx has no 3D or XV support - is it always likely to be like that?

Keep up the good work,
John

---

### Post by lucazade on 2011-08-26
> **stevensj said:**
> Hi,

Just wondering what you guys think that state of the drivers will be once OO lands.  Which do you think will be better, psb_gfx or emgd?  It seems like there is more work happening with emgd at the moment.  At the moment the wiki says that psb-gfx has no 3D or XV support - is it always likely to be like that?

Keep up the good work,
John

John at the moment there are no interesting news about psb_gfx, so no 3D or XV... we'll see in kernel 3.1.0 if at least psb_gfx will work out of the box (so without tricks to install oneiric and ppa to make it work).


Emgd will *probably* switch (redirect efforts) to Wayland because meego 1.3 will use this video server, so I think we likely won't see xorg 1.10/1.11 support.
Thopiekar in the meanwhile is repackaging xorg 1.9 for Oneiric and emgd, fixing some old bugs and compiling against new stuff for improved performances.

If I'll see any good news I'll post here.

---

### Post by fjgaude on 2011-08-26
Thanks, Luca, for the update...

---

### Post by lucazade on 2011-08-26
> **fjgaude said:**
> Thanks, Luca, for the update...

You're welcome! :)

---

### Post by mattrope on 2011-08-26
> **lucazade said:**
> 
Emgd will *probably* switch (redirect efforts) to Wayland because meego 1.3 will use this video server, so I think we likely won't see xorg 1.10/1.11 support.


Meego IVI 1.3 plans to be configurable for either X-based operation or Wayland-based operation, so EMGD will be providing support for both types of stacks.  On the X side of things, the driver binaries we ship will match whatever X server version Meego 1.3 ships (unclear at this point whether that will be 1.9 or 1.10, but our codebase supports both).

---

### Post by lucazade on 2011-08-26
> **mattrope said:**
> Meego IVI 1.3 plans to be configurable for either X-based operation or Wayland-based operation, so EMGD will be providing support for both types of stacks.  On the X side of things, the driver binaries we ship will match whatever X server version Meego 1.3 ships (unclear at this point whether that will be 1.9 or 1.10, but our codebase supports both).

thanks Matt
this is the best confirmation I could have expected!

---

### Post by jbernardo on 2011-08-26
> **mattrope said:**
> Meego IVI 1.3 plans to be configurable for either X-based operation or Wayland-based operation, so EMGD will be providing support for both types of stacks.  On the X side of things, the driver binaries we ship will match whatever X server version Meego 1.3 ships (unclear at this point whether that will be 1.9 or 1.10, but our codebase supports both).
Any idea if it will have an updated vaapi, so that finally mplayer plays with subtitles?

---

### Post by mattrope on 2011-08-26
> **jbernardo said:**
> Any idea if it will have an updated vaapi, so that finally mplayer plays with subtitles?

Media encode/decode is handled by a different team, so I'm not as plugged into exactly what's going on with that part of the driver.  My impression was that subpicture support (for subtitles and other kinds of picture-in-picture functionality) was supposed to be one of the new features already supported by the 1.8 release, although it might only be possible when specific configuration settings are set.  I'll ask around and see if I can find out.

---

### Post by jbernardo on 2011-08-26
> **mattrope said:**
> Media encode/decode is handled by a different team, so I'm not as plugged into exactly what's going on with that part of the driver.  My impression was that subpicture support (for subtitles and other kinds of picture-in-picture functionality) was supposed to be one of the new features already supported by the 1.8 release, although it might only be possible when specific configuration settings are set.  I'll ask around and see if I can find out.
That would be great, thank you! It is quite frustrating to always get the subpicture error and having to boot Maverick to use the PSB drivers.

I also wonder if XBMC with vaapi support will work without subpicture support, but haven't tried it yet.

Of course, if it is configurable and already in 1.8, then it is even better.

---

### Post by thopiekar on 2011-09-04
On what is working tista there? : [https://launchpad.net/~tista/+archive/psb-gfx-daily/+packages](https://launchpad.net/~tista/+archive/psb-gfx-daily/+packages)

Sounds like a mix of drivers :/ is he trying to get psb_gfx working with 3D support?

---

### Post by lucazade on 2011-09-04
yes, he was trying to integrate psb_gfx with 3d bits of pvr binary drivers.. obviously a mission impossible also for Tista :)
probably in the next moths we'll see Alan Cox doing this directly in the kernel (at least hooks for binary stuff, I suppose), anyway nothing in the short term.

---

### Post by thopiekar on 2011-09-04
sounds f**king crazy :D
Hope we won't need Xorg downgrades then :D

---

### Post by jbernardo on 2011-09-04
Any of the 1101HA users was able to install oneiric? I wanted to test the EMGD drivers, but I never could get the live cd to finish booting, always got a kernel panic. I tried with Kubuntu Alpha 3, Ubuntu alpha 3 and Kubuntu 2011/08/30 nightly, and all fail, apparently with a squashfs error which is in fact a kernel panic. I tried passing all kernel options I could think of, tried different USB keys, all for nothing.
I am going to try with the alternate (text only) install next, but if that fails also I am out of ideas.

---

### Post by thopiekar on 2011-09-04
Well, try this then: [http://uck.sourceforge.net/](http://uck.sourceforge.net/)
Or install Ubuntu Natty on it and do a do-release-upgrade -d as root ;)

---

### Post by lucazade on 2011-09-04
> **jbernardo said:**
> Any of the 1101HA users was able to install oneiric? I wanted to test the EMGD drivers, but I never could get the live cd to finish booting, always got a kernel panic. I tried with Kubuntu Alpha 3, Ubuntu alpha 3 and Kubuntu 2011/08/30 nightly, and all fail, apparently with a squashfs error which is in fact a kernel panic. I tried passing all kernel options I could think of, tried different USB keys, all for nothing.
I am going to try with the alternate (text only) install next, but if that fails also I am out of ideas.

so strange.. this guy is able to boot oneiric with the 1101ha:
[http://ubuntuforums.org/showthread.php?t=1837473](http://ubuntuforums.org/showthread.php?t=1837473)
(thopiekar IIRC has got a 91mt so should be close to yours for some stuff)

no idea.. only different hw I could think (to try to unload in case) are acpi module, webcam, sd card reader, eth0 and wlan... the rest should be more or less the same of any gma500 netbook, i suppose, as part of intel chipsets.

have you tried to boot without quiet and splash to see where it hangs?

---

### Post by jbernardo on 2011-09-04
> **lucazade said:**
> so strange.. this guy is able to boot oneiric with the 1101ha:
[http://ubuntuforums.org/showthread.php?t=1837473](http://ubuntuforums.org/showthread.php?t=1837473)
(thopiekar IIRC has got a 91mt so should be close to yours for some stuff)

no idea.. only different hw I could think (to try to unload in case) are acpi module, webcam, sd card reader, eth0 and wlan... the rest should be more or less the same of any gma500 netbook, i suppose, as part of intel chipsets.

have you tried to boot without quiet and splash to see where it hangs?
I'll check that thread...
I've tried without quiet and splash, that was how I was able to see it was a panic. It seems it happens either when starting x or just before, I am not sure, as suddenly everything scrolls off screen with the dump and all the squashfs errors after the panic.

---

### Post by tista on 2011-09-05
Been a while guys. ;)

Yeah I've been working on a lot of other projects... So sorry for frozen daily build on psb_gfx! :sad:

and then I have much time again to continue such "Mission Impossible". so today I'm willing to reboot my daily build project. a couple of days ago, I had contacted Mesa/Gallium dev team, and made much precious discussions with them.

Let's relight the fire!! :P

cheers.

**EDIT**

Just now I've uploaded latest psb_gfx copied from git... named "psb-dkms - 0.3.1+git20110826.cf9f115~oneiric2".
I've modded/added some stuff to compile against generic 3.0.0 kernel. and then it seems to be built without any warnings/errors on my 3.0.0-10-generic kernel. but unfortunately I didn't run it, so haven't any ideas whether it works well or not... :P

tonight I would re-install oneiric beta1 on my VAIO-P, well ASAP I would try to run!

ciao.

---

### Post by lucazade on 2011-09-05
@tista
Yes, you can! (tm)

---

### Post by syg00 on 2011-09-06
I have a Gateway LT30 that I look after. Basically a PITA.
Currently running Maverick with poulsbo o.k. 
Tried Natty, and was a disaster. emgd didn't have any brightness at all - with "acpi.backlight=video" I could use the hot buttons, but they had no effect.
Decided to try Oneiric - seems much better. Same issue with the hot buttons (psb-gfx), but seems to default to max brightness. The lady who owns the kit will be *much* happier with that.
Hope things keep improving.
For the moment the boot will default to Maverick (for sanity).

Thanks.

---

### Post by lucazade on 2011-09-06
> **syg00 said:**
> I have a Gateway LT30 that I look after. Basically a PITA.
Currently running Maverick with poulsbo o.k. 
Tried Natty, and was a disaster. emgd didn't have any brightness at all - with "acpi.backlight=video" I could use the hot buttons, but they had no effect.
Decided to try Oneiric - seems much better. Same issue with the hot buttons (psb-gfx), but seems to default to max brightness. The lady who owns the kit will be *much* happier with that.
Hope things keep improving.
For the moment the boot will default to Maverick (for sanity).

Thanks.

a disaster because of brightness hotkeys broken on your netbook?
to me seem the smallest problem of gma500 drivers.. in a everyday 2d experience there are near no differences using psb, iegd, emgd, fbdev or psb_gfx and this applies for every ubuntu release (and by extension also for other distros)
the only significant difference are in 3d area and vaapi hd playback.. and for the effort to make everything working.

---

### Post by syg00 on 2011-09-06
> **lucazade said:**
> a disaster because of brightness hotkeys broken on your netbook?Yep.
A netbook (any portable) is bloody near useless if you can't read it in (normal) bright light.
On Natty, it was barely usable indoors - unreadable outdoors.

Oneiric appears much better - real test will be in full daylight tomorrow.

---

### Post by lucazade on 2011-09-06
> **syg00 said:**
> Yep.
A netbook (any portable) is bloody near useless if you can't read it in (normal) bright light.
On Natty, it was barely usable indoors - unreadable outdoors.

Oneiric appears much better - real test will be in full daylight tomorrow.

so don't you have backlight at all?
it this case it is a real pity.. but first time i hear that.

---

### Post by syg00 on 2011-09-06
Yeah, Natty was a bummer. No real problem - on that machine I always stay a few months behind the release cycle anyway.
Oneiric seems good for backlighting, even in full sun. Can live without brightness controls.

Has anyone reported no mouse pointer (synaptic) on boot from cold (off overnight) ?. Has happened twice now. Plugging in an external USB mouse works fine. Likewise the synaptic pad comes to life after a reboot.

---

### Post by fjgaude on 2011-10-07
Hello, Luca, et al! Will we see an update to psb_gfx for oneiric? And an update to the link:

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

So close to having 3D on Poulsbo, eh?

---

### Post by lucazade on 2011-10-07
Ciao fjgaude!
non credo, bisogna aspettare il kernel 3.1.. ah wait.. this is an international forum .. lol ;)

I don't think so, we should wait for the next kernel release in order to have an updated psb_gfx driver. Atm the one available in the ppa repo is working pretty well. Unfortunately no hw accel for video (vaapi) and no 3D, for these we still need to use emgd.

---

### Post by fjgaude on 2011-10-07
Thanks for the quick reply. I'm happy with 2D with a hi-res 10" screen. Very nice... now to get oneiric released and a 3.1 kernel.

---

### Post by thopiekar on 2011-10-12
While working on different projects now T didn't know that we will have that a good driver for GMA500! When will be the drivers released? Are we really getting 3D + vaapi acceleration or are you kidding?
Tried the psb_gfx dkms some weeks ago and had still the same problem with my display.. (the driver uses just the half of the screen).. is this driver with the working psb_gfx driver already released at [http://kernel.org/?](http://kernel.org/?)

tista: I know it is off topic but could you make some patchworks for s2-liplianin for Oneiric? Maybe even for 3.1-* kernels?
Would be awesome :)

---

### Post by tista on 2011-10-12
@thopiekar,

been a while! :P

Since web based kernel git page had been hidden because of its security, I've not been searching new codes... :S

my last dkms package for psb_gfx was 0.3.1+git20110826.cf9f115~oneiric2 on my PPA. So I might have to pull and sync to latest git ASAP... ;)

P.S:
Oh S2?!
I didn't do yet... and if you knew where the latest code base was, let me know. :P
And I would push the souces to my bzr after I could finish the patchworks for kernel-3.1 or higher...

cheers guys.

---

### Post by thopiekar on 2011-10-12
here it is:
[http://mercurial.intuxication.org/hg/s2-liplianin/](http://mercurial.intuxication.org/hg/s2-liplianin/)

Would also be great if you could make a dkms package for that. thanks!

---

### Post by lucazade on 2011-10-12
> **thopiekar said:**
> While working on different projects now T didn't know that we will have that a good driver for GMA500! When will be the drivers released? Are we really getting 3D + vaapi acceleration or are you kidding?
In the readme of psb_gfx in git it was written that this driver should have (don't know at what level of implementation is atm) hooks for propreitary xorg driver+opengl+vaapi stuff for pvr drivers (available in meego repos).
Tista tried some magic to glue stuff but it seems atm really difficult to get something working.. I hope Alan Cox will tell us when bits are ready.

> **thopiekar said:**
> Tried the psb_gfx dkms some weeks ago and had still the same problem with my display.. (the driver uses just the half of the screen).. is this driver with the working psb_gfx driver already released at [http://kernel.org/?](http://kernel.org/?)

Because KMS feature of psb_gfx conflicts with plymouth. Only workaround known is to disable plymouth completely (removing splash from kernel args is not enough) by using this:
sudo mv /etc/init/plymouth.conf /etc/init/plymouth.conf.disabled

---

### Post by thopiekar on 2011-10-12
> **lucazade said:**
> In the readme of psb_gfx in git it was written that this driver should have (don't know at what level of implementation is atm) hooks for propreitary xorg driver+opengl+vaapi stuff for pvr drivers (available in meego repos).
Tista tried some magic to glue stuff but it seems atm really difficult to get something working.. I hope Alan Cox will tell us when bits are ready.



Because KMS feature of psb_gfx conflicts with plymouth. Only workaround known is to disable plymouth completely (removing splash from kernel args is not enough) by using this:
sudo mv /etc/init/plymouth.conf /etc/init/plymouth.conf.disabled

is really such a dirty fix needed? isn't there a cleaner way like a kernel option?

---

### Post by lucazade on 2011-10-12
> **thopiekar said:**
> is really such a dirty fix needed? isn't there a cleaner way like a kernel option?

Good question.. i'm not aware of any, I'll give it a look

---

