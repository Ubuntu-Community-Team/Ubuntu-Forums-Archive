---
title: "Vista/Hardy Networking"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by petrophase on 2008-05-11
I'm a linux newbie. I have a desktop and laptop, both dual boot with Ubuntu 8.04 and Vista. I've been able to share files across all combo's except from the Ubuntu desktop to the Vista laptop. That is, my laptop Vista sees another computer on my network, but doesn't know its name, and it is not accessible to Vista. So I can't access any of my Ubuntu desktop shares on the Vista laptop. 
I'm doing all this via samba. Thus far I've been able to avoid manually editing the smb.conf. I can't get to swat via 127.0.0.1:901, even though it's supposed to be installed, and system-config-samba crashes when I open it.
This is all for my home network, so it's not too critical, but it is very annoying that I have networking in all directions but this one. Help, please?

---

### Post by peitschie on 2008-05-13
What error messages appear if you open system-config-samba from a terminal?  I suspect you are seeing this error:  [https://answers.launchpad.net/ubuntu/+question/31292](https://answers.launchpad.net/ubuntu/+question/31292)

To actually share a folder though you don't need this program.  All you need to do is to right-click on the folder you want to share, and go down to "Sharing Options" and set the details there.  Or is that what you tried that didn't work properly...?

What do you mean by vista not knowing the name of the Ubuntu computer?

---

