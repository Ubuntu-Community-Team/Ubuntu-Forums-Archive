---
title: "Making a webpage load at system startup"
date: 2006-08-18
forum: Programming Talk
---

### Post by ajred on 2006-08-18
Hi there. 
I'm looking to setup a kiosk like scrolling webpage. I'm able to make the full screen scrolling web page.
What I need to happen is, in the  case of power outage, make the system automatically login without authentication. Also, I need my scrolling web page to load automatically when the system starts up.  Is this possible?    

Thanks in advance

---

### Post by philipacamaniac on 2006-08-19
Sure, that's as easy as a writing a simple script that opens firefox with a fullscreen option. Then just add that script to your session startup (System -> Preferences -> Sessions). 

Another way is to actually create a script that starts X without GNOME or KDE, but only the browser, or only a browser and a simple window manager like TWM.

It sounds like you're trying to create a public kiosk. You should check out
[http://openkiosk.sourceforge.net/](http://openkiosk.sourceforge.net/)

---

### Post by Colonel Kilkenny on 2006-08-19
> **ajred said:**
> Hi there. 
I'm looking to setup a kiosk like scrolling webpage. I'm able to make the full screen scrolling web page.
What I need to happen is, in the  case of power outage, make the system automatically login without authentication. Also, I need my scrolling web page to load automatically when the system starts up.  Is this possible?    

Thanks in advance

I suggest using Opera as a browser because it has very nice kiosk-mode built in.

Check out [http://www.opera.com/support/mastering/kiosk/](http://www.opera.com/support/mastering/kiosk/)
Automatic login is easy and some sort of script to launch opera at the start should be also piece of cake.

---

### Post by ajred on 2006-08-20
Thanks for the responses,  i'm gonna try and get this working today ! =)

---

