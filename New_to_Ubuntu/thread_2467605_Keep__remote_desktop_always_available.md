---
title: "Keep  remote desktop always available"
date: 2021-10-01
forum: New to Ubuntu
---

### Post by toot-fluegelhorn on 2021-10-01
I am running Hirsuite Hippo. Out of the box install, no tinkering whatsoever on the box.
I want to use this as machine as a headless computer, which means closed lid, sitting on the shelf and doing its intended thing.
For this I need to be able to acces the remote desktop whenever I need to.

Currently it is only possible to access the remote desktop when the user is logged on locally.

Remote desktop is set up from the settings->sharing menu.
Which config file do I need to modify to accomplish this?

Please advise

---

### Post by ActionParsnip on 2021-10-01
What are you doing on the system that needs the full desktop session? There may be a sleeker solution to what you want to do. This will bypass the issue

---

### Post by toot-fluegelhorn on 2021-10-06
Thanks for responding.
your reply is a worth a different discussion and very off topic. But out of courtesy I'll answer your question. 
I use remote desktop a lot on a couple of my macs, makes it easy for me to have terminals and apps on that desktop that I can quickly switch back to. Sure, I can SSH on my local device, but then I have to make the effort of having multiple terminal sessions on different local desktops to keep them apart. 
I also have another linux (debian) jobbie running, where I do it the same way. It required a lot of tinkering to get it running reasonably well. 
Brings me back to the days of compiling my own kernel and **** hoping one day Linux would just work out of the box. 20 years later.. still hoping.

So I'd like to prevent having to install another VNC server on a system that already has one on board, so which modifications are required to get this thing usable as headless pc, and if I may ask on top how that machine would advertise this service on my local network as well?

---

### Post by TheFu on 2021-10-06
VNC doesn't "advertise." Sorry.  The client needs to know either the DNS name or IP address and the port used by that VNC listener.  VNC and RDP are both highly attacked:  [https://www.theregister.com/2021/09/30/eset_threat_report/](https://www.theregister.com/2021/09/30/eset_threat_report/)

People that use Linux desktops do find that linux-to-linux "just works" when they don't fight doing it the native way, which is very often required when mixing OSes.  I long for the day when my Android tablet can "facetime" with family members too, but I won't hold my breath.

As for having connections to different systems *just so*, have you checked out tmux or screen?  Reconnecting to the same terminal sessions from multiple clients is what they do.

If OSX was standard X11, you could use X11 over an ssh tunnel to run GUI programs.  Does MacOX have an X/Server?
Proprietary OSes often don't support standard methods of doing things. Sigh.

---

### Post by ActionParsnip on 2021-10-07
If you use a different virtual desktop in Mac, or set the terminal prompt to a different colour then you can distinguish between the local terminal and remote easily. It's a much sleeker solution and you basically don't need VNC

---

