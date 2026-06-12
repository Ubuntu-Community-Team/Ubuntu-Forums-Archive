---
title: "Ubuntu Software Center limited when running live off USB"
date: 2019-01-08
forum: New to Ubuntu
---

### Post by cmcesq on 2019-01-08
Hi everyone. Just wondering if someone can give me some insight here. I'm running Ubuntu 18.04 Live off a USB stick (I want to try and get used to it before doing full install). when I open Ubuntu Software Center, the options are *very* limited. For example, there are only four games(!!!) I can't believe there are no other Linux games out there. Are the options limited because I'm running live? Or is this an actual limitation of Ubuntu?[/SIZE]

---

### Post by oldos2er on 2019-01-08
It's a limitation of the Software Center (at least as far as I know. I don't use SC). Using Synaptic, I see four games in the "main" repository. In both "universe" and "multiverse" there are many more listed. There are plenty other Linux games that are not in Ubuntu's repos, for example Steam games.

---

### Post by yetimon_64 on 2019-01-08
It has been a while since I've tried to install extra software to a live image, but I do clearly remember having to enable several repositories when trying to do so. The live cd/usb image has only one or two of the usual four repos enabled from my memory.

I have on occasions enabled all the usual repos and installed into the live environment; but one thing to remember is when you restart the system such additions will be lost and you will have to re-enable all the repos and reinstall any additional software after a reboot if you continue with the live image.

It is possible to make a live image with "persistence" but I've always found it to be a rather complex/tricky task with varying results here. A persistence partition used with a live image can save changes and extra software if set up correctly. May be worth searching google or other web search engines for "ubuntu live USB with persistence" (or similar wording) for guides on how to set up if you want to continue with live images and additional software after a reboot.

Regards, yeti.

---

### Post by duchuymobile on 2019-01-08
[COLOR=#000000]I see four games in the "main" repository ?[/COLOR]

---

### Post by oldrocker99 on 2019-01-09
Look in the "Multiverse" section with synaptic. If you haven't installed Synaptic, do it.
```
sudo apt install synaptic
```

---

