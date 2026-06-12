---
title: "Is there any way to disable my headphone jack?"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by Famicommander on 2008-06-30
The headphone jack on my laptop has been ripped off, and I can't get sound from my speakers unless I put something metal in the hole where my headphone jack was.

I was wondering if there was a way to disable my headphone jack so that I might get sound from my speakers again without having to open up my laptop or buy a USB sound card.

I'm running Xubuntu 8.04 on a KDS Reliant 6184 laptop.

---

### Post by nowshining on 2008-06-30
more than likely the problem is with your laptop - not the os, so I don't think disabling the headphone jack will help at all. For that u'll have to have it fixed.

---

### Post by Famicommander on 2008-06-30
> **nowshining said:**
> more than likely the problem is with your laptop - not the os, so I don't think disabling the headphone jack will help at all. For that u'll have to have it fixed.
I think disabling the port will fix the problem because the computer seems to think that there are headphones plugged in, which is why I can get sound from the speakers by sticking metal in the hole where the port was. If the headphone port is disabled, then they will be bypassed altogether and sound will come from my speakers.

I know it can be done because I did it in Windows before I installed Linux. It's just a question of how.

---

### Post by kansasnoob on 2008-06-30
Try installing > gnome-alsamixer from synaptic. You'll then find it in Sound & Video. Many, many toggles:

[ATTACH]75876[/ATTACH]

[ATTACH]75877[/ATTACH]

---

### Post by Famicommander on 2008-06-30
> **kansasnoob said:**
> Try installing  from synaptic. You'll then find it in Sound & Video. Many, many toggles:

[ATTACH]75876[/ATTACH]

[ATTACH]75877[/ATTACH]
But I'm running Xubuntu. I'm using Xfce and not GNOME. I installed the package, but I don't know how to access it.

---

### Post by Famicommander on 2008-06-30
I got it installed and I opened it up in Terminal, but there are no toggles. It's just a blank box.

---

### Post by nowshining on 2008-06-30
in terminal

alsamixer

right key - move to the next bar

up - up the volume
down - lower the volume

spacebar - mute/unmute

---

### Post by Famicommander on 2008-06-30
> **nowshining said:**
> in terminal

alsamixer

right key - move to the next bar

up - up the volume
down - lower the volume

spacebar - mute/unmute

It's comepletely blank when I open it.

---

### Post by nowshining on 2008-06-30
hmmmm screenshot us - mouse cursor over the terminal window, alt+printscreen - upload it as an attachment.

---

### Post by Famicommander on 2008-06-30
This is what I get when I try to edit my preferences in gnome-alsamixer:
```
jason@ubuntu:~$ gnome-alsamixer

(gnome-alsamixer:5348): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
Segmentation fault
jason@ubuntu:~$ 

```

---

### Post by Famicommander on 2008-06-30
> **nowshining said:**
> hmmmm screenshot us - mouse cursor over the terminal window, alt+printscreen - upload it as an attachment.
There's nothing to see. It's literally just a blank box with the close/maximize/minimize bar on top.

---

### Post by nowshining on 2008-07-01
i see - um in terminal - type just alsamixer that's all :)

u should get something similiar to the screenshot below:

---

