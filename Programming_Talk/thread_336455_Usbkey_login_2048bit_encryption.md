---
title: "Usbkey login 2048bit encryption"
date: 2007-01-11
forum: Programming Talk
---

### Post by RaZoR-x11 on 2007-01-11
Hey, 

First off i was thinking about make a login manager like GDM login but with a difference instead off using user name and password's use a usb stick / key / thub / which would have the 128,256,512,1024,2048 encryption key basic as a file say .key.2048 so the os would find it and ur username and password aka 2048 encryption code in the file,

i am trying to find way's i made one for window's 9x and me but linux is a new ball game to me im just wondering what any off you think this is a good, bad, stupid, whatever idea,

Ohh and allso instead off sudo... using a usb-key to access root?


Any idea's please.
:D:-k:eek:
RaZoR

---

### Post by slavik on 2007-01-11
the idea is interesting and should not be difficult once you can get a C/C++ program to actually read in this information.

Here are some troubles I see you might run into:
- there is no automounting without X
- you will have to write your own login manager (or modify GDM, I suggest writing your own as proof of concept and then attempting to modify GDM)

if your program is ran in daemon mode during start up (meaning it has root access) then it should not be a problem.

Some solutions:
- for the automounting problem, you can write a simple perl script that would get the messages from dmesg and would look for the usb device to mount it
- login manager shouldn't be difficult as it can be very small, since you need very little functionality (read file on usb drive, decrypt, log in the user)

---

### Post by tommie-lie on 2007-01-12
Gdm and especially pam is highly pluggable, I'd suggest writing a pam plugin for authentication. For instance, there is an already existing pam_bioapi module that provides functionality to log in with a fingerprint scanner (or other BioAPI devices). It certainly would be less work compared with implementing your own full-blown display manager.

---

### Post by RaZoR-x11 on 2007-01-13
Thank you both for the reply, i am going to finish my own login manager
as i will no the code etc... makes it easier to work with making plug-ins etc
anyway cheer's

RaZoR;)

---

