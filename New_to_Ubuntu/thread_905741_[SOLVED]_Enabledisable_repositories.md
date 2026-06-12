---
title: "[SOLVED] Enable/disable repositories"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by gusteman on 2008-08-30
Hi there, here I am again. Still trying out things and learning about Unix, Linux and Ubuntu. For those who tried to help me out with my sound problems: I finally got it solved. Thanks to the Community. But here is what I am faced with now:
I am trying to download the HPLIP package for a HP printer (F4180)
I downloaded from the HPLIP-site the regular tarball and planted it on my desktop. Then I opened the terminal and got started, following the directions on the site. 
Everything worked fine until I got the warning that [COLOR="Red"]CD-ROM/DVD source repository is enabled and that it shouldn't be![/COLOR] From that point on I am stuck. I even tried the "automatic install" but even there it failed on the same item.
I googled around and found lots of information about repositories but nowhere I could get a clue on how to find them or how to change their setting. Anybody has an idea? Help would be very welcome.
Regards, Gusteman (*btw meanwhile I keep on searching*)

---

### Post by alienexplorers on 2008-08-30
The repositories are in system>administration>software sources.

---

### Post by kellemes on 2008-08-30
Isn't your printer automagically recognized from the printer configuration dialog?

---

### Post by gusteman on 2008-08-30
@ alienexplorers:
I haven't yet tried the printer configuration and here is why:
before buying the printer I checked out at HPLIP if that printer was supported. On the same site I found explanations about how to download the drivers and install them under Linux so I was willing to give it a try. With the result as mentioned above.
@ kellemes:
after googling for an answer to my problem I stumbled on the same answer you gave me. In the example shown there I saw a window with a series of possibilities to check/uncheck software sources. But when I opened software sources the only source i could find (besides the checked lines of Main, Universe, Restricted and Multiverse software, downloadable from the Internet) was a rectangular window: installable from CD-ROM/DVD: cd-rom Ubuntu 7.04 Feisty Fawn.
And while I'm typing this I sense that your answer will be to uncheck this cd-rom in that particular window, is it not?

---

### Post by drs305 on 2008-08-30
> **gusteman said:**
> 
And while I'm typing this I sense that your answer will be to uncheck this cd-rom in that particular window, is it not?

While I can't speak for kellemes, unchecking the CD-rom is what you should do.

I don't know if it is available for feisty, but for later versions of ubuntu the HPLIP package is available from the normal repositories in synaptic. Before dealing with a tarball you might want to check see if it is available as a package in your repositories. Just click in synaptic's package window (where all the apps are listed), type HPLIP and see if it's listed.

---

### Post by gusteman on 2008-08-30
@ drs305:
I did not mention it in posting the thread but I already had done what you suggested and indeed found through synaptic that are already listed:
- hpijs
- hplip
- hplip-data
so normally I should be able to install the printer without any problem.
Untill this moment I still haven't done this (but I suppose I will anyway) but the main reason for my question was not to start up the printer but to get to know the way how to enable or disable repositories. You never know when I might be once again confronted with the need to alter them. And as far as I can tell with the little knowledge I acquired up to this moment, I can mark this post as SOLVED. Thank you all once again for helping me out. May the beans be with you :lolflag:

---

