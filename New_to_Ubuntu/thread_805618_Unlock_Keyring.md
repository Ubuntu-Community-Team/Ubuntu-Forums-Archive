---
title: "Unlock Keyring"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by special ed on 2008-05-24
When ever I boot up Ubuntu 8.04 I get a window that opens that kind of bothers me. It say:
 
Unlock Keyring:

Enter password for default keyring to unlock.
The application nm-applet (user/bin/nm-applet wants access to the default keyring, but it is locked

It won't connect to the internet until I enter the password (which I know). It does this every time I log in. Is there a way to make it automatically does this

---

### Post by owenll on 2008-05-24
> **special ed said:**
> When ever I boot up Ubuntu 8.04 I get a window that opens that kind of bothers me. It say:
 
Unlock Keyring:

Enter password for default keyring to unlock.
The application nm-applet (user/bin/nm-applet wants access to the default keyring, but it is locked

It won't connect to the internet until I enter the password (which I know). It does this every time I log in. Is there a way to make it automatically does this

There are a few threads on this forum regarding this issue: One recently started: [http://ubuntuforums.org/showthread.php?t=805602](http://ubuntuforums.org/showthread.php?t=805602) and some that provide solutions: [http://ubuntuforums.org/showthread.php?p=2776815](http://ubuntuforums.org/showthread.php?p=2776815) and [http://ubuntuforums.org/showthread.php?t=187874&highlight=key+login](http://ubuntuforums.org/showthread.php?t=187874&highlight=key+login) 

I found this problem annoying but found a solution in one of these that involved not using nm-applet.

A google search and search these forums are also good!

---

### Post by special ed on 2008-05-24
forgive me I'm new to linux.

I tried the links you suggested but no luck.

Are there instructions for dummies like me?

---

### Post by hyperair on 2008-05-24
Set your default keyring's password to blank. I'm not sure how to do this with the default GNOME Keyring utility, but with Seahorse (sudo apt-get install seahorse), you can go to System->Preferences->Encryption & Keyrings and change the "unlock password" of the login password to "", i.e. blank password or unencrypted keyring.

---

### Post by owenll on 2008-05-24
> **special ed said:**
> 
I tried the links you suggested but no luck.


This is what I tried and it worked for me:

[http://ubuntuforums.org/showpost.php?p=4736313&postcount=42](http://ubuntuforums.org/showpost.php?p=4736313&postcount=42)

Follow the link to wicd.sourceforge. It involves installing Wicd and thus removing nm-applet

I replaced gutsy with hardy to get the version I needed. Hope it works for you. No guarantees - just telling you what worked for me - couldn't get any of the other solutions to work.

> Please note that this will remove network-manager, which is the default GNOME network manager and may cause loss of network connection temporarily. 

---

### Post by hyperair on 2008-05-24
Before trying to install wicd and removing NetworkManager, I'd suggest you try my method first (setting a blank password for GNOME Keyring). It's less invasive and requires less time. You can always just switch to wicd if it still fails, though it shouldn't, because I haven't had any problems with my method in Ubuntu or in Archlinux.

---

### Post by special ed on 2008-05-24
It's fixed

Thanks for your help.

---

