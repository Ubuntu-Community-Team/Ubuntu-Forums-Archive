---
title: "How To Exit Console?"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by Eric Qel-Droma on 2008-07-03
How do I get out of the text screen after I've hit Ctrl+Alt+F1?  Is that "console"?  I typed "help" to check the command list, but I couldn't find anything helpful.

Thanks,

Eric

---

### Post by philinux on 2008-07-03
ctrl alt f7

---

### Post by sisco311 on 2008-07-03
Ctrl+Alt+F7

---

### Post by avtolle on 2008-07-03
Type exit at the prompt.

---

### Post by cardinals_fan on 2008-07-03
You may need to reboot to get back to the GUI login screen.  To sign out of the console, type 'exit'.

---

### Post by Dr Small on 2008-07-03
CTRL + ALT + F7 will take you back to the Xsession.

---

### Post by Eric Qel-Droma on 2008-07-03
> **avtolle said:**
> Type exit at the prompt.

I tried this specifically and got nothing.  In fact, the only commands that did anything for me were "reboot", "help" and "ps3videomode", as I was working in 7.10 on my PS3.

Thanks, though.

Eric

---

### Post by TheTrlak on 2008-07-03
I personally found on Heron that ctrl + alt + F7 actually does nothing, nor does exit. Typically i just sudo reboot. Or depending as I am only ever in that mode disabling or enabling my gui i tend to use /etc/init.d/gdm restart lol... I recommend not using htat last one :P

---

### Post by |{urse on 2008-07-03
or

rm -rf /tmp/X0-lock

sudo killall Xorg

startx

---

### Post by philinux on 2008-07-03
ctrl alt f7 

works fine here.

---

