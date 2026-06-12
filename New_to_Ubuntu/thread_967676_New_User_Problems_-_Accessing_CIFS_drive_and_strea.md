---
title: "New User Problems - Accessing CIFS drive and streaming media"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by dhlevine on 2008-11-02
I'm newly making the switch over to Ubuntu from a lifetime of using Windows, and generally being glad I did - but having some troubles that I can get sorted with my network drive and streaming media.  I've read around on these, but the discussions I've found so far either don't seem to solve my problem, or are just beyond my current level of understanding.  So, if someone could help me fix them, using small words that even a humanities professor like me can understand, I'd greatly appreciate it.  I'm not totally useless (I can use the Terminal, basically), but you're probably safe in underestimating my linux knowledge.

For background: I'm currently running Ubuntu 8.04 on an Asus EEE 1000H computer, with the EEE kernel from array.org.

- I have a Western Digital MyBook World Edition network drive that I can't seem to get mounted properly.  With Ubuntu out of the box, I was able to connect to the drive, but couldn't get permission to change anything in existing folders.  I could create and use a new folder, and read from the existing folders.  I followed the Setting Up Samba guide ([https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)), just as a client, and now while I can still see the drive through Network, I get an error saying that there is no application to open the "Public" folder.  My understanding is that the MB is set up with CIFS - and, I've looked at some of the MB hacking guides, but I'd rather not do something so drastic...

- I can't seem to get websites that stream media working properly (esp. those that stream Windows Media content, but I have trouble with others sometimes, too).  I've installed mozilla-mplayer, which is the fix that I'd seen most often, but that doesn't seem to work - if I try to stream, I get a mplayer logo for the plugin, but then the stream just stops.

Any help or advice would be greatly appreciated, and if there's more info I should be giving, I'm happy to.

- Daniel

---

### Post by Paqman on 2008-11-02
There's a good guide about connecting to shares using CIFS [here](http://ubuntuforums.org/showthread.php?t=288534).

In short:
[list]
[*]Install smbfs
[*]Create some mount points
[*]Edit fstab
[*]Set up some security
[*]Profit!
[/list]

If you're having trouble with the machine not shutting down correctly, scroll down the OP for some of the fixes posted there.

Also, Intrepid seems to handle the permissions on shares better than Hardy. Not exactly sure why, new version of smbfs maybe?

---

### Post by dhlevine on 2008-11-04
Thanks - the guide was very helpful, and I now have a much more stably mounted drive.

I still can't get the permissions right, though.  Even when I open the file browser as root, if I try to change permissions on a folder, I get an error telling me it's not a directory.

---

