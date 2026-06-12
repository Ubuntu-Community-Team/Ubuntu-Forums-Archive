---
title: "Desktop --&gt; Server"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by Konstabel on 2008-10-03
Is it possible to change from a normal ubuntu installation to a server installation without basically reformatting the harddrive and starting over.

The only access I have at this time is an ssh connection.

---

### Post by Kellemora on 2008-10-03
Hi K

Yes, all the server options are just packages you install in place of options you are currently running, or along with them for that matter.

Technically, you are a Server, then added Desktop features to that to make it into a Desktop.

Linux is quite a bit different than the Doze.  The hard drive containing the program you want to run can be anywhere on your LAN and to Linux it appears to be on your own machine.
Once I learned that, I didn't need humongous hard drives in all the machines, just use them as workstations.

TTUL
Gary

---

### Post by hyper_ch on 2008-10-03
it is, bascially you need to do two things

(1) install server kernel

(2) remove gdm from booting up at start

Server kernel is optimized for server stuff and the 32-bit version supports out-of-the-box up to 64 GB ram.
GDM is the graphical login manager, by disabling it the server will not start X.

---

