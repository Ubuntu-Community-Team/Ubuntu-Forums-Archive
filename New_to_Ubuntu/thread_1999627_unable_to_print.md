---
title: "unable to print"
date: 2012-06-08
forum: New to Ubuntu
---

### Post by Nadarasan on 2012-06-08
I am unable to print any thing .The printer is fine.  Everytime I give a print and view the print status.It shows as heldeven though the settings show otherwise or it shows rendering completed and after it nothing happens.

---

### Post by philinux on 2012-06-08
> **Nadarasan said:**
> I am unable to print any thing .The printer is fine.  Everytime I give a print and view the print status.It shows as heldeven though the settings show otherwise or it shows rendering completed and after it nothing happens.

Not enough info given for members to respond to your problem. Which version of ubuntu and which printer make and model.

---

### Post by IWantFroyo on 2012-06-08
Run this and browse for your printer:
```
gksudo system-config-printer
```
 
Select a driver, and set it up again.

---

### Post by Nadarasan on 2012-06-08
ubuntu 12 and printer is xerox phaser3117

---

### Post by IWantFroyo on 2012-06-08
Again, I recommend using the GTK2 printer setup.
 
Try setting up your printer in here.
```
gksudo system-config-printer
```

---

### Post by philinux on 2012-06-08
> **Nadarasan said:**
> ubuntu 12 and printer is xerox phaser3117

Open the Dash type pr then use the gui to delete the printer and then add it from scratch.

---

### Post by cogier on 2012-06-08
Xerox creates its own drivers for Linux. You can download from here
[http://www.support.xerox.com/support/phaser-3117/downloads/enza.html?operatingSystem=linux&fileLanguage=en_GB]("http://www.support.xerox.com/support/phaser-3117/downloads/enza.html?operatingSystem=linux&fileLanguage=en_GB")

---

