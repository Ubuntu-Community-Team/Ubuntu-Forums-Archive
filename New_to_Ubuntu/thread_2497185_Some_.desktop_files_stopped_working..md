---
title: "Some .desktop files stopped working."
date: 2024-04-26
forum: New to Ubuntu
---

### Post by m-elodie on 2024-04-26
Hello!

Not really new to Ubuntu, but new to Ubuntu24 which is new itself.

I'm uisng .desktio files for application refusing to be pinned to taskbar.
Some are working, some are not.
For instance Quartus (FPGA development) works fine and the app starts when double-clifking
the .desktop file icon.
I also sometimes use Arduino for junior high school kids teaching, and this one doesn't work.
Double-click doesn't do anything. But double click on the file (arduino-ide_2.3.2_Linux_64bit.appimage)
runs fine (it compiles, loads the image onto the board and executes without any problem).
I'm also sure that the path is correct since it was working in Ubuntu 23, and beside this, the
path in the .desktop file corresponds to the IDE location.

Does anybody know what's wrong?

Thanks.

Elodie.

---

### Post by psychohermit on 2024-05-05
What happens if you enter from command line path-to/arduino-ide_2.3.2_Linux_64bit.appimage?

--glenn

---

### Post by m-elodie on 2024-05-11
Hello!
Sorry for the delay.
If I use the path which is in the desktop file which in my case is ~/Applications/arduino-ide_2.3.2_Linux_64bit.appimage,
I get a core dump
As for the readable message, it says: The SUID sansbox helper binary was found, but is not configured correctly. Rather than running without sandboxing, I'm abording now.
you need to make sure that /tmp/.mount_arduinRzskts/chrome-sandbox is owned by root, etc, etc.
Problem: there is no .mount_arduinRzskts in /tmp

Beside this, double-cick on that application works fine.

Thanks,

Elodie.

---

