---
title: "Newest software-properties update does not work"
date: 2011-07-23
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-07-23
The newest package software-properties (0.81.2) from yesterday does not work.
This application does not start from Synaptic nor from menu (system settings - software sources) nor from terminal (sudo software-properties-gtk).

Downgrading to the previous version (0.80.13) solves the issue.

Does anyone else get this?

---

### Post by mc4man on 2011-07-23
Dead here - from terminal shows numerous warnings/ some errors

---

### Post by Harry33 on 2011-07-23
Right, and this is the bug report (815016):

[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/815016](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/815016)

---

### Post by mc4man on 2011-07-23
just ran another update and now it works, though not sure exactly what
- small snafu, had switched workspaces and logged out while synaptic was still running, had to complete in recovery
(some pixbuf libs were included

If you still see there should be a .crash in /var/crash

Also  noticed the updates gave me a new session menu, no restart though much better

---

### Post by dino99 on 2011-07-23
on i386:
- open as usual from synaptic
- from terminal: open with errors

have confirmed and posted the details.

---

### Post by mc4man on 2011-07-23
> **dino99 said:**
> on i386:
- open as usual from synaptic
- from terminal: open with errors

have confirmed and posted the details.

Works fine here all ways inc. new system settings in indicator
They're all warnings here now from terminal, no more errors
(was one, (fatal),  on .gnupg, so just because created that dir. - now there is some trustdb.gpg file inside


> gpg: /home/doug/.gnupg/trustdb.gpg: trustdb created

---

### Post by Harry33 on 2011-07-23
Definitely not working here.
I have all the updates installed available.
Using 64-bit with gnome-shell (no Unity installed) and nvidia-current 280.04.

---

### Post by dino99 on 2011-07-23
> **mc4man said:**
> Works fine here all ways inc. new system settings in indicator
They're all warnings here now from terminal, no more errors
(was one, (fatal),  on .gnupg, so just because created that dir. - now there is some trustdb.gpg file inside

glance at .gnupg: last trustdb.pgp modified on Feb 20th
other files are older.

---

### Post by VinDSL on 2011-07-23
> **Harry33 said:**
> Does anyone else get this?

No issues here - it's working every which way to Sunday...  ;)

[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/Screenshot at 2011-07-23 03:36:32(650x520).png[/IMG]]("http://vindsl.com/images/Screenshot at 2011-07-23 03:36:32.png")[/INDENT]


I have all available updates installed.
Using 32-bit with Unity and nVidia-current 280.04.

---

### Post by mc4man on 2011-07-23
> **Harry33 said:**
> Definitely not working here.
I have all the updates installed available.
Using 64-bit with gnome-shell (no Unity installed) and nvidia-current 280.04.
32 bit here, Did you get a .crash in /var/crash?
I had one orig., wouldn't let me use because of some packages not updated, that's what lead to updating, ect.



> glance at .gnupg: last trustdb.pgp modified on Feb 20th
Installs here - latest 07/17 don't have a ~/.gnupg

Edit - tried Gs - also works

---

### Post by Harry33 on 2011-07-23
> **mc4man said:**
> 32 bit here, Did you get a .crash in /var/crash?
I had one orig., wouldn't let me use because of some packages not updated, that's what lead to updating, ect.
...
Installs here - latest 07/17 don't have a ~/.gnupg

No I do not have /var/crash directory at all.
No .gnupg either.

Could someone try 64-bit and with gnome-shell session.

---

### Post by mc4man on 2011-07-23
Works fine, -   64 bit, live session. todays iso which is current as of right now.

---

### Post by Harry33 on 2011-07-23
This is debugged now.
The update-notifier needs to be installed too, if the latest software-properties 0.81.2 is used.
I used to have update-manager and update-notifier uninstalled. Then only earlier version of software-properties 0.80.13 works OK.

---

### Post by mc4man on 2011-07-23
> **Harry33 said:**
> This is debugged now.
The update-notifier needs to be installed too, if the latest software-properties 0.81.2 is used.
I used to have update-manager and update-notifier uninstalled. Then only earlier version of software-properties 0.80.13 works OK.
Interesting - at least it can still be disabled from running from startup apps (hidden by default

While it doesn't bother much on this machine with decent amount of ram, on a mem challenged one that's one on a host of processes where nvidia/cairo-gl causes excessive memory use and mem growth over time

---

### Post by Harry33 on 2011-07-23
> **mc4man said:**
> Interesting - at least it can still be disabled from running from startup apps (hidden by default

While it doesn't bother much on this machine with decent amount of ram, on a mem challenged one that's one on a host of processes where nvidia/cairo-gl causes excessive memory use and mem growth over time

That is true.

---

### Post by VinDSL on 2011-07-23
> **mc4man said:**
> While it doesn't bother much on this machine with decent amount of ram, on a mem challenged one that's one on a host of processes where nvidia/cairo-gl causes excessive memory use and mem growth over time
> **Harry33 said:**
> That is true.
Extra credit reading:  [https://bugs.launchpad.net/ubuntu/+source/cairo/+bug/725434](https://bugs.launchpad.net/ubuntu/+source/cairo/+bug/725434)  :D

---

### Post by VinDSL on 2011-07-23
w00t!!!

Just downgraded libcairo2 from 1.10.2-6ubuntu2 to 1.10.0-1ubuntu3 and...

Mem usage is back to "normal" - 288mb sitting idle at desktop, instead of 688mb!


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/Screenshot at 2011-07-23 14:34:03(650x520).png[/IMG]]("http://vindsl.com/images/Screenshot at 2011-07-23 14:34:03.png")[/INDENT]


```

$ date && lsb_release -sd || cat /etc/*release &&  uname -s -r && unity --version && /usr/lib/nux/unity_support_test -p && dpkg -s mesa-utils

Sat Jul 23 14:43:30 MST 2011
Ubuntu oneiric (development branch)
**[COLOR="Red"]Linux 3.0.0-0300-generic[/COLOR]**
unity 4.4.0
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  **[COLOR="Red"]2.1.2 NVIDIA 280.04[/COLOR]**

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 132
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

```

Gonna go pin it, before I forget...  :D

---

### Post by VinDSL on 2011-07-23
Okay...

Went to pin downgraded Libcairo2 and noticed Banshee was broken.

Reinstalling Banshee would cause havoc, based on the dialog box, so...

I upgraded libcairo2 from 1.10.0-1ubuntu3 to 1.10.2-2ubuntu2

**[cairo (1.10.2-2ubuntu2) natty]("https://launchpad.net/ubuntu/+source/cairo/1.10.2-2ubuntu2")** is working fine for me - low mem usage and no broken packages.

Pinned!


[INDENT][INDENT][IMG]http://vindsl.com/images/Screenshot at 2011-07-23 15:21:29.png[/IMG][/INDENT][/INDENT]


If I run across any problems, I'll report back.  ;)

---

### Post by Harry33 on 2011-07-24
> **VinDSL said:**
> Okay...
Went to pin downgraded Libcairo2 and noticed Banshee was broken.
Reinstalling Banshee would cause havoc, based on the dialog box, so...
I upgraded libcairo2 from 1.10.0-1ubuntu3 to 1.10.2-2ubuntu2
...
If I run across any problems, I'll report back.  ;)

Libcairo does have continuous problems especially with nvidia-current.
Could this be your issue too?

---

### Post by VinDSL on 2011-07-24
> **Harry33 said:**
> Libcairo does have continuous problems especially with nvidia-current.
Could this be your issue too?
Yes, it's the same old story.

The gl builds (e.g. with the gl backend enabled) chew up almost all of my (1gb) memory.

With '--enable-gl' removed, this machine runs fine with nvidia-current.

I'm sure this memory problem will be addressed (again) eventually, but I was looking for a workaround.

I've been running 1.10.2-2ubuntu2 for 8 hours with no problems (outside the norm).  I haven't noticed any mem leaks, et cetera, so I guess I'll run it until the devs come up with a proper fix, or it breaks my install, whichever comes first.  ;)

---

### Post by Harry33 on 2011-07-24
This thread was originally written because the application Software Sources refused to work in my setup after an update (0.81).
The reason was that now this application is tied to Update Manager via Update Notifier.
Well I have a minimalistic setup, and I did not have Update Manager Installed (I do not use it). I use Synaptic.

What is behind this, is that the updating process is centralised to Update Manager.
Synaptic has been dropped. Yes, it will still be found in repos, but for how long.
Update Manager is a simple application and easy to use.
But IMO it really is not a tool to use with dev versions.

---

### Post by Harry33 on 2011-07-25
The above mentioned issue has been fixed.
The latest version of software-properties (0.81.3) doesn't crash if update-manager/update-notifier are not installed.

See this:
> 
software-properties (0.81.3) oneiric; urgency=low
  * softwareproperties/gtk/SimpleGtkbuilderApp.py:
    - remove unneeded debug output for gobjects without a get_name()
      function
  * softwareproperties/gtk/SoftwarePropertiesGtk.py:
    - do not crash if update-notifier is not installed (LP: #815016)
  * softwareproperties/AptAuth.py:
    - do not access ~/.gnupg from AptAuth() (LP: #815034)
  * softwareproperties/SoftwareProperties.py:
    - add CDROM add support into the dbus backend (LP: #815860)


---

