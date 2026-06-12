---
title: "Unable to turn cooling device on"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by springerja on 2008-09-07
I have searched this extensivly but have only found solutions after the system has already booted. When I turn on the computer (a Compaq Presario S6300NX Desktop) The Ubuntu loading bar appears, and at about a third of the way through it switches to scrolling text, which ends up being only - 
"ACPI: Unable to turn cooling device [f7c45f18] 'on'"
over and over. I have tried ctrl+alt+f2 and gotten nothing, same with ctrl+alt+f1.

This is the second time that I have reached this error - first time I simply reinstalled ubuntu, and it works fine for the first one or two reboots, but then it goes to this. The first time the only app that I had added was ndiswrapper to hook up my wireless drivers.

Any help would be greatly appreciated - but please make it step-by-step, and include where I would enter anything.

Thank you

---

### Post by Shazaam on 2008-09-07
Looks like a bug. See here...
[http://ubuntuforums.org/showthread.php?t=293963](http://ubuntuforums.org/showthread.php?t=293963)

---

### Post by springerja on 2008-09-07
I've seen that post, and the many others like it. I have no problem turning blacklisting the fan or trying any of the other solutions listed, but how do I input any of those commands? I cannot get out of the screen that is simply scrolling the error message repeatedly.

---

### Post by springerja on 2008-09-07
I managed to get through the boot after running the live desktop cd, re-installing GRUB, and disabling ACPI, then restarting. Then the desktop froze up when I tried to open Network Manager, and when I turned off the computer, waited, and turned it back on I went straight back to the previous issue.

---

