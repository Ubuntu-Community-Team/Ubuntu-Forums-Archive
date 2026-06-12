---
title: "SyncEvolution on Hardy Heron"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by Handonam on 2008-05-07
I tried to install SyncEvolution on hardy heron, but the dependencies are off.  There seems to be quite a few things that do not work well with each other, such as the Libgconf11 (i think that's what it was) which seems to be outdated.

Does anyone have any way, for a newbie like me, to work around this?  i'm not too confident about tar's unless someone can help  me get the right dependent packages for it.

---

### Post by asrai on 2008-05-07
I'm not sure what is happening there, syncevolution installed fine on both my computers (both running hardy).  Did you add deb [http://www.estamos.de/download/apt](http://www.estamos.de/download/apt) stable main to your repositories and then install it through synaptic? If not how did you install it?

Also - can I just check which version of syncevolution you installed - there are 3 in the repos - 2.6 2.8 or 2.12?

---

### Post by Handonam on 2008-05-07
I followed this [guide]("http://ubuntuforums.org/showpost.php?p=2532774&postcount=55"), but replaced it with syncevo 0.7 instead of 0.5, and i disregarded the first command where it aptitude installs "libgconf11", which couldn't be found.

then i did a sudo checkinstall (as user handobuntu), and got this:


```
Copying files to the temporary directory...OK

Stripping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package... FAILED!

*** Failed to install the package

```

checked the log:```

(Reading database ... 107802 files and directories currently installed.)
Unpacking syncevolution (from .../syncevolution_0.7-1_i386.deb) ...
dpkg: error processing /home/handobuntu/syncevolution-0.7/syncevolution_0.7-1_i386.deb (--install):
 trying to overwrite `/usr/share/doc/syncevolution/README', which is also in package syncevolution-evolution-2.12
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/handobuntu/syncevolution-0.7/syncevolution_0.7-1_i386.deb
/var/tmp/oUFlcIXmCQSSOMVjmVNbC/dpkginstall.log 
```


i also did synaptics software install (as you suggested) and installed 2.12.  that was fine, i believe.  But still, the plugin doesn't show up on my evolution mail program

by the looks of it, seems like package 0.7 is conflicting with package 2.12.  not sure what to do about this

---

### Post by asrai on 2008-05-07
Ok good stuff.  The plugin won't show up in evolution though.  There is a guide to getting it set up at [http://www.estamos.de/projects/SyncML/GettingStarted.html](http://www.estamos.de/projects/SyncML/GettingStarted.html)  follow that and it will set it up so you can sync via the command line. 

Once you've edited all the files as it says on that website, you should be able to sync from the command line.  If you're using scheduleworld the command will probably be "syncevolution scheduleworld" to sync all types both ways.

 To make it easier for myself (and my husband who also uses it) I created an application launcher (right click on the panel, click on add to panel, then select custom application launcher.  This will open a new box and you should change the 'type' to 'application in terminal'.  I put in the command syncevolution scheduleworld.  You just need to click on this icon on your panel to do a full normal sync.  

Give that a go and let me know if you need any more help with it.

---

### Post by asrai on 2008-05-07
The guide for syncevo you used to install 0.7 (and 0.7 itself) is pretty old.  You don't need those, just syncevolution 2.12.

Do you know how to remove the 0.7 files?

Unless something has dramatically changed recently there is no GUI for syncevolution at all, it is all command line based (but if you make the icon like I did above you do not need to keep using the command line to run it).

---

### Post by Handonam on 2008-05-07
so if i start fresh (doing this on the laptop now, as opposed to the desktop), i only install SyncEvo 2.12 and then make the configs from the link you posted?  I see SyncEvo 2.12 in my synaptics, and will probably give it a go.


i successfully got SyncEvo 0.6 on the desktop, though.  I disabled 2.12 that i had on there earlier, and followed through the rest of that guide to making the cfg's.

---

### Post by asrai on 2008-05-07
Yes just installing 2.12 should work just fine. Let me know how you go with it.  It is a very useful little app :)

Good to hear that you've got it working on the desktop.

You do need to be careful and make sure that the id names in the config file are different on the desktop and laptop otherwise it will cause chaos!

---

### Post by Handonam on 2008-05-08
> **asrai said:**
> Yes just installing 2.12 should work just fine. Let me know how you go with it.  It is a very useful little app :)

Good to hear that you've got it working on the desktop.

You do need to be careful and make sure that the id names in the config file are different on the desktop and laptop otherwise it will cause chaos!

yay! i got the desktop synchronized with .06!  Going to try and get the 2.12 version going.

But a few questions before i nail this sucker: 
-D you think it's possible to make one that can auto update every set intervals or so?
-Which ID's are you talking about?

---

### Post by asrai on 2008-05-08
Yay I'm so glad it is working for you.

The id I mentioned is the device id - this is in the ~/.sync4j/evolution/scheduleworld/spds/syncml/config.txt file that will be created by following the install process for 2.12.

I definitely think it is possible to set it to automatically update.  I haven't set that myself yet but I believe it can be done using cron or gnome-schedule which is in the universe repository (go to system/administration/software sources and make sure that universe is enabled.

---

### Post by ArchangHell on 2008-06-02
Dumb question, but where are the "example configurations included in your installation"

thx

---

### Post by theZoid on 2008-06-30
> **asrai said:**
> Ok good stuff.  The plugin won't show up in evolution though.  There is a guide to getting it set up at [http://www.estamos.de/projects/SyncML/GettingStarted.html](http://www.estamos.de/projects/SyncML/GettingStarted.html)  follow that and it will set it up so you can sync via the command line. 

Once you've edited all the files as it says on that website, you should be able to sync from the command line.  If you're using scheduleworld the command will probably be "syncevolution scheduleworld" to sync all types both ways.

 To make it easier for myself (and my husband who also uses it) I created an application launcher (right click on the panel, click on add to panel, then select custom application launcher.  This will open a new box and you should change the 'type' to 'application in terminal'.  I put in the command syncevolution scheduleworld.  You just need to click on this icon on your panel to do a full normal sync.  

Give that a go and let me know if you need any more help with it.

Asrai....I've got a question, I've got it syncing, even put a launcher in the panel....however, I can't set a log directory without giving me an error....can you tell me what your log directory settings are in the config.txt and what is your name and path in your home directory?  I don't care where it is, or what it's called, but I'm doing something wrong.  So it's disabled right now, and working other than that.  Thanks!

---

