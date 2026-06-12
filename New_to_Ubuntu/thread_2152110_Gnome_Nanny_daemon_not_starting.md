---
title: "Gnome Nanny daemon not starting"
date: 2013-06-06
forum: New to Ubuntu
---

### Post by Muketeer on 2013-06-06
Hello Ubunteers, i've been trying to install Gnome Nanny on my lubuntu (raring ringtail) system but every time i click on the "parental control" icon all i get is  a message telling me that Nanny Daemon is  not started.  Others have had this problem before and i followed a thread which suggested that reinstalling from the right repositories would work, but i've done this and it still gives the same error.  During the install i get the following in terminal:

 Failed to fetch [http://ppa.launchpad.net/guadalinex-members/ppa/ubuntu/dists/raring/main/binary-i386/Packages](http://ppa.launchpad.net/guadalinex-members/ppa/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/nanny/ppa/ubuntu/dists/raring/main/source/Sources](http://ppa.launchpad.net/nanny/ppa/ubuntu/dists/raring/main/source/Sources)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/nanny/ppa/ubuntu/dists/raring/main/binary-i386/Packages](http://ppa.launchpad.net/nanny/ppa/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.

Does Gnome Nanny simply not work in raring?  What can i do to make it work?

Thanks to anyone that can help!

---

### Post by newb85 on 2013-06-06
Ah yes, Nanny.  Here's what I've been able to gather.  (My experience is with Ubuntu, not Lubuntu.)


The two PPAs that are returning error messages ended with Lucid (10.04).  (Thus the error messages.)


They ended there because Canonical added Nanny to the repos with Maverick (10.10).


Then with Natty (11.04), Gnome was replaced with Unity, GDM was replaced with LightDM, and Nanny broke.  Apparently, the maintainers overlooked a dependency needed to run the daemon (I haven't identified that dependency yet), but since that dependency was required by Gnome, it was installed by default in Ubuntu prior to 11.04.  Simply installing Gnome seemed to solve that problem, even when Unity was in use.  However, scheduling and limits to machine use still didn't seem to work, probably because of the change in Display Managers.


Unfortunately, because of the functionality problems, Canonical has since removed Nanny from the repos again.  I haven't found any current PPAs with it, either.  (Apparently, interest in parental controls has been declining in recent years.)  


I'm guessing that manually installing the version from the 12.04 repos along with that missing dependency would get everything but the machine use limitations and scheduling back up and running.  I'll do a little digging and see what I can find...

---

