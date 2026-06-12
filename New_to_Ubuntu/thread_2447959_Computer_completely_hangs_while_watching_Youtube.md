---
title: "Computer completely hangs while watching Youtube"
date: 2020-07-29
forum: New to Ubuntu
---

### Post by sakh on 2020-07-29
I am a lifetime Windows user who made the complete shift to Linux last week. Obviously, I am a complete newbie.

I was watching Youtube several times and many times, after watching for around 5 to 7 minutes, my laptop completely hangs. I cannot move the cursor, switch tty or anything. Maybe another important piece of information is that this happens gradually. First the video freezes, but audio is fine. Then I try to pause the clip, exit fullscreen, or attempt anything else, and everything freezes up. Running Firefox on Wayland with VAAPI enabled did not result in an freeze. However, tried on other DE's and Chrome, and got the same result.

I tried reading /var/log/kern.log but could not find anything (mostly just don't know what to look for). Not sure if I'm expected to post the log file, or what information to provide.

I am running Ubuntu 20.04 on Ryzen 2500u, and all packages are up to date.

If anything is wrong in this post, please excuse me and let me know what I can add.
Thank you.

---

### Post by ajgreeny on 2020-07-29
You don't mention what graphics hardware you have which is probably important for us to be able to help you.

Please show us the output of terminal command ```
inxi -Fzx
```
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by sakh on 2020-07-29
Thanks for replying. I have the integrated Radeon Vega 8 Graphics.

```

System:    Kernel: 5.4.0-42-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 Desktop: KDE Plasma 5.18.5 
           Distro: Ubuntu 20.04.1 LTS (Focal Fossa) 
Machine:   Type: Laptop System: ASUSTeK product: VivoBook_ASUS Laptop X505ZA_X505ZA v: 1.0 serial: <filter> 
           Mobo: ASUSTeK model: X505ZA v: 1.0 serial: <filter> UEFI: American Megatrends v: X505ZA.311 date: 05/21/2019 
Battery:   ID-1: BAT0 charge: 19.5 Wh condition: 32.7/42.1 Wh (78%) model: ASUSTeK ASUS Battery status: Discharging 
CPU:       Topology: Quad Core model: AMD Ryzen 5 2500U with Radeon Vega Mobile Gfx bits: 64 type: MT MCP arch: Zen 
           L2 cache: 2048 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm bogomips: 31938 
           Speed: 1366 MHz min/max: 1600/2000 MHz Core speeds (MHz): 1: 1369 2: 1477 3: 1368 4: 1368 5: 1368 6: 1368 7: 1366 
           8: 1368 
Graphics:  Device-1: AMD Raven Ridge [Radeon Vega Series / Radeon Vega Mobile Series] vendor: ASUSTeK driver: amdgpu v: kernel 
           bus ID: 03:00.0 
           Display: x11 server: X.Org 1.20.8 driver: amdgpu FAILED: ati unloaded: fbdev,modesetting,vesa 
           resolution: 1920x1080~60Hz 
           OpenGL: renderer: AMD RAVEN (DRM 3.35.0 5.4.0-42-generic LLVM 10.0.0) v: 4.6 Mesa 20.0.8 direct render: Yes 
Audio:     Device-1: Advanced Micro Devices [AMD/ATI] Raven/Raven2/Fenghuang HDMI/DP Audio driver: snd_hda_intel v: kernel 
           bus ID: 03:00.1 
           Device-2: Advanced Micro Devices [AMD] Family 17h HD Audio vendor: ASUSTeK driver: snd_hda_intel v: kernel 
           bus ID: 03:00.6 
           Sound Server: ALSA v: k5.4.0-42-generic 
Network:   Device-1: Intel Wireless 8265 / 8275 driver: iwlwifi v: kernel bus ID: 01:00.0 
           IF: wlp1s0 state: up mac: <filter> 
           Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet vendor: ASUSTeK driver: r8169 v: kernel port: f000 
           bus ID: 02:00.0 
           IF: enp2s0 state: down mac: <filter> 
Drives:    Local Storage: total: 931.51 GiB used: 94.25 GiB (10.1%) 
           ID-1: /dev/sda vendor: Toshiba model: MQ04ABF100 size: 931.51 GiB temp: 32 C 
Partition: ID-1: / size: 146.64 GiB used: 94.22 GiB (64.3%) fs: ext4 dev: /dev/sda5 
Sensors:   System Temperatures: cpu: 37.8 C mobo: N/A gpu: amdgpu temp: 37 C 
           Fan Speeds (RPM): cpu: 2500 
Info:      Processes: 272 Uptime: 4m Memory: 6.80 GiB used: 1.23 GiB (18.1%) Init: systemd runlevel: 5 Compilers: gcc: 9.3.0 
           Shell: bash v: 5.0.17 inxi: 3.0.38


```

 Thank you.

---

### Post by uninvolved on 2020-07-29
This might be easier than you think.

Open the affected browsers, navigate to their settings page, and check to see if "Hardware Acceleration" is enabled. 

If it is enabled, disable it and restart the brower.

If it is not enabled, return here and hopefully someone else knows where the problem is. The symptoms you describe *can be* caused by HA being enabled.

---

### Post by ajgreeny on 2020-07-30
I am out of touch with AMD and the amdgpu drivers, and which graphics chips work with that driver, but I do note in your inxi output that amdgpu FAILED.

That seems suspicious to me but wait for more posters who know more than I do before doing anything other than the suggestion above about HA.

---

### Post by sakh on 2020-07-30
Thanks for your suggestion. I disabled HA but it froze again. Also, just to be clear, when I run Firefox with HA enabled (on Wayland) using VAAPI, it doesn't seem to cause it to freeze. The couple times I have tried this never resulted in a crash.
For reference, I use this:
```

MOZ_ENABLE_WAYLAND=1 firefox

```

---

### Post by monkeybrain20122 on 2020-07-30
> **ajgreeny said:**
> I am out of touch with AMD and the amdgpu drivers, and which graphics chips work with that driver, but I do note in your inxi output that amdgpu FAILED.

That seems suspicious to me but wait for more posters who know more than I do before doing anything other than the suggestion above about HA.

Not really. It says "driver: amdgpu" and "FAILED: ati". It looks fine. You have to read the spaces and the colons correctly. ;)

@OP, what are the outputs if you start firefox in the terminal and go to Youtube?

---

### Post by sakh on 2020-07-30
```

Gtk-Message: 16:54:28.359: Failed to load module "appmenu-gtk-module"
Gtk-Message: 16:54:42.733: Failed to load module "appmenu-gtk-module"

###!!! [Parent][RunMessage] Error: Channel closing: too late to send/recv, messages will be lost

```

The Gtk-Message appears several more times.

---

### Post by sakh on 2020-07-30
Just as an update: the system finally crashed while using VAAPI, however it crashed a bit differently this time. The video kept running but the youtube interface refused to respond. I was also able to access all other windows and the system was fairly responsive (apart from being able to open new applications) until it too, finally crashed and I had to hard reset.

---

### Post by monkeybrain20122 on 2020-07-31
Seems like a graphic driver issue, how did you install the amd driver? Is it the open source driver or the proprietary one? Can you upgrade or downgrade it? Sorry I don't have much experience with amd so I might be out to lunch.

---

### Post by sakh on 2020-08-01
I haven't installed any driver manually, but opening the driver settings says that no drivers are required. But afaik it's the open source one (amdgpu if I'm not wrong)

---

### Post by Yellow Pasque on 2020-08-01
I suspect overheating.

---

### Post by monkeybrain20122 on 2020-08-01
You can try updating your driver like described [here]("https://linuxconfig.org/amd-radeon-ubuntu-20-04-driver-installation"). Upgrading the open source driver with ppa is easy. The amd proprietary driver is [here]("https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-20"), now it supports Ubuntu 20.04 (but may be difficult to set up and hence more risky, see the first link, I don't have any experience setting up amd driver so can't verify the info)

---

### Post by mIk3_08 on 2020-08-01
I think you must use some light weight Ubuntu flavors... or You can try use Linux Mint its an Ubuntu based Linux Distro O.S as it continue to use the package repositories from the latest Ubuntu release. Desktop layouts as same as MS Windows.

---

### Post by CelticWarrior on 2020-08-01
> **mIk3_08 said:**
> I think you must use some light weight Ubuntu flavors... or You can try use Linux Mint its an Ubuntu based Linux Distro O.S as it continue to use the package repositories from the latest Ubuntu release. Desktop layouts as same as MS Windows.

It's more nuanced than that.
Mint is popular but that doesn't mean good. Volkswagens are popular.
And Mint isn't any lighter than many or most official Ubuntu derivatives.
Desktop layout nothing like current Windows 10. Cinnamon desktop although purposefully designed in staunch opposition to Canonical's Unity and committed to keep the ill perceived functionality of the more familiar proprietary OSes, mostly but not only Windows (its contemporary version), evolved into a thing of its own.

If one really needs a very light OS now, the Ubuntu family is no longer a good choice whereas before Lubuntu would be the go to lightweight distro.

---

### Post by mIk3_08 on 2020-08-01
> **CelticWarrior said:**
> It's more nuanced than that.
Mint is popular but that doesn't mean good. Volkswagens are popular.
And Mint isn't any lighter than many or most official Ubuntu derivatives.
Desktop layout nothing like current Windows 10. Cinnamon desktop although purposefully designed in staunch opposition to Canonical's Unity and committed to keep the ill perceived functionality of the more familiar proprietary OSes, mostly but not only Windows (its contemporary version), evolved into a thing of its own.

If one really needs a very light OS now, the Ubuntu family is no longer a good choice whereas before Lubuntu would be the go to lightweight distro.



It's more nuanced than that.
Mint is popular but that doesn't mean good. Volkswagens are popular.

===> Yeah! I agree. Just like Ubuntu 20.04;  New and shiny does't mean Its good. :-D

And Mint isn't any lighter than many or most official Ubuntu derivatives.
Desktop layout nothing like current Windows 10. Cinnamon desktop although purposefully designed in staunch opposition to Canonical's Unity and committed to keep the ill perceived functionality of the more familiar proprietary OSes, mostly but not only Windows (its contemporary version), evolved into a thing of its own.

===> Its not Ms win10 I mean, its more like Ms win 7 or even you can make it MS win10 if you know how to modify it. 

If one really needs a very light OS now, the Ubuntu family is no longer a good choice whereas before Lubuntu would be the go to lightweight distro.

===> No, there are still light Ubuntu that you can still use for your low specification system hardware. Its all about the modification of your Operating System (OS) to make it lighter and I think Ubuntu Linux System is made for old hardware system computers but not obsolete. Drivers of old system hardware are still intact inside the kernel.  It is all about how you craft your OS based on your System Hardware.

---

### Post by monkeybrain20122 on 2020-08-01
> **mIk3_08 said:**
> I think you must use some light weight Ubuntu flavors... or You can try use Linux Mint its an Ubuntu based Linux Distro O.S as it continue to use the package repositories from the latest Ubuntu release. Desktop layouts as same as MS Windows.


This is how OP described his problem "Running Firefox on Wayland with VAAPI enabled did not result in an  freeze. However, tried on other DE's and Chrome, and got the same  result."  I could be wrong but that sounds very much like a graphic driver problem.

OP didn't give more info about his laptop, but the amd-ryzen-5-2500u came out in 2017 and so he is not using 15 year old antique hardware and anything that can run Win10 should have no problem running Ubuntu. I don't get this "use a light OS" advice that I keep hearing since Ubuntu switched to a modern DE in 11.04, it might make sense back then since many people were using Linux on 7-8 year old hardware and 2011 -7 = 2004 and there were some very weak machines. But this is 2020, 4 G of ram is minimum even on reburbished laptops for less than $200. If I were a new user I would get the impression from the "use a light OS" people that you'll need a super computer to run Ubuntu, if that is the  case it is a useless distro.

---

### Post by sakh on 2020-08-01
> **monkeybrain20122 said:**
> You can try updating your driver like described [here]("https://linuxconfig.org/amd-radeon-ubuntu-20-04-driver-installation"). Upgrading the open source driver with ppa is easy. The amd proprietary driver is [here]("https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-20"), now it supports Ubuntu 20.04 (but may be difficult to set up and hence more risky, see the first link, I don't have any experience setting up amd driver so can't verify the info)

I think this worked! I followed the first link and installed the drivers. After installation I ran ```
lshw
``` again and got the following result:
```

  *-display                 
       description: VGA compatible controller
       product: Raven Ridge [Radeon Vega Series / Radeon Vega Mobile Series]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:03:00.0
       version: c4
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix vga_controller bus_master cap_list
       configuration: driver=amdgpu latency=0
       resources: irq:55 memory:e0000000-efffffff memory:f0000000-f01fffff ioport:e000(size=256) memory:fe700000-fe77ffff

```

So I thought that the default driver is the one that is still being used, but I find videos are more fluid now, and of course my computer hasn't crashed yet (fingers crossed!), so I am attributing this to the new drivers. In case the problem crops up again, would you recommend me to go for the 2nd link?
Thank you for your help !

---

### Post by sakh on 2020-08-01
Hi all,
The problem was solved by installing Radeon drivers.
If anyone was wondering, my laptop is fairly new and has no problem running Ubuntu and could handle Windows 10 too.

Thank you all so much for you help! And **monkeybrain20122 **for pointing me to the right place! You all saved someone reluctantly have to return to Windows 10 hahaha.

---

### Post by monkeybrain20122 on 2020-08-01
> **sakh said:**
> 

So I thought that the default driver is the one that is still being used, but I find videos are more fluid now, and of course my computer hasn't crashed yet (fingers crossed!), so I am attributing this to the new drivers. In case the problem crops up again, would you recommend me to go for the 2nd link?
Thank you for your help !

It is still using the open source driver, but the ppa provides a newer version. The second link gives the proprietary driver provided by the manufacturer (AMD), it is supposed to give better performance if you use the laptop for graphic intensive stuffs like video editing and gaming, but the installation seems a bit more complicated and there maybe some gottchas, for other non graphic intensive stuffs you may not see a difference (I heard that unlike Nvidia, the amd open driver actually stacks up pretty well against the proprietary driver since most parts of the amd driver are open source anyway, except for some "special sauce", while the Nvidia open source driver is completely reversed engineered) 

I can't really provide any help there since I don't have any experience installing AMD drivers, my machines have either intel or Nvidia cards. I am afraid you will have to do some research on your own or start a new thread so someone with better knowledge  will assist you. Oh, one thing that I can think of if you do want to try the proprietary driver, make sure to find out what happens if you have a kernel update, do you have to reinstall the driver? With the open driver, kernel and driver update is seamless, you don't have to do anything.

**P.S.** One more thing, if you don't want the driver to keep upgrading, disable the ppa once everything works for you, but don't remove it as in the future you may need to activate it again in case something get out of sync (it is rare but it happens if you try to install something and get the error that xxx depends on yyy.n but yyy.n+2 is installed) Or don't do anything and keep upgrading the driver when it is available.

---

### Post by sakh on 2020-08-01
Ohh ok, got it. Yeah I neither game or do video editing at all, so I'm not going to go down that road, better to keep things working decently right now.
Got it. I read that I should remove the drivers I installed today, before performing a major update to my OS.
I might keep the ppa enabled since battery life is a bit of an issue for me and I'm hoping there will be some improvements on that front, but I'll definitely bear it in mind.
Thanks

---

### Post by monkeybrain20122 on 2020-08-01
> **sakh said:**
> Ohh ok, got it. Yeah I neither game or do video editing at all, so I'm not going to go down that road, better to keep things working decently right now.
Got it. I read that I should remove the drivers I installed today, before performing a major update to my OS.
I might keep the ppa enabled since battery life is a bit of an issue for me and I'm hoping there will be some improvements on that front, but I'll definitely bear it in mind.
Thanks

No, you don't need to remove the driver (downgrading with ppa purge) unless you do an OS upgrade. All other upgrades including kernel would work seamlessly. But I won't recommend OS "upgrade" anyway, when you want to install a new Ubuntu release, just backup your data and do a clean install.

---

### Post by sakh on 2020-08-02
Ok and for disabling the ppa, how often should I enable it and update the drivers?

---

### Post by monkeybrain20122 on 2020-08-02
> **sakh said:**
> Ok and for disabling the ppa, how often should I enable it and update the drivers?

If you always want the update, you can just left it enabled, the oibaf ppa updates every several days, if I remember correctly.

---

