---
title: "No Sound Hardware after upgrade"
date: 2022-09-18
forum: New to Ubuntu
---

### Post by cwmoser2 on 2022-09-18
I selected to upgrade my Ubuntu OS and now I have no Sound.
Under System->Preferences->Hardware->Sound->Hardware there is no device.

I did note that this upgraded version, 20.04.4 LTS, seems noticeably faster.
I was though expecting an upgrade to 22.04, oh well.

How do you restore/install the sound driver?

---

### Post by guiverc on 2022-09-18
What product/release are you using? 

By upgrade was it a normal package upgrade?  a *release-upgrade?   *Please try and be specific.  

Did you make any changes to your system last session where the sound worked?

If a normal upgrade; as we don't know what release you're using, we cannot know what packages the upgrade may have included - but also how often do you upgrade?  ie. was this with today's upgrade? and do you upgrade daily? or how often do you upgrade?

FYI:  the most recent significant change I can think of was with  20.04 where if you're using the HWE kernel stack; the 5.13 kernel upgraded to 5.15 ~a month or so ago (*a kernel change means new kernel modules are used; kernel modules more commonly are known as drivers...*) - but you've given no clues as to your product/release & how often you upgrade...

---

### Post by cwmoser2 on 2022-09-18
In my old 20.04, the one before I upgraded, the sound driver was there:
HDA-Intel - HDA ATI HDMI

... but missing after I upgraded.
(I was able to verify this because I kept a copy of the older OS in a separate partition.)

---

### Post by guiverc on 2022-09-18
So you're using Ubuntu 20.04 LTS.  

I mentioned Ubuntu 20.04 LTS users using the HWE kernel stack recently (*about a month ago*) upgraded from the 5.13 kernel stack to the 5.15 that came from Ubuntu 22.04 LTS, but you didn't say if you're using Ubuntu 20.04 Desktop (*which defaulted to HWE* *kernel stack*) or Ubuntu 20.04 LTS Server (*which defaults to the more stable GA kernel stack*). 

You also didn't say how often you upgrade... ie. the kernel stack for 20.04 LTS systems using HWE occurred roughly a month ago...  

Either way; at grub you should see your older kernels there; which would still include a 5.13 stack (*from the now [EOL 21.10 release]("https://fridge.ubuntu.com/2022/07/19/ubuntu-21-10-impish-indri-end-of-life-reached-on-july-14-2022/")* *which is why it upgraded to 5.15*) allowing you to confirm that's what worked..   If you confirm that, the easiest fix (*rather than use the unpatched/insecure 5.13 kernel*) would be switching to the GA kernel stack; ie. returning to the 5.4 kernel that receives support for the life of Ubuntu 20.04 LTS).

---

### Post by cwmoser2 on 2022-09-18
I lost my sound drivers when it upgraded.
 from:
5.4.0-124-generic #140-Ubuntu SMP

to:
5.4.0-125-generic $141-Ubuntu SMP

(I used the "command uname -a" for the above.)

My -124 kernel has these two sound drivers and the -25 has none:
- Built-in Audio (for my external speakers)
- Turks HDMI Audio [Radeon HD6500/6600/6700M series] (for speakers built in Monitor)

---

