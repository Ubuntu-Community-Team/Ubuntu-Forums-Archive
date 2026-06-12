---
title: "Unity Not Loading"
date: 2011-08-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by andyrogers2008 on 2011-08-12
Hi

I have upgraded to 11.10 in the middle of July with no issues at all, Gnome Shell Working, Unit 2d & 3d working all as well.

But however since around the beginning of August, Unity no longer wants to load its Menu, and Unity side bar any more.

All I get is my background and the top menu being this (the Nautilus menu):-

[ATTACH]199916[/ATTACH]

I dont even get any indicators, or Logout button.

Has anyone else had this, and is it fixable or can I do something to get Unity working again as I see from other posts people have it working.

I was hoping the latest round of updates would resole the problem, but so far nothing had changed.

Any input would really be appreciated.

Thanks

Andy

---

### Post by Woody1987 on 2011-08-12
This is exactly what has happened to me. I have a radeon 6950 and the open source drivers were working fine, but the fan was spinning far too fast so I opted for fglrx but they didnt work correctly, so I removed them. Ever since then I have this same problem in both unity and unity2d

---

### Post by P-I H on 2011-08-12
In case you are using the fglrx driver it might create that kind of problem.
In my case, after today's updates, I am able to login to Gnome and Ubuntu 2D with fglrx. With the open radeon driver I can login to Gnome, Ubuntu and Ubuntu 2D.

---

### Post by andyrogers2008 on 2011-08-12
So are we saying this is graphic driver related?  My initial thoughts were it maybe compiz related.

I have got an Intel based graphics setup in my laptop.  Are there any other drivers which I could try instead?

Thanks

Andy

---

### Post by cecilpierce on 2011-08-12
Last updates killed unity again, have to go to tty1 and type startx, then goes into classic.....crud   :(

---

### Post by Bowmore on 2011-08-12
One reason causing Unity to crash at login is when using a solid color or gradients as a wallpaper. I was going to file a bug when I found this one: [Unity crashes if you select a gradient as wallpaper](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/825091)

---

### Post by andyrogers2008 on 2011-08-12
I have just tried a different wallpaper in case, and no wallpaper but this made no difference.

---

### Post by andyrogers2008 on 2011-08-12
right ok, i seem to have got my self working again now by first doing a 
apt-get autoremove compiz-core --purge

then reinstall compiz-core unity ubuntu-desktop

---

### Post by cecilpierce on 2011-08-12
didnt work for me, blank screen with pointer, Alt+SysRq+K to log out, then choose unity 2d is all I can get   :confused:

---

### Post by rbrick49 on 2011-08-12
> **P-I H said:**
> In case you are using the fglrx driver it might create that kind of problem.
In my case, after today's updates, I am able to login to Gnome and Ubuntu 2D with fglrx. With the open radeon driver I can login to Gnome, Ubuntu and Ubuntu 2D.
@P-I-H didyou install the new beta driver from amd I tried tistas no luck and fglrx from repos no luck
regards ron

---

### Post by P-I H on 2011-08-12
@rbrick49

I have tried all installation methodes. The one on the cchtml.com page, jfernyhough's methode, install with Synaptic and install with Additional Drivers. Now all installation methodes are working, but with the driver I get the problem described in this thread or the problem with the black boxes when running Unity 3D.

---

### Post by andyrogers2008 on 2011-08-13
a couple of other things I did before I tried to reinstall compiz from reading other people's unity problems was:-

1) remove all of the files from /home/username/.compiz/session
2) try unity --reset

May work or may not work, these had no effect for me but may be usefull for someone else.

---

### Post by mc4man on 2011-08-13
for the heck of it - browse to /usr/share/xsessions, there will be several .desktops inside
Then run this, are they all removed? (& folder itself
```
sudo apt-get purge gnome-session
```
 
If not then delete any visible file(s) left in xsessions (or the folder itself) and then re-install
```
sudo apt-get update && \
sudo apt-get install gnome-session
```

Then do a restart

---

