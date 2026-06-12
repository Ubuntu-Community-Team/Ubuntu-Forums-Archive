---
title: "semi-interactive clutterised main menu mockup 8)"
date: 2008-11-03
forum: Programming Talk
---

### Post by | MM | on 2008-11-03
Hi,

So whilst ignoring impending exams I felt compelled to play around with the clutter toolkit.

As a wee project i decided to fool around with some ideas i had for the main menu.  What i came up with represents a about three evenings of learning, and playing with the Gimp and Photoshop.

Here's a screenshot of my clutterised main menu mockup:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=90917&stc=1&d=1225700512[/IMG]

It's inspired by some [Gnome 3 usability ideas that i saw via p.g.o]("http://live.gnome.org/Boston2008/GUIHackfest/WindowManagementAndMore"), opera and adobe acrobat.

You too can play with the semi-interactive clutterised main menu mockup; i've [attached]("http://ubuntuforums.org/attachment.php?attachmentid=90919&d=1225700818") all my python code and images, et cetera.

But first you'll need to install all the clutter 0.8 libraries, if you are using Ibex its simply a matter of:
```
sudo apt-get install libclutter-0.8-0
```

You'll also need to install pyclutter which is not in main or universe, but .debs are hosted here: [[AMD64 pyclutter]("https://edge.launchpad.net/%7Ejames-w/+archive/+files/python-clutter_0.8.0-0ubuntu1~ppa1_amd64.deb")] [[i386 pyclutter]("https://edge.launchpad.net/%7Ejames-w/+archive/+files/python-clutter_0.8.0-0ubuntu1~ppa1_i386.deb")] ([https://edge.launchpad.net/~james-w/+archive](https://edge.launchpad.net/~james-w/+archive))

Once all those have been installed you can play with my mockup.  To run:
```
python /path/to/mocker.py
```

Hopefully you wont see too many bugs.  I am guessing if you do see bugs it will be because you are missing icons or something.

I am eager to hear what people think.

---

### Post by Flimm on 2009-09-24
Interesting. I'm not sure why you'd need clutter to render everything, though.

---

