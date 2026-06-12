---
title: "[SOLVED] Installing Sketchup 7 on Wine"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by lightnin on 2008-11-27
Hi

My Wine is 0.9.46

I have downloaded Sketchup7 installer and it fails with the message "This Operating System Is Not Supported"

I have never used wine before - I see others have installed sketchup , so what might I be doing wrong ?

Thanks

---

### Post by C.S.Cameron on 2008-11-27
After installing wine and downloading SU for Windows I right click on it and pick open with wine application.
It installs ok for me but there are tricks getting it to work.
(I have only gotten it working perfect with Nvidia graphics.
Will try to post the other tricks later, but am now stuck in Tokyo trying to get to Bangkok.
I think it works better with wine post 1.0.


EDIT:
After installing with wine,
Go to /home/YOURNAME/wine/drive_c/windows/regedit.exe
expand HKEY_CURRENT_USER
expand software, google, sketchup, glconfig, display and click HW_OK
Change the value to 1.
In wine configuration add SketchUp to applications and set windows version to XP.
open SU and close the startup windows as quick as possible, may need a reboot.

---

### Post by lightnin on 2008-11-28
> **C.S.Cameron said:**
> After installing wine and downloading SU for Windows I right click on it and pick open with wine application.



now that is where I get stuck !  , it doesn't install .

---

### Post by C.S.Cameron on 2008-11-28
This might be worth looking at:
[http://wiki.winehq.org/GoogleSketchup](http://wiki.winehq.org/GoogleSketchup)

---

### Post by lightnin on 2008-11-29
no good for me, but thanks for the link.

I dont get past the installer saying 'wrong OS' !

Whet is the latest WINE for ubuntu ?

I'll try and install something else to see what happens.

---

### Post by Homie Bongo on 2008-12-16
same problem here, any solution?

---

### Post by lightnin on 2008-12-18
I haven't had time to 'play' yet - so , no solution from me, sorry

---

### Post by fsiddique on 2008-12-22
I had the same problem. The version of Wine isn't the problem. If you go to Applications -> Wine -> Configure Wine

...you should see an Operating System drop-box. I believe the default is set to Windows 2000. You must change this to Windows Xp or higher to support Sketchup 7.

Hope that helps!

---

### Post by lightnin on 2008-12-23
thank you

that worked :)

---

### Post by tripundra on 2009-07-24
Has anyone tried sketchUp 7 on a Macbook with the intel GMA gcard?

I've changed the regedit and still nothing and everyone talks about the Nvidia card!

---

### Post by juliomeza on 2010-05-26
Thanks :)
It worked

---

