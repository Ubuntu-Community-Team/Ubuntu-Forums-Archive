---
title: "Having some trouble with rdesktop / Terminal Server Client to Windows machines"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by kalibar on 2008-06-26
Hey all, long-time Windows and OS X user but recent Ubuntu-convert-hopeful here. :) I have several Windows machines that I hit remotely: mine and my fiancee's gaming PCs, my headless Win2K3 fileserver (with a very fussy thermal printer attached to it), and a new Windows Server 2008 machine loaded with proprietary software that I help my dad manage remotely for his business.  I have a few questions about tsclient/rdesktop usage that I'm wishfully hoping you guys will be able to help me out with, as a few resolutions would greatly enhance my Ubuntu experience.

[LIST=1]
[*]**Is it possible to display the desktop background and to "show window contents while dragging" on the remote machine?** I didn't see options for them and couldn't figure it out from Googling, either. This isn't hugely major or anything, but I prefer to see them both when connected to machines on my LAN. 
[*]**Is it possible to open .rdp connections directly from my window manager?** When I double-click an .rdp connection in ~/.tsclient, it opens with gedit and right-click -> "Open with other application" doesn't present Terminal Server Client or rdesktop as options. I added the Terminal Server Client applet to my panel and while it's alright, I'd really prefer the ability to open the .rdp files directly and ultimately to index them with GNOME Do -- I have this setup working under OS X through RDC:Mac and Quicksilver, and it's been amazingly fast and convenient for me. I type 2-3 keystrokes, press Enter, and I'm connected.
[*]**Is it possible to define a single key-combo that takes precedence over the remote session in full-screen?** RDC:Mac works like this by default: I can Command+Tab to apps on my local machine while inside a remote session, but Alt+Tab between Windows apps on the remote session still works fawlessly. If I could tell tsclient to allow Super+Tab to let me switch between other apps (without having to hit Ctrl+Alt+Enter first each time), that would be really neat.
[*]**How can I make tsclient connect to Windows Server 2008 in RDPv5?** This might be a Microsoft problem, but it's not one I've had to troubleshoot before now, since RDC:Mac and the Windows XP Remote Desktop client obviously both connect to Server 2008 flawlessly. Selecting RDP in tsclient works, but it won't allow me to connect my local disk and WindowsKey+R doesn't work properly in my remote session (sounds minor, but "Run" and Launchy are basically the only ways I nav myself around on Windows machines). When trying to connect using RDPv5 and ensuring that the en-us keyboard is selected, I receive this message: *ERROR: Failed to extract public key from certificate*. Some Googling has led me to believe that Server 2008 is employing some kind of new encryption that rdesktop may not understand, but I couldn't find a concrete resolution. Any help on this would be appreciated.
[/LIST]Thanks in advance for the help. This is such a great community, and searching for stuff here has already solved a ton of little things for me.  I'm looking into setting up UltraVNC on a few of my machines here to at least partially factor out tsclient/rdesktop, but to be honest I've been extremely pleased with RDP in the past and am only slightly excited to try out alternatives.

Thanks again!

---

### Post by cprofitt on 2008-06-28
> **kalibar said:**
> 
[LIST=1]
[*]**How can I make tsclient connect to Windows Server 2008 in RDPv5?** This might be a Microsoft problem, but it's not one I've had to troubleshoot before now, since RDC:Mac and the Windows XP Remote Desktop client obviously both connect to Server 2008 flawlessly. Selecting RDP in tsclient works, but it won't allow me to connect my local disk and WindowsKey+R doesn't work properly in my remote session (sounds minor, but "Run" and Launchy are basically the only ways I nav myself around on Windows machines). When trying to connect using RDPv5 and ensuring that the en-us keyboard is selected, I receive this message: *ERROR: Failed to extract public key from certificate*. Some Googling has led me to believe that Server 2008 is employing some kind of new encryption that rdesktop may not understand, but I couldn't find a concrete resolution. Any help on this would be appreciated.
[/LIST]
 
Thanks again!

In server 2008 you have three options for RDP. At this point I have not been able to use the most secure option which specifies RDP with network level authentication (AD I believe), but if I select the option to allow any version of RDP it works.[IMG]http://mtoo.mvps.org/images/ws2008-initial21.jpg[/IMG]

---

### Post by kalibar on 2008-06-29
Hey, thanks for the reply -- I appreciate it. :)

Yeah, that was the first setting I checked.  Still no love on RDPv5, but that's what allowed generic RDP to work.  Are you using 32-bit Ubuntu?  I'm using the AMD64 release of Hardy and while I hate to start blaming 64-bit for my problems, I'm half-tempted to try the 32-bit version just to see how much stuff (if any) clears up.

Any advice on the rest of the issues? Thanks again for taking the time, it's quite helpful.

---

