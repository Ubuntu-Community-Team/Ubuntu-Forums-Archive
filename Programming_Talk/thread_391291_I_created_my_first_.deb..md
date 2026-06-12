---
title: "I created my first .deb."
date: 2007-03-23
forum: Programming Talk
---

### Post by H.E. Pennypacker on 2007-03-23
Oh, it was a nightmare.  There were creepy voices in the background, and it seemed as if gases were rising from my floor.  The doors were creaking, and it seemed creatures in the dark were after me.  After a few breaks, a few prayers, and a few tears, a .deb was born.

Oh, it was gruesome.  It only took me about two hours (no kidding), and the errors I received were fairly minimal compared to all the compilation errors I used to receive as a Linux newbie.  Anyhow, the product of my labor is an imperfect Serpentine .deb.

It doesn't even check for dependencies, because it doesn't recognize any dependencies.  I intentionally took out all dependencies so that dpkg-buildpackage would not give me errors.  Well, who cares.  The .deb file successfully installed Serpentine anyway.

Next project: become a Linux developer within 24 hours.

---

### Post by Wybiral on 2007-03-23
> **H.E. Pennypacker said:**
> Next project: become a Linux developer within 24 hours.

24 hours? :) Best of luck!

---

### Post by j_g on 2007-03-23
> Oh, it was a nightmare.

You're telling me.

I find it a lot easier to make an RPM file, and then convert it to DEB using a utility called alien. I posted another message in another thread detailing more about how to do that.

---

### Post by josephus on 2007-03-23
How are you creating the deb files?  I've been using checkinstall and found it to be relatively pain free.

---

### Post by H.E. Pennypacker on 2007-03-23
Wybiral, watch me.  I am getting there (yeah right!).

J_G, that looks like too much of an round-about way.  

Josephus, using checkinstall apparently does not do everything you'd want.  In other words, I believe it is not a complete process, but I could be wrong.  I used the following guide:

[http://doc.gwos.org/index.php/Deb_Guide](http://doc.gwos.org/index.php/Deb_Guide)

I'll have to see is using checkinstall is just as good.

---

### Post by AlexenderReez on 2007-03-23
nice guide...

i want to rty to build....:guitar:

---

### Post by AlexenderReez on 2007-03-23
nice guide...

i want to try to build....:guitar:

---

### Post by j_g on 2007-03-23
> looks like too much of an round-about way.

It is indeed a roundabout way. But I found the deb packaging system to be so convoluted, that it was much, much easier to deal with RPM's single "spec" file, and let alien deal with the messy details of debian packaging.

---

### Post by blanky on 2007-03-23
Haha, I created my first deb I think last month, it was a [DPMaster Deb]("http://instagib.jorgepena.be/downloads/linux/dpmaster_1.6-1_i386.deb") which my friend uses to run a master server for the game I'm writing. I actually got it working fairly quickly after reading [this]("http://www.debian.org/doc/maint-guide/") (*Okay okay, I skipped a couple things and skimmed through the rest hehe*). I eventually got a working deb (*One of my friends tried it*), but when I went to send it to my friend running a server (*Dapper 6.06 LTS*), it wouldn't work because of a high libc dependency or something. So he (*A Gentoo developer*) ssh'ed into my computer and debootstrapped a dapper install into my home directory and re-did it himself :') Now we have a fine working dpmaster package.

---

