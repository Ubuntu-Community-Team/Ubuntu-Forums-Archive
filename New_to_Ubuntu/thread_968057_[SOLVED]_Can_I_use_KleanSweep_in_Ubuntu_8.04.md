---
title: "[SOLVED] Can I use KleanSweep in Ubuntu 8.04?"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by boof1988 on 2008-11-02
I'm running Ubuntu 8.40 (gnome).  And I am interested in using [KleanSweep](http://linux.bydg.org/~yogin/#).

Here's the description of KleanSweep at Applications->Add/Remove Applications on my desktop:

> KleanSweep allows you to reclaim disk space by finding unneeded files. It can search for files basing on several criterias; you can seek for:
* empty files
* empty directories
* backup files
* broken symbolic links
* broken executables (executables with missing libraries)
* dead menu entries (.desktop files pointing to non-existing executables)
* duplicated files
* orphaned files -- files not found in RPM (for rpm-based distros, e.g. Fedora Core, Suse) or DPKG (for dpkg based distros, e.g. Debian and Ubuntu) database
* obsolete thumbnails (thumbnails conforming to freedesktop.org standard, pointing to non-existing images)

The author's website indicates that [KleanSweep](http://linux.bydg.org/~yogin/#) requires "KDE libraries" as shown below:

> KleanSweep consists of KDE-based (C++) graphical frontend and small helper Perl script that performs actual searching. All searches, except for orphaned files, duplicates and dead menu entries are as fast as usual 'find' would be. KleanSweep requires KDE libraries and Perl.

So the question is...

Can I run KleanSweep on my system and which libraries do I need to download?

---

### Post by phidia on 2008-11-02
There's an app that could help in easily determining the libs you need called getlibs.
It works for both 32 & 64 bit systems-check it out from the thread [here]("http://ubuntuforums.org/showthread.php?t=474790").

Note: I didn't realize that kleansweep was in the repos

---

### Post by oldos2er on 2008-11-02
The beauty of using a package manager like apt is that it handles all the dependencies for you. Use Add/Remove or Synaptic Package Manager to install kleansweep.

---

### Post by boof1988 on 2008-11-02
Thanks for the fast replies.

I just wasn't sure if anything would happen after downloading some KDE libraries.  I'm new to Linux so I don't know what will happen with some applications.

I'll add the application and see what happens.  I am hoping that I can have it go through an image library (sculpture pictures) and find duplicate images.

---

### Post by Paqman on 2008-11-02
> **boof1988 said:**
> 
I just wasn't sure if anything would happen after downloading some KDE libraries.

The only thing that will happen is that they will take up a bit of extra disk space :)

Whenever you launch a KDE app on a Gnome desktop, the system will have to load up all those KDE libs, so the app may be slower to launch than a Gnome app would be. But otherwise it'll run fine. Likewise for Gnome apps on KDE.

Like many people I use Amarok on Gnome all the time. Not an issue.

---

### Post by boof1988 on 2008-11-02
I tried it out on a test case and it worked fine.  Thanks for the help.

I copied some images to a new folder and then used KleanSweep on it and it detected the duplicate image.  Not quite ready to use it on any system or root directories.  Probably wont do that ever.

The package manager is quite a good thing.  I used Applications->Add/Remove Applications and it (I guess) installed all the needed "associations".  Didn't need to install any other pieces.

Thanks again.

---

### Post by boof1988 on 2008-11-02
> **Paqman said:**
> The only thing that will happen is that they will take up a bit of extra disk space :)

Whenever you launch a KDE app on a Gnome desktop, the system will have to load up all those KDE libs, so the app may be slower to launch than a Gnome app would be. But otherwise it'll run fine. Likewise for Gnome apps on KDE.

Like many people I use Amarok on Gnome all the time. Not an issue.

I used Amarok for a short time... but when I tried to use the help (I think that's what I was trying to do), there was an error or something that said I didn't have some necessary thing installed.

Maybe I'll try it (Amarok) again.  there were some pretty cool things about it.  I especially liked that there is an embedded wiki link to the artist.  Wiki rules.

:guitar:

---

### Post by Paqman on 2008-11-03
> **boof1988 said:**
> I used Amarok for a short time... but when I tried to use the help (I think that's what I was trying to do), there was an error or something that said I didn't have some necessary thing installed.


You might want to take note of exactly what it said was missing. If you went to Synaptic and installed that package (which will probably have some bizarre name) then you might find it works. IIRC I had to do the same to get the lyrics working.

There's also Exaile, which is a Gnome-flavoured copy of Amarok. It's pretty good.

---

### Post by boof1988 on 2008-11-03
> **Paqman said:**
> You might want to take note of exactly what it said was missing. If you went to Synaptic and installed that package (which will probably have some bizarre name) then you might find it works. IIRC I had to do the same to get the lyrics working.

There's also Exaile, which is a Gnome-flavoured copy of Amarok. It's pretty good.

Thanks... I'll take a look at those.  after reading your post I downloaded Exaile to try it out.

Now... To the music.

---

