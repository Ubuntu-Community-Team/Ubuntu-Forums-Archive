---
title: "Desktop failing to start today due to glib2.0 update"
date: 2011-08-17
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Catharsis on 2011-08-17
UPDATE: This bug has been fixed in glib2.0 - 2.29.16-0ubuntu2. The problem was a conflict with libzeitgeist-gio.


Hi all, just wanted to share a friendly warning of breakage from Bryce Harrington:

[QUOTE=Bryce Harrington]Jono and jcastro brought to our attention today a rather nasty bug that
we expect most users who update oneiric today will hit, which causes the
GNOME session to fail.  X then exits normally but you're left at the
console (or a black screen).

The problem was traced to the glib2.0 update to 2.29.16 from today.

As a workaround, if you downgrade to the previous glib2.0, the desktop
starts up properly (confirmed by Sarvatt, myself, and jcastro).

You may find the old glib2.0 debs in /var/cache/apt/, or from launchpad:

 [https://launchpad.net/ubuntu/+source/glib2.0/2.29.14-0ubuntu1/+build/2644912](https://launchpad.net/ubuntu/+source/glib2.0/2.29.14-0ubuntu1/+build/2644912)
 [https://launchpad.net/ubuntu/+source/glib2.0/2.29.14-0ubuntu1/+build/2644910](https://launchpad.net/ubuntu/+source/glib2.0/2.29.14-0ubuntu1/+build/2644910)

Bryce[/QUOTE]

The original email from ubuntu-devel can be found [here](https://lists.ubuntu.com/archives/ubuntu-devel/2011-August/033977.html).

---

### Post by rbrick49 on 2011-08-17
> **Catharsis said:**
> UPDATE: This bug has been fixed in glib2.0 - 2.29.16-0ubuntu2. The problem was a conflict with libzeitgeist-gio.


Hi all, just wanted to share a friendly warning of breakage from Bryce Harrington:



The original email from ubuntu-devel can be found [here](https://lists.ubuntu.com/archives/ubuntu-devel/2011-August/033977.html).
yes I have that bug from a new install today unity goes to black screen unity-2
d slow but ok ,gnome-shell appears ok.

---

### Post by garvinrick4 on 2011-08-17
#Have one install that when downgraded to 2.29.14 successfully boots now.
#Using mirror anl.gov in United states- up to date mirror. With upgrades complete. (4:40 PM Pacific
stard time. United States.)

Date: Wed, 17 Aug 2011 14:32:41 +1000 Source: glib2.0 Binary: libglib2.0-0 libglib2.0-udeb libglib2.0-bin libglib2.0-dev libglib2.0-0-dbg libglib2.0-data libglib2.0-doc libgio-fam libglib2.0-0-refdbg Architecture: [COLOR=Red]source Version: 2.29.16-0ubuntu2[/COLOR] Distribution: oneiric Urgency: low Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com> Changed-By: Christopher James Halse Rogers <raof@ubuntu.com> Description:   libgio-fam - GLib Input, Output and Streaming Library (fam module)  libglib2.0-0 - GLib library of C routines  libglib2.0-0-dbg - Debugging symbols for the GLib libraries  libglib2.0-0-refdbg - GLib library of C routines - refdbg library  libglib2.0-bin - Programs for the GLib library  libglib2.0-data - Common files for GLib library  libglib2.0-dev - Development files for the GLib library  libglib2.0-doc - Documentation files for the GLib library  libglib2.0-udeb - GLib library of C routines - minimal runtime (udeb) Launchpad-Bugs-Fixed: 827753 Changes:   glib2.0 (2.29.16-0ubuntu2) oneiric; urgency=low  . 
  [COLOR=Red] * Add Conflicts: against libzeitgeist-gio.  
This package was removed in the      Natty cycle, but upgraders might still have it installed. 
 It used the      API added in the now-dropped 71_gio_launch_handler patch, and so now breaks      anything using glib.  (LP: #827753)[/COLOR]

---

### Post by rapiertg on 2011-08-18
The update does not fix my laptop. Checked, and zeitgeist-gio is not installed. 2.29.16-0ubuntu2 and 2.29.16-0ubuntu1 are not working.

---

### Post by garvinrick4 on 2011-08-18
> The update does not fix my laptop. Checked, and zeitgeist-gio is not  installed. 2.29.16-0ubuntu2 and 2.29.16-0ubuntu1 are not working.I had to downgrade to 2.29.14 which I got from launchpad from another install in
.deb so it was already made and dropped in a drive in /media/home and booted
into install that was not booting(also no internet).
ctrl/alt/F1
log-in
then changed directories to
cd /media/home
ls
sudo dpkg -i (copy and paste package name in .deb)
sudo reboot
Then it booted into X
#Will have to upgrade back when all is well to 2.29.16
#You did notice it is a problem specific to installs that were upgraded and not to
fresh installs of 11.10

---

### Post by Catharsis on 2011-08-19
> **rapiertg said:**
> The update does not fix my laptop. Checked, and zeitgeist-gio is not installed. 2.29.16-0ubuntu2 and 2.29.16-0ubuntu1 are not working.

Are you sure that you're affected by this bug and not another one? Did downgrading the package fix it?

---

### Post by rapiertg on 2011-08-19
Downgrading to  2.29.14 helped. Networking and X are working. Don't think if its zeitgeist related as i purged it completelly.

---

### Post by Catharsis on 2011-08-19
> **rapiertg said:**
> Downgrading to  2.29.14 helped. Networking and X are working. Don't think if its zeitgeist related as i purged it completelly.

You should probably file a new bug report then.

---

### Post by rapiertg on 2011-08-21
Found out what was causing it:
[https://bugs.launchpad.net/ubuntu/oneiric/+source/wncksync/+bug/829778](https://bugs.launchpad.net/ubuntu/oneiric/+source/wncksync/+bug/829778)

---

