---
title: "Default keyring password nag"
date: 2012-01-03
forum: New to Ubuntu
---

### Post by Pd456 on 2012-01-03
Hi,   I'm using Puredyne 'Carrot and Coriander' based on Ubuntu 9.10.   Could someone tell me how to save the password for wifi so that I don't get the Default Keyring Password nag at the start up.   Thanks

---

### Post by jjex22 on 2012-01-03
Of corse this isn't recommended, but you need to reset the keyring's password to blank - this is particularly unadvised if you are using auto login (I suspect you are if it keeps asking for the password.)

To do this, use the program "Seahorse" It'll give you a warning about not being very secure of something, but will let you change it to blank. Sorry I can't be more precise, I'm on my tab at the mo, so Can't check, but it's pretty straight forward!

If you disable autoamtic login and sign in each time you power on, the keyring should start wi-fi automatically without password prompt - unless you changed the password?


The keyring acts the same as KDE's Wallet and OSX's Keychain - it encrypts and stores your passwords, so in terms of security it's best to use a different password for log in, mail key ring, wifi keyring etc... and not then store them as a sticky on your desktop!

---

### Post by Pd456 on 2012-01-04
I guess I don't have Seahorse, I tried to run it but it's not there.
   I guess I should start by learning to install something like Flash and then Seahorse. Or maybe there is an easier way.

---

### Post by kalfusisagod on 2012-01-04
you can do this to install stuff via the command line
```
sudo apt-get install seahorse
```

To get to terminal, press CTRL-ALT-T hope this helps!

---

### Post by Pd456 on 2012-01-05
I tried "sudo apt-get" for seahorse and flash, neither worked, it said no file exists. Seahorse-plugins is something but that didn't work either.  I also tried several different apt codes and tutorials that I found around the net, with tar.gz files etc. It seems like some of the files are out of date.  How do I copy/paste into a terminal?

---

### Post by gandaran on 2012-01-05
> **Pd456 said:**
> I tried "sudo apt-get" for seahorse and flash, neither worked, it said no file exists. Seahorse-plugins is something but that didn't work either.  I also tried several different apt codes and tutorials that I found around the net, with tar.gz files etc. It seems like some of the files are out of date.  How do I copy/paste into a terminal?
seahorse is already installed on ubuntu, look for passwords and encrypted keys app.

---

