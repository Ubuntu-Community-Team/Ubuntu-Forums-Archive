---
title: "New User, desperatly need help, nothing works"
date: 2020-09-16
forum: New to Ubuntu
---

### Post by adamfarsight1 on 2020-09-16
Update: When I test Pop_OS with nvidia drivers, it works, I have sound and graphics card is recgonized. Any ideas so I can use Ubuntu?
Update 2: PopOs only works sound and video wise, it freezes non stop and the popstore is unusable. 

I just want to use a computer without being on Windows. Problem is Windows worked. I got my computer which is a skytech blaze II on sale. came with windows 10 home. Speakers worked. Video Card worked. I have searched these forums, reddits forums, random google results, random duckduckgo results and nothing works.

ryzen 5 2600 6 core
nvidia 1650
mother board is biostar A320MH
8GB ddr4
base ubuntu 20.04 focal
kernel right now 5.4.0-47-generic x86_64 bits: 64 compiler: gcc v: 9.3.0
Secure boot NOT on and never has been. It is disabled

I have no drivers. Going to driver manager has nothing. Just grey box. I purge anything nvidia* and try again installing u 440-450. Same thing, everything is empty, Nvidia server settings just a grey box. No options. I even went to their site and found my GPU and downloaded it from there and it seems to run in the text editor. Gets to about 95% and then says cannot read characters, retry or edit. No matter what happens, freezes.

Sound says only HDMI monitor, from nvidia tu116 high definition audio vendor. Sound server ALSA v k5.4.0-47 generic.  my monitor has no speakers and I have only ever used a DisplayPort cable from monitor to GPU. 

Tried kernels 5.4, 5.6(someone in audio said this and after purging pulseaudio and redoing some steps including pulse control fixed for them, also alsactrl restore does not work, and sudo apt-get remove timidity fails as its not installed.) and 5.8. All nothing. 
Display is still x11. I even moved the /etc/x11/xorg.conf file so it would regenerate it as another forum said. Nothing. I do ubutnu-drivers devices and then again autoinstall and says nothing to install. 

Please I just want to have sound and utilize my graphics card so I can play games in Steam.

---

### Post by mastablasta on 2020-09-17
> **adamfarsight1 said:**
> Update: So everything works fine when I test Pop_OS with nvidia drivers, so equipment works. Any ideas so I can use Ubuntu?


POP_OS! adds some patches to kernel and some modifications. how secure and stable are those patches, only poeple thta made them know. they also offer support for them. 

a user here had similar issues with new Ryzen and nvidia 1650. i am not sure they managed to find resolve them all but partially you might resolve them by using kernel switch at boot 
iommu=soft

i would say if PopOS works well on the machine why not just use that? it's a much easier solution.

if you are so focused on using ubuntu on this machine, then why not get  a PC that has it preinstalled? or one that comes without OS and is certified for linux? or no OS but confirmed to work with linux? you bought PC that has windows preinstalled, so of course everything has to work on windows, otherwise people would be returning it left and right. so the manufacturers of this PC made sure everything works with windows. so now you would have to make modifications on your own to make it work with Ubuntu. just like POP OS creators made. so why now just use PopOS? Or windows 10? as a bonus on windows 10, windows games will work and there are a lot more of them than there are linux games.

---

### Post by guiverc on 2020-09-17
If Pop works, why not take note of what it is using (kernel modules in use, packages & their source & if anything is different *conf* wise to your other preferred OS) and then try and match that on your preferred system.

If it was a Pop patched kernel  there won't be many clues to find. But *testing* that kernel on a Ubuntu system for example may reveal the fix is in there (what I'd do from there I don't know, it may be worth chasing up the patch you need & compile into your preferred kernel yourself, or given that's a potential load of work now & into to the future, just using their kernel maybe easier, or as @mastablaster suggested you could just use that OS)

When you get one *distr**o* of GNU/Linux working the way you want, I've usually found it pretty easy to find what is different to the other one you'd prefer.

---

### Post by adamfarsight1 on 2020-09-17
> **mastablasta said:**
> POP_OS! adds some patches to kernel and some modifications. how secure and stable are those patches, only poeple thta made them know. they also offer support for them. 

a user here had similar issues with new Ryzen and nvidia 1650. i am not sure they managed to find resolve them all but partially you might resolve them by using kernel switch at boot 
iommu=soft

i would say if PopOS works well on the machine why not just use that? it's a much easier solution.

if you are so focused on using ubuntu on this machine, then why not get  a PC that has it preinstalled? or one that comes without OS and is certified for linux? or no OS but confirmed to work with linux? you bought PC that has windows preinstalled, so of course everything has to work on windows, otherwise people would be returning it left and right. so the manufacturers of this PC made sure everything works with windows. so now you would have to make modifications on your own to make it work with Ubuntu. just like POP OS creators made. so why now just use PopOS? Or windows 10? as a bonus on windows 10, windows games will work and there are a lot more of them than there are linux games.


"i would say if PopOS works well on the machine why not just use that? it's a much easier solution. " It does not work well, it crashes constantly, I hate the layout and the popstore freezes every time I click it. When I said everything works fine, I meant there is sound and my video card is recognized.

"if you are so focused on using ubuntu on this machine, then why not get a PC that has it preinstalled?" I'm not from America so maybe you have those in your store but I've never seen them and special shipping, if possible, would cost more than a computer which since I am not rich, cannot just buy a new one.

---

### Post by rsteinmetz70112 on 2020-09-17
If you want to use Ubuntu I'd suggest starting over with the latest version of Ubuntu as there have been some reported issues with the some AMD and Nvidia chips. If these issues still exist they will likely be worked out soon. You may want o start with the server iso as it has the base os and most of the issues seem to be with the gui. If that works OK then you can always install the Ubuntu desktop on it.

You can install the iso on a USB drive and run it in live mode to see if what problems if any show up there.

If you want to pursue this then:
[LIST]
[*]Make sure you update the motherboard firmware. 
[*]You don't mention the storage but if you have solid state drives of any type make sure their firmware is updated.
[*]Download the latest Ubuntu iso and burn it to a USB drive or DVD.
[*]Wipe your drive including any partitions.
[*]Install the latest Ubuntu iso using the defaults.
[/LIST]

Carefully note any problems you have and ask for help.

---

### Post by TheFu on 2020-09-17
I have a Asus B450, Ryzen 2600 and nVidia 1030 GPU.  Extremely stable.

For the GPU, I'm using nvidia-430 and nvidia-430-dev packages.  I don't know where the 1030 vs 1650 driver support overlaps.
```
$ sudo lshw -short -C memory
/0/21                                 memory      32GiB System Memory
/0/21/0                               memory      8GiB DIMM Synchronous **2866** MHz
/0/21/1                               memory      8GiB DIMM Synchronous 2866 MHz
/0/21/2                               memory      8GiB DIMM Synchronous 2866 MHz
/0/21/3                               memory      8GiB DIMM Synchronous 2866 MHz
```
I did have to turn back the RAM speed for stability using XMP/DOCP settings. The installed RAM is 3200Mhz.   2966Mhz wasn't stable without more tweaking than I was willing to perform. Once it was stable, it has been very stable.
The CPU is at stock settings with the stock cooler.  Sensors show the CPU temperatures are usually sub-50 degC, but under heavy load, the cores go to 95 degC. I have the fan set to "silent" profile, but whenever the load temperature is above 70 degC, the CPU fan goes full speed, as controlled by the BIOS. I only have 1 case fan to go with the PSU fan.  I've read that anything over 80 degC is too hot.  I haven't seen any throttling messages in any logs.  

Currently, some of the cores are definitely being slowed:
```
CPU:       Hexa core AMD Ryzen 5 2600 Six-Core (-HT-MCP-) cache: 3072 KB 
           clock speeds: max: 3400 MHz 1: 3182 MHz 2: 3765 MHz 3: 3196 MHz
           4: 2207 MHz 5: 3759 MHz 6: 2762 MHz 7: 2798 MHz 8: 3760 MHz
           9: 3184 MHz 10: 2342 MHz 11: 3760 MHz 12: 3023 MHz

$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +93.0°C  (high = +70.0°C)
```

Had a Core i7 that had overheating problems under load. There would be multiple "core slowed due to thermal throttle" messages in the logs. I've not seen that in logs with AMD.

---

### Post by grahammechanical on 2020-09-17
My hardware is ancient compared to what you people are using. That said, I am using the HDMI/Display port out connector on my lowly Nvidia GT 220 card. It connects to the HDMI input on the TV/monitor and sound comes out to the TV speakers. Your monitor does not have speakers. So, where do you want sound to come out of? 

We do not get the option to choose a different sound output from the Sound Settings utility until after we plug an audio device into an audio out socket on the motherboard. May be you have tried this but you do not say you have tried it. First, plug earphones or an amplifier + speakers into an audio out socket and then see if the Sound Settings utility offers the option to select an onboard audio device as the sound output.

It is possible in Ubuntu to use HDMI/Display port video out to a monitor and have audio output from the onboard audio card going out to earphones or speakers. If the machine is a laptop with built in speakers then the onboard audio card should be detected. And I do not know why it is not being detected.

As a general principle if we have the latest hardware then we need to install the very latest version of Ubuntu. We need to have latest Linux kernel and the latest Linux Hardware Enablement stack = latest hardware drivers. The latest version of Ubuntu is 20.10. It is still under development and it will not be released until the last week in October. ISO images of the development version are produced daily and we can download them from here:

[http://cdimage.ubuntu.com/ubuntu/daily-live/current/](http://cdimage.ubuntu.com/ubuntu/daily-live/current/)

Regards

---

### Post by sdsurfer on 2020-09-18
I have (access to) two System76 Gazelles, both with Nividia GPU's, and a home built desktop with an Nvidia card. Not on Pop OS but give this a try, it was a recurring issue on all and it worked.

Go into Software and Updates and hit the Additional Drivers tab. See if anything comes up for Nvidia. If it does, select the metapackage from nvidia-driver-440. It seems that it always wanted to default to the X.Org noveau driver. Once I set this, all the freezing issues went away.

---

### Post by TheFu on 2020-09-18
The
```
sudo ubuntu-drivers autoinstall
```
should effectively be the same as the GUI "Additional Drivers" method proposed.  In theory. ;)

---

