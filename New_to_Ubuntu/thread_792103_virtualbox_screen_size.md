---
title: "virtualbox screen size???"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Fenris_rising on 2008-05-12
hi all

ive just installed virtual box on 8.04 to host XP (eek!) so i can
run google sketchup without having to leave my beloved ubuntu (you just know im a newby now dont you!) got it all working fine luckily. but my query is
the virtual screen/window is abit small. the window can go full screen but the app contianed within stays fixed. is there a fix for this or is that just the way it is?

cheers

---

### Post by sdennie on 2008-05-12
Depending on how you've installed VirtualBox, you should have a menu option Devices->Install Guest Additions.  If you install that, you should be able to resize the window to any arbitrary size and Windows will update to fill the window.

---

### Post by Fenris_rising on 2008-05-12
ahh! i saw that at the bottom of a dropdown list i think. ill try it tomoz.
thanks for your speedy reply.

---

### Post by lakelovers on 2008-05-12
I have the same question and followed the instruction to go to "Device" drop-down menu to install the add-on's but there was an error during the installation and a warning if I continued the system might be effected. Did you run into the same thing and if so, how did you proceed?

---

### Post by Fenris_rising on 2008-05-13
well guest additions didnt do it for me. i presume this may be to do with the way i installed it. however by right clicking in the virtual XP screen i went as you would normally into the properties > settings and changed the resolution from 800 x 600 to 1154 x 864. this made my virtual window just slightly smaller than the 'real' desktop. all i need to do now is sort out how to share a common area so i can pass info/documents between the virtual and real OS.

---

### Post by sdennie on 2008-05-13
Fenris_rising, you may have to play around with the Machine->Auto Resize Guest Display option to get the dynamic guest display size to work.  Also, if you go to Devices->Shared Folders, you can add folders that are visible within the VM just as if they were shared over the network.

lakelovers, I think it's safe to ignore any warnings on the Guest Additions.  If you want to be sure, you can take a snapshot of the system before installing and, if it doesn't seem ok after installing the additions, just revert back to that snapshot.

---

### Post by teamkiller87 on 2008-05-13
I know this might sound stupid, but after installing Guest Additions did you hit Host+F (by default Host is Right Ctrl) to go into Fullscreen Mode?

---

### Post by Fenris_rising on 2008-05-13
@ vor. thanks for that i'll give it a try l8r.
@ teamkiller. i tried that, i got a fullscreen window but xp didnt expand to fill it. my solution posted above seems to be permanant so its all A-OK
here. gawd i love Ubuntu.

---

### Post by mr2v6 on 2008-08-23
I too have a similar problem, when I click Devices > Install Guest Additions, ... nothing happens.  

Does anyone have the same experience and have information as to why this happens?

thanks,
MR2V6

---

### Post by paulspignon on 2009-03-30
All the postings are a bit old here so my humble contribution may be no longer be of interest, but here goes.

XP (SP2) host, Debian "Lenny" (jeez, who comes up with these names?) guest, VirtualBox 2.1.4
To install Guest Additions or do anything with VBoxManage the guest must be in the "powered down" state - otherwise command-line invocations of VBoxManage will say the guest is "not mutable" and do nothing, the GUI will just do nothing.
OK, fixed that, then had that problem with the guest window not filling the whole VM window, regardles of Ctrl+F.
Found out that VBoxClient has to be running, and it usurps the normal X11 configuration. In my case it lives at /usr/bin. Now have it start automatically on boot-up.
VirtualBox documentation says nothing about these points - very poor Sun!

/Paul

---

