---
title: "panels(well i think it's more than that)"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by sameer.india on 2008-07-26
I have two panels one on top and the other on the bottom of the screen.
The top panel has the button for shutdown/logout/etc.
When I use that both the panels disappear.
I would have sent a screenshot but I also am unable to save any file to the computer.
Firefox doesn't give the back option.
I use a laptop but the computer takes about a minute to show the power management icon in the notification area. If I go to it through the system menu there is no 'on battery' tab.
It even takes as much time to start networking.
Even the system monitor shows one of my CPUs(core 2) being used more than before.
All this started since yesternight after I configured AMAROK.
I can't make head or tail of it.
All was fine till then.

---

### Post by sameer.india on 2008-07-26
Well the processes section of system monitor shows that trackerd is using so much CPU

---

### Post by Elfy on 2008-07-26
Turn off tracker for the moment then and see if it's that causing the problem.

When you installed and configured amarok - did anythine else get installed, did youdo it with synaptic - if so check the history.

---

### Post by sameer.india on 2008-07-26
I've tried closing tracker but it don't change anything.
Amarok came with KDE, A long time ago.
I just configured it yesterday.
And I was offline while I configured it.

---

### Post by sameer.india on 2008-07-26
All I can do now is surf not download.
I try to save anything it just doesn't happen.
No error messages nothing.

---

### Post by Elfy on 2008-07-26
When you say you configured it I assume you mean you hadn't used it previously - is that right? IF that is the case you can remove the hidden folder and see if that caused, but I don't really see what you could have configured to cause this problem.

Has turning off tracker not stopped the cpu usgae?

---

### Post by sameer.india on 2008-07-26
Turning off tracker stopped cpu usage.
But guess what although regularly update my machine right now update-manager is showing 334mb to download.
The update manager shows packages like gnome panel to be downloaded.
as if i just installed ubuntu from the live cd.

---

### Post by Elfy on 2008-07-26
I'd be extremely surprised if it's the fault of amarok then ;)

What exactly did you do yesterday - history in synaptic will show some - or look at your bash history and see if that sheds any light on recent happenings

```
cat ~/.bash_history
```

---

### Post by sameer.india on 2008-07-28
I got it. Thanks for trying to help.
I realised my root partition had no space in it. I just finished editing the partitions and all is fine now.
Except that if i sleep my machine all the sound is gone when i wake it.

---

### Post by richaoj on 2008-07-28
this is a common problem for some machines.  i had the problem -- the volume was reset to mute on waking up from sleep.  what kind of machine are you running? 

As for the firefox thing, you can easily restore your forward and back buttons in
View --> Toolbars --> Customize.

---

### Post by sameer.india on 2008-07-28
the firefox problem is solved.
And the sound doesn't come even when I have set my program's(any media player), alsamixer's, and the machine's volume on full (no mutes).
I have to restart the machine.
Its a lenovo y500.
realtek speakers(HDA card ALC262), intel core 2 duo, 1.73 GHz, 1 GB ram, 160GB harddisk.

---

### Post by richaoj on 2008-07-28
a google search didn't turn up much, but you might try after resuming from suspend opening a terminal and typing:

sudo /etc/init.d/alsa-tools restart

and see if that fixes your problem.  if so we can simply use a script to automatically run this every time you wake from sleep.

---

### Post by sameer.india on 2008-07-28
thanks i'll try that later right now i'm somewhere else on some other machine.

---

### Post by Elfy on 2008-07-28
If you have hardy installed and haven't chnaged anything I would assume it is likely to be more of a problem with pulseaudio.

---

