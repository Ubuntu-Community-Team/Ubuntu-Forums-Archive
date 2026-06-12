---
title: "&quot;Ugly&quot; fonts?"
date: 2011-08-19
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ratcheer on 2011-08-19
I have a fairly vanilla installation of Oneiric AMD-64. I have noticed several places where ugly (to me) fonts are used. My top left panel title is shown that way and it pretty much ruins Google Earth. Am I missing something in my installation that would fix this?

Thanks,
Tim

---

### Post by Enigmapond on 2011-08-19
I'm not familiar with Oneiric. Does it NOT have an appearance preferences that you can customize all the fonts?

---

### Post by MacUntu on 2011-08-19
Known bug in Unity 2D (the title font one). Not sure about Google Earth as this doesn't run on my 64-bit system.

---

### Post by 3vi1 on 2011-08-19
> **ratcheer said:**
> I have a fairly vanilla installation of Oneiric AMD-64. I have noticed several places where ugly (to me) fonts are used. My top left panel title is shown that way and it pretty much ruins Google Earth. Am I missing something in my installation that would fix this?

Thanks,
Tim

None of my Oneiric test systems are showing the ugly fonts.  I don't know what's causing it, but it looks to be specific to your installation.

---

### Post by 3vi1 on 2011-08-19
> **MacUntu said:**
> Known bug in Unity 2D (the title font one).

Ahhh... that explains why I wasn't seeing the problem.  I'm using the normal Unity.

---

### Post by ratcheer on 2011-08-19
> **MacUntu said:**
> Known bug in Unity 2D (the title font one). Not sure about Google Earth at this doesn't run on my 64-bit system.

Thank you. I will just wait, then, and hope future updates straighten it out.

Tim

---

### Post by ratcheer on 2011-08-19
New info:

I installed lots of Ubuntu updates, this afternoon. The title font in the top panel is now normal. But the application font being used by Google Earth is still horrible. No other apps seem to be affected. And I cannot find any option in Google Earth to change the font it uses.

I will try to find out if there is any info in Google Help.

Tim

---

### Post by ratcheer on 2011-08-19
Problem solved. Solution (from Google Earth Support pages) was to install Microsoft Truetype fonts (package ttf-mscorefonts-installer), which included having to agree with the Microsoft license. I never had to do that before, though.

Tim

---

### Post by cariboo on 2011-08-19
Obviously you never installed the ubuntu-restricted-extras meta package, the mscorefonts are installed as part of the process, and you always have to agree to the eula before the fonts will be installed.

---

### Post by ratcheer on 2011-08-19
> **cariboo907 said:**
> Obviously you never installed the ubuntu-restricted-extras meta package, the mscorefonts are installed as part of the process, and you always have to agree to the eula before the fonts will be installed.

You are right, I hate that package ("hate" is too strong a word, but it is more than just "dislike"). You need one little feature and it installs 300 different things.

Thanks,
Tim

---

### Post by lucazade on 2011-08-20
[https://bugs.launchpad.net/unity-2d/+bug/820274](https://bugs.launchpad.net/unity-2d/+bug/820274)

---

### Post by VinDSL on 2011-08-20
> **cariboo907 said:**
> Obviously you never installed the ubuntu-restricted-extras meta package, the mscorefonts are installed as part of the process, and you always have to agree to the eula before the fonts will be installed.

> **ratcheer said:**
> You are right, I hate that package ("hate" is too strong a word, but it is more than just "dislike"). You need one little feature and it installs 300 different things.
I love the ubuntu-restricted-extras meta package, but h-a-t-e the mscorefonts!

In the old days, I would install the package, then delete the fonts.

Now, I install the package, but DO NOT agree to the EULA, e.g. the butt fugly mscorefonts won't infect my system.  LoL!

---

### Post by ratcheer on 2011-08-20
> **VinDSL said:**
> ... the butt fugly mscorefonts won't infect my system. LoL!
 
If you think those are ugly, look at the Google Earth screen shot in post #1. They were all but unreadable.
 
Tim

---

