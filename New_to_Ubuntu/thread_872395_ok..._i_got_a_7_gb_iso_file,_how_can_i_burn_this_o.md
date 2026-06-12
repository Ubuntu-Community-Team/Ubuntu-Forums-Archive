---
title: "ok... i got a 7 gb iso file, how can i burn this on dvds?"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by SchindlerShadow on 2008-07-27
ok i have a 7 gb iso file and i have about 30 blank dvd-r's. how can i fit this? oh and it has to be bootable b/c its a backup of the mac os x install (mine was starting to get scrashed up). anything i can do to burn it? oh and i know how to burn dvds w/ ubuntu. thx 4 any1 who helps! :KS (and i have a dual layer dvd rw drive)

---

### Post by tamoneya on 2008-07-27
that needs to be burned to a dual layer DVD.  Those are 8+ GB.

---

### Post by SchindlerShadow on 2008-07-27
> **tamoneya said:**
> that needs to be burned to a dual layer DVD.  Those are 8+ GB.
relly? do they sell that in like walmart??

---

### Post by ramjet_1953 on 2008-07-27
You have two choices.

1. If you have a dual-layer DVD burner, buy dual-layer DVDr's.

2. Install either k9copy or dvd95. Either of these programs will allow you to compress the iso down to fit on a 4.7Gb DVD-r.

You can then use Brassero to burn the iso.

I prefer k9copy, but if you are running GNOME as your desktop, when installing this application a few extra files will also be installed, which allow this KDE application to run under GNOME.

I have had good success with k9copy and the resulting iso produces a DVD virtually indistinguishable from the original.

Regards,
Roger :cool:

---

### Post by tamoneya on 2008-07-27
not sure about walmart specifically but ive seen them at places like best buy.  They arent exactly exotic.

---

### Post by SchindlerShadow on 2008-07-27
> **ramjet_1953 said:**
> You have two choices.

1. If you have a dual-layer DVD burner, buy dual-layer DVDr's.

2. Install either k9copy or dvd95. Either of these programs will allow you to compress the iso down to fit on a 4.7Gb DVD-r.

You can then use Brassero to burn the iso.

I prefer k9copy, but if you are running GNOME as your desktop, when installing this application a few extra files will also be installed, which allow this KDE application to run under GNOME.

I have had good success with k9copy and the resulting iso produces a DVD virtually indistinguishable from the original.

Regards,
Roger :cool:
ok i dl and installed k9copy, now how do i use it?? and do i need the origanal disk? b/c i cant find it XD but i have the iso

---

### Post by ramjet_1953 on 2008-07-27
If you don't have the original DVD, just use Synaptic to install [COLOR="Blue"]gmountiso[/COLOR].

This will then allow you to mount the iso and if you choose your DVD drive as the mount point, you can use either dvd95, or k9copy to compress it.

As far as using k9copy, it is pretty self explanatory.

However, you can always type this into a terminal, after k9copy is installed.

```
k9copy --help
```

Regards,
Roger :cool:

---

### Post by SchindlerShadow on 2008-07-27
> **ramjet_1953 said:**
> If you don't have the original DVD, just use Synaptic to install [COLOR="Blue"]gmountiso[/COLOR].

This will then allow you to mount the iso and if you choose your DVD drive as the mount point, you can use either dvd95, or k9copy to compress it.

As far as using k9copy, it is pretty self explanatory.

However, you can always type this into a terminal, after k9copy is installed.

```
k9copy --help
```

Regards,
Roger :cool:
what mount point should i mount it 2?

ok i mounted it to /media/cdrom0 now what do i do to compress? oh and thx 4 ur help!

whenever i click to mount /media/cdrom0 in k9copy, it closes??? and look at this

 k9copy --help
Usage: k9copy [Qt-options] [KDE-options] [options] 

A DVD Backup tool for KDE

this dosent relly help.... and btw this isent a movie, its and install 4 mac os x.

---

### Post by ramjet_1953 on 2008-07-28
I'm sorry.

It didn't sink in that this was a data iso, not a video DVD.

I'm not sure that it is a good idea to compress this image.

Again, two options.

1. Buy a dual layer DVD-R. This is the simplest option.

2. Search for a package that allows you to split an image across multiple discs.

Regards,
Roger :cool:

---

### Post by DGortze380 on 2008-07-28
you can try to use th split command.
```

man split

```

probably won't work as a live disk though. I think if you're trying to make an extra copy of your os x install disks you really need dual-layer DVDs (assuming it's leopard).

---

### Post by SchindlerShadow on 2008-07-28
> **ramjet_1953 said:**
> I'm sorry.

It didn't sink in that this was a data iso, not a video DVD.

I'm not sure that it is a good idea to compress this image.

Again, two options.

1. Buy a dual layer DVD-R. This is the simplest option.

2. Search for a package that allows you to split an image across multiple discs.

Regards,
Roger :cool:
any1 know of a pagage like in choise #2?

---

### Post by SchindlerShadow on 2008-07-28
> **DGortze380 said:**
> you can try to use th split command.
```

man split

```

probably won't work as a live disk though. I think if you're trying to make an extra copy of your os x install disks you really need dual-layer DVDs (assuming it's leopard).
yea it is leperd XD oh and dose any1 know if it will run on an amd pc? iv read articals saying that it can!

---

### Post by DGortze380 on 2008-07-28
> **SchindlerShadow said:**
> yea it is leperd XD oh and dose any1 know if it will run on an amd pc? iv read articals saying that it can!

Thats not a question you're going to get an answer to here as it violates Apple's EULA

---

### Post by tamoneya on 2008-07-28
using split will not work well at all.  It will totally mess up the ISO file format.  You might be able to get brasero to make two ISOs out of one but even if you did leopard would probably be looking for files that were on the other disk assuming that it didnt attempt to calculate the checksum of the disc to check its integrity / validity

---

### Post by SchindlerShadow on 2008-07-28
> **tamoneya said:**
> using split will not work well at all.  It will totally mess up the ISO file format.  You might be able to get brasero to make two ISOs out of one but even if you did leopard would probably be looking for files that were on the other disk assuming that it didnt attempt to calculate the checksum of the disc to check its integrity / validity
wow that ment nothing 2 me... lol thanks all 4 ur help! im now (at 1:00 am) going 2 walmart to hopefully find and buy a dvd DL, hope i find it! oh and in case i dount, plz keep posting other ways of getting it 2 work! thx all!!!

---

### Post by tamoneya on 2008-07-28
make sure your drive supports it.

---

### Post by SchindlerShadow on 2008-07-28
> **tamoneya said:**
> make sure your drive supports it.
awwwwww i dident find any =_( ohh well 2morrow ill go and look @ best buy, even tho my dad hates it (b/c they dount accept tax exemption XD). ill try 2 get my mom 2 take me thier 2morrow, till then good night ppl!

omfg! its $50 for a 25 pack! wtf? it costs $8 for a 5 pack on ebay! best buy dose suck! i just need 1!!

---

### Post by tamoneya on 2008-07-28
ive definitely agree they suck.  That was never in doubt but if you need something and they have it.  I order 99% of my stuff on newegg anyways.  Best buy is emergencies only for me.

---

### Post by Dr Small on 2008-07-28
Get a DoubleLayerd DVD that holds 8.5GBs.

---

### Post by SchindlerShadow on 2008-07-28
> **tamoneya said:**
> ive definitely agree they suck.  That was never in doubt but if you need something and they have it.  I order 99% of my stuff on newegg anyways.  Best buy is emergencies only for me.
yea but ima try 2 get it off ebay.

---

