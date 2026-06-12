---
title: "Sound issues in 8.04"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by jimjesus on 2008-04-27
I have an integrated sound card and a separate pci one. My speakers are usually plugged into my soundcard but when I am in ubuntu only the splash screen noise plays then there is no sound once I am in. However, if I plug my speakers into my integrated soundcard, I can hear everything fine. How can I make all my sounds play through my pci soundcard?

---

### Post by kai60 on 2008-04-27
Hi mate,

it depends on what sound card you have for your PCI card. Just do a Google search on your sound card and Ubuntu and that should give you somewhere to start from.

I am afraid that I won't be of much more help to you, other than to say that most on board devices tend to work out of the box, which is always handy and its only the add-ons that can sometimes cause hassles.

Good luck...

---

### Post by Tatty on 2008-04-27
You probably need to disable your on-board soundcard in your BIOS.

---

### Post by Z47isthenew42 on 2008-04-27
I'm no expert, but perhaps you can see if riven0's advice in [this thread]("http://ubuntuforums.org/showthread.php?t=771759") helps.

---

### Post by 1scorpio on 2008-04-27
had the same problem disble system sound from bios

---

### Post by jimjesus on 2008-04-27
I'd really rather not disable my system sound because I use both while in windows(one for game sounds, the other for ventrilo). I know there is a command like:
```
sudo asoundconf set-default-card "example"
```
But it just gives me some warning when I try that.

---

