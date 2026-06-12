---
title: "ThinkPad X1 carbon gen 7 with ubuntu 18.04 LTS no audio output"
date: 2020-03-22
forum: New to Ubuntu
---

### Post by hzdl on 2020-03-22
Hello forum, I have been using Ubuntu for several years now, though do not consider myself an expert. I recently got a new laptop -- a Thinkpad X1 Carbon Gen 7 that has Dolby Atmos speakers (4 speakers that ares supposed to give a surround sound type effect). The laptop came with Windows 10. I partitioned the hard drive and installed Ubuntu 18.04 as a dual boot.

For the life of me I cannot get the speakers to output any audio. There is only a dummy output listed in the settings.

Here are some specs:

```

System:    Host: xxxxxx Kernel: 5.3.0-42-generic x86_64
           bits: 64 gcc: 7.4.0
           Desktop: Gnome 3.28.4 (Gtk 3.22.30-1ubuntu4)
           Distro: Ubuntu 18.04.4 LTS
Audio:     Card Intel Device 9dc8 driver: snd_soc_skl bus-ID: 00:1f.3
           Sound: Advanced Linux Sound Architecture v: k5.3.0-42-generic

```

I have tried several fixes that I dug up around the internet, including this one which looked promising: [https://www.sysorchestra.com/setup-soundcard-and-microphone-on-lenovo-thinkpad-x1-carbon-7th-gen-with-linux-mint-19-3/](https://www.sysorchestra.com/setup-soundcard-and-microphone-on-lenovo-thinkpad-x1-carbon-7th-gen-with-linux-mint-19-3/)

Two points to add:
[LIST=1]
[*]I also cannot get alsamixer to work. I just get the error ```
cannot open mixer: No such file or directory
``` (alsa-base and alsa-utils are installed) 
[*]Interestingly, the speakers work beautifully when I am in a live session, i.e., the "try ubuntu" option from the USB boot. I do not understand how the speakers can work perfectly in the live session, but somehow not when I do the full install. 
[/LIST]

Any help would be so appreciated!

---

### Post by hzdl on 2020-03-26
Hey all, I just got a Thinkpad  X1 Carbon Gen 7 that has Dolby Atmos speakers (4 speakers that ares  supposed to give a surround sound type effect). The laptop came with  Windows 10. I partitioned the hard drive (followed instructions) and installed Ubuntu 18.04 as a  dual boot.

I cannot get the speakers to output any audio. There is only a dummy output listed in the settings.

Here are some specs:

```

System:    Host: xxxxxx Kernel: 5.3.0-42-generic x86_64
           bits: 64 gcc: 7.4.0
           Desktop: Gnome 3.28.4 (Gtk 3.22.30-1ubuntu4)
           Distro: Ubuntu 18.04.4 LTS
Audio:     Card Intel Device 9dc8 driver: snd_soc_skl bus-ID: 00:1f.3
           Sound: Advanced Linux Sound Architecture v: k5.3.0-42-generic

```

I have tried several fixes that I dug up around the internet, including this one which looked promising: [https://www.sysorchestra.com/setup-soundcard-and-microphone-on-lenovo-thinkpad-x1-carbon-7th-gen-with-linux-mint-19-3/](https://www.sysorchestra.com/setup-soundcard-and-microphone-on-lenovo-thinkpad-x1-carbon-7th-gen-with-linux-mint-19-3/)

Two points to add:
[LIST=1]
[*]I also cannot get  alsamixer to work. I just get the error ```
cannot open mixer: No such  file or directory
``` (alsa-base and alsa-utils are installed)
[*]Interestingly, the speakers work beautifully when I am in a  live session, i.e., the "try ubuntu" option from the USB boot. I do not  understand how the speakers can work perfectly in the live session, but  somehow not when I do the full install.
[/LIST]

Any help would be so appreciated!

I posted this in hardware but didn't get any help. Beyond install I'm pretty much a newb so any help would be appreciated. Thanks!

---

### Post by MimziM on 2020-03-26
Try purging and reinstalling alsa 

```
sudo apt-get remove --purge alsa-base pulseaudio
sudo apt-get install alsa-base pulseaudio
sudo alsa force-reload

```

---

### Post by coffeecat on 2020-03-26
@hzdl, I've merged your two threads and placed the merged thread in New to Ubuntu. Please do not cross-post - this causes confusion. I notice you did not bump your first thread. If you don't get a response after 12-24 hours, it is OK to bump the thread so that those in different time zones may notice it near the top of the thread queue. If you don't bump, people may simply assume that you have abandoned the thread. Also - if you thing it helpful to have the thread moved to a different sub-forum, please use the report button in your post to request this. The report button is used for more than just reporting problematic posts - it is an efficient way to send a request to forum moderating staff.

Now to your question:

[quote=hzdl]I do not understand how the speakers can work perfectly in the live session, but somehow not when I do the full install.
[/quote]

Please re-read the other thread you posted to - [https://ubuntuforums.org/showthread.php?t=2438740](https://ubuntuforums.org/showthread.php?t=2438740) - including the linked bug report. The live session would be using the original version of the kernel that your release of Ubuntu came with, and your sound works with that. Did you do an upgrade after you installed Ubuntu? If so, presumably the kernel upgrade introduced the bug described in the bug report that has broken your sound. I haven't checked the details of the kernel versions mentioned in the bug report against what you report is in your system but, hopefully, an upcoming kernel upgrade will fix your issue.

If not, bump this thread if you get no further replies and someone may be able to suggest something.

---

### Post by him610 on 2020-03-28
Please show results between code tags...
```

dpkg -l alsa*

```

---

### Post by hzdl on 2020-03-29
I finally had time to get back to this. coffeecat's suggestion worked! I re-installed without the wifi so updates did not install automatically. Should I now just not install any updates for a while? 

It does seem that the solution is to not let the kernel update until the newer one is ready, but to be honest I don't know how to boot a prior kernel if I need to in the future. I'll look into how to do this but for now, thank you to everyone and sorry for being such a forum noob.

---

### Post by coffeecat on 2020-03-29
> **hzdl said:**
> Should I now just not install any updates for a while?

That's probably not a good idea. Apart from the kernel, updates include security updates, and updates for any browsers you have installed. I would not want to be behind with these. 

> **hzdl said:**
> It does seem that the solution is to not let the kernel update until the newer one is ready, but to be honest I don't know how to boot a prior kernel if I need to in the future. 

As far as I can make out, this is probably just a one-off situation where a particular kernel version (5.0.3.-42) introduced a bug which is affecting your audio chipset. Since you have now re-installed, the only kernel you will have will be the original one that the installer ISO was prepared with. If you now do an update, including the kernel, you will still be able to boot into the original kernel from the grub menu. According to the bug report, the kernel 5.0.3-43, currently in the proposed repository, should fix this problem. Hopefully, this version will pass testing and be moved into the main repository soon, and be generally available.

---

