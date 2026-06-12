---
title: "Partitioning"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by mormor on 2008-05-06
Hi. I installed 8.04 and did a clean install. Wiped out vista wich really worked really slow on my laptop. Now, due to missing Photoshop and some of my games, I consider making a xp-partition on my laptop. (I repartitioned so that I have the complete disc in one partition, maybe not so smart? :P )

I have about 180gb free space so that should not be a problem, I just wondered if it is a easy and fast way to single out some gbs in an own partition. And to install xp in a dual boot. Any help apriciated: )

---

### Post by shifty_powers on 2008-05-06
first, consider virtualisation such as vmware.

second, use gparted, you can find it in synaptic ;)

---

### Post by muteXe on 2008-05-06
I don't think M$ likes sharing the disk with anyone. In other words, it might be less hassle to install windows again (which will get rid of your ubuntu), then reinstall ubuntu, using the ubuntu installer to leave yourself a small windows partition.
mute

---

### Post by shifty_powers on 2008-05-06
> **muteXe said:**
> I don't think M$ likes sharing the disk with anyone. In other words, it might be less hassle to install windows again (which will get rid of your ubuntu), then reinstall ubuntu, using the ubuntu installer to leave yourself a small windows partition.
mute

it's not that hard. the only thing is that windows WILL overwrite grub with it's own master boot record, mbr.

it would just be a case of reinstalling grub. there are several howto's to do that, i'm sure...

---

### Post by mormor on 2008-05-06
will vmware/wine etc be sufficient to run photoshop at full tilt boogie? Or rather full functionality? I had a few problems with both wine and crossower in gutsy.

---

### Post by shifty_powers on 2008-05-06
> **mormor said:**
> will vmware/wine etc be sufficient to run photoshop at full tilt boogie? Or rather full functionality? I had a few problems with both wine and crossower in gutsy.

what version of photoshop?

edit: and vmware/virtualbox means you would be installing windows as a 'guest' os that will run within a window, WITHIN your linux desktop environment. Very good for stuff like photoshop but bad generally for gaming. Not sure if any free virtualisation suites will work with directx yet.... Also, as you will have two os's running side by side, will depend on your pc specs ;)

edit: for example, photoshop cs2 is rated as platinum, i.e. should work flawlessly out of the box, but cs3 is bbronze/stroke garbage... (in wine this is. look at [wine application database](http://appdb.winehq.org), very handy ;))

---

