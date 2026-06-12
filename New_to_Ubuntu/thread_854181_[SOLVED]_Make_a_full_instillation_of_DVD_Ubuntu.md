---
title: "[SOLVED] Make a full instillation of DVD Ubuntu"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by Alan Coleman on 2008-07-09
I have a Copy of Hardy on DVD and installed it. To my surprise it installed the same as the CD. I want to install all the software on the DVD, to get a feeling of what Ubuntu has to offer not just the cd version. Is there a way to do this other than going through each package one by one and installing them individually which would take days?

Thanks
ac

---

### Post by Elfy on 2008-07-09
If they are a list of debs then you could I believe run this from terminal, you would need to cd into the folder, tab autocomplete will help 

```
cd /media/cdrom
```

if that's how the disc mounts, then navigate through the folders to the folder containing packages then

```
sudo dpkg -i *.deb
```

which would install all the debs in that folder. You might problems with dependencies but not sure.

---

### Post by billgoldberg on 2008-07-09
You want to install all the software in the ubuntu repositories?

This is madness I tell you, madness.

:lolflag:

---

### Post by Elfy on 2008-07-09
No - I think just what's on the dvd - it did take someone 10 hours to do the repos,

---

### Post by Vivaldi Gloria on 2008-07-09
Start synaptic, remove all the repos other than the dvd. Then refresh. Now the list will give all the programs in the dvd. Choose & install.

Some programs may clash with each other so I don't think you can install all.

Also be careful about security. By default no ports are listening in a default ubuntu install. Why would you want to install any server program if you are not going to use it? 

I don't know what is on the dvd btw. I'm just making guesses.

I also think that the dvd has nothing to do with "what ubuntu can offer". You are coming with a windows mindset. It is the repositories which are the soul of ubuntu. 

See also the apps at:

[http://www.gnomefiles.org/](http://www.gnomefiles.org/)

and maybe also at the kde-files site.

---

### Post by Elfy on 2008-07-09
> **Vivaldi Gloria said:**
> Start synaptic, remove all the repos other than the dvd. Then refresh. Now the list will give all the programs in the dvd. Choose & install.

Some programs may clash with each other so I don't think you can install all...

+1

You might possibly find you have dependency errors as well.

---

### Post by chalewa on 2008-07-09
yea i understand what you mean, but there is really no point in this. you are just going to end up with all kinds of conflicting programs. 

for instance, wicd and network manager cannot coexist. 

what someone should do is develop a version of ubuntu called like bloatbuntu or something with all kinds of bells and whistles pre-installed.

---

### Post by sydbat on 2008-07-09
> **chalewa said:**
> what someone should do is develop a version of ubuntu called like bloatbuntu or something with all kinds of bells and whistles pre-installed.Isn't there something like that on the market now...um...what's the name...Vis-something...

---

### Post by Alan Coleman on 2008-07-09
"What someone should do is develop a version of ubuntu called like bloatbuntu or something with all kinds of bells and whistles pre-installed."

I was useing knoppix 5.3 dvd today and it dose come with bells and wistles
at least on the live dvd. 

It did'nt install so well though.

Thanks for the replys.
I shall work on it.
ac

---

### Post by k3lt01 on 2008-07-09
> **chalewa said:**
> what someone should do is develop a version of ubuntu called like bloatbuntu or something with all kinds of bells and whistles pre-installed.It's called Ultimate Ubuntu and even has its own forums. I found out about it through this forum.

---

### Post by chalewa on 2008-07-10
> **k3lt01 said:**
> It's called Ultimate Ubuntu and even has its own forums. I found out about it through this forum.

yea i remember reading about this a while back, i guess i didn't realize that it had actually come to fruition.

---

