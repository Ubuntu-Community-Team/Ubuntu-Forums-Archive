---
title: "Installing an rpm? command prompt?"
date: 2012-11-24
forum: New to Ubuntu
---

### Post by chilliepierre on 2012-11-24
I used to be a whiz back in 2007, but now I am a dunce.  :(  Please help me.  Where do I get started in learning about Ubuntu and how to get a command prompt and how to install an rpm, etc?

Thank you,
Chillie

---

### Post by Frogs Hair on 2012-11-24
If you absolutely can't find a .deb package you can install alien and give the tutorial at the link a try . It is dated and I have never used it, but alien is in synaptic.


[http://www.howtogeek.com/howto/ubuntu/install-an-rpm-package-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/install-an-rpm-package-on-ubuntu-linux/)

---

### Post by chilliepierre on 2012-11-24
In Ubuntu 12:10, how do I get the command line?  I hate being so stupid, but I am so rusty.  Thanks!

---

### Post by howefield on 2012-11-24
Keyboard shortcut is Ctrl + Alt + T

Or open the dash by pressing the Super (Windows) key and start typing terminal, once launched you can lock the icon to the launcher is desired.

---

### Post by zombifier25 on 2012-11-24
Click the first button in the left Launcher, type "terminal" and choose the result. Or press Ctrl + Alt + T.

---

### Post by chilliepierre on 2012-11-24
It's not finding the file.  I'm trying to install adobe flash.  I appreciate your help.

Thanks,
Chillie

---

### Post by howefield on 2012-11-24
Try

```
sudo apt-get update
```

then

```
sudo apt-get install flashplugin-installer
```

---

### Post by chilliepierre on 2012-11-24
Not available.  :(

---

### Post by newb85 on 2012-11-24
flashplugin-installer should be in the Multiverse.  Make sure you have it enabled in Software Sources.

---

### Post by chilliepierre on 2012-11-24
Newb85 - huh?

---

### Post by howefield on 2012-11-24
Just to check seeing as you mention .rpm, what OS version are you running ?

---

### Post by MadmanRB on 2012-11-24
open the software center (the icon looks like this [http://upload.wikimedia.org/wikipedia/commons/2/20/Ubuntu_Software_Center_icon_v2.svg](http://upload.wikimedia.org/wikipedia/commons/2/20/Ubuntu_Software_Center_icon_v2.svg))

Search for Ubuntu-restricted-extras
install
done

---

### Post by newb85 on 2012-11-24
> **chilliepierre said:**
> Newb85 - huh?

Okay, the software you install using apt-get comes from repositories (a.k.a. repos) and personal package archives (PPAs).  There are four Ubuntu repos and a partners repo set up in Ubuntu by default, but not all of them are enabled by default.  If you pull up the Dash and open Software Sources, you should be able to see which repos are enabled.  If the multiverse repo is not enabled, then flashplugin-installer won't be available.

---

