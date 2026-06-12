---
title: "Trying to upgrade to 7.10"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by Spoken on 2008-05-01
ok, so i had some BIG issues upgrading to 8.04 and had to restore my computer to 7.04.
im trying to upgrade back up to 7.10 through update manager but when the upgrade process starts, i get this error message

```

Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)

```

it says i should check my network connection, but how could i be posting this if i didnt have one?

============================================================================
UPDATED INFORMATION BELOW
===========================================================================
ok so i used terminal to open update manager

i used 

```

sudo update-manager -c -d

```

it opened update manager, and i selected the 7.10 upgrade.  and it still stopped and gave me the error above.  but here is the output i got in terminal.

```

warning: could not initiate dbus
extracting '/tmp/tmpZUqUJs/gutsy.tar.gz'
authenticate '/tmp/tmpZUqUJs/gutsy.tar.gz' against '/tmp/tmpZUqUJs/gutsy.tar.gz.gpg' 
could not send the dbus Inhibit signal: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.


```

---

### Post by Spoken on 2008-05-02
sudo update-manager -c -d didnt work! :(

---

### Post by Spoken on 2008-05-02
gah, i woke up with hopes someone would have posted.

---

### Post by cool_penguin on 2008-05-02
Why don't your back up all your data and opt for a fresh installation of 8.04? A fresh installation has always work great for me in my experience.

---

### Post by aheckler on 2008-05-02
You might be better off just getting a LiveCD of whatever version you want and doing a straight-up fresh installation.

EDIT: Ack, cool_penguin beat me to it!

---

### Post by cool_penguin on 2008-05-02
Bravo ! We both said the same thing. 


Cheers

---

### Post by Spoken on 2008-05-02
i want to upgrade, not fresh install, i have my reasons.

---

### Post by bjm1904 on 2008-05-02
If you're worried about forgetting which packages you have/haven't installed, try

dpkg -get-selections file.txt

(or something similar - you may want to check that one). This grabs all your installed package selections and outputs them to a text file. Now if you do a clean install and choose 'set' rather than 'get', to download and install them again. You can also set up a partition with /home as the mount-point to maintain your personal files.

A clean install is preferable to an upgrade, but I don't want to be doing that on the basis I've written my own custom software (and hacked some drivers to get them to work with some proprietary hardware) I'm a little hesitant of doing so myself!

---

### Post by bjm1904 on 2008-05-02
you could also use dpkg-parsechangelog incidentally - it achieves the same end

---

### Post by Oldsoldier2003 on 2008-05-02
> **Spoken said:**
> i want to upgrade, not fresh install, i have my reasons.

get the 7.10 alternate installer cd and pop it in the drive. you'll get the option to upgrade.

---

### Post by Sef on 2008-05-02
> i want to upgrade, not fresh install, i have my reasons.

You can only downgrade (8.04 > 7.10) by a clean install.  

Your options are either 

1) A clean install of 8.04, which may resolve your problems.  

2) A clean install of 7.10.

---

### Post by Oldsoldier2003 on 2008-05-02
> **Sef said:**
> You can only downgrade (8.04 > 7.10) by a clean install.  

Your options are either 

1) A clean install of 8.04, which may resolve your problems.  

2) A clean install of 7.10.

The OP is sitting at 7.04 wanting to go to 7.10, the 8.04 upgrade failed causing him to restore 7.04

---

