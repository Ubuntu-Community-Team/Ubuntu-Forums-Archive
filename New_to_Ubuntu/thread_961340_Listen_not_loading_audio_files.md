---
title: "Listen not loading audio files"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by worlestone on 2008-10-28
Hi,

I've just installed Xubuntu, which by default uses Listen for audio files.  On loading Listen noting happens.  I've tried changing the preferences to open my music folder and tried reloading the library, but nothing happens!

I have also installed Amarok and all is well with this, working as it should.

Any ideas on getting Listen to play?

Thanks

---

### Post by quirks on 2008-10-28
Try launching it from the command line and see whether it gives you/us some helpful errors.

---

### Post by worlestone on 2008-10-28
The results from running this in Terminal are:

adrian@adrian-desktop:~$ sudo listen
[sudo] password for adrian: 
Error grabbing key 174, 0x9a67408
No iPod support
location: /usr/lib/xulrunner-1.9.0.3/libxpcom.so 
before 3
335 folder monitored


Anyone care to interpret?

---

### Post by quirks on 2008-10-28
Is this what happens when you try to play some songs? Or does this happen, when you just open the program? It would be interesting to know what it says, when you actually try to play music (because this is where it misbehaves, right?). As far as I can tell the program does not report any (serious) errors in the output given.

BTW, you were not supposed to run it as root. Leave the sudo at the beginning away.

---

### Post by worlestone on 2008-10-28
Nothing happens when I try to play songs!

Scrap that, it has now startewd to work, no idea why, I've not chamnged anything or done anything different.  Maybe running as root to start kicked something?

Thanks anyway

---

### Post by cariboo on 2008-10-28
If you run Listen as root, the configuration files are in /root this may lead to problems down the road, run Listen as a normal user, and what you are running into won't happen again.

Jim

---

