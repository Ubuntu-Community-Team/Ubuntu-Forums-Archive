---
title: "System keeps freezing after 14.04 update"
date: 2014-04-30
forum: New to Ubuntu
---

### Post by connor-jolley1980 on 2014-04-30
Let me preface my question by pointing out that I am a complete amateur when it comes to Linux.My problem started a few days after I upgraded to 14.04, everything worked fine but recently my system freezes usually a few minutes after booting up. I've googled the issue and have found bug fixes for the system freezing up before Unity launches but not after. I have to hard reset the system when it becomes unresponsive.

I don't know where to begin in terms of providing output so would appreciate advice.

I found one thread that is currently unresolved, the user was asked to provide the /var/log/dmesg so I have included a pastebin log to mine - I hope this helps
[http://pastebin.com/idmbE3BM](http://pastebin.com/idmbE3BM)

What else should I be providing to help resolve this issue?

---

### Post by LastDino on 2014-04-30
System info? Particularly GPU and drivers.

---

### Post by connor-jolley1980 on 2014-04-30
What do I need to do to find such information? Can you suggest terminal input?

EDIT:

GPU: GeForce GT 745M/PCIe/SSE2

NVIDIA 331.38 from NVIDIA 331 (proprietary)

---

### Post by LastDino on 2014-04-30
> sudo dmidecode -q

Or
> sudo lshw

specifically for GPU
> $ lspci -v | grep VGA

---

### Post by connor-jolley1980 on 2014-05-02
Pretty sure it's related to this known bug

[https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1220426](https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1220426)

Everything works fine as long as I use a mouse and not the touchpad

---

### Post by LastDino on 2014-05-02
Seems like that bug is not solved. Well, you should probably add a bug report there as well. I also see one solution:#18, it doesn't seem to be perfect but if it fit your need, do try them out.

I would also try to keep an eye out for updates with nvidia and touch pad drivers.

---

