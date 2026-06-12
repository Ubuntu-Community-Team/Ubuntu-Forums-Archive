---
title: "how to change volume with terminal command?"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by cvaty on 2008-11-27
im trying to figure out if there is a way to change my volume to 100% using a terminal command.
i'd like to use this with an alarm panel applet so that when my music player launches at set time the volume can be set at max avoiding the silent alarm :)

thanks

---

### Post by cmay on 2008-11-27
[php]alsamixer[/php]that should work. i have installed extra programs for sound but i think alsa mixer is installed per default. otherwise the package can be fetched from synaptic

---

### Post by Xiong Chiamiov on 2008-11-27
Alsamixer isn't very scriptable.  You can set sound with a command using amixer.

---

### Post by cmay on 2008-11-27
yes sorry i misread the question. alsa mixer is just a mixer that runs in the terminal and can not just be scripted. thanks for the clarification.

---

### Post by Bazookan on 2012-05-10
I know this is an old thread but still. First of all,Xiong said right....I am just expanding on it.

$amixer -c 0 scontrols
In my case, I got
Simple mixer control 'Master',0
Simple mixer control 'PCM',0
Simple mixer control 'Mic',0
Simple mixer control 'IEC958',0
Simple mixer control 'IEC958 Default PCM',0
Simple mixer control 'IEC958',1
Simple mixer control 'Beep',0
Simple mixer control 'Docking Mic',0
Simple mixer control 'Internal Mic',0

$amixer -c 0 Master 30DB
would set the volume to -30DB level.

---

### Post by nothingspecial on 2012-05-10
> **Bazookan said:**
> I know this is an old thread 

It is, and so must be closed.

---

