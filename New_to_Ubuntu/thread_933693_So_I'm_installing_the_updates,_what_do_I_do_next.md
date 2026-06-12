---
title: "So I'm installing the updates, what do I do next?"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by Obero on 2008-09-29
Just installed Ubuntu, and am now installing the updates. What do I do next, I'm an ABSOLUTE beginner!

---

### Post by oilchangeguy on 2008-09-29
> **Obero said:**
> Just installed Ubuntu, and am now installing the updates. What do I do next, I'm an ABSOLUTE beginner!

what do you mean, what do you do next? after you install the updates there is nothing else to do, until more updates are available. you'll see the star burst icon when there's more.

---

### Post by gn2 on 2008-09-29
What do you normally do with your computer e.g. pictures, music, surf the net, office tasks, whatever?
Just do that :)

---

### Post by Obero on 2008-09-29
> **oilchangeguy said:**
> what do you mean, what do you do next? after you install the updates there is nothing else to do, until more updates are available. you'll see the star burst icon when there's more.

So you just leave it like that and don't install flash or anything, is that what you did?

What I mean, is in your situation, what would you do afterwards, what would you install, etc. and I'd like to know how. I don't know what to do, it's a completely new setting, so that's why I ask. Also, installing things are different so that's why I asked.

---

### Post by titico on 2008-09-29
What do you do next depends on what you WANT to do next!!

You can install programs, configure your desktop environment as you please...

Just tell us what you want to do :P

---

### Post by titico on 2008-09-29
Try to go to

Applications > Add/Remove

There you can find some good programs you can install with that utility

---

### Post by OutOfReach on 2008-09-29
How about getting familiar with the operating system?
What else is there to do? Just live your normal computer life. (Browse the web, e-mail, etc etc) Try new things, get familiar, etc

---

### Post by oilchangeguy on 2008-09-29
> **Obero said:**
> So you just leave it like that and don't install flash or anything, is that what you did?

What I mean, is in your situation, what would you do afterwards, what would you install, etc. and I'd like to know how. I don't know what to do, it's a completely new setting, so that's why I ask. Also, installing things are different so that's why I asked.

ok, your first post was VERY vague. go to applications, add/remove, and look around. there's lot's you can install on your computer. just depends on what you want/need.

---

### Post by Obero on 2008-09-29
> **titico said:**
> What do you do next depends on what you WANT to do next!!

You can install programs, configure your desktop environment as you please...

Just tell us what you want to do :P

I don't know what I want to do! lol I just want all the basics, and the priorities to be done so my family can use it easily! I need flash, and everything else, I'm asking for recommendations here on what to do next I'm not quite sure!

---

### Post by Obero on 2008-09-29
> **oilchangeguy said:**
> ok, your first post was VERY vague. go to applications, add/remove, and look around. there's lot's you can install on your computer. just depends on what you want/need.

Yeah I agree it was vague, but what this is more of your opinion on what you would install or do next on a clean install and how I can do that too. Of course it would be have to be highly recommended.

---

### Post by mike1234 on 2008-09-29
Let Ubuntu do it's thing. It will let you know if you need to reboot. Usually it doesn't. With some kernel updates, video updates for restricted drivers, etc. Also when you try to watch a dvd movie, it will let you know if you need to download codecs too. It's really user friendly. Just don't go crazy installing stuff as a way of experimenting. You're asking for trouble if you do. Just take little steps at first. Remember when you learned how to walk?

M.

---

### Post by rodriguez24 on 2008-09-29
> **titico said:**
> Try to go to

Applications > Add/Remove

There you can find some good programs you can install with that utility

I second this. That is what I did when I first installed Ubuntu. Just browse and see what interests YOU. I installed the Kanji Dictionary, maybe/probably you don't want that. :)

---

### Post by Obero on 2008-09-29
> **rodriguez24 said:**
> I second this. That is what I did when I first installed Ubuntu. Just browse and see what interests YOU. I installed the Kanji Dictionary, maybe/probably you don't want that. :)

So how do I install this software from a CD that came with my printer?

---

### Post by Bölvaður on 2008-09-29
you need the restricted extras. Go into System &#8594; Administration &#8594; Synaptic Package manager
and look up ubuntu-restricted-extras.

That should be it. The things in that package are all normal things that you'd use, but are not supported from the company behind ubuntu. That includes flash (which is supported by adobe of course)


Perhaps downloading some songs and testing out rythmbox would be the next thing after that.
oh btw go to System &#8594; Preferences &#8594; Sound
and put everything on Alsa, it will make it possible to listen to mp3 and surf youtube at same time... perhaps you might not need it, but hey... then you know what needs to be done if it doesnt.

---

### Post by oilchangeguy on 2008-09-29
> **Obero said:**
> So how do I install this software from a CD that came with my printer?

you don't. the cd was probably written for windows, mac, and not linux. just hook up the printer. in most cases ubuntu will load the needed software.

---

### Post by Therion on 2008-09-29
I would suggest you do two additional things.

1. 
Navigate to System/Administration/Synaptic Package Manager.
Search for, download and install "ubuntu-restricted-extras".
Type it in just as you see with no "quote" marks.  This will allow you to play .mp3 files and other files that have "restricted" codecs that Ubuntu can't install by default for legal reasons.

2.
While still in Synaptic Package Manager, search for, download and install another package called: "libdvdcss2".  This will help if you want to play factory stamped DVD's... Movies and such.

---

### Post by Bölvaður on 2008-09-29
> **Obero said:**
> So how do I install this software from a CD that came with my printer?

no, probably are all the drivers you'll need installed already.
just plug it in and try, btw what printer do you have?

---

### Post by uberdonkey5 on 2008-09-29
ah, OK. well, depends what you want. But here is a run down of what I'd do (basically) on my own system.

1. check mic, speakers, dvd drive are all working (and internet, but guess that must be working!)

2. Ubuntu doesn't come with all the codecs to play music (like mp3) cos these are copyrighted and you are supposed to pay for them. However, enable multiverse and universe repositories in synaptic package manager

then, in add/remove programs find gstreamer codecs and add them

TO GET RESTRICTED CODECS, at the terminal type:
sudo apt-get install ubuntu-restricted-extr

3. install Skype

4. install realplayer

5. install picasa

6. Sometimes things can go REALLY wrong when messing around with ubuntu, like loosing all your menus. I like to be able to access the terminal no matter what happens. Therefore what has saved my bacon is a nautilus script, which allows you to right click with your mouse and open a terminal in any file or on the desktop..
be able to open a terminal in any file with right click of mouse (very useful)
[http://ubuntu-tutorials.com/2006/12/29/right-click-to-launch-custom-scripts-with-nautilus-ubuntu-6061-610/](http://ubuntu-tutorials.com/2006/12/29/right-click-to-launch-custom-scripts-with-nautilus-ubuntu-6061-610/)

in addition, I go into keyboard shortcuts and set a shortcut (like ctrl+alt+T) to open terminal. Also set other shortcuts while you are there.

7. go to
[http://gnome-look.org/](http://gnome-look.org/)
and make your desktop pretty (ah, you probably have to install compiz for most of these. do a search on this)

8. remove unwanted software (I remove games). Don't remove evolution! it messes around with your desktop as well if you remove it.

Basically ubuntu is VERY customisable. Do what you want, these are just my suggestions. If you come from windows you have to realise you can do LOTS (both good and bad!) of things. Just search on the net.

---

### Post by titico on 2008-09-29
if you want your family use the computer you probably want some kind of 
msn utility, or games, or word processor programs...

Take a look around ubuntu comes with some good programs...If none of them fit with your expectations, browse the web for more or try some from the add/remove manager o synaptic manager.

If you want to install the printer post here the version of it.
You can also try to browse the web and i'm sure you'll find guides to install it...It is a good way to start learning =]

---

