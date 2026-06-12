---
title: "flash etc"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Savakker on 2008-04-25
Im seeing big grey squares with play buttons on websites where there is a flash item. When I click on them they display correctly.

I seem to remember ages ago there was a package that you could download that had all these codecs and players in for linux.  

It was a long time ago and Ive totally forgotten the name of it.

Is there a similar package available now that will sort out all these propriatory progarammes in one fell swwop?

Thanks

---

### Post by Paqman on 2008-04-25
> **Savakker said:**
> 
I seem to remember ages ago there was a package that you could download that had all these codecs and players in for linux.  


[Click here to install it](apt:ubuntu-restricted-extras)

---

### Post by Savakker on 2008-04-25
Ok thanks...

have downloaded it (and installed it I think!) and still get this...
oh damn, how to link an image...ho hum....

for those watching in black and white,,,,the flash squares still are grey with big play arrows inside them lol

Also...I have a ati 3850 graphics card and after downloading the ati driver, it wants me to be the super user to install it.

Now I know that that will mean a =prefix of sudo...but what on earth comes after???

Is there a hand-holding thread somewhere that can get us new users through the basic set-up (video, audio, flash, graphics cards, etc etc) because at the moment, the simplest things are taking ages to configure.

As much as I want it to, ubuntu doesnt just work, it still seems to presume a lot of prior knowledge.  Thats not actually a problem,linux is trying to fit in with stuff that wasnt designed around it, I understand that, but access to basic set up info would be worth its weight in gold.

Cheers

---

### Post by spiderbatdad on 2008-04-25
The correct way to install that package is through synaptic package manager on your system, or use apt: ```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by spiderbatdad on 2008-04-25
> **Paqman said:**
> [Click here to install it](apt:ubuntu-restricted-extras)

Reported:
It is inappropriate to post links that attempt to install software on someone else's computer. Please post appropriate advice on how to install software.

---

### Post by mister_pink on 2008-04-25
I don't know what the forum rules are regarding install links but it not like that was a malicious hidden download, the link was appropriately titled. If it was a problem then they could remove such functionality from the forum, it shouldn't be difficult.

Anyway, that probably won't fix the problem, you've obviously got flash installed otherwise it wouldn't play when you clicked it. A screenshot may help. I think I've seen a thread with a similar problem that had a solution so if I can find it I'll let you know.

---

### Post by LaRoza on 2008-04-25
> **spiderbatdad said:**
> Reported:
It is inappropriate to post links that attempt to install software on someone else's computer. Please post appropriate advice on how to install software.

That is a Firefox specific URL scheme which uses apt (look at the URL).

---

### Post by spiderbatdad on 2008-04-25
> **LaRoza said:**
> That is a Firefox specific URL scheme which uses apt (look at the URL).

It is my own opinion then, that it is inappropriate to post links that install software on another's computer. There is no instruction involved in such a post, and it seems just a step short of social engineering in my opinion. What if someone following that link wants to un-install the package? Will the poster provide a link for that? Who learns from such a post?
My apologies to the the poster. I do not accuse him of malicious behavior, but I disagree with the practice.

---

### Post by tjwoosta on 2008-04-25
i also get the big grey square that i have to click on to make things play(no autoplay), i figure its because i installed the swfdec player (or whatever its called) instead of flashplayer-nonfree

how could i uninstall it so i can install the regular flash?

---

### Post by Utnubuster on 2008-04-25
> **Savakker said:**
> Im seeing big grey squares with play buttons on websites where there is a flash item. When I click on them they display correctly.

I seem to remember ages ago there was a package that you could download that had all these codecs and players in for linux.  

It was a long time ago and Ive totally forgotten the name of it.

Is there a similar package available now that will sort out all these propriatory progarammes in one fell swwop?

Thanks

I just used the thing in firefox when there's a plugin missing

---

### Post by gusmoney on 2008-04-25
> **tjwoosta said:**
> i also get the big grey square that i have to click on to make things play(no autoplay), i figure its because i installed the swfdec player (or whatever its called) instead of flashplayer-nonfree

how could i uninstall it so i can install the regular flash?

Experiencing the same 'Big Play Button' problem, I found the amalgamated answer in another thread [ubuntuforums.org/showthread.php?t=766108&highlight=flash](ubuntuforums.org/showthread.php?t=766108&highlight=flash)

First, uninstall the goofy player: ```
sudo apt-get purge swfdec-mozilla
```

Then install the working alternative:  ```
sudo apt-get install flashplugin-nonfree 
```

---

### Post by Savakker on 2008-04-26
The advice to remove then install flash plug in worked a treat, thanks.

---

### Post by FredB on 2008-04-26
goofy player ? I don't need the adobe version of flash for my own use. And using nspluginwrapper, no thanks.

---

### Post by Terpsicore on 2008-04-26
Your instructions worked great gusmoney.

Thanks a lot :)

---

