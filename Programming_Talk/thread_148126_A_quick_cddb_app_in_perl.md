---
title: "A quick cddb app in perl"
date: 2006-03-21
forum: Programming Talk
---

### Post by Haegin on 2006-03-21
Hi, I am trying to learn perl and in an attempt to "get stuck in" I want to try and make a cddb looker upper for a load of mp3 files I have. I have tried easytag and it just crashed and nothing else seems able to do what I need. I just want something to look at all the mp3s in a certain directory recursively and use cddb to get some info on them. It doesn't have to be 100% right obviously but it would really speed everything up. Is this possible in perl and where do you suggest I look to get started?

---

### Post by psychicdragon on 2006-03-21
CDDB lookups require a DISCID, without the actual disc in the drive I don't think you'll be able to generate the DISCID. Unless you happen to have all the tracks from the CD, but I'm not certain.

There's a perl module in apt called libcddb-get-perl, that you could take a look at.

You should also take a look at the documentation on the freedb.org: [Here]("http://freedb.org/modules.php?name=Sections&sop=listarticles&secid=2")

---

