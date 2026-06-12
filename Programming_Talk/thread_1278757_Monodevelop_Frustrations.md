---
title: "Monodevelop Frustrations"
date: 2009-09-29
forum: Programming Talk
---

### Post by mybluevan on 2009-09-29
I've been having a ton of problems trying to get the 2.0 version of Monodevelop in the repos to work right. I'm going to try and detail the problems and solutions here for poor future souls who are unfortunate enough to stumble upon these things. #-o

My first major problem was that I couldn't get the UI editor to work. It didn't even run when I compiled the empty GTK# project. It kept complaining about a missing gtk-sharp library in the GAC. So, I tried to go in and reinstall the the dll into the GAC. It still didn't recognize the library. I even tried removing everything under "mono" and "cli" in Synaptic. Nothing.

Then, Monodevelop wouldn't start. I guess all my efforts in trying to fix the GAC only made it worse. It was looking for the 2.12 version of gtk-sharp.dll. Well, it was in the GAC and reinstalling it didn't help either.

Finally, I took drastic measures:
[LIST=1]
[*]Removed everything under "mono" and "cli" in Synaptic (completely removed).
[*]Went into /usr/local and ran "find . | grep mono | xargs sudo rm" (run "find . | grep mono" first to make sure they're all mono related files).
[*]Went into /usr and ran "find . | grep mono" selectively deleting anything mono related.
[*]Proceeded to install monodevelop and dependencies fresh from the repo (along with any programs that bit the dust in the process, like gnome-do).
[/LIST]

This seemed to clear the issue up finally.

Until.....


For some reason, Monodevelop stopped letting me create projects. It was working fine earlier this afternoon for the first time since I started trying to use it. Then it suddenly stopped after creating a couple projects.

I noticed the little splash screen when you start Monodevelop hung around after it started. (it hides behind the window and I almost didn't see it.) It would hang after clicking forward on the second screen where it asks for misc project settings/addons like packaging, gtk#, etc. The source files were created, but the .csproj and .sln files were not. I also didn't see any errors when run from a terminal. There were 2 Monodevelop processes when I went to kill it in System Monitor. One looked normal and idled at 0 CPU, while the other was running at about %50 CPU and had some strange status that I don't remember.

I tried the steps from earlier and they didn't fix anything. ](*,) I started to write this post, asking for help when I decided to check in my home directory for configuration files. Bingo.

Here's how to COMPLETELY wipe out everything mono and start from SCRATCH:
[LIST=1]
[*]Follow steps 1-3 outlined above.
[*]Run "find . | grep mono" from / to find anything and everything mono related and then go delete it.
[*]I even went as far as to remove the cached mono install files in /var/cache/apt/archives
[*]BE SURE to remove the mono related directories from ~/.config/ (I think those were what was messing me up)
[*]Install monodevelop and dependencies fresh from the repo (along with any programs that bit the dust in the process, like gnome-do).
[/LIST]

Now I just hope Monodevelop will hold out long enough for me to get my homework done. [-o<

---

### Post by directhex on 2009-09-30
This comes up WAY more than it should.

In 99% of cases, problems are caused by the presence of Mono in /usr/local (i.e. self-compiled). The problem you describe would fit the description - there is one GAC per Mono install, so if MD is being executed with the "wrong" GAC, then it won't see libraries which were only installed into the packaged system GAC

---

### Post by mybluevan on 2009-09-30
That's what I thought was probably the case here. I vaguely recall trying to install a beta version or something similar about a year ago from the source available on the Mono website. Obviously though, my second issue was due to a bad configuration in the end. 

Still, it's nice to know how to completely wipe Mono off a system in case you run up against a problem that seems to defy all logic and debugging. It likes to hide little leftovers all over the system that could potentially mess up a reinstall. Very annoying for a beginner who thinks they just did a complete reinstall from Synaptic.

---

### Post by directhex on 2009-09-30
> **mybluevan said:**
> That's what I thought was probably the case here. I vaguely recall trying to install a beta version or something similar about a year ago from the source available on the Mono website. Obviously though, my second issue was due to a bad configuration in the end. 

Still, it's nice to know how to completely wipe Mono off a system in case you run up against a problem that seems to defy all logic and debugging. It likes to hide little leftovers all over the system that could potentially mess up a reinstall. Very annoying for a beginner who thinks they just did a complete reinstall from Synaptic.

Reinstalling from synaptic is usually enough. The problem is /usr/local - stuff in there is not packaged, not handled by synaptic, and a higher priority when executing commands on the command line

---

