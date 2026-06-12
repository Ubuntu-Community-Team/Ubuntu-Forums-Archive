---
title: "Display Problem AMD64"
date: 2012-11-16
forum: New to Ubuntu
---

### Post by cathobie on 2012-11-16
Trying to run Ubuntu 12.10 (32bit) Live Demo (Try Ubuntu mode) on HP dv6800, AMD64  notebook from iso on DVD.  I get screen splits with repeated overlapping desktop options. I believe it gets to the Welcome Screen but it's too difficult to read with the multiple images.  Any suggestions how to solve the video problem while booting from DVD.

---

### Post by klein de usa on 2012-11-16
maybe trying the 64bit iso and see if that helps

---

### Post by Bashing-om on 2012-11-16
klein de usa; Hi ! Welcome to the forum.

You will have better performance from your machine using a "64" bit install. What you may be experiencing at this time, however, may be a graphics driver issue.

Boot with "nomodeset" option:
Boot the install dvd ->soon as bios screen clears;
depress and hold shift key -> boot option screen;
depress f6 key -> boot options;
choose the "nomodeset" option with arrow key -> enter to accept;
depress f10 key to continue booting....

if you get the gui desk top:
From the launcher on left side of screen (version 12.04) choose System setting ->
Additional Drivers-> choose the recommended drivers to install.

[INDENT]just try'n to help <== BDQ

[/INDENT]

---

### Post by cathobie on 2012-11-16
Thanks!

That did the trick.

The "nomodeset" much change the default video option during boot.

I'm wondering why I never got the screen to Install Ubuntu or run it in Demo Mode?
It ran in Demo mode by default.

Thanks again for the precise procedures.

---

### Post by Bashing-om on 2012-11-17
cathobie; - apologize to both for mixing up the monikers-

Glad you got it working.
On the difference of drivers between demo/actual install: I can not really advise other than the demo runs out of ram, and the install from disk- someone else chime in, is not the driver from "demo" a vesa driver ? ... I presume there is a greater range of drivers available on the install.
 
Then again, with internet connectivity on the demo, are drivers found and installed in the ram environment ?
[INDENT]still learning, even after all these years ==> BDQ

[/INDENT]

---

