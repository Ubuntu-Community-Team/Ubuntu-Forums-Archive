---
title: "Monodevelop doesn't compile files"
date: 2005-05-17
forum: Programming Talk
---

### Post by mostwanted on 2005-05-17
The compile and the run options in Monodevelop don't work. I've just installed the packages from hoary and commandline compiling works. Do I need to set up a classpath or something perhaps?

---

### Post by Sniffer on 2005-05-20
[QUOTE=mostwanted]The compile and the run options in Monodevelop don't work. I've just installed the packages from hoary and commandline compiling works. Do I need to set up a classpath or something perhaps?[/QUOTE]


I have the same problem, manually i compile with the mcs something.cs...but when using monodevelop the output is nothing...so no exe file....

I believe that monodevelop still have a good road to take, is buggy..and eclipse maybe it's a better solution by now.

---

### Post by mostwanted on 2005-05-20
Okay, it seems you can compile files in projects, at least it gets some response (outputs "compiling filename etc") but no compiled files appear anywhere. The "fake" compiling never ends.

Too bad I guess :( Monodevelop seemed like a nice IDE for Mono development.

---

### Post by jhill on 2005-05-22
[QUOTE=Sniffer]I have the same problem, manually i compile with the mcs something.cs...but when using monodevelop the output is nothing...so no exe file....

I believe that monodevelop still have a good road to take, is buggy..and eclipse maybe it's a better solution by now.[/QUOTE]

Monodevelop is really far out of date.  Monodevelop 0.5.1 is what's in the repos, but 0.7 just came out (and I believe it is in breezy already...)

---

### Post by tread on 2005-05-22
I think I had trouble compiling single source files, but when I made a project it seemed to work fine.

---

### Post by Sniffer on 2005-05-22
[QUOTE=jhill]Monodevelop is really far out of date.  Monodevelop 0.5.1 is what's in the repos, but 0.7 just came out (and I believe it is in breezy already...)[/QUOTE]

Do you have it installed in hoary without problems??

Thks 
Sniff.

---

### Post by rlcoach on 2005-05-23
[QUOTE=mostwanted]The compile and the run options in Monodevelop don't work. I've just installed the packages from hoary and commandline compiling works. Do I need to set up a classpath or something perhaps?[/QUOTE]

I have the very same problem, anybody any ideas :(.

---

### Post by Sniffer on 2005-05-24
[QUOTE=rlcoach]I have the very same problem, anybody any ideas :(.[/QUOTE]


By the suggestion above (i didn't test it yet) if you add Breeze Reposit. to your sources list, you should be able to install a recent version of mono and monodevelop...If you will try comment your results.

---

### Post by jaboo on 2005-05-24
[QUOTE=Sniffer]I have the same problem, manually i compile with the mcs something.cs...but when using monodevelop the output is nothing...so no exe file....

I believe that monodevelop still have a good road to take, is buggy..and eclipse maybe it's a better solution by now.[/QUOTE]

Actually, I do not think the problem with with mono or monodevelop. I have compiled the source packages for mono, all of the various sharps, and monodevelop. The result was a working installation of mono with a monodevelop that worked as one would expect. I think the ubuntu packages either did something wrong when packaging or when compiling the sources. It really is too bad as mono really is a great ooption for a dev platform. They really should pay attention to mono for the breezy release. By the time of the official release of breezy, mono 1.2 final should be available.

---

### Post by Sniffer on 2005-05-25
[QUOTE=jaboo]Actually, I do not think the problem with with mono or monodevelop. I have compiled the source packages for mono, all of the various sharps, and monodevelop. The result was a working installation of mono with a monodevelop that worked as one would expect. I think the ubuntu packages either did something wrong when packaging or when compiling the sources. It really is too bad as mono really is a great ooption for a dev platform. They really should pay attention to mono for the breezy release. By the time of the official release of breezy, mono 1.2 final should be available.[/QUOTE]

That could be, i had the same problem when installin mplayer from packages and only when i install it from the source i could have a very functional video player.

Yep monodevelop package could be broken.....but in relation of tracking your apps is always good to install by packages..at least it's easy.

I will try the breezy package and if fails here i go :/configure && make && make install

Sniff.

---

### Post by jaboo on 2005-05-25
[QUOTE=Sniffer]That could be, i had the same problem when installin mplayer from packages and only when i install it from the source i could have a very functional video player.

Yep monodevelop package could be broken.....but in relation of tracking your apps is always good to install by packages..at least it's easy.

I will try the breezy package and if fails here i go :/configure && make && make install

Sniff.[/QUOTE]

I was wanting to do the same thing you suggest; a dist-upgrade to breezy. However, when I did it this past weekend, I found that my system was totally trashed and had to do a reinstall. I then read in these forums that Breezy is going to be broken for a few weeks due to C++ migration for the new gcc (at least I think that was the reason given). So, you might want to hold off on a complete upgrade.

---

### Post by ponchorage on 2005-05-25
[QUOTE=jaboo]Actually, I do not think the problem with with mono or monodevelop. I have compiled the source packages for mono, all of the various sharps, and monodevelop. The result was a working installation of mono with a monodevelop that worked as one would expect. I think the ubuntu packages either did something wrong when packaging or when compiling the sources. It really is too bad as mono really is a great ooption for a dev platform. They really should pay attention to mono for the breezy release. By the time of the official release of breezy, mono 1.2 final should be available.[/QUOTE]

jaboo, could you or somebody else please possibly write up a small step-by-step tutorial of how to get a working installation of mono and monodevelop?

I tried following the directions on the monodevelop site, but kept running into dependency problems. I would really like to get monodevelop working on Ubuntu and it sounds like there are quite a few others here that are with me.

Any help would be greatly appreciated, I'm sure.

---

### Post by Zingam on 2005-05-30
install the latest package from mono-project.com it contains mono and it works for me.

---

### Post by ponchorage on 2005-05-30
[QUOTE=Zingam]install the latest package from mono-project.com it contains mono and it works for me.[/QUOTE]

Does monodevelop work for you? I think that is where the problem lies.

---

### Post by Zingam on 2005-05-31
[QUOTE=ponchorage]Does monodevelop work for you? I think that is where the problem lies.[/QUOTE]
 Yes it does. It does not work without problems but it works. Sometimes it crashes. Sometimes it requires a reboot because it doesn't start but generally it works.

---

### Post by ponchorage on 2005-05-31
How did you overcome the issue of the GUI never actually compiling? I, like the others that have posted here, can compile from the shell, but the GUI just sits there and never compiles anything.

---

