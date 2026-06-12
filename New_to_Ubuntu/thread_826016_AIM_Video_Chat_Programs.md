---
title: "AIM Video Chat Programs?"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by polotip on 2008-06-11
So I am looking for a program which can use AIM Video chat...  Skype works, but my friend is on AIM, so I need to use AIM.  Is there anything available on UBUNTU which will allow this?!?!?!
Thanks,
Brian

---

### Post by Daveth on 2008-06-11
any of this

[http://www.nirmaltv.com/2008/04/19/18-multi-protocol-im-clients-for-windows-mac-and-linux/](http://www.nirmaltv.com/2008/04/19/18-multi-protocol-im-clients-for-windows-mac-and-linux/)

any use?

---

### Post by polotip on 2008-06-11
I dont think any of the ones supported by linux have video chat...

---

### Post by MmmmJoel on 2008-06-12
> **polotip said:**
> So I am looking for a program which can use AIM Video chat...  Skype works, but my friend is on AIM, so I need to use AIM.  Is there anything available on UBUNTU which will allow this?!?!?!

None for AIM, but keep your eye on [Empathy]("http://live.gnome.org/Empathy"). It already does video for Jabber.

---

### Post by guitarman_usa on 2009-10-22
There's a solution that's not completely pure AIM video chat, but its one that has worked rather well for me.  There's a plugin for pidgin called Fonomo Video.  It adds a webcam icon to the conversation window and launches a webpage that you can use to video chat with someone else using Flash.  

If you go this route, make sure you grab 0.1.16 from 
[ftp://ftp.grokthis.net/pub/fonomo/pidgin-fonomobutton-0.1.6.tar.bz2]("ftp://ftp.grokthis.net/pub/fonomo/pidgin-fonomobutton-0.1.6.tar.bz2")
or else you'll probably run into some compiling errors using the ./configure, make, #make all install, make install-user method outlined in the install guide.

Also, for some reason it grabbed a very large (128x128 ) icon from my theme so to force the nice small one that's included you can just delete the "camera-webcam" string on line 91 of fonomobutton.c before you compile.

---

