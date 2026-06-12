---
title: "Resolving audio problems in Intel HDA / Netbook"
date: 2017-05-10
forum: New to Ubuntu
---

### Post by mfbruno on 2017-05-10
Hello guys, i'm an lubuntu user about a year now, but not a advanced one, far from it actually.
A problem have haunted me since i decided to go linux on my modest netbook: The headphone volume controlling the speakers volume, which results in mute sound every boot.
The specs:


> 
-Computer-
Processor        : 2x Intel(R) Atom(TM) CPU N2100   @ 1.60GHz
Memory                : 2034MB
Operating System        : Ubuntu 17.04
-Display-
Resolution        : 1024x600 pixels
OpenGL Renderer        : Unknown
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : HDA-Intel - HDA Intel (NM10/ICH7 Family)
-Input Devices-
 HDA Intel Mic
 HDA Intel Headphone
-SCSI Disks-
ATA OCZ-VERTEX4



Well, after extensively look for some solution in the forums and only finding workarounds, i decided to go berserk and purged the pulseaudio and pavucontrol. It worked, like a charm, the audio is exactly how it's supposed to be. But, of course, i found a problem... as expected to happen, the audio tray has gone. To resolve this, i installed QasMixer:

>  sudo apt-get install QasMixer 

Then, in Preferences > LXSessions apps go to startups aplications and add
 > qasmixer --tray

Now everything seems fine, but after running some tests i note that is the "headphone" value who still controls the speakers, but now at least works ok, doesn't start without sound and the QasMixer really help.

So, am i missing something here? Or i actually learned and achieved something in Lubuntu troubleshooting? Because i'm feeling really proud of myself :o

Anyway, maybe this is still a workaround, maybe there is a better sollution in the depts of the internet, but i wanted to share anyway.

Oh, Lubuntu is 17.04
And sorry for my english, it is not my native language :(

---

