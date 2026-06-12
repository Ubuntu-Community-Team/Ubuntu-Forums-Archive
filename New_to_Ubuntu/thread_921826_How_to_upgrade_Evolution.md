---
title: "How to upgrade Evolution?"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by mhedges48 on 2008-09-16
Hello, I am using Hardy with Evolution 2.22.3.1. I can no longer open attachments in Evolution, I always get this error at the status bar:
"Error while Saving attachment." When I click on this it this says cannot create file and then Success.

I read that this was a bug in the release. However, I do not know how to update Evolution, can someone please point me in the right direction? I have been looking without any luck or out of newbie stupidity...

many thanks

---

### Post by ptn107 on 2008-09-16
I can't seem to reproduce that problem with Evolution in 8.04 64-bit.  Before you go off trying to install the newer version from Intrepid (which may be a bad idea anyway), I would try the following:

1-Back up your /home/$USER/.evolution folder.  Save the backup elsewhere.
tar -cvjf evolution-backup.tar.bz2 /home/$USER/.evolution/*
2-Remove the evolution folder
sudo rm -r /home/$USER/.evolution
3-Remove evolution itself.
sudo apt-get remove --purge --auto-remove evolution
4-Reinstall evolution.
sudo apt-get install evolution
5-See if the problem persists.  If no, restore your backup.  Then check for the problem again (it could be something with your settings and not evolution itself).

**If you still want to try the newer evolution from the coming Intrepid (8.10) release** (haven't done it, don't know if it works; also note that downgrading from intrepid's version to hardy's sucks and might not work correctly):
1-Make a backup of your current sources.list
sudo cp /etc/apt/sources.list /etc/apt/sources.backup
2-Change your software sources from hardy to intrepid
sudo sed -i 's/hardy/intrepid/g' /etc/apt/sources.list
3-Update your package lists
sudo apt-get update
4-Install [the new] evolution (do not install any other software from Intrepid, seriously)
sudo apt-get install evolution evolution-exchange evolution-plugins
5-Restore your original sources.list file
sudo cp /etc/apt/sources.backup /etc/apt/sources.list
6-Update your package lists
sudo apt-get update
7-Check to see if problem persists (who knows it may have been evolution all along)

If the Intrepid version ends up not working or messes up your system downgrade back to the old (8.04) evolution:
sudo apt-get install evolution=2.22.3.1-0ubuntu1 evolution-exchange=2.22.3-0ubuntu2 evolution-plugins=2.22.3.1-0ubuntu1

---

### Post by Pro-reason on 2008-09-16
You have the latest version available for Ubuntu Hardy Heron.  To get an even more recent version, you'd have to download the source code and compile it yourself.  It's not for the faint-hearted (newbies).  It's for nerds who like tinkering with their system, rather than users who just want to send attachments.

If the bug is in this release, a better option is to open Synaptic, find the evolution package, and then hit Ctrl-E to bring up all available versions.  On my system I can see 2.22.3.1-0ubuntu1, 2.22.2-0ubuntu1.2 and 2.22.1-0ubuntu3.  Choose a different (older) version to install.  Remember, old is gold.  ;-)

You could always just use Thunderbird or Cone or something else until Evolution is fixed, too.

---

### Post by mhedges48 on 2008-09-17
Thank you both. I am still having the same problems after starting over (I purged as instructed above. I tried to force an old install in synaptic, although it showed the old version it wouldn't let me install anything but the most current so I reinstalled that from scratch).

Could it maybe be some permissions problem in the cache folder?

I still receive a message like this when trying to open and/or save any attachment:
¨¨¨
Error while Saving attachment.

Cannot create output file: /home/matt/.evolution/cache/tmp/evolution-tmp-EDsKj6/0330_93712_Invoice_VdS.pdf:
 Success
"¨¨¨¨¨

thanks and best wishes!

---

### Post by mhedges48 on 2008-09-18
I was able to downgrade Evolution and still have the problem...

---

### Post by hobitt on 2008-11-04
Hej, thanks to ptn107.

It worked great. :guitar:

---

### Post by drorata on 2009-03-07
I wanted to enable Google contacts sync with evolution, but since I'm using 8.04 it was not supported. pn107's hint seems to solve the issue!

Thanks a lot!

---

### Post by iamkrazee on 2009-03-07
If you´re not comfortable with CLI then just run your synaptic. The options there are pretty much self-explanatory and you can figure out what ptn is saying. :)

---

### Post by Nepherte on 2009-03-07
I don't think it's a good idea to install evolution 2.24 on your hardy. Evolution is so tightly integrated in gnome it will probably require you to upgrade most gnome related packages to 2.24. Your safest bet would be to upgrade ubuntu to intrepid if you really want the new evolution.

---

### Post by drorata on 2009-03-07
I'm afraid I got the warnings too late...

So now, Evolution works OK, but indeed many other GNOME related features are broken... :(:(:(

For example:
- The screen resolution menu has changed and works differently.
- I get an error message on log in:
There was an error starting the GNOME Settings Daemon.  Some things, such as themes, sounds, or background settings may not work correctly.  The Settings Daemon restarted too many times.  GNOME will still try to restart the Settings Daemon next time you log in.

So, now the question is, should I try the "UNDO" offered by PNT? That is re-installing the previous version of Evolution?

---

