---
title: "Palm m125 hotsync"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by Sheneron on 2008-08-09
Hi, I am fairly new to ubuntu and do not know much of anything, hence the location of this thread.  Yet I am learning so bear with me.

I recently bought a palm pilot m125 and it came with a usb hotsync cradle.  I can't seem to get it to work with the computer, and I always get this error message.  "The connection between your handheld computer and the desktop could not be established.  Please check your setup and try again."

I have a computer with windows on it, and it does this same thing.  The usb is plugged in correctly and the palm pilot is on the cradle correctly.  Also, the usb ports work on both computers because I have tried usb drives in them.  I am not really sure what it is, but I would appreciate any help.
Thanks.

---

### Post by SlalomMan on 2008-08-09
I had an m125 once, and now a TX. They're always pretty finnicky when it comes to computer connections; I've never tried to sync with ubuntu. I think that your best bet would be to make sure that you have USB selected; sometimes in the palm desktop software it defaults to serial. I'm not totally sure how the palm utility for Ubuntu works, though.

I use network sync with my TX, and i'm pretty sure that the m125 doesn't have that.

The thing you should probably try is to run "lsusb" from a terminal and see if your palm pilot even shows up in Ubuntu; if not, you can blame the usb cable, I think.

Have you tried going to System->Preferences->Palm OS Devices? That may work for you.

Hope this helps.

---

### Post by Sheneron on 2008-08-09
Thanks for the fast reply.

That seemed to work and it would hotsync, but kpilot wasn't working.  I restarted my computer, and now I get this error whenever I try to hotsync it.

Failed to connect using device 'Cradle' on port '/dev/pilot'.  Check your configuration, as you requested old-style usbserial 'ttyUSB' syncing, but do not have the usbserial 'visor' kernel module loaded.  You may need to select a 'usb:' device.

---

### Post by Sheneron on 2008-08-09
Well I got that problem fixed by doing # sudo modprobe visor

But now I can't get it to work with kpilot.  Kpilot just doesn't even see that its there I guess.  Whenever I try to do the configuration wizard with the palm it times out.

---

### Post by ianchristie on 2008-09-02
I just got my M125 to hotsync after reading through this thread. I decided to select usb: instead of /dev/pilot and that seemed to work perfectly.

---

### Post by ianchristie on 2008-09-02
Well, seens it only worked once and now I can't get it to sync.

---

### Post by ianchristie on 2008-09-02
Well, seems I can only get it to sync properly when I tell the Palm utility to get info from the pda or send to the pda

---

