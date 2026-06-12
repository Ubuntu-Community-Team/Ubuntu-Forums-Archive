---
title: "How to replace FF3 with Firefox 2"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by neurostu on 2008-04-25
Can I backport FF3 to FF2 in Hardy Heron? I had a lot of extensions that I used which are not compatible with FF3 beta.

Also what are the major features that FF3 offers that 2 didn't have?

---

### Post by bt224 on 2008-04-25
use Synaptic to uninstall FF3, then same to install FF2. I had the same issue.

---

### Post by neurostu on 2008-04-25
```

 sudo apt-get install firefox-2 firefox-2-gnome-support

```

---

### Post by FredB on 2008-04-25
> **neurostu said:**
> Can I backport FF3 to FF2 in Hardy Heron? I had a lot of extensions that I used which are not compatible with FF3 beta.

Also what are the major features that FF3 offers that 2 didn't have?

Which are your guilty extensions ?

And for the changes :

[http://www.mozilla.com/en-US/firefox/3.0b5/releasenotes/](http://www.mozilla.com/en-US/firefox/3.0b5/releasenotes/)

---

### Post by spacefreak86 on 2008-04-25
Should be able to go into Add/Remove programs, remove out Firefox 3 beta, apply, then add in Firefox 2. I too had to do this, as it just wouldn't load at all on my computer :(

---

### Post by Paqman on 2008-04-25
> **neurostu said:**
> Can I backport FF3 to FF2 in Hardy Heron? I had a lot of extensions that I used which are not compatible with FF3 beta.

You can actually have both at the same time.

The Nightly Tester Tools extension allows you to disable version checking for extensions on FF3. There's no guarantee they'll work, but it's an option.

> 
Also what are the major features that FF3 offers that 2 didn't have?

It's been completely redesigned behind the scenes, and is a lot quicker. On the surface not much has changed, but the way it now waits to ask if you want to remember a password until *after* you've successfully logged in is a great feature.

---

### Post by neurostu on 2008-04-25
So when i tried to run firefox 2 it didn't grab all my settings that were imported over from gutsy, those got put with firefox 3, how do I get firefox 2 to see the preferences that I had originally set?

---

### Post by bt224 on 2008-04-26
sorry, you can't now. Again, happened to me and I wasn't so happy.

---

### Post by neurostu on 2008-04-26
There has got to be a way to revert to FF2 and have FF2 recognize my old settings?

Somebody has to know how to do this...

---

### Post by billgoldberg on 2008-04-26
> **neurostu said:**
> There has got to be a way to revert to FF2 and have FF2 recognize my old settings?

Somebody has to know how to do this...

Have you tried just downloading firefox from the mozilla website?

[http://www.mozilla.com/en-US/firefox/](http://www.mozilla.com/en-US/firefox/)

Someone asked why ff3 is better than ff2.

The most noticeable thing is that it's faster (a lot faster) and more stable.

---

### Post by SunnyRabbiera on 2008-04-26
> **neurostu said:**
> There has got to be a way to revert to FF2 and have FF2 recognize my old settings?

Somebody has to know how to do this...

I do, at least for the most part.
You still have your bookmarks and cookies right?
You can check if they are still there by un hiding the mozilla folder by opening up your home directory and go up to "view" and select "show hidden files."
in your mozilla directory you might still have your bookmarks and cookies at least, for exentions though I am afraid you have to re install them.
also if you need help in installing firefox 2 I can teach you, its very simple but lets go the steps shall we?

---

### Post by philinux on 2008-04-26
If you make a backup of your bookmarks this is all you can restore.

Once FF3 has use your profile folder FF2 cannot use it. 

You have to delete it and let FF2 create it's own new one. Then you can recover your bookmarks. 

I've found FF3 works fine.

---

### Post by SunnyRabbiera on 2008-04-26
> **philinux said:**
> If you make a backup of your bookmarks this is all you can restore.

Once FF3 has use your profile folder FF2 cannot use it. 

You have to delete it and let FF2 create it's own new one. Then you can recover your bookmarks. 

I've found FF3 works fine.

yeh for me it crashed a couple of times, plus the extension thing very important to many users (me included)

---

### Post by FredB on 2008-04-26
Well. I saw a lot of post like this thread. What about staying on gutsy if you want to use firefox 2 ?

---

### Post by SunnyRabbiera on 2008-04-26
well its not like its impossible to get firefox 2 in hardy, heck I did it, its in the repos and brainlessly easy to remedy :D

---

### Post by FredB on 2008-04-26
You didn't answer my question. Why do people bother installing hardy - and the bad boy Fx 3 beta 5 - instead of staying with gutsy ?

Is there somebody threatening them with a rocket launcher or what ?

---

### Post by neurostu on 2008-04-26
So Hardy actually works better with my hardware. I had a lot of issues with my wireless adapter, Hardy solved all of these problems.  Hardy for me is a better OS.


So I know that the following commands will replace FF2 with FF3
```

sudo apt-get install firefox-2
sudo apt-get remove firefox-3.0

```

I even added an extension called Nightly tester tools to FF3 that allowed me to run all my FF2 extensions. I'd say about 1/2 of them work, and luckily they were the ones I really wanted.


Does anybody know what FF2 uses as the profile folder in Hardy?  Can I just move the FF3 profile folder over the FF2 profile folder and get everything to copy over that way?

What if I remove FF3 and FF2, copy over the profile folder from my old install and then install FF2, will that work?

---

### Post by philinux on 2008-04-26
Please read my previous post.

---

### Post by veritas366 on 2008-04-26
I've had much worse luck with FF3.  It will sometimes take a long time to load and worse, it will gray out the entire browser until it is finished loading a page...so you can't even switch to a new tab.  Often it hangs altogether though this seems only to affect Youtube.

This is a pretty cheap laptop I'm using and I'm actually thinking of just getting xubuntu for speed, but I had no issues with Gutsy/ff2

Also, strangely, I uninstalled ff3 and uninstalled ff2 and then reinstalled ff2...all via synaptic...and then without thinking I clicked on the original FF3 icon in the task bar...and FF3 came up.  I'm using it now, in fact.  I think I must have had an "ADHD" moment on that, though.  Or is there a separate Ubuntu Firefox I should have uninstalled?

---

### Post by neurostu on 2008-04-26
Philinux:

I did read your post.

   I have my old gutsy /home folder backup up (with my FF2 profile), can I use the firefox profile from THERE to replace the FF2 profile in hardy and get all my extensions moved over?

Where is the ff2 profile folder saved in Hardy?

---

### Post by philinux on 2008-04-26
> **neurostu said:**
> Philinux:

I did read your post.

   I have my old gutsy /home folder backup up (with my FF2 profile), can I use the firefox profile from THERE to replace the FF2 profile in hardy and get all my extensions moved over?

Where is the ff2 profile folder saved in Hardy?

Right yes you can as it's a FF2 profile. The folder is in the same place
/home/username/.mozilla it's a hidden file you need ctrl h to see them, but you must already know that. :lolflag:

---

### Post by neurostu on 2008-04-26
So let me see if I get this straight...

When FF3 is installed .mozilla is taken over by ff3 and ff2 has to create a new profile folder (where is this NEW folder?).

when you remove FF2 & FF3 and delete the .mozilla folder, when you install FF2 it will create this .mozilla folder  which you can copy let say a gutsy .mozilla folder over... right?

---

### Post by SunnyRabbiera on 2008-04-26
> **FredB said:**
> You didn't answer my question. Why do people bother installing hardy - and the bad boy Fx 3 beta 5 - instead of staying with gutsy ?

Is there somebody threatening them with a rocket launcher or what ?

its about trying something new, after all hardy is the LTS and support for gutsy will soon drop out.
I wanted to give hardy a shot and see how it was in comparison to gutsy, for me yes its a LOT better for the most part then gutsy but I see it has a few quirks with firefox 3 being one of them.
But I wanted to see how firefox 3 was doing too, and I can tell already why its a beta, everything is trial and error and well I got the error :D

---

### Post by FredB on 2008-04-26
> **SunnyRabbiera said:**
> its about trying something new, after all hardy is the LTS and support for gutsy will soon drop out.

12 months is soon ?

> I wanted to give hardy a shot and see how it was in comparison to gutsy, for me yes its a LOT better for the most part then gutsy but I see it has a few quirks with firefox 3 being one of them.

What about live cd testing, so ? ;)

> But I wanted to see how firefox 3 was doing too, and I can tell already why its a beta, everything is trial and error and well I got the error :D

Well. I had not used a single stable release of firefox since I'm using it. Always using the "bleeding edge" and never get lost any single data...

Too lucky ?

---

### Post by SunnyRabbiera on 2008-04-26
well the Live can only tell you so much, something might work great on the live but stink when installed...
hey I opted to give hardy a install as there was really nothing stopping me, I wanted to see if hardy lived up to the hype, and for the most part it has.

---

