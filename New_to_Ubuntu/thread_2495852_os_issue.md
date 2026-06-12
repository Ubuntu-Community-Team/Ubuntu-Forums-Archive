---
title: "os issue"
date: 2024-03-04
forum: New to Ubuntu
---

### Post by londiklaunchpad on 2024-03-04
Getting these. What to do. How to restore without formatting & losing hard disk data

---

### Post by Rubi1200 on 2024-03-05
Hi and welcome to the forums :-)

You're not giving us very much information to work with.

Please try and answer these questions as best you can:

1. what version of Ubuntu is installed?
2. are you dual-booting with Windows?
3. what happened BEFORE this happened?
4. can you boot the computer with a liveUSB and access your files?

I really hope you have good backups of all your important data.

---

### Post by londiklaunchpad on 2024-03-05
[COLOR=#000000]1. what version of Ubuntu is installed? 22.04[/COLOR]
[COLOR=#000000]2. are you dual-booting with Windows? No[/COLOR]
[COLOR=#000000]3. what happened BEFORE this happened? everything was working fine, but when i was shutting down the system, it wouldnot shutdown properly & take long time, so i switched off the power supply a few times[/COLOR]
[COLOR=#000000]4. can you boot the computer with a liveUSB and access your files? Have not tried[/COLOR]

[COLOR=#000000]I really hope you have good backups of all your important data. No back ups[/COLOR]

---

### Post by MAFoElffen on 2024-03-05
From an installer LiveUSB... Please post the results of this, posted within CODE Tags:
```

lsblk -e7 -o name,label,size,fstype,model

```

---

### Post by ajgreeny on 2024-03-05
Having forced a shutdown i suspect you need to run fsck on the root filesystem whichmay have been corrupted.

The output of the command given above should help discover which partition that is so please do that and we may be able to help further.

---

