---
title: "Integrated KDE Distro"
date: 2008-06-16
forum: Other OS Talk
---

### Post by Luk8 on 2008-06-16
Hello everyone!

I've seen a lot (and I mean a LOT !) of forum topics asking for the best KDE distro around, however, I'm more interested in having a distro with a very well integrated KDE ( all the tweaks for firefox to integrate in kde - from theme to icons,kget,kprinter(?) etc, and for other gtk apps as well ). Basically, it should be a distro that really focuses on KDE, rather than has it as an option alongside Gnome.

I'm looking for it to have all the KDE goodies ( custom patches etc ) integrated by default.

Also, I'd prefer it be based on Debian, since apt-get+the massive amount of packages is much more better for me then yum ( tried openSuse quite a few times in the last month, just didn't do it for me ).

So, given the facts mentioned above, what would be the most KDE focused/integrated distro you would recommend to me ?

Thank you !

---

### Post by LaRoza on 2008-06-16
> **Luk8 said:**
> 
I've seen a lot (and I mean a LOT !) of forum topics asking for the best KDE distro around, however, I'm more interested in having a distro with a very well integrated KDE ( all the tweaks for firefox to integrate in kde - from theme to icons,kget,kprinter(?) etc, and for other gtk apps as well ). Basically, it should be a distro that really focuses on KDE, rather than has it as an option alongside Gnome.

Also, I'd prefer it be based on Debian, since apt-get+the massive amount of packages is much more better for me then yum ( tried openSuse quite a few times in the last month, just didn't do it for me ).


Firefox doesn't use QT. Whatever this mysterious "intergration" is, it won't be happening with Firefox. That is why Konqueror exists ;)

Try OpenSUSE with KDE?

---

### Post by Luk8 on 2008-06-16
Firstly, thank you for your reply.

Uhm, I must have expressed myself ambiguously (it happens, since English is not my native language).

Firefox can be integrated within KDE with some patches, so that it uses KDE dialogs instead of gtk ones, is themed with the qt engine, the downloads are started with kget, it uses kprinter instead of the default dialog, and so on ( you can find a guide here for what I've mentioned: [http://gentoo-wiki.com/HOWTO_Integrate_Firefox_with_KDE](http://gentoo-wiki.com/HOWTO_Integrate_Firefox_with_KDE) ).

I hope that I now explained part of that < mysterious "intergration" > ;) .

I allready said I tried openSuse with KDE and didn't like it, so that's not really an option right now.

Looking forward for more solutions :) .

---

### Post by danbuter on 2008-06-16
OpenSUSE is the only distro I know that really optimizes/changes KDE to a regular appearance. But it's RPM, and you don't like it.

---

### Post by cardinals_fan on 2008-06-16
I love SLAX.  It provides a lightweight but full-featured KDE implementation with the stability of Slackware.  If being Debian-based is important, consider Sidux.

---

### Post by 67GTA on 2008-06-16
openSUSE :twisted: 

Debian based brings to mind Mepis and Sidux, but they don't have the tweaks your talking about.

---

### Post by igknighted on 2008-06-17
Which opensuse did you try?  11.0 is light years better than 10.3, so if you used 10.3 then you may wish to look again.  Plus, if you include build service repo's, suse has (almost certainly) the largest package repositories out there.  Oh... and the new Zypper/Yast2 combo is actually quite fast.  Installing packages is on par with apt/synaptic and yum/packagekit, and updating is much faster than anything debian based due to the tremendous integration of deltaRPMs.

EDIT: I don't think ANY kde distro has most of those tweaks by default.  I would recommend building your own spin (or donating your time to add these to Kubuntu), as there seems to be demand for them.  This is how open source improves... community members and users see the true needs and should contribute back what they can.

---

### Post by karellen on 2008-06-17
as previously said, opensuse
and you might want to take a look at Mandriva, I like the way 2008.1 "does" KDE

---

### Post by darrelljon on 2008-06-17
I'm just guessing but Knoppix, sidux or Kanotix?

---

### Post by gabhla on 2008-06-17
Maybe sidux.  Debian based with default KDE.

---

### Post by Luk8 on 2008-06-18
Thanks for all the suggestions so far. Keep'em coming guys! ;) 

I've tried openSuse 10.3 and final RC of 11.0 . Requiring me to handle 70 manual decisions on what to do with some packages just for installing something is a very sure no-no for me.

I guess I'll try openSuse again sometime in the future, just not now.

---

### Post by 67GTA on 2008-06-18
> **Luk8 said:**
> Thanks for all the suggestions so far. Keep'em coming guys! ;) 

I've tried openSuse 10.3 and final RC of 11.0 . Requiring me to handle 70 manual decisions on what to do with some packages just for installing something is a very sure no-no for me.

I guess I'll try openSuse again sometime in the future, just not now.

This is the reason I quit using opensuse. I thought this was supposed to be fixed in 11. If it's not, I guess I will skip it too.

---

### Post by MONODA on 2008-06-19
I would go for opensuse 11, it should come out today.

---

### Post by Luk8 on 2008-06-19
> **67GTA said:**
> This is the reason I quit using opensuse. I thought this was supposed to be fixed in 11. If it's not, I guess I will skip it too.

There's a chance **I** screwed up something, I do not want to discourage people trying it, as a lot of the people seem to recommend it. Maybe you'll have a much better experience than me ;) .

---

### Post by 67GTA on 2008-06-19
There is supposed to be a new feature for 11 in Yast>Software Repos. It has a priority setting for each repo. 0 is the highest and 99 is the lowest. I haven't tried it yet. I just ordered the DVD this morning. 10.3 gave me a headache because of the package conflicts between the opensuse and packman repos. Sometimes installing one package from packman caused 10-20 manual decisions from me to get it installed because opensuse packages conflicted with them. Sometimes I would give up because I wasn't sure about the package being removed, and there was no confirmation that it would be replaced with an equal from packman.

---

