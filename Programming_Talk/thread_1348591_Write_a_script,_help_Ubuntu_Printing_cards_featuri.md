---
title: "Write a script, help Ubuntu: Printing cards featuring Ubuntu application/package data"
date: 2009-12-07
forum: Programming Talk
---

### Post by mpt on 2009-12-07
Hi folks

For the Ubuntu Software Center 2.0, we’re introducing [subcategories for installable software]("https://wiki.ubuntu.com/SoftwareCenter#Genre"). However, we need a little programming help in working out what those subcategories should be.

We want to do a [card sorting]("http://en.wikipedia.org/wiki/Card_sorting") exercise to categorize the packages. Basically this means recruiting user test participants, showing them 50 or so cards each with information about one package, and getting the participants to arrange those cards into categories.

But, how to print those cards? Each card needs to show some of the same information as the Ubuntu Software Center shows:
[LIST]
[*]the application’s name from [FONT="Courier New"]app-install-data[/FONT], or the package’s synopsis
[*]the application’s summary from [FONT="Courier New"]app-install-data[/FONT], or the package’s name
[*]the application’s icon from [FONT="Courier New"]app-install-data[/FONT], or a generic package icon
[*]the package’s description.
[/LIST]

As a starter, here’s a script that chooses 50 packages at random and prints their name, summary, and description:

```
#! /usr/bin/python
import random
import apt
cache = apt.Cache()
for package in random.sample(cache, 50):
    print "Package: %s" % package.name
    print "Summary: %s" % package.candidate.summary
    print "Description: %s" % package.candidate.description

```

The next step here is to parse the [FONT="Courier New"]/usr/share/app-install/[/FONT] files to return the icons and human-readable names if they’re present, falling back to the basic package data if they’re not.

Once we have that, we need to turn that data into a printable card (ideally with multiple cards per page). What’s the best way to do this? Maybe a script that produces an SVG, with the icon and text embedded. Maybe a “Mail Merge” in OpenOffice.org Writer. Maybe something else. Anyone have any ideas? :)

Thanks in advance to anyone who can help out.

---

### Post by blackgr on 2009-12-07
why not use enscript to convert text file to pdf and then from there convert it to image with imagemagick?

edit:
lets say we have
```

Package: fso-sounds-none
Summary: void ringtones for the freesmartphone.org frameworkd
Description: This packages configures the freesmartphone.org frameworkd for no ringtones.

This package is part of the freesmartphone.org software stack and it is targeted for smartphones.

```
in a file called testfile

```
enscript -p `cat testfile | grep "Package:" | awk '{print $2}'`.ps testfile
```

will create a file called: fso-sounds-none.ps
then
```
ps2pdf fso-sounds-none.ps
```
and
```
pdf2svg fso-sounds-none.pdf fso-sounds-none.svg 1
```

and there you have a nice svg file with your text inside

---

