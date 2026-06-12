---
title: "how to install new fonts from ms windows xp"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by kroisos73 on 2008-05-28
hi to everyone

pls help me how to install fonts from ms windows (like tahoma etc) to ubuntu


thanks anyway!!!

---

### Post by indytim on 2008-05-28
Search in either synaptic or adept for fonts.  There is a MsFonts  app for installing the fonts.  I'm on Windows right now so I can't give you the specific app name.

IndyTim

---

### Post by gali98 on 2008-05-28
> **indytim said:**
> Search in either synaptic or adept for fonts.  There is a MsFonts  app for installing the fonts.  I'm on Windows right now so I can't give you the specific app name.

IndyTim

Right something like restricted_fonts or restricted_extras
but I am also on a windows machine at the moment.
Kory

---

### Post by odysseusjak on 2008-05-28
What I did was copy my Windows font folder to cd or usb drive, boot into Ubuntu and then copy the font folder to your home directory.  Next, RENAME the font folder to .fonts (this makes it a hidden folder).  Reboot your system and log in to Ubuntu.  You will now have access to all of your Windows fonts.

---

### Post by quinnten83 on 2008-05-28
You can try with this [link]("http://tombuntu.com/index.php/2008/04/17/how-to-install-fonts-in-ubuntu-804/")

---

### Post by Uikku on 2008-05-28
Hello!
I'd first install **ubuntu-restricted-extras** in Synaptics. And then the beloved fonts not included there I would copy either to folder **/usr/share/fonts** (fonts available to all users) or **/home/username/.fonts** (fonts available to just me). After copying the font cache should be updated by the command
```
sudo fc-cache -f -v
```
in terminal.

---

