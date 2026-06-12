---
title: "enlightenment e17 not working"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by Periswell on 2008-09-29
hi i tried to install enlightenment today and e16 works but when i heard that e17 was usable i installed it. now when i load the session at the login screen, it says
> xsession: unable to launch "/opt/e17/bin/enlightenment" xsession --- "/opt/e17/bin/enlightenment" not found: falling back to default session.

i dont know what to do. please help.

-josh

---

### Post by lapubell on 2008-09-29
i would apt-get remove-purge both e16 and e17 then reinstall just e17.

but I'm lazy.

---

### Post by lapubell on 2008-09-29
you might also want to look into opengeu.

[http://opengeu.intilinux.com/Home.html](http://opengeu.intilinux.com/Home.html)

it is ubuntu but with e17 as the main xsession instead of gnome.

---

### Post by Tux Aubrey on 2008-09-30
I agree with removing the whole shebang and starting again.

Where did you install e17 from?  The version in the Ubuntu repos (ie in default synaptic) is way way too old to bother with (it is a 2004 build that is more of an extension to e16 than a true e17 desktop.)  As far as I know, no one has packaged a more recent build specifically for Ubuntu - but there is a very recent build available from the Debian experimental repo or from [http://xsm.alphagemini.org/E17/repository/index.html](http://xsm.alphagemini.org/E17/repository/index.html).  That repo includes debs for build e16.999.050 which is where e17 current stands.

It does _not_ install cleanly on Hardy Heron without resolving a couple of conflicts first (I did it successfully last night but can't remember the exact packages you need to upgrade first as I'm not on my home machine).  Reply or PM me if you want the details.

In my opinion you would be FAR FAR better off installing it from source (svn) via one of the scripts available to do it properly.

[Here's a full How-To for Ubuntu]("http://ubuntuforums.org/showthread.php?t=916690") and a cut down step-by-step version (by me!) is [HERE]("http://cafelinux.org/OzOs/content/how-install-ozos-desktop-existing-os").  That's based on Rui Pais "OzOS" modifications to the developers' script and will give you the option of adding a few other tools to do e17 backups and restoration.  It also avoids some of the flakier e17 modules and apps that can cause grief for new users. (But you can add them later if you like pain)

The other alternative is to go with [OpenGEU]("http://opengeu.intilinux.com/Home.html") or [Maryan Linux]("http://www.maryanlinux.com/") which are (as stated above) Ubuntu with a recent e17 default desktop (both are at version 16.999.043). They are both very solid distros now and have some nice additional tools. [Elive]("http://www.elivecd.org/") is sort of the same but based directly on Debian (but the latest beta of Elive is terribly unstable).

Finally, you could use a [full OzOS install ]("http://cafelinux.org/OzOs/content/ozos-iso-downloads-torrents")- this is a very minimal Xubuntu base with Rui Pais script to install, update and generally maintain e17.  It is not as "fully featured" as either Maryan or OpenGEU but provides a very solid base on which to build a system (the Ubuntu repos are enabled).  Rui has also built a "minimal Gnome" desktop that is available from the OzOS repos to be installed alongside e17.

If I've missed anything, I'm sure someone will jump in.

:guitar:

---

