---
title: "Agere Systems HDA modem"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by dizz1s4u on 2008-08-25
Hello all,
I have run into some issues getting my modem to work.  I downloaded the scanModem program and it ran.  I sent the file off to [email]discuss@linmodem.org[/email] and they helped some.  Now I run the sudo slmodemd -c USA  --alsa hw:0,6
and it says:
SmartLink Soft Modem: version 2.9.9e-pre1 Sep 30 2007 00:07:03
symbolic link `/dev/ttySL0' -> `/dev/pts/2' created.
modem `hw:0,6' created. TTY is `/dev/pts/2'
Use `/dev/ttySL0' as modem device, Ctrl+C for termination.

Then I can open KPPP and it says modem ready, dialing, ...no carrier.

I have good dial tone and it works in Windows.  Any thoughts on what I am missing?  Someone suggested drivers, but where can I get those?

---

### Post by candtalan on 2008-08-25
sometimes a messaging system in the house can disturb things particualrly if a message is stil waiting to be heard - the dial tone will be non standard.

---

