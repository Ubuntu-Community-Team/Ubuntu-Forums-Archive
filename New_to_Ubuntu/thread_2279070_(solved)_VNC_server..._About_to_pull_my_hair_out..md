---
title: "(solved) VNC server... About to pull my hair out."
date: 2015-05-20
forum: New to Ubuntu
---

### Post by Tadaen_Sylvermane on 2015-05-20
In the idea of simplifying my life I have realized that the only reason I use my laptop these days is for Kmymoney. Thats it, everything else is easily done with a tablet or something. I did some research and found that there are vnc clients for android. So for the past 2 hours I have been trying, and failing to get a vnc server to work. I have googled no less than 20 guides so far, each one contradicts the others. My goal is to sell my laptop which is currently running kubuntu, create a virtual machine on my server strictly for kmymoney and vnc into it from my tablet.
 
What or where can I find a simple, easy to follow guide that actually works. Most of the time I just get a grey screen on my tablet. I got it to work a few times awhile ago but couldn't repeat it while trying to use a different DE. It's getting frustrating fast. Any suggestions or what or how or ... anything?

---

### Post by TheFu on 2015-05-20
Which desktop/window manager do you have configured for VNC to use?  It sounds like X/Windows is running, but no WM/DE has been requested.  I haven't used VNC in years and years, but isn't there an option in the vncserver settings to start with the WM you prefer?  Generally, for remote desktops, you need a lite-weight DE - don't choose Unity. Either pure openbox or LXDE would be good.

See the answers here:
[https://askubuntu.com/questions/178962/how-to-start-lxde-session-automatically-after-tightvncserver-starts-to-make-me-a](https://askubuntu.com/questions/178962/how-to-start-lxde-session-automatically-after-tightvncserver-starts-to-make-me-a) but be certain that you install lxde before changing the ~/.vnc/xstartup file as prescribed.

---

### Post by MartyBuntu on 2015-05-20
> **Tadaen_Sylvermane said:**
> ...simplifying my life...

You want simple (and secure)?

Use Teamviewer. You'll kick yourself for not going that route earlier.

---

### Post by Tadaen_Sylvermane on 2015-05-20
> **TheFu said:**
> Which desktop/window manager do you have configured for VNC to use?  It sounds like X/Windows is running, but no WM/DE has been requested.  I haven't used VNC in years and years, but isn't there an option in the vncserver settings to start with the WM you prefer?  Generally, for remote desktops, you need a lite-weight DE - don't choose Unity. Either pure openbox or LXDE would be good.

See the answers here:
[https://askubuntu.com/questions/178962/how-to-start-lxde-session-automatically-after-tightvncserver-starts-to-make-me-a](https://askubuntu.com/questions/178962/how-to-start-lxde-session-automatically-after-tightvncserver-starts-to-make-me-a) but be certain that you install lxde before changing the ~/.vnc/xstartup file as prescribed.

I will try Openbox right now. I think I found my problem in that link, I wasn't using the full path to the de / wm, in this case I was just using "exec startxfce4" instead of "exec /usr/bin/startxfce4" It was starting Xwindows, that I'm sure of.

---

### Post by TheFu on 2015-05-20
> **MartyBuntu said:**
> You want simple (and secure)?

Use Teamviewer. You'll kick yourself for not going that route earlier.

Will teamviewer work behind the same NAT connection? I don't think the OP intends to access VNC over the internet - at least I hope not. VNC always needs a separate security layer when used over the  internet - ssh tunnelling or openvpn.

There are other compelling remote desktop solutions if you elect to trust a 3rd party. Some claim to handle HiDef streaming video well.

---

### Post by Tadaen_Sylvermane on 2015-05-20
No, just lan use. Problem is solved. All those useless guides I found waste of time. The link you posted gave me the answer. I now have access to kmymoney, my laptop is off. I will try to sell the laptop and get a bigger tablet. Thank you very much.

 Openbox works beautifully by the way. Autostart doesn't seem to be working right but that is a small problem.

---

### Post by Adam_Kleiner on 2015-05-23
Yes, remember that VNC is completely in the clear... Really I personally wouldn't even use it wirelessly over the local network without having it wrapped in SSH. There are SSH clients available for Android, so you can download one of your choice (that you deem trustworthy). If you really insist on using VNC directly over WLAN, make sure you've got at least WPA2 security and the password isn't shared with anyone you don't trust with everything you're going to do on VNC - most routers do have a guest network feature these days that allows you to have a separate password to hand out to guests.

---

