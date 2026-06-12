---
title: "Monodevelop ignoring Breakpoints"
date: 2009-07-11
forum: Programming Talk
---

### Post by doas777 on 2009-07-11
hello all,

I've installed monodevelop from the repos, and written a little test code. when i went to debug it, i set a breakpoint, and clicked the "Debug" button. the application ignored the breakpoints, and ran through to exit.

is there anything I need to do specifically for ubuntu to get step through working?

Thanks!

---

### Post by doas777 on 2009-07-11
well, I got it working by fully purging it, and reinstalling with synaptic, so i could make sure to get all the expansions. got some debugging love.

now I just need to figure out why xmlNode.childnodes is always null, even though there are children. if it's not one thing, it's another.

---

### Post by itsols on 2010-03-05
> **doas777 said:**
> well, I got it working by fully purging it, and reinstalling with synaptic... 

I have the same problem... I tried reinstalling but nothing seems to have changed.

What do you mean by 'purging'?

---

### Post by doas777 on 2010-03-05
> **itsols said:**
> I have the same problem... I tried reinstalling but nothing seems to have changed.

What do you mean by 'purging'?

there are two options for removing a program from apt or synaptic: "remove" and "purge".
removing just gets rid of the executables and global configuration, but leaves any config files in your ~/. purging removes the executables and all known config files. 
I don;t think a purge really made a big differance over removing in my case, but I did it just to be sure. I think I was missing a few optional packages. go though synaptic, and make sure you have all the mono-develop debug packages installed.

---

### Post by itsols on 2010-03-05
Thank you doas777 for your quick response.

I do all, if not most of my install/removals from synaptic. I find myself a newbie on Ubuntu despite it being my default OS for some time now...

Where do we find 'purge' on synaptic? I only see options like reinstall, complete removal, etc., but not purge.

Perhaps I'm missing out on something... Pls advise.

---

### Post by doas777 on 2010-03-05
> **itsols said:**
> Thank you doas777 for your quick response.

I do all, if not most of my install/removals from synaptic. I find myself a newbie on Ubuntu despite it being my default OS for some time now...

Where do we find 'purge' on synaptic? I only see options like reinstall, complete removal, etc., but not purge.

Perhaps I'm missing out on something... Pls advise.

just right click on an app that is checked. you will see an option for "Mark for Complete Removal". 
in apt, it's 
```

sudo apt-get purge <package-nickname>

```

the next thing i would recomend if this doesn't work, is to pull down the latest version of monodevelop from novell instead of using the repos. the version in the repos is at least 6 months old at this point.

---

### Post by itsols on 2010-03-05
Thank you once again doas777...

Here's my problem:

1. I can't use monodev 2.x since I'm on Ubuntu 8.04 and I've seen a few threads that warn against installing the new MD on it.

2. I've done a complete removal and reinstalled monodev. Then the first time I opened a test solution, I DID SEE the break-point option & F9 option in the pop-up menu. But when I moved the mouse to the correct place where I needed to put the breakpoint, it was just gone! I can only assume this is a bug.

Finally, I want to thank you for all your time and effort and really appreciate trying to help out. And as far as monodev is concerned, I think I'll stop chasing.

Many thanks for your support!
Khalid

---

### Post by itsols on 2010-03-05
For the information of all those trying to enable beak-points on monodev using ubuntu 8.04...

I think this is a bug that we cannot enable break points. This is why:

When the cursor is in the code window, click on the left side of a statement (near the line number). You only get the toggle menus.

Now click first inside the error window on monodev and then click the mouse against the source code line in the code window. NOW YOU SHOULD GET THE TOGGLE MENU AS WELL. Unfortunately, they seem disabled.

So in short, I don't think break-points will ever work here in this version.

Happy computing anyway!

---

