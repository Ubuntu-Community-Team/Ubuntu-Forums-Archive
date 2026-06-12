---
title: "Best command to reset apt sources to distro release defaults?"
date: 2011-10-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by effenberg0x0 on 2011-10-12
I'm looking for an automated way to make sure users PCs have the right sources.list and, if possible, disable other ppas at /etc/apt/sources.list.d/ .

A bash script is easy, but requires users downloading the script, chmodding +x, running with sudo.

I imagine there probably is a more standard way to do it which I'm unaware off.

Regards,
Effenberg

---

### Post by 23dornot23d on 2011-10-12
Pull in a clean template of the sources ....... thats the easiest way .......

I used to store one on my Gmail account ..... not sure if one exists here though ....

I would expect it to ..... :confused:  thing is repos can change over time ....

---

### Post by Quackers on 2011-10-12
Try this for non-latest versions

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by effenberg0x0 on 2011-10-12
Yes, of course.

I have a script to backup current settings, wget the right one sources (if $os_version ==x.x, ... ) from an internal IP, update && upgrade. But it is a little too much for an average user. 

Of course there's also Ubuntu sources.list around the web, one could paste in gedit, the CD-ROM/USB too, but still likely to confuse users. Same thing for Ubuntu sources.list generator at [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/).

I was hoping there was some command in Ubuntu to auto do it. But I'm guessing there is not.

Regards,
Effenberg

---

### Post by 23dornot23d on 2011-10-12
Nice one Quackers ....  [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

I was just looking back to when this first started and that was in the links ....

the other was 

[http://ubuntuforums.org/showthread.php?t=1742588](http://ubuntuforums.org/showthread.php?t=1742588)

But it only renames from Natty to Oneiric ...... so loads of additional ppa's would be included this way ..... that is if they still exist ....

@ [effenberg0x0]("http://ubuntuforums.org/member.php?u=260143")

> 
I was hoping there was some command in Ubuntu to auto do it. But I'm guessing there is not.
I too would like to see a command for it ...... a fresh start so to speak - if anyone needed it.

a replacement default list may do it ....... and cleaning out some other directories with 
additional PPa's

____________________________________________________________

There is the Apt-setup ..... source package but it only seems to check for validity of existing
packages ......

[https://launchpad.net/ubuntu/oneiric/+source/apt-setup](https://launchpad.net/ubuntu/oneiric/+source/apt-setup)

```

apt-setup is used to generate an /etc/apt/sources.list for the installed
system. It does this by creating a new sources.list file (commenting out
the previous contents) and then running each program in
/usr/lib/apt-setup/generators/ in turn (run-parts ordering). Each generator
is passed the name of a temporary file that it can write sources.list lines
(and comments) to.

After the generator finishes writing the file, apt-setup-verify will be run
on it to verify that each line of the sources works, and it will be
added to the sources.list. Generators can also run apt-setup-verify
themselves and do their own error recovery if it fails. apt-setup-verify
tests each line of the file and comments out lines that do not work, and
exits zero if all deb and deb-src lines in the file are ok, 30 if the
verification process was canceled, and otherwise nonzero on error.

Generators should add both "deb" lines and corresponding
deb-src lines to the sources.list. apt-setup-verify will handle commenting
out any deb-src lines for unavailable sources.

Generators can ask configuration questions using debconf. To support
backing up, generators should exit with the special return code of 10 if
the user backs up from their first question. Each generator should provide
a progress bar text template named apt-setup/progress/<generator>, where
<generator> is the script's name with leading numbers removed. Anything
after the first dot (if any) will also be removed when constructing the
progress template name, so that different scripts that share the same
purpose can easily be written.

Generators can advance the progress bar from PROGRESS_FROM up to
PROGRESS_TO, or it will be moved to the next step before the next
generator is started.

apt-setup-verify runs apt-get update inside debconf-apt-progress, to update
the progress bar with apt progress information. By default the progress bar
will not be moved. Use --from and --to options to override this. The values
of these options will be used as start and end points for the progress bar;
each source line to be tested will get an equal share. The resulting values
are passed on to debconf-apt-progress.
For example:
    apt-setup-verify --from 1 --to 100 <file>

Note that apt-setup and its generators may be run against some other system
in a chroot (i.e., when installing Debian). If apt-setup is running this
way, then ROOT will be set to the root of the chroot that it is acting on
and all sources.list validation will occur inside the chroot.

apt-setup is split into several udebs that contain different generators.
These udebs are installed depending on the type of install; for a install
from CD, cdrom-detect queues apt-cdrom-setup for install, for an install
from the network, choose-mirror queues apt-mirror-setup, etc.

```

---

### Post by jbicha on 2011-10-12
You might need to ppa-purge each of your PPAs in case you're using an experimental PPA with newer packages than are available in the official repositories.

---

### Post by thatguruguy on 2011-10-12
I have several different computers running Ubuntu. Although I usually do a clean install, I decided to just upgrade one of them from 11.04 to 11.10.  During that process, I was informed that several of my ppas (essentially all of the ones I had installed myself) would be disabled during the upgrade process, and that I would have the option to re-enable them after the upgrade by launching Software Sources from the Ubuntu Software Center.

I don't know if it has always been handled that way, but I thought that was a smart way to handle it.

---

### Post by effenberg0x0 on 2011-10-12
> **jbicha said:**
> You might need to ppa-purge ....

Exactly, as I can't be sure if something has effectively been installed (and what) from each different sources.list entry or sources.list.d/*ppa* I may found in every PC that will go through an update. Good advice.

> **thatguruguy said:**
> I have several different computers running Ubuntu. Although I usually do a clean install, I decided to just upgrade one of them from 11.04 to 11.10.  During that process, I was informed that several of my ppas (essentially all of the ones I had installed myself) would be disabled during the upgrade process, and that I would have the option to re-enable them after the upgrade by launching Software Sources from the Ubuntu Software Center.

I don't know if it has always been handled that way, but I thought that was a smart way to handle it.

I was unaware of this, I believe it is a new feature. I'll try on one PC. Thanks for the tip.
My fear is that punctual users might have installed something that will conflict with the new packages, creating either a install or a first run incompatibility problem.

Regards,
Effenberg

---

