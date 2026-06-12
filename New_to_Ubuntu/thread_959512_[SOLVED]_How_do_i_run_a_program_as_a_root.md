---
title: "[SOLVED] How do i run a program as a root"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by Linuxidiot on 2008-10-26
Hello again :) well i downloaded a nvidia graphics driver that i would like to install but when i get in from the terminal it says i must run this asa root....anyone help on how i might achieve that...at the moment i have it on my desktop(where everything i download goes)

---

### Post by Xiong Chiamiov on 2008-10-26
Prefix the command with "sudo".  If you're launching a graphical utility, use "gksudo".

[See]("https://wiki.ubuntu.com/RootSudo").

---

### Post by Linuxidiot on 2008-10-26
thank you, ive always wondered what that sudo command was for:)

---

### Post by CatKiller on 2008-10-26
It's much easier to install the NVidia driver using the normal package management than with the script that you can download from NVidia's site. System -> Administration -> Hardware Drivers is probably the easiest way.

Otherwise, you can install the nvidia-glx, nvidia-glx-new or nvidia-glx-legacy (depending on which card you have) package through Synaptic.

---

