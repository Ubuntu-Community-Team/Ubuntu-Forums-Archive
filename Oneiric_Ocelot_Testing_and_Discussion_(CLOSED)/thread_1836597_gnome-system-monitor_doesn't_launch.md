---
title: "gnome-system-monitor doesn't launch"
date: 2011-08-31
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sgage on 2011-08-31
For the last couple of days, gnome-system monitor has been aborting at launch with the following error:

gnome-system-monitor: symbol lookup error: /usr/lib/libgiomm-2.4.so.1: undefined symbol: g_time_zone_monitor_get_type

Anyone else seeing this bug?

---

### Post by cariboo on 2011-08-31
Works fine here.

---

### Post by RavisPohan on 2011-08-31
I get this too, with gnome-system-monitor and with inkscape, to date; running up-to-date oneiric on amd64.

---

### Post by sgage on 2011-08-31
> **RavisPohan said:**
> I get this too, with gnome-system-monitor and with inkscape, to date; running up-to-date oneiric on amd64.

I am on amd64 oneiric as well.

---

### Post by dino99 on 2011-08-31
with i386 and logged as gnome-classic:

oem@oem-desktop:~$ gnome-system-monitor
gnome-system-monitor: symbol lookup error: /usr/lib/libgiomm-2.4.so.1: undefined symbol: g_time_zone_monitor_get_type

reported: [https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/838196](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/838196)

---

### Post by sgage on 2011-08-31
> **dino99 said:**
> with i386 and logged as gnome-classic:

oem@oem-desktop:~$ gnome-system-monitor
gnome-system-monitor: symbol lookup error: /usr/lib/libgiomm-2.4.so.1: undefined symbol: g_time_zone_monitor_get_type

reported: [https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/838196](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/838196)

Thanks dino!

---

### Post by P-I H on 2011-08-31
Works fine here on an amd-64 system installed from today's ( 31/8 ) daily build.

---

### Post by lidex on 2011-08-31
I get this as well. Unity on amd64. Also affecting PulseAudio Volume Control.

```
lidex@dev-desktop:~$ pavucontrol
pavucontrol: symbol lookup error: /usr/lib/libgiomm-2.4.so.1: undefined symbol: g_time_zone_monitor_get_type

lidex@dev-desktop:~$ gnome-system-monitor
gnome-system-monitor: symbol lookup error: /usr/lib/libgiomm-2.4.so.1: undefined symbol: g_time_zone_monitor_get_type
```

EDIT:I'm getting same error with inkscape

---

### Post by VinDSL on 2011-09-01
> **sgage said:**
> For the last couple of days, gnome-system monitor has been aborting at launch with the following error:

gnome-system-monitor: symbol lookup error: /usr/lib/libgiomm-2.4.so.1: undefined symbol: g_time_zone_monitor_get_type

Anyone else seeing this bug?

> **RavisPohan said:**
> I get this too [...]

Me too! Oneiric Unity 3D, 32-bit - 3.0 & 3.1 kernel(s).

> **dino99 said:**
> with i386 and logged as **gnome-classic** [...]
Interesting!

Here's my output from cli:

```

vindsl@Zuul:~$ gnome-system-monitor
gnome-system-monitor: symbol lookup error: /usr/lib/libgiomm-2.4.so.1: undefined symbol: g_time_zone_monitor_get_type
vindsl@Zuul:~$

```
Smells like a missing library, to me...  ;)

---

### Post by dino99 on 2011-09-01
maybe a gconf/dconf race: settings changed when we switch unity/classic ?

---

### Post by VinDSL on 2011-09-01
> **dino99 said:**
> maybe a gconf/dconf race: settings changed when we switch unity/classic ?
I booted into "Classic" one time, and my "Unity" install has had problems ever since.

Now, every time I boot into "Unity 3D", an error related to "Classic" comes up.

The only reason I know "System Monitor" is broken, is because I use it to kill the notification process. Clicking "Cancel" on the error dialog doesn't do jack!  It just keeps coming back, like a bad dream.

LoL!  Oh, what a tangled web we weave...  :D

---

### Post by sgage on 2011-09-01
> **VinDSL said:**
> Me too! Oneiric Unity 3D, 32-bit - 3.0 & 3.1 kernel(s).


Interesting!

Here's my output from cli:

```

vindsl@Zuul:~$ gnome-system-monitor
gnome-system-monitor: symbol lookup error: /usr/lib/libgiomm-2.4.so.1: undefined symbol: g_time_zone_monitor_get_type
vindsl@Zuul:~$

```
Smells like a missing library, to me...  ;)

That was the first thing I checked, but libgiomm seems to be there...

---

### Post by MadCow108 on 2011-09-01
the symbol is defined in libgio to which libgiomm should be linked
```
$ ldd -r /usr/lib/libgiomm-2.4.so.1 | grep gio
	libgio-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0 (0x00007f256fc06000)
```
```
$ nm --dynamic /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0 | grep g_time_zone_monitor_get_type
000000000007bca0 T g_time_zone_monitor_get_type
```

try reinstalling libglibmm-2.4-1c2a and libglib2.0-0
```
sudo apt-get install --reinstall libglib2.0-0 libglibmm-2.4-1c2a
```

---

### Post by dino99 on 2011-09-01
> **MadCow108 said:**
> the symbol is defined in libgio to which libgiomm should be linked
```
$ ldd -r /usr/lib/libgiomm-2.4.so.1 | grep gio
	libgio-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0 (0x00007f256fc06000)
```
```
$ nm --dynamic /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0 | grep g_time_zone_monitor_get_type
000000000007bca0 T g_time_zone_monitor_get_type
```

try reinstalling libglibmm-2.4-1c2a and libglib2.0-0
```
sudo apt-get install --reinstall libglib2.0-0 libglibmm-2.4-1c2a
```

just reinstall them but still same issue

oem@oem-desktop:~$ gnome-system-monitor
gnome-system-monitor: symbol lookup error: /usr/lib/libgiomm-2.4.so.1: undefined symbol: g_time_zone_monitor_get_type

---

### Post by ricotz on 2011-09-01
> **dino99 said:**
> just reinstall them but still same issue

oem@oem-desktop:~$ gnome-system-monitor
gnome-system-monitor: symbol lookup error: /usr/lib/libgiomm-2.4.so.1: undefined symbol: g_time_zone_monitor_get_type

Just to solve this confusion, this is caused by a the newer glib2.0  2.29.18 which broke the API/ABI in its development cycle and the other  apps/libs like glibmm2.4 need to catch up to solve this problem.

---

### Post by MadCow108 on 2011-09-01
2.29.18 is not in the archives.
Also I find it weird that they would break api in a minor bugfix release

---

### Post by dino99 on 2011-09-01
> **ricotz said:**
> Just to solve this confusion, this is caused by a the newer glib2.0  2.29.18 which broke the API/ABI in its development cycle and the other  apps/libs like glibmm2.4 need to catch up to solve this problem.

Thanks to take time to glabce here, not a big issue after all, will wait the next step. ;) report invalidated

---

### Post by sgage on 2011-09-01
> **MadCow108 said:**
> 2.29.18 is not in the archives.
Also I find it weird that they would break api in a minor bugfix release

It's in ricotz' testing ppa, though - I backed off to .16 and system monitor works fine. Guess I'll mark this thread solved...

---

### Post by MadCow108 on 2011-09-01
> **sgage said:**
> It's in ricotz' testing ppa, though - I backed off to .16 and system monitor works fine. Guess I'll mark this thread solved...

that ppa is most likely broken then.
judging from their soversion libgio-2.0 has never broken api yet (libglibmm once), I doubt they do it in a third digit version increase.
these core components are for good reasons extremely api/abi stable, it usually only happens on major transitions (like gnome2 -> gnome3, kde3 -> kde4 etc)

---

### Post by sgage on 2011-09-01
> **MadCow108 said:**
> that ppa is most likely broken then.
judging from their soversion libgio-2.0 has never broken api yet (libglibmm once), I doubt they do it in a third digit version increase.
these core components are for good reasons extremely api/abi stable, it usually only happens on major transitions (like gnome2 -> gnome3, kde3 -> kde4 etc)

I don't know about any of that. I just know that when I ppa-purged ricotz/testing, the problem went away.

---

### Post by ricotz on 2011-09-01
> **MadCow108 said:**
> that ppa is most likely broken then.
judging from their soversion libgio-2.0 has never broken api yet (libglibmm once), I doubt they do it in a third digit version increase.
these core components are for good reasons extremely api/abi stable, it usually only happens on major transitions (like gnome2 -> gnome3, kde3 -> kde4 etc)

glib 2.29.x is not a stable version! they can do whatever they want as long the final version (2.30) is compatible with 2.28. Updating glibmm2.4 to 2.29.12 solves the issue.

---

### Post by dino99 on 2011-09-01
> **ricotz said:**
> glib 2.29.x is not a stable version! they can do whatever they want as long the final version (2.30) is compatible with 2.28. Updating glibmm2.4 to 2.29.12 solves the issue.

Thanks it works smootly ;)

---

