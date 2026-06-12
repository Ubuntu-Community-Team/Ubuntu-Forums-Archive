---
title: "Resolution setting"
date: 2022-06-19
forum: New to Ubuntu
---

### Post by satman1w on 2022-06-19
I have just installed V22.something after huge pain because setup procedure was mostly invisible due to the resolution chosen by installation which my monitor was unable to display.
When it was finally installed it started in some odd resolution and my monitors resolution wasn't even on the list in display settings... so I found a procedure which enables my resolution so now I can choose 1920x1080 but I have to do it every time after startup???

Is there a better way to do it or this procedure is what I will have to do again and again?

regards

---

### Post by Impavidus on 2022-06-19
Ubuntu versions are simply the year and month of release, so the second number is as important as the first. You probably installed 22.04, as the next 22.something release hasn't been released yet.

Can you tell a bit more about your graphics hardware and what moronic procedure you used to enable the correct resolution? This looks like a graphics driver problem. I've never had a graphics driver problem myself, but that's because I never used a graphics card that needed special configuration or proprietary drivers.

---

### Post by satman1w on 2022-06-20
Hi impavidus,

So the OS is Ubuntu 22.04 LTS
Motherboard is Supermicro server MB X8STI with Intel(R) Xeon(R) CPU W5590  @ 3.33GHz with onboard graphics and 24GB RAM
Monitor is some samsung HD capable and first I wanted full HD resolution but now I think 1600 x 900 will do well enough.

It is not the procedure which is problematic it is the fact that I have to repeat it every time after boot... an procedure is as follows:

xrandr

cvt 1920 1080
xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode VGA-1 "1920x1080_60.00"

after that everything looks ok so I suspect the driver is ok... or not?

what is especially frustrating is the fact that for the same reason (wrong resolution) I was unable to install the thing without additional chemistry...

I am occasional Ubuntu user and I don't speak "Linux fluently" but with a little help from google I can achieve most of the tasks... so you can speak to me as to an adult :-D


What I would like is to set 1600 x 900 once and for all even if the login splash screen would be in some strange distorted resolution - I can live with it...

That is the whole story and I hope that you will understand my frustration

regards to all

---

### Post by satman1w on 2022-06-21
Attitude that never cease to amaze me... I don't have an answer for your question, or I really don't want waste my time on answering but I'll make you elaborate your question to a detail...

Thanks

---

### Post by TheFu on 2022-06-21
> **satman1w said:**
> Attitude that never cease to amaze me... I don't have an answer for your question, or I really don't want waste my time on answering but I'll make you elaborate your question to a detail...

Thanks

Calling our baby ugly, perhaps, wasn't the right first step?  Just sayin'.    Impavidus monkeyed your term, which seemed like a human -to- human thing to do.   Nobody here is paid. We are all volunteers and have lives. Sometimes those lives get in the way of forum stuff. Sorry.  Without Impavidus' question and your answer, I wouldn't have bothered looking into this.

You are welcome.

Very few people would have a Supermicro system AND install a desktop release on it.  They'd install the server release and ssh in from their normal Linux workstation to manage it.  Ubuntu Server doesn't have any GUI.

[https://www.supermicro.com/products/motherboard/Xeon3000/X58/X8STi.cfm](https://www.supermicro.com/products/motherboard/Xeon3000/X58/X8STi.cfm)

That motherboard has a "Matrox G200eW 16 MB DDR2 " GPU, which isn't exactly normal.  We generally see nvidia, amd and intel GPUs and iGPUs here and are well versed in the issues for them.  

And to throw a wrench into the works, 22.04 defaults to Wayland, not xorg for AMD GPUs.  I know they backed Wayland as the default out for nvidia, but I don't know what they did for other GPUs.  Maybe the release notes says?  IDK.  I force Xorg for other reasons.  xrandr doesn't work with Wayland.

I did a forum search for that GPU and found another with the exact same GPU where the user never reported back about the fix, so we don't know.  I did see that the Matrox G200 was released in 1998. Don't know about the "G200eW". 16MB isn't exactly much gpu RAM for a GUI today.  It is a very limited GPU.

Setting the resolution can be accomplished in a few different ways.  The "correct" method would be to create an xorg.conf file, place the correct monitor, mouse, keyboard and GPU settings in the correct format and place it into /etc/X11/xorg.conf.d/ to be picked up.  In the last 10 yrs, xorg has an ability to probe the hardware for known GPUs and used the EDID from the monitor connection to ensure the most compatible resolution is chosen.  But sometimes things don't work due to non-standard GPUs, monitors, adapters, cables, KVM-switches ... all sorts of reasons.

There must be hundreds of example xorg files on the internet, but each one is unique and the one you need will be unique as well.  That's just the way it is. Sorry. My setup isn't like yours, so the GPU and modes and default mode won't help, since they are specific to my monitors, pulled from the EDID information.  I use a KVM-switch and adapter that lies with the EDID, so I've had to override it manually.  The modelines did come from the EDID information ... without the adapter or KVM switch involved.

Another solution which is more approachable is to get your addmode and xrandr commands to run as part of the login process.  Historically, we'd use the ~/.xinitrc and ~/.xprofile to set these things up, but newer login managers seem to ignore those methods. 

I don't use KDE. A quick web-search found this for KDE startup: 
[https://docs.kde.org/trunk5/en/plasma-workspace/kcontrol/autostart/index.html](https://docs.kde.org/trunk5/en/plasma-workspace/kcontrol/autostart/index.html)  Perhaps it will make sense to KDE people?
[https://www.kubuntuforums.net/forum/currently-supported-releases/kubuntu-20-04-focal-fossa-lts/desktop-environment-support-ab/661111-kubuntu-20-04-setting-the-screen-resolution](https://www.kubuntuforums.net/forum/currently-supported-releases/kubuntu-20-04-focal-fossa-lts/desktop-environment-support-ab/661111-kubuntu-20-04-setting-the-screen-resolution) says to drop the commands into a script and put the script in a specific place with execute permissions.

That's all I've found.  Good luck.

---

### Post by QIII on 2022-06-23
@satman1w

Four things:

You will catch more flies with honey than with vinegar.  

The forum volunteers are here as they have time and might not respond immediately.

Asking you to clarify something is part of the support process, even if the person who asks does not have the time to continue the conversation.

Catching the eye of the Forums Staff in such a manner is quite probably not in your best interests.  Please refer to the Ubuntu Forums Rules (see the link in my signature) and adjust your language and attitude appropriately.

---

### Post by MAFoElffen on 2022-06-23
I answered for the "same" [here]("https://ubuntuforums.org/showthread.php?t=2476189&p=14101211#post14101211") for my SuperMicro Server board in my main Workstation... That works from boot, through console, splash and graphics layers... It does that by setting the graphics mode at Kernel Boot through KMS. The instructions there works for both XServer and Wayland... 

Though those instructions were written for a Systems Administrator at his skill level (the target audience). I can go into more detail if you need... Or read the first post of my [Graphics Resolution Sticky]("http://ubuntuforums.org/showthread.php?t=1743535") in my signature line. Then that may make more sense to you.

By just what you have said... I am assuming you are trying to set it with 'xrandr' on the fly. If you are trying to use 'xrandr' to set, that is a temporary solution. Meaning, it only works for the current session, when X is already started (late). If it logs out of the Desktop Environment, powers down or reboots, you have to reset that again. That is not a permanent solution. You could certainly add it to your $HOME/.bashrc file, but I always felt that as a sort of hack for persistent graphics settings. That only makes the change when the Desktop starts, after the Splash and the Graphical Login Screens...

We are patient. Go at your own speed, to understand what you need to do to fix your issue. Ask questions. Learn. Communication is the mutual understanding between all parties involved.

None of us are paid for anything here. We, in this Community, are all volunteers... We help others because it is the right thing to do.

---

### Post by TheFu on 2022-06-23
Thanks  MAFoElffen.  That will help others find a solution, if they can search the forums.

---

