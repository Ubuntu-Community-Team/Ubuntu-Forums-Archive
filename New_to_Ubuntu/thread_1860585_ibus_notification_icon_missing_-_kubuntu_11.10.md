---
title: "ibus notification icon missing - kubuntu 11.10"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by Zerp64 on 2011-10-14
I've installed ibus and anthy for japanese input, and changed my keyboard input settings. For now, ibus is working decently, except for the fact that the notification icon doesn't show up, and even after configuring ibus by running 'ibus-settings' through the terminal to always show the language bar menu, it doesn't show up. So both the language bar and the notification icon are missing, which means that I can't configure anthy to allow me to switch writing modes. Can someone help me out? I'd like to be able to restore this missing icon and have the option to show to language bar.

I am using kubuntu 11.10 x64.

---

### Post by jtarin on 2011-10-14
We just had this discussion ......[here.]("http://ubuntuforums.org/showthread.php?t=1859622")

---

### Post by Zerp64 on 2011-10-14
Except for the fact that the topic you've linked to in that post seems to apply to Unity/gnome. Not KDE.

---

### Post by jtarin on 2011-10-14
Whoops! Not using Kubuntu...sorry.

---

### Post by Zerp64 on 2011-10-15
No problem at all.

---

### Post by Nippondanji on 2011-10-18
I'm facing the same problem on Kubuntu 11.10. In my case, the panel and the candidate selection popup aren't displayed either. Do you see them?

On a lot of reboot attempts, they are sometimes displayed. It must be a timing problem.

---

### Post by pansz on 2011-10-18
Bump, I'm also stuck at this. ibus icon and panel missing after upgrade to kubuntu 11.10 (it works in 11.04)

---

### Post by Zerp64 on 2011-10-20
> **Nippondanji said:**
> I'm facing the same problem on Kubuntu 11.10. In my case, the panel and the candidate selection popup aren't displayed either. Do you see them?

On a lot of reboot attempts, they are sometimes displayed. It must be a timing problem.

Yeah, it's like the program is entirely invisible. Nothing at all shows up related to the program, which means I can't configure anthy, for instance. I haven't tried rebooting to fix the problem. I'll try and confirm this.

---

### Post by Zerp64 on 2011-10-24
Bump yet again.

---

### Post by kc7rwx on 2011-10-31
Any progress on this? 

Having the same problem.  Found this bug [https://bugs.launchpad.net/ubuntu/+bug/854333]("https://bugs.launchpad.net/ubuntu/+bug/854333")

Thanks for any input.  I need to get it ibus working.

---

### Post by norbulinux on 2011-11-01
try follow the steps explain in:

[http://ur1.ca/5kt2z](http://ur1.ca/5kt2z)

and add kimtoy from [https://launchpad.net/~wengxt/+archive/kimtoy](https://launchpad.net/~wengxt/+archive/kimtoy)

;-)

---

### Post by chandra on 2012-02-03
See whether this helps:

[http://wiki.debian.org/I18n/ibus](http://wiki.debian.org/I18n/ibus)

---

### Post by SnappyU on 2012-02-10
Try ```
ibus-daemon -x -r -d
```

---

