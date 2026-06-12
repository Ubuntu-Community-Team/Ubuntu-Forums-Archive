---
title: "Battery not charging"
date: 2016-08-31
forum: New to Ubuntu
---

### Post by kate.t on 2016-08-31
I'm already battling a sound problem, but oh goody! I have another problem.

This morning when I first started using my new Lenovo G50-70 laptop (64 bit, preinstalled with 16.04), I noticed that in spite of having the laptop plugged in and charging overnight, the power level indicator said only 21%. Since I've been using this laptop for the last hour and a half, the indicator remains at 21% while it's plugged in.

I ran the following command, upower -d and got the following information:

```
Device: /org/freedesktop/UPower/devices/line_power_ADP0
  native-path:          ADP0
  power supply:         yes
  updated:              Wed 31 Aug 2016 10:11:18 AM MST (4253 seconds ago)
  has history:          no
  has statistics:       no
  line-power
    warning-level:       none
    online:              yes
    icon-name:          'ac-adapter-symbolic'

Device: /org/freedesktop/UPower/devices/battery_BAT0
  native-path:          BAT0
  vendor:               Lenovo IdeaPad
  serial:               BAT20101001
  power supply:         yes
  updated:              Wed 31 Aug 2016 11:21:19 AM MST (52 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    warning-level:       none
    energy:              6.14 Wh
    energy-empty:        0 Wh
    energy-full:         28.08 Wh
    energy-full-design:  28.51 Wh
    energy-rate:         0 W
    voltage:             14.323 V
    percentage:          21%
    capacity:            98.4918%
    icon-name:          'battery-low-charging-symbolic'

Device: /org/freedesktop/UPower/devices/DisplayDevice
  power supply:         yes
  updated:              Wed 31 Aug 2016 10:23:19 AM MST (3532 seconds ago)
  has history:          no
  has statistics:       no
  battery
    present:             yes
    state:               charging
    warning-level:       none
    energy:              6.14 Wh
    energy-full:         28.08 Wh
    energy-rate:         0 W
    percentage:          21%
    icon-name:          'battery-low-charging-symbolic'

Daemon:
  daemon-version:  0.99.4
  on-battery:      no
  lid-is-closed:   no
  lid-is-present:  yes
  critical-action: HybridSleep
kathleen@kathleen-Lenovo-G50-70:~$ 

```

Is it possible that my battery is actually charged at 100%, but reading its power level incorrectly?

If that's not possible, why is my battery level stubbornly stuck at 21% charge, and what can I do about this?

Thanking you in advance for any help you can render!

Kathleen

---

### Post by kate.t on 2016-08-31
1fallen,

To stay on topic, I'm responding to you here.

Regarding your suggestion (in another thread) to let the battery discharge completely, remove it, replace it, and power it on with the computer plugged in, I'm kind of...leery...even anxious.

Is there any chance that, when I try that, it just might not charge up at all? I need this computer to finish a freelance project. If it's safe to do, I'll try it. 

Kathleen

---

### Post by QIII on 2016-08-31
Hello.

You have confounded the continuity of two threads by answering another here.  Who is to say 1fallen will even see this post?  What thread were you responding to with this, so I can move this post where it belongs?

---

### Post by kate.t on 2016-08-31
QIII,

Sorry for the confusion!

I began a new thread (this one) when I noticed my battery problem this morning. Soon thereafter, I remarked on it briefly in the thread about my bluetooth stereo headphones putting out mono sound.

1fallen has been helping me there. She/he made a suggestion, and I responded there that I would answer her/him in this thread, because I didn't want to be off-topic.

In my post to her/him in this thread I reiterated the suggestion she/he had made so that anyone reading here would know what she/he said.

I'm sorry if I violated any rules. I was trying to be appropriately on-topic. Shall I edit my post here in this thread to remove any reference to 1fallen and simply say that someone had made that suggestion, and I was leery of it, and what does everybody/anybody think? 

Kathleen

---

### Post by DogMatix on 2016-08-31
As a freelancer myself I would complete any project you are in the midst of before tinkering with a mission critical machine if you are concerned. Lenovo does provide 'Power Management software' that does have an option to stop the battery charging to 100% to, I believe, prolong the batteries life span. But, this is Windows specific software and I can't see how this can be related to a laptop with Ubuntu pre-installed. Have you tried charging it again or from a different plug socket. Was the laptop turned off completely whilst it was charging? Just to eliminate the obvious.

@QIII 1fallen is aware of this thread.

---

### Post by #&amp;thj^% on 2016-08-31
> **QIII said:**
> Hello.

You have confounded the continuity of two threads by answering another here.  Who is to say 1fallen will even see this post?  What thread were you responding to with this, so I can move this post where it belongs?

I will take ownership QIII my bad...She had asked in another thread, so feeling like I should respond, Well here it is
> Yes I saw your battery issue also...all I can say there is Lenovo Bios can be a handful at times. Having owned a couple myself.[IMG]https://ubuntuforums.org/images/smilies/icon_biggrin.gif[/IMG]
[http://www.bing.com/search?q=lenovo+...gy&form=OSDSRC]("http://www.bing.com/search?q=lenovo+laptop+bios+buggy&form=OSDSRC")
Off topic for this thread _**but I would the first chance you get is to  totally discharge the battery once**_, and remove it, and then put it back  in and power on with the cord plugged in.
Maybe??...or Maybe not??
Thread was here: [https://ubuntuforums.org/showthread.php?t=2335154&page=3](https://ubuntuforums.org/showthread.php?t=2335154&page=3)

I should have worded that a bit better and DogMatix is spot on
> I would complete any project you are in the midst of before tinkering with a mission critical machine if you are concerned.
 
Just wait till you are done with your project kate.t, as i am just shooting from the hip here...all though that has worked for me personally. (And I am a He) ;)
To be clear though wait till you are done with your project.

---

### Post by kate.t on 2016-09-01
Thank you, DogMatix and 1fallen!

Your advice to wait until I'm done my project was good. However, I didn't see that until later in the evening AFTER I took 1fallen's original advice to let the battery drain and then recharge.

A friend here said to me, "Why not try it? The worst that will happen is that you'll be using your computer on the electric plug while you chase down a new battery."

So I threw caution to the wind! Your suggestion worked, 1fallen. My battery is now fully charged. Of course, not knowing WHY it happened to begin with is going to bug me. It's another one of those inscrutable Linux mysteries...;)

Kathleen

---

### Post by #&amp;thj^% on 2016-09-01
> **kate.t said:**
> Thank you, DogMatix and 1fallen!

Your advice to wait until I'm done my project was good. However, I didn't see that until later in the evening AFTER I took 1fallen's original advice to let the battery drain and then recharge.

A friend here said to me, "Why not try it? The worst that will happen is that you'll be using your computer on the electric plug while you chase down a new battery."

So I threw caution to the wind! Your suggestion worked, 1fallen. My battery is now fully charged. Of course, not knowing WHY it happened to begin with is going to bug me. It's another one of those inscrutable Linux mysteries...;)

Kathleen
Yay!!! I thought that would work.:D
I will never lead you astray with out proper warning.  I am not convinced however this is all related to Linux though.
Our other problem that we won't confuse here in this thread...is defiantly related. (Shhh :-$)
I will see you there when I am satisfied with the risk. 
Cheers:KS

---

