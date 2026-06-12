---
title: "several gripes with the desktop"
date: 2011-09-22
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by KhaaL on 2011-09-22
Since last release, i moved to linux mint but decided to jump back to ubuntu to see what has been in the works since.

My overall experience hasn't been the most pleasing, and I hope I can the following: 

I have my laptop connected to[LIST]
[*]my TV through a reciever with a HDMI cable, and I have the TV off so I can just listen to music. However the TV is counted as a monitor and dialog boxes appear there when my current monitor is full. Configuring window placement in compis config manager dosent help. Is there a workaround?

[*]Is it possible to remove the unity bar at the left? I much prefer docky. 

[*]Is it possible to have a "clean" gnome 3 install?

[*]Holding the mouse cursor and scrolling between tabs within config menus seems to work only in certain places, is this a problem with unity or gnome 3?
[/LIST]

---

### Post by dino99 on 2011-09-22
everything is possible, none of compiz/unity is required if you install gnome-shell and/or gnome-session-fallback (indeed remove ubuntu-desktop first)

---

### Post by KhaaL on 2011-09-22
I heard about a lot of people trying that with a following mess. Is there specific instructions i need to follow in order to avoid that?

---

### Post by kaldor on 2011-09-22
> **KhaaL said:**
> I heard about a lot of people trying that with a following mess. Is there specific instructions i need to follow in order to avoid that?

The mess was due to installing GNOME 3 on Natty. Ubuntu 11.04 used GNOME 2, so installing GNOME 3 stuff was a huge task. Loads of libraries needed to be updated, changed, etc, so there was huge potential for stuff to go wrong. 

In Oneiric, Unity is ported to GNOME 3 now and there are no issues whatsoever when using or installing GNOME Shell. It was extremely painless for me; all I had to do was *sudo apt-get install gnome-shell*, relogin, and all was well. No problems in the least.

Edit:

You can use Docky. I recommend using the GNOME 3 fallback session for this.

---

### Post by ronacc on 2011-09-22
or you can install one of the variants Kubuntu , Lubuntu , Xubuntu . Many of us are finding one of them more to our liking than the current incarnation of Ubuntu itself .

---

### Post by KhaaL on 2011-09-22
> **kaldor said:**
> The mess was due to installing GNOME 3 on Natty. Ubuntu 11.04 used GNOME 2, so installing GNOME 3 stuff was a huge task. Loads of libraries needed to be updated, changed, etc, so there was huge potential for stuff to go wrong. 

In Oneiric, Unity is ported to GNOME 3 now and there are no issues whatsoever when using or installing GNOME Shell. It was extremely painless for me; all I had to do was *sudo apt-get install gnome-shell*, relogin, and all was well. No problems in the least.

Edit:

You can use Docky. I recommend using the GNOME 3 fallback session for this.

Thanks, gnome 3 works so nicely i don't have the need for docky. Quite slick and responsive! But being unable to scroll between tabs with mousewheel is *very* annoying. I installed KDE4 too and it was nice, but lacked in responsiveness. 

> **ronacc said:**
> or you can install one of the variants Kubuntu , Lubuntu , Xubuntu . Many of us are finding one of them more to our liking than the current incarnation of Ubuntu itself .

I'm aware of them all (and of other distros aswell), but instead of having to sit through another reinstall I was rather intrested to fix my current situation.

---

### Post by cariboo on 2011-09-22
> **KhaaL said:**
> Since last release, i moved to linux mint but decided to jump back to ubuntu to see what has been in the works since.

My overall experience hasn't been the most pleasing, and I hope I can the following: 

I have my laptop connected to[LIST]
[*]my TV through a reciever with a HDMI cable, and I have the TV off so I can just listen to music. However the TV is counted as a monitor and dialog boxes appear there when my current monitor is full. Configuring window placement in compis config manager dosent help. Is there a workaround?

[*]Is it possible to remove the unity bar at the left? I much prefer docky. 

[*]Is it possible to have a "clean" gnome 3 install?

[*]Holding the mouse cursor and scrolling between tabs within config menus seems to work only in certain places, is this a problem with unity or gnome 3?
[/LIST]

For your last point, Unity is built on top of Gnome 3 (GTK-3), I assume you mean gnome-shell?

I'm using Unity at the moment, and can scroll between tabs on all the apps I've tried so far.

---

### Post by KhaaL on 2011-09-23
> **cariboo907 said:**
> For your last point, Unity is built on top of Gnome 3 (GTK-3), I assume you mean gnome-shell?

I'm using Unity at the moment, and can scroll between tabs on all the apps I've tried so far.

I had that issue in unity and also in gnome 3. Its inconsistent, because in some applications (such as nautilius) tab scrolling works fine, while in other applications ( if memory serves, some configuration from the upper-right bar in unity) didn't have that. Oddly, nautilus in gnome 3 dosent allow scrolling between tabs... Bug or feature?

---

### Post by cariboo on 2011-09-23
> **KhaaL said:**
> I had that issue in unity and also in gnome 3. Its inconsistent, because in some applications (such as nautilius) tab scrolling works fine, while in other applications ( if memory serves, some configuration from the upper-right bar in unity) didn't have that. Oddly, nautilus in gnome 3 dosent allow scrolling between tabs... Bug or feature?

With the way the gnome devs are removing configuration options in gnome 3, I'd probably say it's a feature.

---

### Post by KhaaL on 2011-09-23
> **cariboo907 said:**
> With the way the gnome devs are removing configuration options in gnome 3, I'd probably say it's a feature.

I'm afraid so. I'm all for less is more philosophy, but when it comes to cut away my choices... I might aswell run windows.

---

### Post by cariboo on 2011-09-23
It is only gnome 3 based distributions that are losing configuration options, there are still plenty of other distributions that don't use gnome at all, have a look at Xubuntu or Lubuntu, both are official members of the Ubuntu family. There are links to the isos in my beta 2 announcement thread.

---

### Post by KhaaL on 2011-09-23
> **cariboo907 said:**
> It is only gnome 3 based distributions that are losing configuration options, there are still plenty of other distributions that don't use gnome at all, have a look at Xubuntu or Lubuntu, both are official members of the Ubuntu family. There are links to the isos in my beta 2 announcement thread.

I'm aware of that. And I know how far KDE4 have gotten. But I am very fond of the gnome shell way to do things, and it saddens me that the end-users choices to customize their desktops are being cut with the new release of gnome 3. But as I understand this has been a known issue with gnome developers being resistant to include new features.

---

