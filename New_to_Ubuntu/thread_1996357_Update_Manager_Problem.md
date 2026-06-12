---
title: "Update Manager Problem"
date: 2012-06-04
forum: New to Ubuntu
---

### Post by Dineshjis on 2012-06-04
Currently unable to run the update manager. it goes and downloads upto a certain point and crashes. 

following message displayed:

[B]Failed to download repository information

- check internet connection[/B]

also shows below message


W:Failed to fetch file:/var/cache/apt-build/repository/dists/apt-build/main/binary-i386/Packages  File not found
, E:Some index files failed to download. They have been ignored, or old ones used instead.


Note: Internet connection works

I have installed ubuntu 12.04 on windows 7 [dual boot]

I am an absolute bigginer and  desperate for help!

Dinesh J

---

### Post by Lyfang on 2012-06-04
Update Manager is a front-end to apt. Try Synaptic or try to upgrade from Terminal:
```
sudo apt-get update && sudo apt-get upgrade
```

Did you change the repositories in Software Sources or /etc/apt/sources.list?

See also: [http://ubuntuforums.org/showthread.php?t=1922461](http://ubuntuforums.org/showthread.php?t=1922461)

---

### Post by krustenBrot on 2012-06-04
Are you from Germany?

I stumbled upon an error today using the update manager, turned out it was the local (german) Server.
To change it open the Update Manager 
-> click on *Settings* in the lower left corner 
-> change to Tab "*Ubuntu Software*" 
-> change the value for "*Download from:* "by clicking on the field right next to it, to: "*Main Server*" 



..enjoy your new, fresh & good looking system :)

):P

---

### Post by Dineshjis on 2012-06-04
> **krustenBrot said:**
> Are you from Germany?

I stumbled upon an error today using the update manager, turned out it was the local (german) Server.
To change it open the Update Manager 
-> click on *Settings* in the lower left corner 
-> change to Tab "*Ubuntu Software*" 
-> change the value for "*Download from:* "by clicking on the field right next to it, to: "*Main Server*" 



..enjoy your new, fresh & good looking system :)

):P

Nope, I am from Sri Lanka and the I have always been using the Main Server. I am quite not getting it. :(

---

### Post by Dineshjis on 2012-06-04
> **Lyfang said:**
> Update Manager is a front-end to apt. Try Synaptic or try to upgrade from Terminal:
```
sudo apt-get update && sudo apt-get upgrade
```

Did you change the repositories in Software Sources or /etc/apt/sources.list?

See also: [http://ubuntuforums.org/showthread.php?t=1922461](http://ubuntuforums.org/showthread.php?t=1922461)

thanks for the info. did it in the terminal but the final message was "W: Failed to fetch file:/Var/Cache/apt-build/repository/dists/ apt-buildermain ary-i386/ packages File not found"

Any solution to redo it through the front end program

Thanks

---

### Post by dmp_mech on 2012-09-14
> **Lyfang said:**
> Update Manager is a front-end to apt. Try Synaptic or try to upgrade from Terminal:
```
sudo apt-get update && sudo apt-get upgrade
```Did you change the repositories in Software Sources or /etc/apt/sources.list?

See also: [http://ubuntuforums.org/showthread.php?t=1922461](http://ubuntuforums.org/showthread.php?t=1922461)

I have similar problem. I used above command but I got failure messages.

dharmesh@patadiya:~$ sudo apt-get update && sudo apt-get upgrade
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


My internet connection is also fine and working. I am writing below what is in /etc/apt/source.list.d
There are two files in that folder.  picaso-octave-precise.list and picaso-octave-precise.list.save.
In each file there is two lines.

deb [http://ppa.launchpad.net/picaso/octave/ubuntu](http://ppa.launchpad.net/picaso/octave/ubuntu) precise main
deb-src [http://ppa.launchpad.net/picaso/octave/ubuntu](http://ppa.launchpad.net/picaso/octave/ubuntu) precise main

I am unable to install octave, and other softwares like vlc media player, libreCAD, etc.

please help me.

---

### Post by newb85 on 2012-09-14
> **dmp_mech said:**
> I have similar problem. I used above command but I got failure messages.

dharmesh@patadiya:~$ sudo apt-get update && sudo apt-get upgrade
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


My internet connection is also fine and working. I am writing below what is in /etc/apt/source.list.d
There are two files in that folder.  picaso-octave-precise.list and picaso-octave-precise.list.save.
In each file there is two lines.

deb [http://ppa.launchpad.net/picaso/octave/ubuntu](http://ppa.launchpad.net/picaso/octave/ubuntu) precise main
deb-src [http://ppa.launchpad.net/picaso/octave/ubuntu](http://ppa.launchpad.net/picaso/octave/ubuntu) precise main

I am unable to install octave, and other softwares like vlc media player, libreCAD, etc.

please help me.

The error messages you're receiving probably mean that something else is using dpkg.  You're not trying to do this while you have Software Center installing something, right?  Also, do you have your system set to automatically install security updates?

---

### Post by black veils on 2012-09-14
i saw errors like this when using live mode, for some strange reason the sources.list file wasnt right, or there was corruption somewhere.

so one of two things might fix it:

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

or simply going into the **update manager** >> **settings** >> **ubuntu software** tab, make sure all are checked >> **other software **tab, make sure all are checked >> **updates **tab, make sure **important security updates** and **proposed updates** are checked. this last one shouldnt be necessary, as it is only about what you allow to update, but it was the only thing which would correct the live systems for me. very strange.

---

### Post by critin on 2012-09-14
> Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

As post #7 said, this often means something is updating or a source is still open.  Make sure Synaptic and Software Center are closed when updating from terminal.  And everything is closed when updating from update manager, and so on.  

Waiting awhile and trying again later often works if nothing is open.

---

