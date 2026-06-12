---
title: "[SOLVED] Newbie help required"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by Captain Aardvark on 2008-06-30
Hi.

I have been looking through a couple of distros of Linux, such as SUSE and Puppy, with a view to using Linux instead of Windows XP and found Ubuntu to be the best for my needs. However, I have a couple of issues I would like help with please.

Since upgrading from 7.10 to Hardy Heron, I noticed that I cannot access my Windows Server 2003 network resources any more. (I am the Network Manager, so have full rights!!) The available networks and computer / server names appear, as before; however, when I click on the server name that holds the shared resources, I am not asked for username / password / domain (as I was in 7.10) and no shared folders appear. (Please note I have not joined the domain, only trying to access the resources at share level).

Also, I cannot play DVDs (CDs work fine). I have a Pioneer DVD-RW DVR-111D player / recorder. When I insert the DVD, the disk correctly appears on the desktop; however, Totem player reports a message "An error occurred - Could not read from resource". I tried other help methods for this, such as installing Gstream, installing the Ubuntu limited resources and installing VLC Media Player; however, none of these have helped!!

The PC is a self build AMD1800+ with 1GB RAM, DVD-RW as described and 14GB
hard disk (it was built as a Linux test bed!!) I added an extra CDROM drive, in case the DVD drive was only being seen as a CDROM drive, but, despite the drives being shown correctly on screen, this was to no avail.

Thank you.

---

### Post by WRDN on 2008-06-30
Regarding DVD playback, the codecs needed aren't installed as standard, because of licensing issues.

You can install them by typing the following command in the terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

Also, run:

```
/usr/share/doc/libdvdread3/install-css.sh
```

Once you have done this, DVD playback should work.

---

### Post by Captain Aardvark on 2008-06-30
Thank you, WRDN!! :)

I just ran the install-css command and the DVD now plays back perfectly!!

---

