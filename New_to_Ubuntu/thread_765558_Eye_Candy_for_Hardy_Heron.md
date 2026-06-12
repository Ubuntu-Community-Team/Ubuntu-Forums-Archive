---
title: "Eye Candy for Hardy Heron"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by bgast1 on 2008-04-24
I want to focus on more eye candy for Hardy Heron tonight. What I would really like to learn to do is set a background to the cube instead of the black. I have asked everywhere, including Compiz forums and so far I haven't gotten an answer. Besides how to do this, perhaps someone who knows a lot about Compiz can give us some tips of other cool stuff we can enable.

---

### Post by overdrank on 2008-04-24
> **bgast1 said:**
> I want to focus on more eye candy for Hardy Heron tonight. What I would really like to learn to do is set a background to the cube instead of the black. I have asked everywhere, including Compiz forums and so far I haven't gotten an answer. Besides how to do this, perhaps someone who knows a lot about Compiz can give us some tips of other cool stuff we can enable.

Hi and maybe start here
[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion##comments](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion##comments)

---

### Post by Mazza558 on 2008-04-24
To get you started, you need this package, so run it in the terminal:

> sudo apt-get install compizconfig-settings-manager

Find the cube plugin, and find the "skydome" section. Then choose an image of choice and tick "use skydome".

---

### Post by bgast1 on 2008-04-24
Thank You. I now have a background when I have the cube. Next thing is I have seen on several screen shots like a shelf at the bottom of the screen with icons on it. How do you do that. 

Also, I would like something on my desktop that could give me the local weather forcast.

---

### Post by elmer_42 on 2008-04-24
That is usally called a "dock" and one of the most popular docks is Avant Windows Manager. I have used it and have to say that it is ace-quality stuff. I think it's in the repos for Hardy, but I'm not sure. If it is, this should work:
```
sudo apt-get install avant-window manager
```

The forecast could probably be handled with a Screenlet or GDesklet. I think these are both also in the repos. I prefer Screenlets, but you have to decide based on your own preferences.

---

### Post by Joeb454 on 2008-04-24
I always had issues with the Skydome on Compiz...It would work until I logged off, then it wouldn't work after that.

---

### Post by bgast1 on 2008-04-24
Joeb454--Just decided to check. Restarted my computer, and Skydome is still perfectly intact. :)

---

### Post by bgast1 on 2008-04-24
Unless someone can tell me more about a dock, or Avant,  and sudo apt-get install avant-window manager didn't work either. Perhaps it isn't available for Hardy Heron?

---

### Post by overdrank on 2008-04-24
> **bgast1 said:**
> Unless someone can tell me more about a dock, or Avant,  and sudo apt-get install avant-window manager didn't work either. Perhaps it isn't available for Hardy Heron?

HI and avant is in the repos, you can search synaptic manager.
You may need to add some reops
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
Just for grins
[http://vids.myspace.com/index.cfm?fuseaction=vids.individual&VideoID=32891366](http://vids.myspace.com/index.cfm?fuseaction=vids.individual&VideoID=32891366)

---

### Post by Joeb454 on 2008-04-24
Yes Avant should be in the repositories :) There is also Kiba-Dock, though last time I check this wasn't in the repositories, and I had to compile it from source :p

---

### Post by elmer_42 on 2008-04-24
Hm. I thought it was in the repos now. I guess it isn't. I believe [this]("http://www.ubuntugeek.com/howto-install-avant-window-navgator-in-ubuntu-gutsy-gibbon.html") is the guide I followed to get it running in Gutsy. It should also work in Hardy.

---

### Post by otrojake on 2008-04-24
The correct code to install avant is:

```
sudo apt-get install avant-window-navigator
```

---

### Post by bgast1 on 2008-04-24
I have dock, now is there a tutorial on how to use it or set it up? (A really really simple one)

---

### Post by otrojake on 2008-04-24
There's some other packages you're going to want to download if they're not already.

```
sudo apt-get install awn-core-applets awn-manager
```

After you run that, the settings for Awn are in System-->Preferences-->Awn Manager.  Just mess around with it a bit.  It's not too difficult to figure it out.

---

### Post by bgast1 on 2008-04-24
It told me that it couldn't find awn-core-applets.

---

### Post by Joeb454 on 2008-04-24
Go to System>Administration>Software Sources and make sure all the repositories are enabled, except for source code and CD :) Then ```
sudo aptitude update
``` and try again :)

---

### Post by elmer_42 on 2008-04-24
If he is using apt-get, will aptitude update work like apt-get update does?

---

### Post by Joeb454 on 2008-04-24
Yes it will, aptitude resolves dependencies a little better than apt-get does in my experience.

Plus if you use tab complete, it makes no difference to type it either :)

---

### Post by bgast1 on 2008-04-24
Hmmmm. Still couln't find it.

```
Reading package lists... Done
bob@bob-desktop:~$ sudo apt-get install awn-core-applets awn-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package awn-core-applets
bob@bob-desktop:~$ 


```

---

### Post by otrojake on 2008-04-24
Shoot, man.  That's my bad.  Ubuntu doesn't have the applets in their repositories by default.  I'm using other repositories that are a little bit more cutting edge, but also a little bit more unstable.  You'll want the awn-manager package (you can't get the applets one by default).  So just do this

```
sudo apt-get install awn-manager
```

Sorry about that.  The fingers were going faster than my mind. ;)

---

### Post by bgast1 on 2008-04-24
Here's the return that I got. 

```
bob@bob-desktop:~$ sudo apt-get install awn-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
awn-manager is already the newest version.
awn-manager set to manually installed.
The following packages were automatically installed and are no longer required:
  libmono-zeroconf1.0-cil libtagc0 libmono-cairo2.0-cil libtaglib2.0-cil
  libboo2.0-cil libkarma0 libavahi1.0-cil
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bob@bob-desktop:~$ 

```

I can sometimes figure things out pretty well, but then other times it's almost walking me through it like I have to do with my 11 month old grand daughter.

---

### Post by otrojake on 2008-04-24
Alright.  You're good to go then.  Go to System-->Preferences-->Awn Manager and fiddle away!:)

---

### Post by Perfect Storm on 2008-04-25
Awn is nice and all (and easy to install), but if you're looking for something more powerfull and tweakable you should try Kiba dock.

---

### Post by bgast1 on 2008-04-25
I'd like to try Kiba Dock. How do I get it? How do I install it?

---

### Post by Perfect Storm on 2008-04-25
You install it from source - [http://ubuntuforums.org/showthread.php?t=554127&highlight=kiba+dock](http://ubuntuforums.org/showthread.php?t=554127&highlight=kiba+dock)

---

