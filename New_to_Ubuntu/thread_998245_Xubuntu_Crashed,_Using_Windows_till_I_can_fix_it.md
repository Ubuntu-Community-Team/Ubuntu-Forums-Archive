---
title: "Xubuntu Crashed, Using Windows till I can fix it"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by The Grey Wizard on 2008-11-30
I was playing Guild Wars in wine and when I went to close the window my computer froze. I tried just waiting it out but after leaving it overnight with no response I hard reset the system. I know Xubuntu hates it when you do that, so I scanned my disk with the windows scan. When I went to log back into Xubuntu it stops at the grub command prompt and won't load Xubuntu. Any help? I'm really sick of being back on Windows and I'm eager to get back on Xubuntu. Please and thanks.

---

### Post by The Grey Wizard on 2008-12-01
Anybody even look at this thread?

---

### Post by cardinals_fan on 2008-12-04
Could you provide any more info (error messages, etc.)?

---

### Post by maheshjr2000 on 2008-12-04
this is a Wine complaint. Did you check the wine appdb if anyone has had an issue like this. Also Im pretty sure there is a command to restore grub off a liveCD but I cant reccommend it till I see an error message.

---

### Post by The Grey Wizard on 2008-12-04
No error message, it froze, I restarted it, grub command prompt is all I got.

---

### Post by cardinals_fan on 2008-12-04
> **The Grey Wizard said:**
> No error message, it froze, I restarted it, grub command prompt is all I got.
I can't figure that out.  WINE crashing should have no system-wide effects (assuming it was run as a regular user).

---

### Post by earthpigg on 2008-12-04
> **cardinals_fan said:**
> **_(assuming it was run as a regular user)._**

;)

---

### Post by handydan918 on 2008-12-04
OH NO!! You mean you CAN execute a virus with ```
sudo wine
```?????????



:p

---

### Post by earthpigg on 2008-12-05
ive actually gotten windows malware while playing around in wine.

i lol'd ;)

---

### Post by caljohnsmith on 2008-12-05
Have you run an "fsck" on the Xubuntu partition yet? I would start by doing that; just boot your Live CD, open a terminal and do:
```
sudo fdisk -lu
```
Figure out which is your Xubuntu partition knowing that it is type "linux" under the "system" category. Then do:
```
sudo fdisk -y /dev/sdaX 
```
And replace sdaX with the Xubuntu partition. Please post the output.

---

### Post by The Grey Wizard on 2008-12-06
Damn, I'm too lazy to make a live disk :P Alright, I'll make one when I get time, the burner on this computer is broken.

---

### Post by newbee70 on 2008-12-06
> **The Grey Wizard said:**
> Anybody even look at this thread?

Na, we are all to lazy. 8-)

---

### Post by The Grey Wizard on 2008-12-06
:P Thanks.

---

### Post by phidia on 2008-12-06
Can you boot in recovery mode from the grub menu?

---

### Post by inxygnuu on 2008-12-06
when grub loads up, press escape, and try to see if you can go to the recovery console thingy. If all fails, try inserting the Xubuntu cd as a last resort.

Best regards,
3v4n;)

---

### Post by The Grey Wizard on 2008-12-07
I tried esc, it won't load, I'll get a capture screen and show you. How do you get a capture screen in grub?

---

### Post by Kareeser on 2008-12-07
> How do you get a capture screen in grub?
With a digital camera and a very steady hand. ;)

---

### Post by inxygnuu on 2008-12-07
> **The Grey Wizard said:**
> I tried esc, it won't load, I'll get a capture screen and show you. How do you get a capture screen in grub?

can you press anything? if not, try to get more help, but if all else fails, backup you files, put in the Xubuntu CD, and look for a/the repair option, but that would be last resort.

Best regards,
3v4n

---

