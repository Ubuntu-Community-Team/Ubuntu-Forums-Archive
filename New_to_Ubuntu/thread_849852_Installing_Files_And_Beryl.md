---
title: "Installing Files And Beryl"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by Oreo Killa 225 on 2008-07-04
Ok, how do I install .exe files, if there are no .tar.gz options for that product?

On a side note, when trying to install beryl-core-0.2.1 on Ubuntu 8.04, it says:

[quote="Konsole"]Configure: error: C compiler cannot create executables
See 'config.log' for more details.[/quote]

Just dual-booted Vista with Ubuntu today, so any help is appreciated.

---

### Post by dizee on 2008-07-04
Beryl is discontinued. It is now known as Compiz fusion and is installable from the repos.

what program are you trying to install that only has .exe files? unless you definitely need that program it would be easier to find a linux equivalent. but if you do need it you can try using the program **wine** to install it.

---

### Post by Oreo Killa 225 on 2008-07-04
Where do I find compiz, and wine?

**EDIT:** Nevermind, found wine.

---

### Post by Dutch70 on 2008-07-04
Check this page for linux equivalents.

[http://ubuntuforums.org/showthread.php?t=831190&highlight=frostwire](http://ubuntuforums.org/showthread.php?t=831190&highlight=frostwire)

---

### Post by ChameleonDave on 2008-07-04
> **Oreo Killa 225 said:**
> Ok, how do I install .exe files, if there are no .tar.gz options for that produc

That shows that you have things back-to-front.

First you see if the software is available in the standard software repositories (use Synaptic to do that).  Secondly, you look online for a .deb file to install.  The third option is to look for a source tarball that you can compile.  If that fails too, then the fourth option is to find a Windows program (ending in .exe usually) and run it using Wine.  The fifth option is to run the program in a Windows installation within a virtual machine.  The sixth and final option, and absolute last resort, is to dual-boot into Windows and run it there.

It seems you're first going for option 3 and then 4.  What about 1 and 2?

---

### Post by Oreo Killa 225 on 2008-07-05
After I went to Pack Manager, installed confiz, what do I do now?

---

### Post by Tatty on 2008-07-05
Compiz is installed in Hardy by default.  Just go to System->Preferences->Appearance, then go to the visual effects tab.  By default you get two preset options of normal or extra.

If you wish to get more involved with customising your compiz settings then you need to install the compizconfig-settings-manager.

If you want to alter your window decorators then you will need to install emerald.

---

### Post by overdrank on 2008-07-05
> **Oreo Killa 225 said:**
> After I went to Pack Manager, installed confiz, what do I do now?

Too add to Tatty

[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

:)

---

### Post by flytripper on 2008-07-05
advanced desktop effects settings in system>preferences

---

### Post by Sef on 2008-07-05
Read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by Oreo Killa 225 on 2008-07-05
Then apparently I already had it installed.

Just thought I didn't, because my friend's looks different.
But I think he uses a different version of Ubuntu.

Thanks.

---

### Post by Oreo Killa 225 on 2008-07-05
By the way, does anyone know any good fonts when using Fire Fox?

---

### Post by Canis familiaris on 2008-07-05
```
sudo apt-get install ubuntu-restricted-extras
```
It will install all the codecs,Flash,Java,and the fonts you require

---

### Post by Oreo Killa 225 on 2008-07-05
I know, but any suggestions on a good one to use?

---

### Post by saratchandra on 2008-07-05
> **Oreo Killa 225 said:**
> Then apparently I already had it installed.

Just thought I didn't, because my friend's looks different.
But I think he uses a different version of Ubuntu.

Thanks.

Intsall ccsm from the repos to configure effects.

---

