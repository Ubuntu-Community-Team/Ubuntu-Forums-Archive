---
title: "Help installing PERL Mozilla::Mechanize"
date: 2009-08-03
forum: Programming Talk
---

### Post by smo0th on 2009-08-03
I've been trying to install Mozilla::Mechanize from the CPAN modules using the CPAN shell, after struggling and googling for hours I installed the dev packages for perl and mozilla, which helped in getting some more stages to work during the installation, I tried installing the dependencies first, meaning clean installs for Mozilla::DOM and Gtk2::MozEmbed, however they produce a common error, they all stop in a line that says
'/usr/bin/perl Makefile.PL INSTALLDIRS=site -- NOT OK'
so I'm out of ideas right now, I'm using ubuntu 8.04 and perl --version shows 'v5.8.8 built for x86_64-linux-gnu-thread-multi'

Any feedback, ideas, hints, tips, clues, advices and productive comments are appreciated.

---

### Post by smo0th on 2009-12-23
anyone? .-.

---

### Post by mrteeth on 2010-03-14
This is how I got it working on Jaunty 9.04:
1. Install packages xulrunner-1.9, xulrunner-1.9-dev, xulrunner-dev, and libgtk2.0-dev. Not sure if you need all the xulrunner packages, but I installed them all.
2. The paths for xulrunner are apparently broken. So you need to create file /etc/ld.so.conf/libxulcrap.conf with contents /usr/lib/xulrunner-devel-1.9.0.18/lib 
My xulrunner version was 1.9.0.18....make sure you use the right number for your version of xulrunner! 
3. Use Cpan (or maybe dh-make-perl?) to install Mozilla::DOM, then Gtk2::MozEmbed, then Mozilla::Mechanize. You can probably just install Mozilla::Mechanize, but I installed them invididually. 

Not sure if this will work for 8.04, but there's a package libgtk2-mozembed-perl in Karmic 9.10 which fixes all this stuff so you can smoothly install Mozilla::Mechanize.

---

