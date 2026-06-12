---
title: "Modems and Evolution"
date: 2011-09-10
forum: New to Ubuntu
---

### Post by mjwk on 2011-09-10
Hi, I'm an absolute beginner at Ubuntu having moved away from Windows due to horrible experiences and now have a separate iMac and also Ubuntu on an old Dell 9160 machine (originally with Windows XP) which I am only likely to use when away at a holiday/work home on a dial up connection (and Broadband is not available). Ubuntu 10.10 is installed.
The problem is two fold. Firstly Ubuntu will not seem to work with the built in Conexant D850 56k V.9x DFVe Modem - it does not recognise it and keeps coming up with "Cannot open modem". The log says:
Wvdial:Internet dialler version 1.60
Cannot open /dev/ttyACMO:no such file or directory
However, I also have a small USB modem - Micronet 2400-2701 and this is recognised and works, albeit incredibly slowly (and much more slowly than a laptop running Windows XP)
Once connected the internet does work but Evolution email won't work. The Send/Receive tab is greyed out and there is no option to tick the 'Work online' tab under the File menu.
I have read much about getting an external modem to plug into a serial port, but that is not an option as there isn't one.
Is there any way to get the internal modem to work? Is there a way to get Evolution Mail to work? Any help would be much appreciated, but please remember that I am a computer dinosaur, so please be gentle!
Thanks

---

### Post by lkraemer on 2011-09-10
mjwk,
There is a chance that it can be made to work.  You need to contact Marvin
and the fine folks at [www.linmodems.org](www.linmodems.org) and start by downloading their
script (ScanModem Tool) to detect the information needed for those folks to
assist you.

You will also need to subscribe to their service (Discussion List) and send
that information as PLAIN TEXT.  That means changing your email account 
setting for Plain text, as that is the ONLY FORMAT they will accept.

They will respond with what will be needed.

The easiest thing to do is locate a Serial, US Robotics Hardware Modem and
use it with a USB to Serial Adapter.

Here is a preview of what you are facing...
[http://ubuntuforums.org/showthread.php?t=1100310&highlight=SM56](http://ubuntuforums.org/showthread.php?t=1100310&highlight=SM56)
Posting #4

It's not a hard process, it just takes a bit of help to keep you going
correctly.  In total it shouldn't take more than 20-30 minutes.

lk

---

