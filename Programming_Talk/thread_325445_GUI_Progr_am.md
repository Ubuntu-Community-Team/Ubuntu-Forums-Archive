---
title: "GUI Progr am"
date: 2006-12-25
forum: Programming Talk
---

### Post by nhandler on 2006-12-25
I am interested in making a linux program with a GUI. I know Perl and a little shell script. I know there are perl modules that allow you to make a GUI. Are there any easy ways to do this for a shell script? I don't want a seperate program to do this. I want to code the gui myself. Is there an easy way to do this? Is there some other language that would be easier to do this in? I want to make sure this program will work on any linux distro without having to install additional stuff.

---

### Post by po0f on 2006-12-25
Cheater,

You could use [GTK with Perl](http://gtk2-perl.sourceforge.net/), though I'd rather suggest you use Python and GTK.  :)

---

### Post by nhandler on 2006-12-25
> **po0f said:**
> Cheater,

You could use [GTK with Perl](http://gtk2-perl.sourceforge.net/), though I'd rather suggest you use Python and GTK.  :)

Does GTK come installed with Perl in Ubuntu? Also, is there an easy way to package up the final perl script so the end user doesn't need to have perl and gtk installed?

As for Python, I tried it once. It was similar to Perl, but it had a few differences that I didn't like. Since I know Perl, I think it would be easier to use.

---

### Post by po0f on 2006-12-25
Cheater,

I doubt it's installed by default, but [it's in the repos](http://packages.ubuntu.com/edgy/perl/libgtk2-perl).

I don't develop with Perl, so I would have no clue as to how you could distribute your script.  If you plan on only distributing to Linux users, most (all?) distros come with Perl installed by default, they would only need to install GTK2 Perl support.

---

