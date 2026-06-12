---
title: "Time to tackle my scanner!"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by kansasnoob on 2008-05-06
I've been using Ubuntu now for several weeks and I'm quite pleased. I do however have an old HP Scanjet 2300c scanner on one of my computers that I'd like to get working.

Now, it does try to work (in fact the scans look great) but the scanner head "bumps" and "stalls" unless you pull the power plug when the head "bumps". IMO the problem is the SANE library is auto-selecting the wrong backend.

Now, sane-genesys.5 appears to fit the bill! 
[http://www.sane-project.org/man/sane-genesys.5.html](http://www.sane-project.org/man/sane-genesys.5.html)

But, I can not build doodly squat from source! Believe me, I'll break my Ubuntu! Then I'll use GParted to reformat my Ubuntu partition (I'm dual booted with Win XP) and then I'll have to start all over again.

So, I'm thinking that the proper backend is in "libsane" and I'd like to look at "libsane" to see if there's something I could edit. Basically I need "sane-genesys.5" or the parts and pieces without the "auto-select".

This should be doable! But if the answer is building from source remember I'm a real noob! Unless it's "cut-n-paste" - "point-n-click" ...... I'll hose it!

No rush, this is not stopping me from doing anything. It's a want ... not a need! But I love the learning process, even when I break things and have to start over it's all good!

I think I suffer from Ubuntu ADHD!

---

### Post by kansasnoob on 2008-05-10
Thought I'd give this a bump in case some new eyes might have an idea.

I'd at least like to take a look at the libsane backends file just to get an idea what I'm up against.

Maybe as simple as:  sudo gedit /etc/sane.d/dll.conf
or: gksu gedit /etc/sane.d/dll.conf
to take a peak, but I'd like some advice prior to fiddling.

---

