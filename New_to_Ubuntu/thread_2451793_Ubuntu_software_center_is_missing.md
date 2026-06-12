---
title: "Ubuntu software center is missing"
date: 2020-10-11
forum: New to Ubuntu
---

### Post by brainbleach on 2020-10-11
For some reason the ubuntu software center (orange icon) has completely disappeared and all I have is the snap store.  How do I get it back?  

Thank you for anyone who takes the time to answer my question.

---

### Post by caseyfen on 2020-10-11
I was just wondering this myself.

---

### Post by brainbleach on 2020-10-11
you had the same thing happen?

---

### Post by caseyfen on 2020-10-11
Yeah, the same thing happened to me. I have the Snap Store still but not Ubuntu Software Center. However, googling around says that it was discontinued I guess? The confusing thing is I just installed this version (20.04.1 LTS) like 3 days ago and it had Ubuntu Software Center and then it disappeared after some updates. I guess they felt like getting rid of it entirely.

---

### Post by brainbleach on 2020-10-11
I literally was using the software center earlier this morning and all of a sudden it just disappeared.

---

### Post by caseyfen on 2020-10-11
I was using it last night as well. I can't even seem to install it manually like it's been entirely removed from the repo. Additional searching shows even more info on Snap being the replacement so I suspect we both just got updates that caused it's removal.

---

### Post by tea for one on 2020-10-11
Here are a couple of alternatives to consider:-

```
sudo apt install synaptic
```

```
sudo apt install gnome-software
```

---

### Post by Dennis N on 2020-10-11
The version of snap store in Ubuntu 20.04 initially is version 467, named "Ubuntu Software":
```
dmn@Tyana-vm:~$ snap list | grep store
snap-store         3.36.0-80-g208fd61  467   latest/stable/&#8230;  canonical*  -

```It has now reverted to version 415, named "Snap Store".
```
dmn@Tyana-vm:~$ snap list | grep store
snap-store         3.31.1+git187.84b64e0b  415   latest/stable/&#8230;  canonical*  -

```
415 is a version that handles snap packages only.
Install **gnome-software** to get a software store that can handle regular packages as well. It will be named 'Software'.
```
sudo apt install gnome-software
```
You can leave Snap Store installed as a convenience for finding snap packages. It has it's own icon.

---

### Post by brainbleach on 2020-10-11
> **Dennis N said:**
> The version of snap store in Ubuntu 20.04 initially is version 467, named "Ubuntu Software":
```
dmn@Tyana-vm:~$ snap list | grep store
snap-store         3.36.0-80-g208fd61  467   latest/stable/…  canonical*  -

```It has now reverted to version 415, named "Snap Store".
```
dmn@Tyana-vm:~$ snap list | grep store
snap-store         3.31.1+git187.84b64e0b  415   latest/stable/…  canonical*  -

```
415 is a version that handles snap packages only.
Install **gnome-software** to get a software store that can handle regular packages as well. It will be named 'Software'.
```
sudo apt install gnome-software
```
You can leave Snap Store installed as a convenience for finding snap packages. It has it's own icon.


Thank you for your response and I was able to get the gnome software installed. Was there a reason this change was made to revert the store to a snap version only?

---

### Post by scriber on 2020-10-11
Thanks for the info, I thought I was losing my mind looking for the software icon :)
Now I have it back !

---

### Post by Dennis N on 2020-10-12
Apparently the reversion to version 415 was unintended. One day later, snap-store has upgraded to version 481. 
```
dmn@Tyana-vm:~$ snap list | grep store
snap-store         3.36.0-82-g80486d0          481   latest/stable/&#8230;  canonical*  -

```
I think this one should handle regular Ubuntu repo packages, but I can't tell as it won't run at all right now. Terminal give us an error message:
```
dmn@Tyana-vm:~$ snap run snap-store
/snap/snap-store/481/usr/bin/snap-store: error while loading shared libraries: libgdk_pixbuf-2.0.so.0: cannot open shared object file: No such file or directory

```
(Attempted on otherwise up-to-date Ubuntu 20.04 after this upgrade.)

Perhaps the best solution to all this is what's given in post #8. At least up to now, a benefit with gnome-software that's of increasing importance to users is gnome-software's ability to manage Flatpak, while Ubuntu Software (snap version) could not. At some point, a new upgraded Ubuntu Software (snap version) may get this ability too.

UPDATE:
The problem above did not repeat after a later restart, immediately followed by an update offered by software updater. What fixed this is unknown, since no snap packages of any kind were upgraded after the snap-store update indicated above: 
```
dmn@Tyana-vm:~$ snap changes
ID   Status  Spawn               Ready               Summary
9    Done    today at 10:06 MST  today at 10:06 MST  Auto-refresh snap "snap-store"
10   Done    today at 10:19 MST  today at 10:19 MST  Refresh all snaps: no updates
11   Done    today at 10:42 MST  today at 10:42 MST  Refresh all snaps: no updates
12   Done    today at 19:03 MST  today at 19:03 MST  Refresh all snaps: no updates
```
"Ubuntu Software" has returned, and "Snap Store" has vanished, but Ubuntu Software still does not manage Flatpak. So it's still necessary to install gnome-software as shown in post #8 to take advantage of the automatic updating of Flatpaks.

---

### Post by grahammechanical on 2020-10-12
Yesterday I upgraded from 18.04 to 20.04 and I have an icon in the launcher called Software. When I click Show details it turns out that Software is Gnome Software and it has installed Addons for Flatpack and Snap. I still have the Snap store installed.

This change over (if it is a change over) has been going on for some time. First, Snaps could only be installed through the command line. Then the Ubuntu Software Centre had limited Snap support. The Snap store was/is an attempt to make Snap applications generally more available. Ubuntu Software Centre has been replaced by a Ubuntu branded Gnome Software with Gnome Software being modified to support Snap applications. Lastly the trademarks of Ubuntu and Gnome are removed.

I think we are seeing an ongoing development process following a general and not specific plan or goal. Adjustments and corrections are made along the way. Just another day in the Linux distribution office.

Regards.

---

