---
title: "AWK, GAWK, MAWK and POSIX"
date: 2007-11-22
forum: Programming Talk
---

### Post by seetho on 2007-11-22
I'm using AWK again in my new project to process some data for insertion into an SQL database and I ran into some minor problems.  I noticed that MAWK (the default AWK installation for Ubuntu) does not support POSIX character classes (such as [:alpha:] to match any alphabetic character) and interval expressions (such as [X]{n} to match exactly n number of X characters).

I had to install GAWK before I could use these features.

The man pages says that MAWK conforms to POSIX 1003.2 (draft 11.3).  Doesn't this POSIX draft include these features?

The man pages for GAWK says it too conforms to POSIX 1003.2, so I'm a little confused about this POSIX conformity thing.

Maybe someone here with good knowledge of POSIX can enlighten me.

I'm basically also wondering why GNU/Linux and other free and open source project base their design on POSIX which is essentially done by IEEE that charges $$$ for access to information?

st

---

### Post by thyrcson on 2008-01-11
Hi seetho,

sorry to revive a rather old thread, but I asked myself the same question yesterday. And I think I found an answer I just wanted to share...

AFAIK the interval expressions are not part of the regex - POSIX 1003.2 regular expressions standard. They are part of the 'extended regular expressions'-set used by egrep and some others.

No wonder interval expressions were not traditionally available in awk. They were added as part of the POSIX standard to make awk and egrep consistent with each other.

But to get thing working you'll have to specify a command line option to enable this 'feature' - even in gawk ```
--W posix
``` or ```
--posix
``` should do the trick. Sadly mawk (a lightweight awk) doesn't support extended regular expressions at all...

... something I had to find out when I tried (and finally succeeded) to fix some broken 1GB+ MBOX files with an Kubuntu Live USB stick.

Happy new year.

---

### Post by seetho on 2008-01-11
Thanks thyrcson!  I had the feeling that nobody was interested in using AWK nowadays so didn't really expect anyone to answer to this question anymore.

I'm still irritated that a lot of AWK codes that works on other UNIX systems will fail on Ubuntu because the default AWK is MAWK instead of GAWK.  In fact should not POSIX  interval should be accepted by default instead of having to specify the --posix switch?

Sometimes I feel that Ubuntu development (and Linux in general) has gone in the direction of eye-candy too much and this has left much of the truly important part unmaintained.  It's like a rusty car body painted over with coat upon coats of expensive shiny new paint - beautiful to look at but if you poke too hard in the wrong places your finger may just go right through.

Anyways (sigh...) I'm hoping Hardy Heron will be an improvement.

Have a happy 2008 too, and thanks again.

st

---

### Post by riks on 2008-07-25
What frustrates me is that the mawk man page states that it "uses  extended  regular expressions as with egrep(1)." I would expect that to mean that [:alnum:] would work.

I ended up installing gawk, and I wonder why this isn't the default implementation of awk.

---

### Post by mbaysek on 2008-11-10
I recently had someone tell me that awk was "broken" on one of our compute nodes.  It turns out that it was because mawk was the default.

If you do a test against the various versions of awk, mawk is much faster for most of the basic operations than the other versions, especially gawk.  When you are processing very large files, this makes a massive difference.

It is for this reason that I am appreciative of Ubuntu's choice to make mawk the default.  gawk is there if you need it, just run it by name.  For anything else, just using awk (mawk) is a much faster experience.

If you really want to permanently make gawk the system-wide default, you can run 
```
sudo update-alternatives -s awk /usr/bin/gawk
```

---

### Post by seetho on 2008-11-12
> **mbaysek said:**
> 
If you do a test against the various versions of awk, mawk is much faster for most of the basic operations than the other versions, especially gawk.  When you are processing very large files, this makes a massive difference.


Thanks.  Now I understand the reason behind it.  In my opinion Ubuntu is mostly used by desktop users and "not so knowledgeable" users like me would expect awk to work as "advertised".  IMHO, would make more sense to make gawk the default awk and users that need to process massive amounts of data can twiddle it to use mawk instead.

---

### Post by troyready on 2010-03-13
Sorry to resurrect an old thread, but this came up highly on a Google search for a problem I was having compiling Linux from Scratch. Just wanted to mention that it fixed my problems building glibc on a Karmic system, but the command listed above needed to be modified slightly:

```
sudo update-alternatives --set awk /usr/bin/gawk
```

---

### Post by bugmum on 2012-06-15
> **mbaysek said:**
> I recently had someone tell me that awk was "broken" on one of our compute nodes.  It turns out that it was because mawk was the default.

If you do a test against the various versions of awk, mawk is much faster for most of the basic operations than the other versions, especially gawk.  When you are processing very large files, this makes a massive difference.

It is for this reason that I am appreciative of Ubuntu's choice to make mawk the default.  gawk is there if you need it, just run it by name.  For anything else, just using awk (mawk) is a much faster experience.

If you really want to permanently make gawk the system-wide default, you can run 
```
sudo update-alternatives -s awk /usr/bin/gawk
```

I know its an old topic, but i got relinked to this side by google :).

mawk is quite nice but it isn't suited for big data, it can't handle more than 32000 columns. I dont know if the new version 1.3.4 (by Thomas E. Dickey [http://invisible-island.net/mawk/mawk.html#download](http://invisible-island.net/mawk/mawk.html#download)) changed this problem.

Gawk can handle big files, but is way slower than mawk on files less than 32k columns.
So for "everyday" use i would prefer gawk, because it can handle all kind of datasizes.

---

