---
title: "rhythmbox opens when I open audacious"
date: 2014-02-17
forum: New to Ubuntu
---

### Post by stylintile on 2014-02-17
Having a problem with rhythmbox.  Every time I open audacious, rhythmbox opens.  If I close rhythmbox it opens again after a few seconds, and continues to open until I close audacious.  I have both as I am still trying to decide which one I like better.  I tried what I read here:
[http://ubuntuforums.org/showthread.php?t=953571&highlight=rhythmbox+opens+when+i+open+audacious](http://ubuntuforums.org/showthread.php?t=953571&highlight=rhythmbox+opens+when+i+open+audacious)
and here:
[http://ubuntuforums.org/showthread.php?t=982945&highlight=rhythmbox+opens+when+i+open+audacious](http://ubuntuforums.org/showthread.php?t=982945&highlight=rhythmbox+opens+when+i+open+audacious)
but I don't have the "open with" anywhere in the right click menu or the properties menu for folders (and I don't understand how that could have anything to do with it).  Has anyone else had this problem?
I am using xubuntu 12.04.  Any help would be greatly appreciated.  I have to go to work now, but I will check back this evening.
Thanks in advance.

---

### Post by Jonor on 2014-02-18
It is not obvious that you have been looking in the best place.
Go to some music file, such as an MP3 file, not a folder, although possibly technically a music file is a folder 
and from the MP3 right click for properties, click the Open With tab, click on Audacious, 
click on the Set As Default button, THEN, when Rhythmbox gets relegated to Recommended Applications, 
right click on Rhythmbox to get the Forget Association button to banish it.

---

### Post by stylintile on 2014-02-18
Thank you for the reply.  I don't have a "open with" tab, just a button, and I have set it to audacious, parole, vlc, gmusic browser, and back to audacious.  But whenever it is set to audacious, rhythmbox opens with it.  I am running xubuntu with thunar as my file manager, which is probably why my properties is a button instead of a tab.  Anyway, I have (temporary at least) uninstalled rhythmbox until I have a little more time to mess with it.  A lot going on for the next few days, so I will play with it some more later this week.  attached is a screen shot of the properties menu.

Thanks again.

---

### Post by monkeybrain20122 on 2014-02-18
In the hidden folder ~/.local/share/applications there is a file called mimeapps.list. You can check and edit file associations there.

---

### Post by stylintile on 2014-02-19
I don't have an local file there: 

```
ls -a /
./    dev/         lib/          mnt/   sbin/     usr/
../    etc/         lib32/       opt/   selinux/  var/
bin/    home/         lib64/       proc/  srv/      vmlinuz@
boot/    initrd.img@     lost+found/  root/  sys/      vmlinuz.old@
cdrom/    initrd.img.old@  media/       run/   tmp/
```

I do have one in the usr folder, but no applications file:

```
ls -a /usr/local/share
./  ../  ca-certificates/  emacs/  fonts/  man/  sgml/    xml/
```

Am I missing something??](*,)

Thanks again for the help.

---

### Post by Jonor on 2014-02-19
My mistake, i overlooked your using xfce/thunar in Ubuntu 12.04.
I envy you being able to unistall Rhythmbox, since it would force me to also uninstall Gnome completely. :mad:

---

### Post by monkeybrain20122 on 2014-02-19
> **Jonor said:**
> My mistake, i overlooked your using xfce/thunar in Ubuntu 12.04.
I envy you being able to unistall Rhythmbox, since it would force me to also uninstall Gnome completely. :mad:

No it won't. Gnome is a metapackage which can be removed with no problem (all the components will just change status to "installled(manual)" in synaptic)  I always uninstall Rhythmbox (in Unity) In Debian it may be a bit of a problem as everything in the gnome-desktop becomes autoremovable,--I have only used sid so maybe it is different in stable,-- but I  never have a problem in Ubuntu even back in the gnome 2 days.
So if everything becomes autoremovable as a result of uninstalling Rhythmbox just change them to "manual" I forgot how to do it, just google in case..

---

### Post by monkeybrain20122 on 2014-02-19
> **stylintile said:**
> I don't have an local file there: 



.local is a hidden file in your home folder. To see it you have to select "show hidden files" in thunar. You may also have a file called mimeapps.list in /usr/share/applications. I don't have xfce now so I can't check. Try 
```
locate mimeapps
```

---

### Post by stylintile on 2014-02-19
Okay, the problem seems to have gone away by uninstalling and reinstalling rhythmbox without doing anything else.  

> You may also have a file called mimeapps.list

I do have that file and have added a note about it in my notes/tricks/commands etc. file. :)  That is definitely useful information.
Thanks to all for the help and tips.  I will now mark this solved.

---

