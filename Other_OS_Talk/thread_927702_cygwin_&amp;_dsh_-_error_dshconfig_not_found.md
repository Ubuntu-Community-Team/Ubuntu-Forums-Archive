---
title: "cygwin &amp; dsh - error dshconfig not found"
date: 2008-09-23
forum: Other OS Talk
---

### Post by andguent on 2008-09-23
I've searched online for a good hour or so and not finding my error. Google is unable to find anyone that has the same error message, so I'm turning to my favorite forums to see if anyone has an idea.

I'm running cygwin on XP (only because I have to) and am trying to get dsh compiled. libdshconfig-0.20.13 compiled fine via the standard ./configure, make, make install. I attempt to repeat the same for dsh-0.25.9 and end up with this

```

checking for getline... no
checking for dup2... yes
checking for setlocale... yes
checking for strcasecmp... yes
checking for strchr... yes
checking for setnetgrent... no
checking for getnetgrent... no
checking for endnetgrent... no
checking for open_dshconfig in -ldshconfig... no
configure: error: dshconfig not found!!

```

libdshconfig installed itself to /usr/local/lib, and I did manually add that to my path (at the beginning too). I also added /usr/bin to the beginning of my path as well for good measure.

I've stumbled through this for a day or two and just not getting anywhere. Any suggestions on how to get dsh to compile would be greatly appreciated. Thanks.

---

### Post by stuv829 on 2008-09-25
Q: What is the difference between a Methodist and a Baptist? A: A Methodist will at lest say "Hi" to you in a liquor store.[wow gold](http://www.mmoinn.com)[world of warcraft power leveling](http://www.mmoinn.com/mmoinn_pl/)i like here [http://www.mmoinn.com/mmoinn_pl/](http://www.mmoinn.com/mmoinn_pl/)

---

### Post by andguent on 2008-10-01
Anyone?

---

