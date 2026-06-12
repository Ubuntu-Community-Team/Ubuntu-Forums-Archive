---
title: "GNOME Classic (No effects) Details"
date: 2012-06-04
forum: New to Ubuntu
---

### Post by Shadius on 2012-06-04
Hey everybody! 

I'm using GNOME Classic (No effects) and I'm curious to know what exactly are those effects that aren't being used. Can anyone point me in the right direction? Maybe some documentation listing the effects or something. The more detailed the better and please try to keep it simple, beginner here! :) Thanks.

---

### Post by traditionalist on 2012-06-04
Some info;

[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

but there is tons of info about it on the net you have to do some searching and sort out what you need.

Just for info I installed this as well; 

```

  ***sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable***
  ***sudo apt-get update***
  ***sudo apt-get install cinnamon***



```

This works with all the stuff I wrote about on GNOME Classic.

here is a test to see if unity will ( theoretically at least ) run on your machine;

```
/usr/lib/nux/unity_support_test -p
```

This is what it tells me;

```

mike@mikepc:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   X.Org
OpenGL renderer string: Gallium 0.4 on AMD CYPRESS
OpenGL version string:  2.1 Mesa 8.1-devel

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
mike@mikepc:~$ 


```

---

### Post by Shadius on 2012-06-04
Hey traditionalist! Thanks for replying. I've been looking at that page for days trying to make sense of it. :lolflag: Getting confused with the naming like GNOME Panel, GNOME Classic, GNOME Fallback, so many GNOMES!!!! I originally had Unity but it was running slow on my computer so I switched to GNOME Classic (No effects). 

Here's my output:
```
shadius@shadius-5410US:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 (RV250 4966) x86/MMX/SSE TCL DRI2
OpenGL version string:  1.3 Mesa 8.0.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       no

Unity 3D supported:       no
shadius@shadius-5410US:~$ 

```
All I can understand from this is that I can't run Unity 3D. The rest is another language to me. Maybe you can clarify?

---

### Post by traditionalist on 2012-06-04
> **Shadius said:**
> ]All I can understand from this is that I can't run Unity 3D. The rest is another language to me. Maybe you can clarify?

I would judge from that that you can run more or less everything except UNITY 3D.  ( No great loss in my opinion) Some things are faster and stabler than others on various machines. The Cinnamon seems very good. Worth a try if you are having problems. It's a nice desktop, easy to use, fast and you can customise it easily, as I already described at length elsewhere.

---

### Post by Shadius on 2012-06-04
> **traditionalist said:**
> I would judge from that that you can run more or less everything except UNITY 3D.  ( No great loss in my opinion) Some things are faster and stabler than others on various machines. The Cinnamon seems very good. Worth a try if you are having problems. It's a nice desktop, easy to use, fast and you can customise it easily, as I already described at length elsewhere.

I'll definitely take a look at Cinnamon. Now, Cinnamon would be another Desktop Environment, right? I'm just trying to get the correct terms down.

---

### Post by traditionalist on 2012-06-04
> **Shadius said:**
> I'll definitely take a look at Cinnamon. Now, Cinnamon would be another Desktop Environment, right? I'm just trying to get the correct terms down.

Yes, it's a different desktop environment. Seems very fast and stable. All the customisations I have tried work on it, ( I am writing this on it) using Firefox.

---

### Post by Shadius on 2012-06-04
> **traditionalist said:**
> Yes, it's a different desktop environment. Seems very fast and stable. All the customisations I have tried work on it, ( I am writing this on it) using Firefox.

Great. I'll check it out.

---

### Post by traditionalist on 2012-06-04
It also all works on the GNOME desktop using the GNOME SHELL, I have tried it out quite extensively;

[[IMG]http://img99.imageshack.us/img99/6649/workspace1001.th.png[/IMG]](http://img99.imageshack.us/i/workspace1001.png/)

I don't know why people are saying this wont work, It works perfectly well.

---

### Post by traditionalist on 2012-06-04
This guy explains how to install themes on the GNOME desktop;

[http://techhamlet.com/forum/viewtopic.php?id=2](http://techhamlet.com/forum/viewtopic.php?id=2)

I don't need to do any of that. The steps I already described elsewhere work perfectly well.

I can only conclude that there is some deliberate obfuscation going on here. Not for the first time either.

However  that may be, I will take a step back from these forums. The  "Explanations" are more confusing than if I sort things out for myself,  apart from often being quite silly.

Bye..............

---

### Post by Shadius on 2012-06-17
Can anyone offer an answer to my question of what effects are not being used in GNOME Classic (No effects)? Basically, explaining the difference between GNOME Classic & GNOME Classic (No effects). Thank you.

---

### Post by vasa1 on 2012-06-17
> **Shadius said:**
> Can anyone offer an answer to my question of what effects are not being used in GNOME Classic (No effects)? Basically, explaining the difference between GNOME Classic & GNOME Classic (No effects). Thank you.

I have found it difficult to find answers to several questions pertaining to GNOME ... I've had better luck with Xfce.

---

### Post by Shadius on 2012-06-17
> **vasa1 said:**
> I have found it difficult to find answers to several questions pertaining to GNOME ... 

As have I. My search continues! ](*,)

---

### Post by vasa1 on 2012-06-17
> **Shadius said:**
> As have I. My search continues! ](*,)

BTW, do you have the option, at log in, to choose GNOME Classic (No Effects) = GCne, in short?

---

### Post by vasa1 on 2012-06-17
> **Shadius said:**
> Can anyone offer an answer to my question of what effects are not being used in GNOME Classic (No effects)? Basically, explaining the difference between GNOME Classic & GNOME Classic (No effects). Thank you.
Poking around, I get the impression that GCne is without compiz: no fancy effects but less chance of borking something.

---

### Post by Shadius on 2012-06-17
> **vasa1 said:**
> Poking around, I get the impression that GCne is without compiz: no fancy effects but less chance of borking something.

Nope, it just says "GNOME Classic (No effects)". I'm curious, in what scenario would it say "GCne"?

---

### Post by vasa1 on 2012-06-17
> **Shadius said:**
> Nope, it just says "GNOME Classic (No effects)". I'm curious, in what scenario would it say "GCne"?

I feel irritated typing out GNOME Classic (No effects). That's why I suggested using GCne here, not that it's a universally accepted abbreviation.
Anyway, since it _is_ an option for you, the best way to find out is to use it.

---

### Post by Shadius on 2012-06-17
> **vasa1 said:**
> I feel irritated typing out GNOME Classic (No effects). That's why I suggested using GCne here, not that it's a universally accepted abbreviation.
Anyway, since it _is_ an option for you, the best way to find out is to use it.

Ohhh :lolflag: Sorry, I misinterpreted GCne as an official name. I prefer to write things out, but now I know your terminology. I use GNOME Classic (No effects) as my default Desktop Environment and I have used the regular GNOME Classic trying to notice the differences between the two. I was looking for sort of a list of the effects not being used in GNOME Classic (No effects). Something with some details.

---

### Post by vasa1 on 2012-06-17
> **Shadius said:**
> Ohhh :lolflag: Sorry, I misinterpreted GCne as an official name. I prefer to write things out, but now I know your terminology. I use GNOME Classic (No effects) as my default Desktop Environment and I have used the regular GNOME Classic trying to notice the differences between the two. I was looking for sort of a list of the effects not being used in GNOME Classic (No effects). Something with some details.

So you don't notice any differences? Bit OT, but when I was switching between Unity 2D and 3D, I tried to get a list of functional differences compiled with *some* success: [http://ubuntuforums.org/showthread.php?t=1972916](http://ubuntuforums.org/showthread.php?t=1972916)   :D

---

### Post by Shadius on 2012-06-17
> **vasa1 said:**
> So you don't notice any differences? Bit OT, but when I was switching between Unity 2D and 3D, I tried to get a list of functional differences compiled with *some* success: [http://ubuntuforums.org/showthread.php?t=1972916](http://ubuntuforums.org/showthread.php?t=1972916)   :D

I notice *some* differences, but I want to know *exactly* what the differences are. I'm more concerned about the specifics and details. Compiz might be one of the things not being used in GNOME Classic (No effects).

---

### Post by vasa1 on 2012-06-17
I was going to suggest this: [http://gnomesupport.org/forums/](http://gnomesupport.org/forums/) but the last post is dated Jun 3, 2012 ;)

Here's an [oldish post]("http://jeremy.bicha.net/2011/09/11/getting-started-with-gnome-in-oneiric/") by one of Canonical's devs: other than "Choose GNOME Classic for a Compiz version or GNOME Classic (No Effects) for the plain Metacity version." I couldn't find much else.

I'm also taking the liberty to predict that finding formal documentation on older GNOMEs will get more difficult. It's not that documentation on the latest n greatest is well-documented either.

BTW, and if you don't mind, other than curiosity, is there any compelling reason for wanting to know the exact differences?

---

### Post by Shadius on 2012-06-17
> **vasa1 said:**
> I was going to suggest this: [http://gnomesupport.org/forums/](http://gnomesupport.org/forums/) but the last post is dated Jun 3, 2012 ;)

Here's an [oldish post]("http://jeremy.bicha.net/2011/09/11/getting-started-with-gnome-in-oneiric/") by one of Canonical's devs: other than "Choose GNOME Classic for a Compiz version or GNOME Classic (No Effects) for the plain Metacity version." I couldn't find much else.

I'm also taking the liberty to predict that finding formal documentation on older GNOMEs will get more difficult. It's not that documentation on the latest n greatest is well-documented either.

BTW, and if you don't mind, other than curiosity, is there any compelling reason for wanting to know the exact differences?

My reason for knowing the exact differences is that it would help me in understanding what is needed in a graphics card to be able to take advantage of everything Ubuntu has to offer. I intend to build a PC soon so I was curious to know about the resources that the effects would be using. At first, I was just curious about the differences. It's gotten to be a bit more refined now. Also, the differences would help me to know what exactly is being loaded for each Desktop Environment, and how well my current setup is handling the loads. It'd give me some type of direction to go in when I'm building my new PC. What to improve on. So far, your answers are guiding me in the right direction. Also, I'm also just a detail-oriented person. :D

---

### Post by vasa1 on 2012-06-17
> **Shadius said:**
> My reason for knowing the exact differences is that it would help me in understanding what is needed in a graphics card to be able to take advantage of everything Ubuntu has to offer. I intend to build a PC soon so I was curious to know about the resources that the effects would be using... Also, I'm also just a detail-oriented person. :D
But then aren't you just a bit concerned that GNOME Classic (no effects) is basically history? I'd have thought you'd want to understand the requirements of the **heaviest DE** rather than a light one if the intention is to be as future-proof as practically possible.

---

### Post by kansasnoob on 2012-06-17
The only real difference is that Classic uses the [Compiz]("http://en.wikipedia.org/wiki/Compiz") window manager, whereas Classic (no effects) uses [Metacity]("http://en.wikipedia.org/wiki/Metacity").

I've made some notes about classic (no effects) here:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

I've tried standard classic using Compiz just briefly and encountered one problem after another, and I've always preferred Metacity anyway, as far back as Gutsy.

---

### Post by kansasnoob on 2012-06-17
> **vasa1 said:**
> But then **aren't you just a bit concerned that GNOME Classic (no effects) is basically history**? I'd have thought you'd want to understand the requirements of the **heaviest DE** rather than a light one if the intention is to be as future-proof as practically possible.

Well it works in Precise which is supported for 5 whole years :)

And SolusOS is working on a development version of Gnome 3 using Metacity. Since both SolusOS and Ubuntu are based on Debian the code will exist so it's simply a matter of time and patience ;)

---

### Post by vasa1 on 2012-06-17
> **kansasnoob said:**
> Well it works in Precise which is supported for 5 whole years :)

And SolusOS is working on a development version of Gnome 3 using Metacity. Since both SolusOS and Ubuntu are based on Debian the code will exist so it's simply a matter of time and patience ;)

I was responding to this: "My reason for knowing the exact differences is that it would help me in understanding what is needed in a graphics card to be able to **take advantage of everything Ubuntu has to offer**."

---

### Post by kansasnoob on 2012-06-17
> **vasa1 said:**
> I was responding to this: "My reason for knowing the exact differences is that it would help me in understanding what is needed in a graphics card to be able to **take advantage of everything Ubuntu has to offer**."

My bad, I didn't read every post :oops:

I just thought to add a few things. If you notice no difference between booting a classic or classic (no effects) session your graphics card is likely forcing "gnome-fallback" which is classic (no effects). You can see by running:

```
echo $DESKTOP_SESSION
```

If it shows "gnome-fallback" then you're running Metacity, if it shows "gnome-classic" you're running Compiz.

Alternatively you can install the package 'wmctrl' and run:

```
wmctrl -m | grep "Name" | cut -c7-
```

That will definitively show which window manager is being used.

Also I'd think that the same command used to check for Unity 3-D compatibility would suffice to see if Compiz will run on your hardware:

```
/usr/lib/nux/unity_support_test -p
```

```
lance@lance-desktop:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945G x86/MMX/SSE2
OpenGL version string:  1.4 Mesa 8.0.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

```

Finally here's a Compiz video:

[http://www.youtube.com/watch?v=E4Fbk52Mk1w](http://www.youtube.com/watch?v=E4Fbk52Mk1w)

That's an older one but you can Google a gazillion of 'em :)

---

### Post by Shadius on 2012-06-18
Thank you kansasnoob. Just what I was looking for. Solved!

---

