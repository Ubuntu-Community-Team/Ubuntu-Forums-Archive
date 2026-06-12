---
title: "New nvidia-current 275.09.07-0ubuntu2 in repos now"
date: 2011-06-23
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-06-23
The newest flavour of nvidia-current (275.09.07-0ubuntu2) has just landed in official Oneiric repos.
That build has the multiarch support.
So it now supports new mesa builds too.
However, the current newest mesa (7.10.3-0ubuntu3) in Oneiric repos is build to break proprietary drivers, so we have to wait for a new build.

See here:
> libgl1-mesa-glx 7.10.3-0ubuntu3
Breaks:
fglrx
nvidia-173
nvidia-current
[https://launchpad.net/ubuntu/+source/mesa/7.10.3-0ubuntu3](https://launchpad.net/ubuntu/+source/mesa/7.10.3-0ubuntu3)
[https://launchpad.net/ubuntu/oneiric/+source/nvidia-graphics-drivers/275.09.07-0ubuntu2](https://launchpad.net/ubuntu/oneiric/+source/nvidia-graphics-drivers/275.09.07-0ubuntu2)

---

### Post by Harry33 on 2011-06-23
Actually I did this installation and it works fine.

I installed the first version of mesa 7.10.3-0ubuntu1, which has the multiarch support, but which does not break the 275.09 series nvidia-current. Then I reinstalled the newest nvidia-current-0ubuntu2.
From here:
[https://launchpad.net/ubuntu/+source/mesa/7.10.3-0ubuntu1](https://launchpad.net/ubuntu/+source/mesa/7.10.3-0ubuntu1)

It is imperative that nvidia-current is installed after the mesa packages, otherwise you will lose 3D and you will get the fallback (gnome-panel3) session but not gnome-shell nor any other session requiring 3D.
From here:
[https://launchpad.net/ubuntu/oneiric/+source/nvidia-graphics-drivers/275.09.07-0ubuntu2](https://launchpad.net/ubuntu/oneiric/+source/nvidia-graphics-drivers/275.09.07-0ubuntu2)

---

### Post by VinDSL on 2011-06-24
Nice one, Harry!

I used your method, on a fresh UbuOO Daily Build (22-Jun).

These are the Mesa debs that I downloaded:

```

libegl1-mesa_7.10.3-0ubuntu1_i386.deb
libegl1-mesa-drivers_7.10.3-0ubuntu1_i386.deb
libgl1-mesa-dri_7.10.3-0ubuntu1_i386.deb
libgl1-mesa-glx_7.10.3-0ubuntu1_i386.deb
libglu1-mesa_7.10.3-0ubuntu1_i386.deb

```

Then nVidia Current:

```

nvidia-current 275.09.07-0ubuntu2

```


And, here is the result...


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-24-jun-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-24-jun-2011.png")[/INDENT]


Thanks!

---

### Post by Harry33 on 2011-06-24
And now the new repaired mesa build (7.10.3-0ubuntu4) is on its way in Launchpad.

Here:
[https://launchpad.net/ubuntu/oneiric/+source/mesa/7.10.3-0ubuntu4](https://launchpad.net/ubuntu/oneiric/+source/mesa/7.10.3-0ubuntu4)

> Changelog
mesa (7.10.3-0ubuntu4) oneiric; urgency=low
  * debian/control:
    - Make the Breaks against the proprietary drivers versioned again now that
      the proprietary drivers work well with multi-arch mesa. (LP: #798049)
 -- Alberto Milone <email address hidden>   Fri, 24 Jun 2011 12:18:53 +0200

---

### Post by VinDSL on 2011-06-24
> **Harry33 said:**
> And now the new repaired mesa build (7.10.3-0ubuntu4) is on its way in Launchpad.

Here:
[https://launchpad.net/ubuntu/oneiric/+source/mesa/7.10.3-0ubuntu4](https://launchpad.net/ubuntu/oneiric/+source/mesa/7.10.3-0ubuntu4)
Heh!

> 
oneiric i386 Successfully built (DONE)


Should I try it?!?!?  :D

---

### Post by VinDSL on 2011-06-24
Caveat emptor!

```

vindsl@Zuul:~$ date && lsb_release -sd || cat /etc/*release &&  uname -s -r && unity --version && /usr/lib/nux/unity_support_test -p
Fri Jun 24 05:11:02 MST 2011
Ubuntu oneiric (development branch)
Linux 3.0-1-generic
unity 4.0.1
[B][COLOR="Red"]X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  138 (NV-GLX)
  Minor opcode of failed request:  4 ()
  Resource id in failed request:  0x24f
  Serial number of failed request:  39
  Current serial number in output stream:  39[/COLOR][/B]

```

Guess I'll be going back to 7.10.3-0ubuntu1  ;)

---

### Post by sparker256 on 2011-06-24
> **VinDSL said:**
> Caveat emptor!

```

vindsl@Zuul:~$ date && lsb_release -sd || cat /etc/*release &&  uname -s -r && unity --version && /usr/lib/nux/unity_support_test -p
Fri Jun 24 05:11:02 MST 2011
Ubuntu oneiric (development branch)
Linux 3.0-1-generic
unity 4.0.1
[B][COLOR="Red"]X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  138 (NV-GLX)
  Minor opcode of failed request:  4 ()
  Resource id in failed request:  0x24f
  Serial number of failed request:  39
  Current serial number in output stream:  39[/COLOR][/B]

```

Guess I'll be going back to 7.10.3-0ubuntu1  ;)

After doing a sudo aptitude update && sudo aptitude safe-upgrade I get exactly the same thing with a unity 2D desktop. Tried X-Plane and it will not run but when I looked at Nvidia settings it looked fine. Normanly if something is messed up Nvidia settings will pop up a dialog box saying there is a problem. Not sure where to go from here. :confused:

Bill

---

### Post by sparker256 on 2011-06-24
> **sparker256 said:**
> After doing a sudo aptitude update && sudo aptitude safe-upgrade I get exactly the same thing with a unity 2D desktop. Tried X-Plane and it will not run but when I looked at Nvidia settings it looked fine. Normanly if something is messed up Nvidia settings will pop up a dialog box saying there is a problem. Not sure where to go from here. :confused:

Bill

Reinstalled Nvidia and fixed it.  :D

Bill

---

### Post by Harry33 on 2011-06-24
The newest mesa packages (7.10.3-0ubuntu4) works very well.
Note, however, that proprietary driver users must reinstall the graphic drivers after the mesa installation. Otherwise the 3D is gone.

---

