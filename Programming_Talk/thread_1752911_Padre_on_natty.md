---
title: "Padre on natty?"
date: 2011-05-08
forum: Programming Talk
---

### Post by 5149.5 on 2011-05-08
Does anyone have Padre running on natty yet?  Does the debugger work for you?

---

### Post by 5149.5 on 2011-05-09
Padre is broken for Natty. If you try to use it, be prepared for errors.

---

### Post by cgroza on 2011-05-09
wxPerl does not work in Natty. It complains about an undefined reference somewhere.
As Padre is based on WxPerl, Padre does not work either.

---

### Post by cgroza on 2011-05-15
Anyone found a fix yet? I really like Perl, and Padre is like their official IDE.
Anyone knows if someone works on a patch?

---

### Post by shawnhcorey on 2011-05-15
I got version 0.85 working from SVN but this is the development version.  That means subject to breakage without notice.

```
mkdir ~/Software

cd ~/Software

svn co http://svn.perlide.org/padre/trunk

cpanm Module::Install Locale::Msgfmt 

cd ~/Software/Padre/trunk/Padre

cpanm --installdeps .

perl Makefile.PL

make

make test

```

---

### Post by cgroza on 2011-05-16
> **shawnhcorey said:**
> I got version 0.85 working from SVN but this is the development version.  That means subject to breakage without notice.

```
mkdir ~/Software

cd ~/Software

svn co http://svn.perlide.org/padre/trunk

cpanm Module::Install Locale::Msgfmt 

cd ~/Software/Padre/trunk/Padre

cpanm --installdeps .

perl Makefile.PL

make

make test

```
Well, it does not work now, so it can't get worse. I will try it.
Thank you.

---

### Post by cgroza on 2011-05-16
Tried it, same error again.

---

### Post by shawnhcorey on 2011-05-18
OK, if you compile it from SVN, the new padre is:
```
~/Software/trunk/Padre/dev
```

The reason the old padre is not working is because of a difference in Wx.  You have to rebuild it.

Special note:  if you are running perlbrew, turn it off:
```
$ perlbrew off
```
If the above says it can't find perlbrew, you're not running it.

**To rebuild Wx:**

First, you need some tools:
```
$ sudo apt-get install build-essential
```

Now, upgrade Wx:
```
$ sudo cpan
[sudo] password for user:

cpan shell -- CPAN exploration and modules installation (v1.9402)
Enter 'h' for help.

cpan[1]> upgrade Wx
...

```

This could take awhile.  It may have to upgrade some dependencies too.

When done, exit cpan:
```
cpan[2]> q
Lockfile removed.
$ 
```

The old padre should now work.  :)

**PS:**  This could break other Wx programs.

---

### Post by cgroza on 2011-05-18
OK, I will try it later.

---

### Post by cgroza on 2011-05-18
I still get this:
```
BEGIN failed--compilation aborted at /usr/local/share/perl/5.10.1/Padre/Constant.pm line 11.
Compilation failed in require at /usr/local/bin/padre line 123.
```

---

### Post by shawnhcorey on 2011-05-18
Gee, that doesn't explain much, does it?  Perhaps you should ask someone with more knowledge than I.  Have you tried the [Padre mailing list]("http://lists.perl.org/list/padre-dev.html")?  Or perhaps, [perlmonks]("http://perlmonks.org/")?

---

### Post by cgroza on 2011-05-18
Hmm, I do not know, maybe I will send an email or two when I will have more time.
Thanks for your support anyway.

---

