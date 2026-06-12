---
title: "Installing applications"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Zalorioresscon on 2008-04-30
The application in particular that i'm trying to install is Flash Player 9.

i downloaded the .tar.gz file and extracted it on my desktop

i'm in the extracted directory and there are two files:

flashplayer-installer and libflashplayer.so

so how do i install this program?

---

### Post by freesitebuilder on 2008-04-30
How to install anything in Ubuntu
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

I've found it really useful :)

---

### Post by Jason2gs on 2008-04-30
Try this...

Right click on flashplayer-installer and bring up the properties box. Under "Permissions" hit the check box (if it's not already ticked) to make it executable.

Then, in a terminal, navigate to the extracted directory and run:

```
'./flashplayer-installer'
```

Tell me if that works.

---

### Post by ibutho on 2008-04-30
You can copy libflashpayer.so to your firefox or iceweasel plugins directory in /usr/lib/firefox-<VERSION> or /usr/lib/iceweasel-<VERSION>. Another option would be to install ubuntu-restricted-extras or flashplugin-nonfree using the Add/Remove Software application. You will need to enable the option to show all software.

---

### Post by Zalorioresscon on 2008-04-30
GREAT! ./flashpayer-install worked perfectly. Thank you all for your responses!

---

### Post by PeterJS on 2008-04-30
Yeah, you'll probably want to install from the package management system. Takes all the hard work out of it. From a terminal:
```

sudo apt-get install flashplugin-nonfree

```
or you could open up Synaptic Package Manager (System > Administration > Synaptic) and search for flashplugin

---

### Post by aysiu on 2008-04-30
For future reference, you can just visit a website that requires Flash and then click the *Install missing plugins* button that'll show up.

---

