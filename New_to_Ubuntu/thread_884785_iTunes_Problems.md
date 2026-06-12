---
title: "iTunes Problems"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by barabaskid on 2008-08-09
I'm trying to connect Rhythmbox to iTunes via network (the former computer running Ubuntu, the latter XP) in order to share music libraries without having to transfer files from computer to computer. Having scoped about online, I see that, as of iTunes 7.0, Rhythmbox can no longer access files running through iTunes. My question, then, is if there is some other software I could run on the XP machine that would allow Rhythmbox to access said files, so I could play them on the Ubuntu computer without transferring the files.

Any advice much appreciated, and be well.

BarabasKid

---

### Post by pytheas22 on 2008-08-09
I'm pretty sure that you can install iTunes in wine now and it will run pretty well.  You can't sync with the iPod but I think that most of the other functionality works.  So installing iTunes in Ubuntu would be one solution.

That said, there's probably a better solution, and one which wouldn't force you to use on Ubuntu a proprietary application that leaves you at the whims of Apple.  Hopefully someone else will have a better suggestion than me, but I wanted to put this out there in case no one else replies.

---

### Post by st33med on 2008-08-09
You can also try Banshee-1 from a special repo. 
Just follow the instructions [here]("https://edge.launchpad.net/~banshee-team/+archive") to add the repo.

---

### Post by barabaskid on 2008-08-09
Banshee-1 loaded fine, but it still can't share music from iTunes 7.0 and up (and I can't downgrade the iTunes on the XP computer). I also am unable to find a guide that details how to make iTunes run under wine, but I'll keep trying.

Anyone who has another solution is welcome to offer it. I'll try anything once.

---

### Post by pytheas22 on 2008-08-09
> I also am unable to find a guide that details how to make iTunes run under wine, but I'll keep trying.

You should just be able to download the Windows installer for iTunes and launch it.  I haven't tried it myself, but I don't think there's any special hacking required.  [This]("http://mikesubuntu.blogspot.com/2007/10/itunes-great-with-wine-yep-its-true.html") might help.

But Banshee may indeed be a better solution.

---

### Post by kwacka on 2008-08-09
I think this is a more current version of banshee (v1.2 - July 30th 2008):
[https://edge.launchpad.net/~banshee-team/+archive](https://edge.launchpad.net/~banshee-team/+archive)

---

### Post by jcbwalsh on 2008-09-02
I just found a new alternative for sharing an iTunes library called SimplifyMedia - [http://www.simplifymedia.com](http://www.simplifymedia.com). I think Apple does something so that iTunes will only share with another copy of iTunes. In Rhythmbox the share appears but doesn't work. 

SimplifyMedia allows you to share libraries between iTunes on Windows or Mac and Rhythmbox in Ubuntu. (It even has an iPhone client.) 

The set up is very simple. The instructions are on the site.

---

