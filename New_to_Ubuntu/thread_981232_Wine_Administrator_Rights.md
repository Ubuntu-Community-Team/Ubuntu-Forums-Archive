---
title: "Wine Administrator Rights"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by Chesamo on 2008-11-13
I have seen this question posted a few times on here, but I've yet to find a solution that has worked.

I need to install a program that requires Administrator rights to run the setup program (dBpoweramp Music Converter). Changing the emulated Windows type to Windows 98 *does not work*. Please don't suggest I just use ffmpeg, for some reason I can't get it to work. (I know that's what I would do) I also need this for future reference in case a different program needs them ;)

I'm somewhat confused as to why Wine doesn't emulate Admin rights in the first place, but then again I'm not a developer.

---

### Post by compiledkernel on 2008-11-13
[http://wiki.jswindle.com/index.php/General_Wine_Troubleshooting](http://wiki.jswindle.com/index.php/General_Wine_Troubleshooting) -- has a clause about Admin privledges. 

Which suggests the same thing youve attempted already. 

What errors do youa actually see when you attempt to run the installer?

Also some interesting bits here -- [http://appdb.winehq.org/objectManager.php?sClass=version&iId=9492](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9492)

---

### Post by Chesamo on 2008-11-13
The only error I get is "Warning! This program requires Administrator rights to install. Do you wish to continue? The program may not have full functionality." Hitting "Yes" installs, but the program doesn't even load. even if I type ```
sudo wine "/home/tony/.wine/drive_c/dBpoweramp/MusicConverter.exe"
``` nothing happens. I don't get messages in Terminal, and it just closes and dumps me back at prompt.

EDIT: I found a program in ../drive_c/windows/system32 called UninstallSpoon.exe (Spoon is the installer used by dBpoweramp) and ran it. It gave me an install prompt, so I installed it and it works fine.

Weeeeiirrd.

---

### Post by compiledkernel on 2008-11-13
ok well lets go another route then, what are you attempting to convert to/from?

---

### Post by Chesamo on 2008-11-13
> **compiledkernel said:**
> ok well lets go another route then, what are you attempting to convert to/from?
Two things:
One, the program started working (as stated in my post above) and two, I figured out a better method.

The whole situation (for those concerned):
I stream music from my server to a SHOUTcast server using sc_trans, and I was trying to resample my music from 48 kHz to 44.1 kHz (since sc_trans only accepts 44.1 kHz at the moment). That would involve converting from mp3 to wav, then back to mp3. I was going to use this converter program to so it, but I found a way better way to do it involving MPG123 and LAME. Thanks for the quick reply, but it's no longer needed ^.^;;
[http://chesamo.blogspot.com/2008/11/now-was-that-so-hard.html](http://chesamo.blogspot.com/2008/11/now-was-that-so-hard.html)

---

