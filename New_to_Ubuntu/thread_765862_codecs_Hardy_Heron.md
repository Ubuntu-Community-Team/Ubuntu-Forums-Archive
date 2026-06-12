---
title: "codecs Hardy Heron"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by basilwatson on 2008-04-24
I used to use Automatix2 to install win32 codecs  whats the story with hardy heron?  are they enabled if so how ?

kind regards Stephen

---

### Post by Moop on 2008-04-24
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Joeb454 on 2008-04-24
Try running the following from a terminal (it's the easiest way) ```
sudo aptitude update
sudo aptitude install ubuntu-restricted-extras
```

Run those 1 line at a time :)

---

### Post by isaacj87 on 2008-04-24
> **basilwatson said:**
> I used to use Automatix2 to install win32 codecs  whats the story with hardy heron?  are they enabled if so how ?

kind regards Stephen

Hey,

I would enable the Medibuntu Repo if you want the w32codecs. Also if you want to enable DVD playback. Here's a link that should explain how. Let me know how it goes. :)

[Click this!]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by SOULRiDER on 2008-04-24
When I tried to play a movie in Totem, it asked me if I wanted to install them. I havnt tested all formats, but most work with just what Totem installed.

---

### Post by kansasnoob on 2008-04-24
This is just a Cut-n-Paste from earlier and i know I'm a grouch, but does anyone bother using "search" anymore to see if someone else has asked a similar question?

Many folks hate this but start by installing the Medibuntu repository:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Just follow the instructions, and remember to add the GPG key.

If you have questions just ask!

Once you're done with that open up Synaptic, then click on "settings" and then on "repositories" and then on the "Third Party Software" tab.

You should see the Medibutu free/non-free square ticked, if not - tick it NOTE: noobs don't want source code ticked!

NOW! we're ready to update our repo's. Click on "reload" in the upper left hand-hand corner ........... and wait! When it's done look at the "report" along the bottom of the screen. It may show some upgrades. If so click on "Mark all upgrades". (This is always safe to do unless you've elected to allow source code or something else crazy) And we only added a new safe repo.

So, let's fix things! You'll notice there's a search option. Click on it1

A window opens that allows you to type text. type this:

gstreamer

There's lot's of it. You do want to install nearly everything that says gstreamer in it! NOT everything on the menu! Totem gstreamer is optional (I prefer Totem over mplayer .......... in fact I'd dump mplayer for Totem), but we're focusing on codecs. Never mind that they're called bad or ugly.

Now type 'sun-java6' in the search bar. You want to mark all "sun-java6" for installation except "sun-java6-doc". (It'll only eat up space you'll never need.)

Now search for "vlc" ...... you want that too!

Now you want "flashplugin-nonfree"!

Next search for "non-free-codecs". Yep that's what you wanted all along!

I'd personally suggest that while we're here, if you ever use Adobe that you go ahead and install "acroread" which is also part of Medibubtu.

Then just clip apply .......... and wait!

Then you should be good to go, but I really love Totem & Xine compared to the default mplayer. just keep in mind that too much can confuse the process. You'll notice that many things I've just suggested bring in parts of the package that start with "lib". That's short for library.

---

