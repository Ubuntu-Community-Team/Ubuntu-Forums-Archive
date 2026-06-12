---
title: "Problem install NVIDIA drivers in Intrepid"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by karthikophobia on 2008-11-01
Hi
I just installed Intrepid on my i386 system. I have an NVIDIA 6200 graphic card. The problem is that when I try to enable it in hardware drivers, it is not activating.

Plz help
Thanq

---

### Post by Pro-reason on 2008-11-01
Perhaps you could try using EnvyNG to get the right drivers.

---

### Post by Sealbhach on 2008-11-01
Check in your Software Sources to make sure that you have Third Party medibuntu repositories enabled.


.

---

### Post by preumbra on 2008-11-01
I had this and other problems.  Here is what I have, what I ran into, and how i solve it.

Ubuntu 8.10 x64
Nvidia 8800 GTX

First I must say you should do everything from the systems>>administration>>Hardware Drivers GUI.  Doing stuff from other than that place caused me problems.

A)  Problem one, chose driver 177 (should work for 6 sereis cards) - but would not activate.  Soluton was just patience.  It takes a bit of time to finish.

B)  Problem two, "Could not enable desktiop settings due to ... / Driver appears not to be in use (or something like that)".  This solution was that after I had completed A) above I needed to reboot.  It tells you that on the GUI but I did not see that.  So I de-activated everything (I had even tried version 173) then re-activated 177.  I then noticed the comment about rebooting.  I rebooted and as is well - did waste several hours though.

Again - i want ot stress the importance of useng the GUI over command line.  The command line has gotten me into trouble several times.

Hope this helps someone.

---

### Post by karthikophobia on 2008-11-01
I reinstalled the OS and the drivers work now. However thanks a lot for your help.

---

