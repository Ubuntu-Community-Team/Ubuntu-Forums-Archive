---
title: "[SOLVED] I bricked my laptop"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by cygnis1 on 2008-05-09
Help!
Yesterday I ran some updates and now my system is messed up.  My desktop is gone, or more exactly, I think it is hidden.  There is a blue screen on the desktop, but not my usual wallpaper and no icons or folders.  When I save anything to the desktop it doesn't appear on the blue screen.  The shortcuts on the top of the screen all work, with the exception of the network manager, which is totally missing and I have no wifi.  Fortunately my ethernet port is functioning.  The trash been cannot be opened.  It shows 19 items in it but it can not be accessed.  Under Places it shows the home folder, but will not show what is in it,the same with Computer,sd1 and sd2. I have tried to burn dvds and cds and the files show up but the programs will not burn.  I have access to Thunderbird and Firefox and most of the programs in Accessories, but I think my file system is screwed up.  Please help.  At the very least I would like to save my information.
Thanks,
Cygnis1:confused:

---

### Post by pedro_orange on 2008-05-09
> **cygnis1 said:**
> Help!
Yesterday I ran some updates and now my system is messed up.  My desktop is gone, or more exactly, I think it is hidden.  There is a blue screen on the desktop, but not my usual wallpaper and no icons or folders.  When I save anything to the desktop it doesn't appear on the blue screen.  The shortcuts on the top of the screen all work, with the exception of the network manager, which is totally missing and I have no wifi.  Fortunately my ethernet port is functioning.  The trash been cannot be opened.  It shows 19 items in it but it can not be accessed.  Under Places it shows the home folder, but will not show what is in it,the same with Computer,sd1 and sd2. I have tried to burn dvds and cds and the files show up but the programs will not burn.  I have access to Thunderbird and Firefox and most of the programs in Accessories, but I think my file system is screwed up.  Please help.  At the very least I would like to save my information.
Thanks,
Cygnis1:confused:

Sounds like a copy to flash disk if you can and reinstall if you ask me. (I wouldn't ask me; I talk crap!)

---

### Post by cygnis1 on 2008-05-09
That is what I thought, however I can't put anything on the flash drive and I cannot even unmount it safely.  I am trying to see if I can email some of the files as attatchments.

---

### Post by bumanie on 2008-05-09
Have you tried opening terminal? If it opens try > sudo dpkg-reconfigure ubuntu-desktop If that doesn't work, or you can't get terminal open, post back and it will probably have to be done via console mode.

---

### Post by cygnis1 on 2008-05-09
the terminal works.  I tried it and got this message:

john@r3-mobile:~$ sudo dpkg-reconfigure ubuntu-desktop
[sudo] password for john:
/usr/sbin/dpkg-reconfigure: ubuntu-desktop is not installed
john@r3-mobile:~$

---

### Post by bumanie on 2008-05-09
In that case, I assume > sudo apt-get install ubuntu-desktop should install it. I was figuring it had been mucked up, but by the look of that message it has been uninstalled. I hope this works for you.

---

### Post by cygnis1 on 2008-05-09
I did this and it wants me to insert the hardy heron cd.  Now this is what got me into trouble in the first place.  Should I do it?

---

### Post by MusicMastaMike on 2008-05-09
You can stop apt from asking for the cd by doing the following:

sudo nano /etc/apt/sources.list

Comment out any lines starting with "deb cdrom:"  Now save and close the file.  

Now do: sudo apt-get update

And then: sudo apt-get install ubuntu-desktop

That should take care of it for you!

---

### Post by bumanie on 2008-05-09
I would tend to think it is your only option. I guess it needs files off the cd to replace the desktop - that's an educated guess. I would have thought it could be done via synaptic, but the message you received disagrees with my assertion about synaptic.

---

### Post by ripin1 on 2008-05-09
what kind of updates were you installing to get no desktop?:confused:

---

### Post by aeiah on 2008-05-09
if you have to go down the backup-and-reinstall route, then you might find it easier to do the backing up whilst in the livecd, of course.

---

### Post by Tomatz on 2008-05-09
It sounds like nautilus is the culprit.

Try reinstalling it via synaptic.

Alternitavly you could try kubuntu:

**sudo aptitude install kubuntu-desktop**

Then logout and change session to kubuntu in the login manager ;)

---

### Post by cygnis1 on 2008-05-09
how do you comment out lines?

---

### Post by bumanie on 2008-05-09
With a > #

---

### Post by cygnis1 on 2008-05-09
I was using the update manager and it asked me to put in the hardy heron dvd, which I did and it updated my computer.  When I restarted the desktop and the  network manager were gone.  I tried to uncomment the line but how do you save it?

---

### Post by MusicMastaMike on 2008-05-09
Firstly, you should be commenting the line (put a # before deb cdrom).  On mine, there are two deb cdrom lines, so both should be commented.  To save, do control+o, then control+x.  I believe that's how it works in nano.

---

### Post by bumanie on 2008-05-09
Try > sudo gedit /etc/apt/sources.list and the uncomment with #. A save button will be at the top of the list box. The other thing to try is to go to software sources (if you can see it) and uncheck the box down the bottom that says cd-rom. However if you upgrade the list as said, that should change anyway. Double check to make sure after the list is fixed.

---

### Post by cygnis1 on 2008-05-09
I was unable to reinstall the gnome desktop but was able to use kde and can see all my files.  I will save it all and do a clean install of hardy and keep my fingers crossed.  Thanks all for the help.  I am sure I will be posting again soon. I don't know this thread isresolved as I have to work on my wifi.
Cygnis1

---

### Post by Tomatz on 2008-05-09
The problem is probably nautilus as nautilus displays files/icons on the desktop and allows you to browse files.

As said, try to reinstall nautilus or try to get the source yourself and compile it.

You can file a bug report [here]("https://bugs.launchpad.net/ubuntu/hardy/") and probably get help from a developer ;)

---

### Post by cygnis1 on 2008-05-09
Thanks to everyone for their help and suggestions.  I was finally able to save my information and do a clean install of Hardy.  I even have my wifi back.  Now I just need to tweak my system and I am set.
Thanks again.
Cygnis1

---

