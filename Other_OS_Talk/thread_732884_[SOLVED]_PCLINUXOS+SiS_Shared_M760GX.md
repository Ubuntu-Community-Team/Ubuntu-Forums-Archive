---
title: "[SOLVED] PCLINUXOS+SiS Shared M760GX"
date: 2008-03-23
forum: Other OS Talk
---

### Post by Arwen on 2008-03-23
Hello everyone!

I have an acer Aspire 5003WLMi laptop with that graphics card on and I've installed pclinuxos.It's not a big problem but I can't change the screen resolution to 1024x1280 which is the most "eye-friendly" in my laptop.I suspect I need to install a driver for the card but I have no idea where to find it (if it exists).Can someone tell me how to solve this?

Thanx for any answer!

---

### Post by seanc7 on 2008-03-23
I haven't used PCLinuxOS in a while now. Are you using the GUI to change the resolution?

I've found a lot of times the GUI won't change the X server resolution properly. You need to login to a command line only and change it.

If I recall correctly, PCLinux is Debian-based or Ubuntu-based not sure which, so you can use this command to reconfigure the resolution.

As root or using SUDO type the following:

"dpkg-reconfigure xserver-xorg"

Note that this will prompt you to configure your keyboard, mouse, monitor, video card and available resolutions.

After doing this, restart KDM or GDM (/etc/init.d/gdm restart OR /etc/init.d/kdm restart).

You should be running at the resolution you want.

---

### Post by Arwen on 2008-03-23
I stronlgy believe It is based on Mandrake and I don't think sudo works.I'll try it though.
I tried to change the resolution by control centre ,it said I should log out and log back on for the changes to take effect but nothing happens.I'll do "dpkg-reconfigure xserver-xorg" and 
"/etc/init.d/kdm restart" and see what will happen.

Thank you for your answer

---

### Post by seanc7 on 2008-03-23
Actually, if it's based on Mardrake, those might not work then.

Since Mandrake is RPM-based not DEB-based. the DPKG-RECONFIGURE utility wouldn't be there. I don't know what the RPM equivalent is.

SUDO is just the command for running commands as root without having to SU or login as root.

To fix this, you'll need someone more experienced in PCLinux or in how to manually configure the X Server config file.

---

### Post by Arwen on 2008-03-24
After reading a lot of stuff and really not understanding a 90% of them all,I decided to improvise a bit:guitar:
I modified (as root)the file XF86Config in /etc/X11 where it said sth about :

Subsection "Display"
Depth 24
Modes "1280x800" "1152x864" ... etc

I wanted "1280x800" so I simply replaced "1280x960"
that previously existed there.Fortunately it worked but it's weird to modify that file.I tried to modify xorg.conf first but it didn't work.I'm not complaining though :-P

To be honest,PCLOS still recognises my card as SiS Real 256E but as long as everything is OK now,I think it's not a problem.

---

