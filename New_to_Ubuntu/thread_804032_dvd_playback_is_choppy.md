---
title: "dvd playback is choppy"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by garrettstarnes on 2008-05-22
I have an ATI Radeon Mobility x1400 graphics card and dvd playback is very choppy.  Works fine on win vista, but not on Ubuntu 8.04.  Any suggestions?

---

### Post by philinux on 2008-05-22
Need to see full specs.

Also install VLC from synaptic. Run it with that.

check system>admin>hardware drivers

---

### Post by garrettstarnes on 2008-05-22
intel core duo processor, 1 gig ram, ubuntu 8.04, ati radeon mobility x1400 graphics card.  

dvd playback pixelizes really bad.

---

### Post by Maestro23 on 2008-05-22
> **garrettstarnes said:**
> intel core duo processor, 1 gig ram, ubuntu 8.04, ati radeon mobility x1400 graphics card.  

dvd playback pixelizes really bad.

What media player are you using? Have looked at the settings for the media player?  

Have you tried disabling Desktop Effects if you have them enabled?

---

### Post by shifty_powers on 2008-05-22
heh well first, do you have the restricted drivers enabled for your graphics card?

---

### Post by garrettstarnes on 2008-05-22
first, i tried usin totem movie player, then someone previously in this thread told me to install vlc, and i'm not getting that to work.  i have enabled the graphics card, and i have not turned off desktop effects because i installed compiz fusion and it was really complicated to get going, so once i finally got it i just left it alone.

---

### Post by philinux on 2008-05-22
What does System>Admin>Hardware Drivers show

---

### Post by garrettstarnes on 2008-05-22
it shows ati graphics driver in use

---

### Post by philinux on 2008-05-22
Did you install VLC from synaptic package manager?

---

### Post by garrettstarnes on 2008-05-22
i did install vlc from synaptic, but when i try to play my movie, i dont get any video.  it just has sound, and no screen whatsoever.  it looks like a music player or something.

---

### Post by Afkpuz on 2008-05-22
Yeah, you need to turn off compiz.  I have an ati card and I can't watch dvds with compiz on.  Just rick click on desktop>change Desktop background>visual effects

once you want to turn compiz back on, just select extra from the same menu.  only problem is that there is a bug in hardy, so you'll have to turn on your fav plugins in compiz.  it doesn't change the settings, just will default back to the original plugins turned on.

---

### Post by philinux on 2008-05-22
Go to synaptic and install ubuntu-restricted-extras

click the link below for medibuntu and follow the instructions.

You're missing codecs. Just a legal thing.

Also go to System>Admin >software sources Make sure you've got the first four ticked.

---

### Post by garrettstarnes on 2008-05-22
ok, i got it to play, but it is just like totem.  it pixelizes.

---

### Post by philinux on 2008-05-22
See my previous post

---

