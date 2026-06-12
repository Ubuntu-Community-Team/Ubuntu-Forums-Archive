---
title: "When trying to boot installer Busybox shows up don't know what to do"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by Jack the amazing on 2008-08-28
when i boot the installer in normal mode it goes into a DOS(sorry dont know what else to use) like screen with BusyBox v 1.1.3 (Debian 1:1.1.3-5ubuntu12) on the top below this intramifs

---

### Post by phidia on 2008-08-28
It would be helpful to see other error messages that come up if any.
Often this is related to hardware-there are lots of [hits]("http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:unofficial&q=BusyBox+v+1.1.3+(Debian+1:1.1.3-5ubuntu12)&start=0&sa=N") searching the "BusyBox..."
entry you included.
Have you tried pressing the Ctrl+d keys and also waiting a bit? Sometimes boot will resume-if this is due to hardware that's slow to respond.

---

### Post by nicedude on 2008-08-28
Also if you are using the live CD you may find out that you need the alternate CD instead as it boots on some systems that won't boot with the live CD.

---

### Post by Daveski on 2008-08-31
This can happen if the CD you installed from has an error. Best to check the CD and/or burn a new one at a slow speed.
Failing that, this could be a symptom of a hardware problem (like a failing disk), or the fact that the installed OS is somehow not able to read the main boot partition - there is a potential workaround you can try:

Press **F6** at the boot up screen.
You should see a line ending with *"--quiet splash."*
Delete --quiet splash, add the option **noapic** after **ro** so you have **ro noapic**

Hit enter to boot.

If this does not work, try **all_generic_ide** instead of **noapic**

See these threads:
[http://ubuntuforums.org/showthread.php?t=854618](http://ubuntuforums.org/showthread.php?t=854618)
[http://ubuntuforums.org/showthread.php?t=844288](http://ubuntuforums.org/showthread.php?t=844288)

---

