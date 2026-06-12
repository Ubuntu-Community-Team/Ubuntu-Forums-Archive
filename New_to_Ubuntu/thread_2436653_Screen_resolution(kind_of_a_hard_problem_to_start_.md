---
title: "Screen resolution(kind of a hard problem to start with)"
date: 2020-02-10
forum: New to Ubuntu
---

### Post by hunterjwizzard on 2020-02-10
Hi folks,

I'm trying to take the plunge and finally learn how to do things under linux. I cobbled together a machine out of some spare parts I had on hand and have been slowly integrating it into my fairly complicated system. I know this is probably not the best approach for a beginner but, here I am. 

I have a 4k monitor and KVM + a bevy of switches and splitters in one room, then all of the PCs are in the other room, connected by long video cables. In the case of the new Ubuntu machine, it is using a single 50' HDMI cable running to a 4-port HDMI splitter, one port of which goes into the 8port KVM. The splitter is doing double-duty as a range extender while also sending the signal to other screens. I have several windows PCs using this exact same configuration, so it's not too out of the ordinary for me.

The problem is, the ubuntu PC is stuck at 1280x720 resolution. When I was building it, I had it in the office hooked directly to the KVM where it was doing 4k without any complaints. This behavior only started when moved into the other room and attached it to the splitter. Unfortunately I cannot easily bypass the splitter as it doubles as a range-extender; I know my windows PCs at least do not work through the KVM without the extender(oddly, they all worked find going directly into the main monitor). 

When I attempt to change the resolution, the screen goes black, stays that way about 15 seconds, then eventually comes back up at the old resolution. This behavior is consistent with it waiting for a confirmation that the new resolution is working(it isn't), then reverting to the old.

[COLOR=#333333][FONT=&quot]Hardware:[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]*Corei3 dualcore 3.4ghz CPU[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]*16gb RAM[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]*2tb HD[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]*450 watt PSU[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]*Ubuntu 18.04 LTS updated an hour ago & nVidia drivers

I can provide all the specific splitters and monitors involved. In case anyone is curious, the project here is to eventually turn the machine into a home theater PC and retro gaming station, hence all of the switching and splitting.

[/FONT][/COLOR]

---

### Post by TheFu on 2020-02-10
Long hdmi runs are troublesome.
The specific nvidia card might be the problem.  Getting the correct driver is sometimes non-trivial.  [https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its](https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its)  Unlike Windows, don't get any drivers directly from any vendor's website. This almost never turns out well.

Have you tried using the Core i3 iGPU instead?

Can you directly connect the monitor and GPU, setup the resolution?  Sometimes splitters and KVMs prevent monitor EDID information.  I've seen this.

---

### Post by hunterjwizzard on 2020-02-10
Ok, I think I might have found it.

When I did as you suggested and plugged into the motherboard GPU, I was able to set 1920x1080i and get the screen to show up, but the resolution flickered badly. I think set it to one of the other settings available, regular old 1920x1080, and it worked without issue. I then switched back over to the graphics card(nVidia 650gtx) and tried setting 1920x1080 and again it worked. So the problem might be with that little old "i".

I would eventually like to get the system capable of outputting 4k, and this makes it sound like a driver issue. I had actually loaded the drivers through the Ubuntu software and updates system as in the recomended link, not simply grabbed them off the website. Whats also interesting is the machine did 4k out of the box with the basic drivers but had other issues. Will see what else this resolves, but for now I also have a few more things to try.

Thanks!

---

### Post by TheFu on 2020-02-10
650gtx is old, isn't it?  Are there any nvidia proprietary drivers supported with the current kernels?  The F/LOSS drivers should be used for unsupported nvidia cards or buy a newer, but not too new, GPU.  AMD GPUs are reported to have better support.

I bet the i3 iGPU can support 4K output.

BTW, always best to post exact models of hardware here, not general "core i3"

---

### Post by CatKiller on 2020-02-10
> **TheFu said:**
> 650gtx is old, isn't it?  

2013; still supported by current drivers. The prior generation *has* dropped from support, though.

For the OP:

1080i is an interlaced resolution. It effectively displays at half the refresh rate, since it does all the odd lines on one frame and all the even lines on the next frame.

Monitor detection happens through a mechanism called EDID. Neither your long cable run nor the adaptors are going to help with that. If plugging your machine directly into the monitor with a normal length cable doesn't give it enough of a nudge to be able to detect and display the native resolution of your monitor you can bypass the EDID stage and tell your machine all about your monitor manually. Even with your machine sending the correct signals, though, that cable run could end up being too long.

---

### Post by hunterjwizzard on 2020-02-11
> **CatKiller said:**
>  you can bypass the EDID stage and tell your machine all about your monitor manually. 

How would I go about doing this?

I ask primarily for the learning experience, as that's whole point of this project.

Supposedly, both the splitter and KVM should be doing EDID-spoofing of the monitor; I also have a hardware EDID emulator I can toss into the mix. Of course most of that is moot since I only actually need the machine to run at 1920x1080(since one of it's outputs is my non-4k TV) but I'd still like to find out how to solve problems like this under linux just so I can get more into the zone.


> **TheFu said:**
> 650gtx is old, isn't it? 

Yes. It was my workstation's graphics card for many years, and has been sitting in a bin for many more. Same story with most of the parts. The motherboard is a spare socket 1150, case was too small for a different project, PSU salvaged from an ewaste collection event... the list goes on and on. At least its an environmentally-conscious PC ;)

---

### Post by TheFu on 2020-02-11
Turns out the 650 gtx isn't old by my standards.  I had an nvidia 7200 GS that wasn't pulled until 12 months ago when proprietary drivers stopped being compatible.

As for manually providing the EDID information, in 25 yrs, I've needed to do that once on 1 machine, so it really isn't worth knowing until you need it.  I've never met anyone else who needed it.  It is a driver option - so it will be different for every driver.  The option for my Dell monitor with a nvidia 1030 is:
```
Section "Device"
....
    Identifier     "Device0"
    Option "CustomEDID" "DFP-0:/etc/X11/xorg-monitor.dell-2412m.edid.raw"
...
EndSection
```
I had to create the file - used some edid tools while directly connected to the monitor to generate that file. I chose the name and directory. The DFP-0 is dependent on the GPU port names.  I also ended up creating some modelines in the monitor section for the xorg.conf file.

99.99999% of the world never needs to know this stuff because it just works.

---

### Post by CatKiller on 2020-02-11
> **hunterjwizzard said:**
> How would I go about doing this?

I ask primarily for the learning experience, as that's whole point of this project.

Supposedly, both the splitter and KVM should be doing EDID-spoofing of the monitor; I also have a hardware EDID emulator I can toss into the mix. Of course most of that is moot since I only actually need the machine to run at 1920x1080(since one of it's outputs is my non-4k TV) but I'd still like to find out how to solve problems like this under linux just so I can get more into the zone.

As TheFu says, you *can* slurp up the EDID and then load it a boot time. The only bit that you're really interested in, though, is the timings that your monitor can handle: if the monitor never says what it can do, the autodetection routine is conservative so that it doesn't break anything. The important numbers are **HorizSync** and **VertRefresh**, which are generally available from your monitor's specifications or manual. The autoconfiguration should have enough information from those ranges to work out which resolutions your monitor can do. You can put those in a configuration snippet in xorg.conf.d, which saves you having to construct a whole xorg.conf. You can also use a full modeline, which gives a specific resolution rather than finding a number of different resolutions; xrandr would use this if you were creating a custom resolution, and the syntax would be the same.

Monitors were terrible at providing EDID for a while, and adaptors can interfere with it: some combinations of signal ports just don't connect the wires that provide that information.

There are a bunch of posts about it and the syntax of the file (I wrote quite a few myself) but shout if you can't find them and I'll see if I can dig one up. There are limits to how much I like repeating myself typing on a phone ;)

---

### Post by CatKiller on 2020-02-12
> **hunterjwizzard said:**
> I know this is probably not the best approach for a beginner but, here I am. 

For the record, this approach will probably serve you well. If you're a tinkerer, like I am and as you appear to be, you'll do fine. If you're specifically trained, as TheFu is, you'll do fine. If you're completely new to computers at all, and you just do what comes naturally, you'll do fine.

The people that really struggle are Windows power users that expect Linux to be a version of Windows that doesn't come from Microsoft. All their habits and conditioning from using Windows will be completely wrong, and it's uncomfortable to suddenly not know how to do things when you consider yourself an expert. Unlearning those habits is a significant bump for those users. 

Poking things to find out how they work, and how they break, and how to make them do what you want, is perfectly healthy. When you get into a position where you've broken things further than your ability to fix them - which is fairly likely to happen at some point with sufficient tinkering - a reinstall is very quick. I'll also channel the spirit of TheFu and say how important backups are.

---

