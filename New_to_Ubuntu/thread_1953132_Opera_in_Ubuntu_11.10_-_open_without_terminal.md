---
title: "Opera in Ubuntu 11.10 - open without terminal?"
date: 2012-04-05
forum: New to Ubuntu
---

### Post by theducksfan2010 on 2012-04-05
I downlaoded and installed Opera: Opera 11.62 for Linux x86-64 from: [http://www.opera.com/browser/download/](http://www.opera.com/browser/download/)  and it installed using the Ubuntu Software Center. But when I go to Dash home and type in Opera, I get nothing. I have to open a terminal and:

office@office-GN584AA-ABA-m9060n:~$ opera

(opera:9183): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(opera:9183): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(opera:9183): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(opera:9183): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

then Opera opens up. I have Opera on 2 different Lubuntu 11.10 computers and on my laptop running Ubuntu 11.10 and I don't have this problem on any of them. How do I get the Opera icon to show up in installed programs, or the dash home or open it other than with the terminal.

If I click on keep in launcher, while it is open and then close Opera, it still shows up in the launcher, but clicking on it will not open Opera up.

---

### Post by Frogs Hair on 2012-04-05
I can only suggest reinstalling , like your other installations Opera works fine for me. I used the GDebi package installer and not the software center for installation. If you have synaptic installed you can mark Opera for re-installation and apply the change there. Open hidden folders in the file browser and remove the .opera file before reinstalling.

---

### Post by theducksfan2010 on 2012-04-05
> **Frogs Hair said:**
> I can only suggest reinstalling , like your other installations Opera works fine for me. I used the GDebi package installer and not the software center for installation. If you have synaptic installed you can mark Opera for re-installation and apply the change there. Open hidden folders in the file browser and remove the .opera file before reinstalling.

Ok, so I went back into Ubuntuu Software Center and uninstalled Opera. I then went into the downloads folder and deleted opera_11.62.1347_amd64.deb and then went back to [http://www.opera.com/browser/download/](http://www.opera.com/browser/download/) and it automatically selected Opera 11.62 for Linux x86-64 which I re-downloaded and then opened with the Software Center. It works properly and is fully functional with icons this time.

---

### Post by Frogs Hair on 2012-04-05
> **theducksfan2010 said:**
> Ok, so I went back into Ubuntuu Software Center and uninstalled Opera. I then went into the downloads folder and deleted opera_11.62.1347_amd64.deb and then went back to [http://www.opera.com/browser/download/](http://www.opera.com/browser/download/) and it automatically selected Opera 11.62 for Linux x86-64 which I re-downloaded and then opened with the Software Center. It works properly and is fully functional with icons this time.

Glad it's working ! I would suspect a package or installation problem the first time around.

---

