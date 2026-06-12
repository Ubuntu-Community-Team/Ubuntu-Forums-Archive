---
title: "Linux on Pocket PC"
date: 2006-12-31
forum: Other OS Talk
---

### Post by shanepardue on 2006-12-31
Have you installed linux on a pocket pc? If so, tell me your experiences with it. What are the benefits from doing such a thing. I'm interested, but I haven't heard any testimonials.

---

### Post by Frak on 2006-12-31
I've heard some good with [Xanadux]("http://wiki.xda-developers.com/index.php?pagename=Xanadux").

---

### Post by jdhore on 2007-01-01
Familiar Linux is pretty damn good IMO...i use it on my HP iPaq hx2495

---

### Post by paridoth on 2007-01-13
I have been trying to get linux on my ipaq H3800 for days now, the guide at handhelds.org has just been confusing and lacking for me, i have the bootloader installed, however im stuck at using kermit, they dont give any information on how to use it, i was wondering if you or someone else could help me out? im basicly trying to figure out how to change the settings in kermit to the ones they specified

"115200 8N1 serial configuration, no flow control, no hardware handshaking"

and wether or not i have to do anything special to get kermit to recognize my ipaq, i have it in the cradle and conected to my computer running ubuntu 6.10 via the serial cable, i am at the bootldr screen, and i have pressed"serial boot loader console" i have kermit installed and open, now what, what commands do i use?

thanks for any help you can offer

---

### Post by marx2k on 2007-01-14
I literally have not heard of or thought about the Kermit protocol for 10+ years. WHOA.

---

### Post by paridoth on 2007-01-14
should i be using something else? it usgests minicom as well, i just thought kermit sounded cooler

---

### Post by marx2k on 2007-01-14
Kermit was a file transfer protocol back in the day...looks like it's still used for things.  Bit as I remember, and I may be wrong, but it had no error checking functionality... which is why Kermit (and Xmodem, YModem and others) were replaced by ZModem and Super ZModem (with tetris!)

Wow, that takes me back.

---

### Post by paridoth on 2007-01-14
i could still use some help getting this working, this is the section from the hanhelds.org guide that i am stuck on

> Press the calendar button on the iPAQ. This is the leftmost action button, labelled "Serial Bootldr Console" on the screen.
#

Make sure the terminal emulator is up and running, and is properly interacting with the bootloader. Proper interaction consists of being able to issue commands, and get responses (e.g. the help command should return the bootloader usage). Your terminal emulator must be set to 115200 8N1 serial configuration, no flow control, no hardware handshaking. Failing to use these settings will lead to trouble, so double and triple check all settings.

If you cannot interact with the bootloader, make sure your terminal settings are correct, the iPAQ is properly connected to the host computer, and the iPAQ is actually on. If everything seems fine, try restarting the host terminal emulator and resetting the iPAQ again.

#

At the "boot>" prompt, issue the following command: load root
#

Proceed to send or "upload" the jffs2 file (from the tarball that you downloaded earlier) with ymodem, using the terminal emulator. If you have not used ymodem before or you have any trouble with this command, please see handhelds-faq/getting-started.html#USING-XYZMODEM.

Note that the bootldr now expects ymodem by default, not xmodem as in earlier versions. If you are unable to use ymodem for some reason, you can revert to xmodem operation with the command set ymodem 0 

i have my ipaq sitting on the bootldr screen and i have it waiting for a serial connection ( i pressed the calender button" the serial port is pluged in ... now what? i start up kermit, but i dont know what to type to get it to conect to the ipaq, and i dont know how to change the settings as it sugested above.

---

### Post by croppyboy on 2007-01-14
I just installed opie on my iPAQ 3835 and it was pretty easy . . . after I started using minicom . . . I wasted a few hours trying to get kermit working  . . . 

I just followed this guide and downloaded minicom from the repos . . .
[http://familiar.handhelds.org/releases/v0.8.4/install/]("http://familiar.handhelds.org/releases/v0.8.4/install/")

this might also help: [http://www.dcglug.org.uk/wiki/?id=view/dist-reviews%2Fmisc%2F4]("http://www.dcglug.org.uk/wiki/?id=view/dist-reviews%2Fmisc%2F4")

Now I just have to figure out how to get Edgy to recognize it when I connect . . .

---

