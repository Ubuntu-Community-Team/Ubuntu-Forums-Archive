---
title: "pointless question"
date: 2007-06-08
forum: Other OS Talk
---

### Post by sw1995 on 2007-06-08
Help!

I am a Linux noob; have been using and learning about Ubuntu for about a month now and REALLY love it. The thing is, I am using an older laptop and it just tends to be too sluggish for my purposes (I teach online history classes). Needless to say, I type a lot and if OpenOffice can't run for me smoothly then I think it is time to bite the bullet and move on (I have tried Xubuntu but really disliked it, perhaps from being "spoiled" by Gnome). For the most part everything runs well; sounds, video, I even had beryl running well but as soon as I try to multi-task everything sssslllllooooowwwwsss down.

In any event, I would hate to switch distros but have heard many good things about PCLinuxOS and in the interest of my productivity was wondering if anyone knew whether or not it would run faster on my machine (2 gig processor, 512 Ram). Long story short, is it a crap shoot as to whether or not another distro would be faster or not? I suspect the answer is an obvious "yes", but, alas, I need someone to speak up for my conscious and tell me to NOT leave Ubuntu!

For instance, after having spent so many hours reading these forums, I feel as though I have learned a great deal about the security of my system. Is that to be expected from other distros? Is PCLinuxOS or OpenSuSe just as "safe" security wise as Ubuntu?

Ok, so two questions:

1.  Can I hope for a "snappier" system elsewhere?
2.  Does security and Linux run across the board?

Thank you in advance for any help!

Cheers!

---

### Post by Pobega on 2007-06-08
Well, keep in mind all GNU/Linux systems are very similar, with minor differences. Most things that apply on Ubuntu will apply on SuSE or PCLOS too. The main difference that I've seen between most distros is package management, and how files/libraries are organized.

That being said, I think you'll definitely find a quicker distribution eventually, but it definitely won't be PCLOS or SuSE, Both distributions are very newbie friendly, but they're definitely not quick. The best thing you can do for speed (And keeping the Debian package manager, APT, which I'm sure you've grown accustomed to) is to try installing Sidux. It may take you a bit longer to set up than Ubuntu (If you're afraid of the terminal then I wouldn't even bother if I were you), but from what I've heard Sidux is the fastest binary distribution around; And I'm **sure** you don't want to spend four days installing Gentoo just for a bit more speed.

---

### Post by sw1995 on 2007-06-08
Thanks for the feedback--I'll certainly check out Sidux!

UPDATE:

I tried out PCLinuxOS and it nearly gave me a panic attack; there is way too much going on in that interface for me although it did seem to be a bit "snappier" at times. Sorry, but I do not need ten different ways to access my internet connection (and it would not recognize my wireless card or wireless mouse and ndiswrapper was not playing nice, whatsoever). Additionally, I felt as though the forum was rotten and incredibly unorganized compared to the Britannica that is "ubuntuforums.org". I have to admit, too, that I found the tongue-in-cheek twist on the Microsoft theme (a la the icon and start-up music) kind of distasteful and, for lack of a better term, pedestrian. I understand the attraction to such distros, however I maintain that the aesthetic and philosophy of Ubuntu is just much more sophisticated.

Ubuntu 1, Everthing Else, 0.

I'll stick with Ubuntu and embrace the lag.

:)

---

### Post by cactaur on 2007-06-09
Well, if OpenOffice is too resource-intensive for you, there are many different options. One is gnome-office. I believe you could install it from Synaptic. By what I hear, it is faster and smaller than OpenOffice. You might find that would work better.

---

### Post by mips on 2007-06-10
Have you tried Fluxbox ?

Another option is to use something like Arch or Gentoo etc. Maybe even try PCBSD.

---

### Post by Rhubarb on 2007-06-10
Abiword is a very fast word processor, and Gnumeric is a very fast spreadsheet app.
You can find both of these apps in the repositories.

---

### Post by Bachstelze on 2007-06-10
If I were you, I'd install Debian. Very similar to Ubuntu but much lighter.

---

### Post by ynnhoj on 2007-06-10
> **Rhubarb said:**
> Abiword is a very fast word processor, and Gnumeric is a very fast spreadsheet app.
You can find both of these apps in the repositories.
i'll second the these recommendations.  abiword is great.

you might also consider using a lightweight window manager; mips mentioned fluxbox.  openbox and icewm also come to mind.  if you search on the forums you'll find plenty of threads with useful information to help you get any of those window managers installed and configured to your liking.

---

### Post by Dedoimedo on 2007-06-11
You could try Puppy or Damn Small, can't get any lighter than that. Maybe also SLAX.
Dedoimedo

---

### Post by LaRoza on 2007-06-11
I just installed Zenwalk on a computer with 64 MB of RAM, and it runs faster than the OS it had before, Windows 98.

It has a lot for such a small package. It uses Abiword as its word processor. I highly recommend it.

---

### Post by smiggs on 2007-06-11
Approaching this from a slightly different angle, you could stick another 512MB RAM in there; it should fly after that. From a software point of view Abi Word and a custom Debian install may well be a good start from getting the best out of your existing hardware. But a small and inexpensive hardware upgrade may well save a whole host of time on software configuration.

---

### Post by jbaerbock on 2007-06-11
I'm using Linux Mint (based on Ubuntu Feisty) and it flies once booted (tad slow on boot though). It includes everything so set up is virtually non existent. Also I remember way back when that Star Office was the thing to get, I don't know if it is out there anymore but I aways heard good things about it back in my Redhat 4.0 days.

---

### Post by igknighted on 2007-06-11
Did you guys even look at his/her system specs!?!  2ghz processor, 512mb ram... nothing should run slow at all.  The issue must be a hardware compatability one.  Can you give any more detailed system specs (brands/models of componenets or the whole laptop)?  Ubuntu should run virtually lag free on far less than that.  Linux folk don't even really consider hardware old until we get below 256mb ram and 1ghz  processor (and even then it is only due to the liveCD... Ubuntu would run fine after installed even on that).  So do look into any incompatabilities you are having, and you might want to try out some other distros.  Since you seem to prefer Gnome, check out Fedora 7 (there is a Gnome LiveCD available, or a DVD for the full installer).  Also, for a much nicer Xfce look at SAM Linux 2007.  Other decent choices are OpenSUSE (no LiveCD though), Debian (as mentioned above) and Mandriva One 2007.1 (make sure you grab the right one for your local language).

EDIT: Do you have java installed properly?  Some OO.o features are reliant on java, so if it isn't installed properly then thats where your issues might come from.  Just a thought.

---

### Post by sw1995 on 2007-06-14
Thank you for all of this feedback; 

I think I have learned that one of my problems is that my laptop tends to just heat up too much--I have subsequently bought a usb driven cooling pad that sits underneath and it helps tremendously. 

As for the recommendations for alternative distros, I'm definitely going to try out some of the live cds just to keep myself occupied.

Thx!

---

