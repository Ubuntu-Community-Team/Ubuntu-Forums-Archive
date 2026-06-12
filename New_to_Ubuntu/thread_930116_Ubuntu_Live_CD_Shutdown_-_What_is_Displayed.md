---
title: "Ubuntu Live CD Shutdown - What is Displayed?"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by KAWill70 on 2008-09-25
I am running the Live CD version of Ubuntu 8.04.1 that was created from an ISO file.

What should display during Shutdown?

My system goes to a black screen quite quickly and only a few lines of text are displayed.  Eventually it gets to a little line type cursor and that is about it.

Hitting Carriage Return moves the cursor down, and sometimes I see some text about restarting.

Is this normal?

Maybe there is some incompatibility in my system or BIOS. 

Thanks,  Kent

---

### Post by nvance on 2008-09-25
When you go to shutdown your system when using the live CD, it should bring you to a logout screen then prompt you to eject the CD and press Enter.
If you are not seeing this, it could be something with your hardware or possibly an issue with the ISO burn that is on your cd.  Have you checked the CD for errors (option is available when you boot off the cd).

Hopefully this helps a bit.

---

### Post by KAWill70 on 2008-09-26
Thanks for the help.

I booted the Live Disk after seeing your note and ran the CD Check.  No errors were found.  I also verified the MD5Sum before I wrote the CD.

When I shut down Ubuntu I click on Quit and it does bring up a Window where I click Restart or one of the other options.

After about 1-2 seconds the screen goes black and a bit later I see some text messages being displayed.  At 18 seconds the CD drawer opens and I assume shutdown is complete.  However, nothing further happens.

I can hit Carriage Return several times and it typically displays something about Restarting.

The last instance displayed a code:  321.617682

I have to hit Reset on the Computer to reboot.

Regards,  Kent

---

### Post by NullHead on 2008-09-26
You should see the ubuntu logo, like when you booted. Once you've installed ubuntu, you can use a tool called "startup-manager" to change the resolution of those images. The resolution is probably off, so it's errors on shutdown for some reason.

---

### Post by KAWill70 on 2008-09-26
The comment on possible image problems was a help - thanks.

I booted using the Safe Graphic Mode option, and now I do see the Ubuntu logo on Restart and Shutdown.

Shutdown actually works, but Restart for some reason does not and I have to hit the reset switch on the computer.

---

