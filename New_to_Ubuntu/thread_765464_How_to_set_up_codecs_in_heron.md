---
title: "How to set up codecs in heron"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by dillonious on 2008-04-24
Hi, just switched from XP via wubi, and I am trying to get myself situated in linux. I have googled and tried some stuff there, but I have been unable to find a working way to add all my codecs into heron. I am looking for something akin to the Klite codec pack which I previously used for XP. As of right now though, I don't even have base mp3 support.

Thanks in advance for any help.

---

### Post by evadwolrab on 2008-04-24
Do a search for VLC.

It's a media player I used in XP and it can run pretty much every type of media file.

---

### Post by Ub1476 on 2008-04-24
Installing ubuntu-restricted-extras probably have every codec you need. But, if you need realplayer, quicktime, encrypted dvd playback, look [here]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by evadwolrab on 2008-04-24
> **Ub1476 said:**
> Installing ubuntu-restricted-extras probably have every codec you need. But, if you need realplayer, quicktime, encrypted dvd playback, look [here]("https://help.ubuntu.com/community/Medibuntu")

The repository linked to there ^ contains codecs from VideoLAN, the people who make VLC. :)

---

### Post by Michael.Godawski on 2008-04-24
Have a look on this guide from the ubuntu community documentation:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by dillonious on 2008-04-24
It wont install the restricted extras. It says I can't on i386.

---

### Post by kansasnoob on 2008-04-24
Many folks hate this but start by installing the Medibuntu repository:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Just follow the instructions, and remember to add the GPG key.

If you have questions just ask!

Once you're done with that open up Synaptic, then click on "settings" and then on "repositories" and then on the "Third Party Software" tab.

You should see the Medibutu free/non-free square ticked, if not - tick it NOTE: noobs don't want source code ticked!

NOW! we're ready to update our repo's. Click on "reload" in the upper left hand-hand corner ........... and wait! When it's done look at the "report" along the bottom of the screen. It may show some upgrades. If so click on "Mark all upgrades". (This is always safe to do unless you've elected to allow source code or something else crazy) And we only added a new  safe repo.

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

