---
title: "How Can I disable the system bell?"
date: 2006-12-08
forum: Programming Talk
---

### Post by fatsheep on 2006-12-08
Okay first off, yes I know I can go to System>Preferences>Sound and disable the bell under GNOME.  HOWEVER, under a login terminal (ctrl+alt+f1 for example), the system bell still is active.  How do I disable it?

---

### Post by po0f on 2006-12-08
fatsheep,

```
[FONT="Courier New"]$ sudo modprobe -r pcspkr[/FONT]
```
And add the following line to /etc/modprobe.d/blacklist:
```
[FONT="Courier New"]blacklist pcspkr[/FONT]
```
Though this question might have been better served in General Help.  :)

---

### Post by fatsheep on 2006-12-09
> **po0f said:**
> fatsheep,

```
[FONT="Courier New"]$ sudo modprobe -r pcspkr[/FONT]
```
And add the following line to /etc/modprobe.d/blacklist:
```
[FONT="Courier New"]blacklist pcspkr[/FONT]
```
Though this question might have been better served in General Help.  :)

That worked, thank you. :)

---

