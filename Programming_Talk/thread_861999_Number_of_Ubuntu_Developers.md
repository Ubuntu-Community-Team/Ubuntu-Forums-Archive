---
title: "Number of Ubuntu Developers"
date: 2008-07-17
forum: Programming Talk
---

### Post by Valter Fukuoka on 2008-07-17
I've ask this question on another forum with no answer, 
so I decide to ask here, even not being sure it belongs here.

I like to know the approximate number of Ubuntu Developers,
including all categories describe in the official (site) page.

Just like to know one approximate idea.

Thanks all.

---

### Post by bobbocanfly on 2008-07-17
There are 85 active MOTUS (masters of the universe) on Launchpad who handle the whole of the universe component and 55 active core-dev's who handle what comes on the CD and other major stuff.

Bear in mind that there are lots of contributors who are not official MOTU's or Core-Devs who do lots of work for Ubuntu

---

### Post by tinny on 2008-07-17
The number would be very large (I have no idea really).

Remember all the Debian Developers!!! With out them we wouldnt have Ubuntu.

---

### Post by Tomosaur on 2008-07-17
Depends what you mean by 'Ubuntu Developers' really.

Much of the backbone of Ubuntu is developed as part of the wider open-source world, then tweaked and modified to fit into Ubuntu nicely.

Canonical employs a number of people to work on Ubuntu itself, but anyone is free to contribute if they can (people like you or me, who have no affiliation with Canonical).

---

### Post by Valter Fukuoka on 2008-07-17
Thank guys.

It's interesting.

I just want to collect some numbers, like :

1010 Debian Developers
2400 Linux Kernel Contributors

I don't know if make any sense at all ...
Just taking notes to have one general idea ...

---

### Post by bobbocanfly on 2008-07-17
To give you a quick idea then 190 people have contributed fixes to Intrepid so far and 435 people had uploads in Hardy.

---

### Post by mssever on 2008-07-17
> **bobbocanfly said:**
> To give you a quick idea then 190 people have contributed fixes to Intrepid so far and 435 people had uploads in Hardy.
The OP should bear in mind that these numbers are unrelated to upstream, including Debian, and that most of the significant changes take place upstream.

---

### Post by bobbocanfly on 2008-07-17
> **mssever said:**
> The OP should bear in mind that these numbers are unrelated to upstream, including Debian, and that most of the significant changes take place upstream.

Yeah true, for example here is a changelog entry for one of my uploads:

```
dx (1:4.4.0-3ubuntu1) hardy; urgency=low

  * debian/control:
    - Fix spelling mistake in description (LP: #195068)
    - Update Maintainer field to match the DebianMaintainerField specification
    - Bump Debian standards version to 3.7.3
    - Add Homepage field
    - Remove obsolete (build-)dependencies on xlibs-dev
    - Lose outdated substitution variable Source-Version in
      favour of current binary:Version.
  * debian/rules: Disable strict aliasing.
  * debian/menu: Move to new section Applications/Science/Data Analysis.
  * debian/dx-doc.doc-base: Remove extra whitespace in empty line to
    placate lintian.

 -- David Futcher <bobbocanfly@gmail.com>  Sun, 24 Feb 2008 14:46:01 +0000
```

Might not make sense to many people but that is just changing things like where the app goes in the aplication menus and fixing descriptions. This is what 90% of Ubuntu development is. 

For things like crashes we do fix the source code, but this is fairly rare and we send it back upstream so that in a few versions time, we can drop our patch as upstream will have included it.

</offtopic-ish>

---

