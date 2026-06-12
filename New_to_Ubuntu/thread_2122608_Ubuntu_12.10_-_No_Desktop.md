---
title: "Ubuntu 12.10 - No Desktop"
date: 2013-03-05
forum: New to Ubuntu
---

### Post by coreymcdonald855 on 2013-03-05
Hello, all! I have just installed Ubuntu 12.10 on my new build and I look forward to familiarizing myself with everything Ubuntu has to offer. However, after booting up, I cannot seem to get my desktop to display. I have the wallpaper, but nothing else. I can open the terminal, but that's about the extent of my knowledge. I Googled a bit, but most solutions involved removing NVidia drivers, which I don't have. I will list my build below and I look forward to your helpful expertise.

AsRock 75 Pro 3
Intel I5 3.1 GHz quad core
DD Radeon HD 7870 GHz Edition
WD3200KS drive

I am stuck on my roommates laptop, but will provide any requested information as soon as possible. Thank you again for the assistance!

---

### Post by mamamia88 on 2013-03-05
why would you install nvidia drivers with an amd card?

---

### Post by coreymcdonald855 on 2013-03-05
I didn't. I was saying most of thr information I found related to nvidia drivers.

---

### Post by mamamia88 on 2013-03-05
Ah my bad I must have read it wrong.  How exactly do you open a terminal if you don't have a desktop?

---

### Post by coreymcdonald855 on 2013-03-05
Ctrl alt t

---

### Post by mamamia88 on 2013-03-05
could you try using the terminal to get to a root prompt with sudo -i then opening synaptic by typing synaptic then removing unity and your radeon driver and reinstalling them both?   or maybe try another desktop like xfce or gnome?  worth a shot better than reinstalling. oh forgot synaptic was uninstalled by default do s sudo apt-get install synaptic first

---

### Post by coreymcdonald855 on 2013-03-05
When I open synaptic, the program begins to load, then closes. Terminal says "Bus error (core dumped)

---

### Post by rickycodie on 2013-03-05
try sudo apt-get autoremove unity --purge and then sudo apt-get install unity

---

### Post by coreymcdonald855 on 2013-03-05
Ricky, gave that a shot. No change.

---

### Post by mamamia88 on 2013-03-05
What radeon driver you are using?

---

### Post by mamamia88 on 2013-03-05
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by coreymcdonald855 on 2013-03-05
1:00.0 VGA compatible controller: AMD nee ATI pitcairn [Radeon HD 7800]

Does that answer the question?

---

### Post by mamamia88 on 2013-03-05
> **coreymcdonald855 said:**
> 1:00.0 VGA compatible controller: AMD nee ATI pitcairn [Radeon HD 7800]

Does that answer the question?

that's not your driver that's your card.   try installing aptitude via apt-get install aptitude then type aptititude search radeon and look for something like xserver-xorg-video-radeon if it has an i next to it it's installed.  maybe you need to uninstall that and install the propietary driver with directions here [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by coreymcdonald855 on 2013-03-05
I installed proprietary driver and rebooted, no change. I am getting a system problem detected notification quite often, if that means anything to ya'll.

---

### Post by mamamia88 on 2013-03-05
> **coreymcdonald855 said:**
> I installed proprietary driver and rebooted, no change. I am getting a system problem detected notification quite often, if that means anything to ya'll.

Ok then I really have no idea unless it's a unity issue.  Open a terminal and install either xubuntu-session or kubuntu-session and reboot when at login screen chose the one you just installed.   If that works then it's obviously a problem with unity

---

### Post by coreymcdonald855 on 2013-03-05
I installed gnome and now have the ability to highlight and create folders. Still no icons nor bars on side. I'll try the method above now

---

### Post by coreymcdonald855 on 2013-03-05
Tried the above method, no change. Installed Gnome 3, got desktop controls after reboot. Upon opening terminal, system encountered an error. No desktop and terminal flashes open then closes. So... there I am.

---

