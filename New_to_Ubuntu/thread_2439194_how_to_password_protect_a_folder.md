---
title: "how to password protect a folder????"
date: 2020-03-24
forum: New to Ubuntu
---

### Post by daylightriot on 2020-03-24
Hi all. Im new to ubuntu and cant find any software or OS options to password protect a folder?  I've tried installing cryptkeeper and gnome encfs manager through terminal commands but both are giving me this error. 

E: Unable to locate package gnome-encfs-manager. 

Anyone know of any software available for the distro im using? if you do, please respond in an 'idiots guide' step by step kind of way. i started using ubuntu today. 

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 19.10
Release:    19.10
Codename:    eoan


Thanks in advance people.

---

### Post by SeijiSensei on 2020-03-24
The standard KDE file manager, Dolphin, lets you encrypt a folder by right-clicking on it and choosing encrypt.  It launches a front-end for GPG.  Have you tried something similar in the standard Ubuntu file manager?

---

### Post by yancek on 2020-03-24
You haven't posted the actual command(s) you used.  The link below explains how to get the software and install it.  The second link below explains some other options, depends upon how secure you need it to be.

[https://itsfoss.com/password-protect-folder-linux/](https://itsfoss.com/password-protect-folder-linux/)

[https://www.howtoforge.com/tutorial/how-to-hide-lock-encrypt-and-secure-your-files-on-linux/](https://www.howtoforge.com/tutorial/how-to-hide-lock-encrypt-and-secure-your-files-on-linux/)

---

### Post by daylightriot on 2020-03-31
Those websites are the instructions I followed. No dice. I'm on Ubuntu 19.10.

---

### Post by daylightriot on 2020-03-31
I'll check out dolphin kde and update this post &#55357;&#56397;

---

### Post by daylightriot on 2020-03-31
Forgot to say thanks, so thank you!! Also, it looks like I need to install the kde desktop environment for full access to dolphin file explorer. I tried dolphin on its own but there were no encrypt options available. Could you confirm that this is the case? This is my uni work laptop and whilst all my files are backed up in clouds it would be a pain setting everything up again.

---

### Post by ActionParsnip on 2020-04-03
[https://askubuntu.com/questions/104542/how-to-encrypt-individual-folders#104984](https://askubuntu.com/questions/104542/how-to-encrypt-individual-folders#104984)

---

### Post by CelticWarrior on 2020-04-03
> **ActionParsnip said:**
> [https://askubuntu.com/questions/104542/how-to-encrypt-individual-folders#104984](https://askubuntu.com/questions/104542/how-to-encrypt-individual-folders#104984)


Do NOT follow this ^^^^ instructions. They are severely outdated and the software is no longer available/maintained.

---

### Post by kevdog on 2020-04-05
Cant you just gpg encrypt a folder on the command line? No need to install a bunch of extra packages.

---

### Post by kurt18947 on 2020-04-05
If you're using gnome, maybe take a look at this:

[https://wiki.gnome.org/Apps/Seahorse/](https://wiki.gnome.org/Apps/Seahorse/)

The benefit to me is that it uses native Gnome. Says it'll encrypt files, I'm not sure about folders. It apparently adds encrypt to the 'files' menu of files/nautilus.

---

