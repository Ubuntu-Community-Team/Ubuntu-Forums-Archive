---
title: "looking for advice on Arch Linux and LXDE"
date: 2008-08-19
forum: Other OS Talk
---

### Post by estyles on 2008-08-19
I am considering trying out Arch Linux, already downloaded the .iso via torrent and am seeding the torrent all day today while I'm at work, so I won't feel bad if I can't get a torrent client up right away in Arch.  Anyway, I was looking for some advice and answers to a couple of questions.

I'm currently running Linux Mint, and I really like it, but I have a few minor issues and I always like to try something new.   So far, I've tried Puppy (I don't really like it, but for what I use it for, speed and size are more important than usability), OpenSUSE (just couldn't get used to the way they did some things, though to be fair, I installed with KDE 4, so that might be a big part of the problem), Mandriva (I kinda liked it - hardware support was great, but I just couldn't see using it over Mint/Ubuntu), gOS (just terrible, IMHO), and OpenGEU (I liked it when I ran in a VM, but couldn't get it to install for me on my actual machine).

I like the idea of installing my system from scratch and determining what I want included and what I don't.  I don't mind editing config files or using the commandline, but I don't want to have to do *everything* from a commandline.  I prefer the GUI for most tasks, mainly because it presents *options*, editing a config file with no idea of the allowed options sucks, as does the possibility of a typo causing hours of frustration because I don't know what the problem is.  Are there a lot of GUI tools available in the user repositories, or should I just resign  myself to doing most things via CLI and config files?

Is it possible to install .rpm (and possibly .deb) packages, maybe through use of Alien, or a tool like it?  I have at least one program that is only available in .rpm - it installed fine in Mint via Alien...  I would hate to lose it, but I'm pretty sure I could compile it from source if I can get the dependencies worked out.

I'm leaning towards LXDE as my desktop environment - it looks pretty nice.  However, I really do like Gnome - it seems very intuitive to me.  And when I installed LXDE as a separate session on Mint, it ran pretty slow (opening my home folder, frex, takes about 1/4 second on Gnome and about 2 seconds on LXDE - other tasks were similarly slow).  Is that normal, or maybe just a known issue on Ubuntu?  Or possibly a conflict with Gnome?  Also, from anyone that knows LXDE well, am I going to find it too different from Gnome to get by?  I feel it's a dilemma because I already know what I like, but I also want to try something different. Also, does Compiz work with LXDE?  (I can look this up, but if someone has a quick answer...)


Any other advice or opinions on Arch?

---

### Post by smartboyathome on 2008-08-19
> **estyles said:**
> Are there a lot of GUI tools available in the user repositories, or should I just resign  myself to doing most things via CLI and config files?

I would say that if you are going to use Arch, you better get used to config files and the terminal, as that is what the Arch wiki uses in order to remain as desktop independant as possible. There are many programs which configure stuff for you though, so if you find stuff you like you are free to use it.

> **estyles said:**
> Is it possible to install .rpm (and possibly .deb) packages, maybe through use of Alien, or a tool like it?  I have at least one program that is only available in .rpm - it installed fine in Mint via Alien...  I would hate to lose it, but I'm pretty sure I could compile it from source if I can get the dependencies worked out.

Its not possible to install RPMs, but DEBs have some help with deb2targz (you have to find all the dependancies still, but it converts the package into a tar.gz package with stuff in /usr, /etc, ...). Honestly, though, you won't really need either, as you can install stuff with yaourt (see the arch wiki) from the "unsupported" AUR repository (see the Arch site :p). If it isn't available as an AUR package, you can always request it or whip it up yourself, it isn't that hard once you learn how. :)

> **estyles said:**
> I'm leaning towards LXDE as my desktop environment - it looks pretty nice.  However, I really do like Gnome - it seems very intuitive to me.  And when I installed LXDE as a separate session on Mint, it ran pretty slow (opening my home folder, frex, takes about 1/4 second on Gnome and about 2 seconds on LXDE - other tasks were similarly slow).  Is that normal, or maybe just a known issue on Ubuntu?  Or possibly a conflict with Gnome?  Also, from anyone that knows LXDE well, am I going to find it too different from Gnome to get by?  I feel it's a dilemma because I already know what I like, but I also want to try something different. Also, does Compiz work with LXDE?  (I can look this up, but if someone has a quick answer...)

I would say try more than LXDE (which isn't fully packaged under Arch yet). I use E17, and it has a similar layout. All the packages you will need are in community, so you will be able to use it out of the box. But you can't use Compiz with E17 unless you install ecomorph (in unsupported, which doesn't always compile), unlike LXDE (which is a desktop environment, E17's a Window Manager + extra). Honestly, though, E17 provides enough eye candy for me without Compiz (and no, it isn't fluxbox/openbox-like eye-candy, it is better ;)). If you are looking more for speed, though, don't use Compiz, it is what will really bog down LXDE (or anything, really).


> **estyles said:**
> Any other advice or opinions on Arch?

Use the beginners guide when you are installing Arch. It is available on the livecd under /arch, use ls to see the files and find it. Open it in nano (imo, the easiest terminal editor of all of them, but not as feature rich as others either) and follow it step-by-step as you work through the install on another tty console (control-alt-f1/f2/... are tty consoles). If you follow the beginners guide, you won't make a mistake on the install (except with partitioning, which I recommend using another disk for, like the GParted livecd, ,as at least for me, Arch's cfdisk doesn't work for partitioning, and when it does, it doesn't move partitions).

---

### Post by estyles on 2008-08-19
> **smartboyathome said:**
> Use the beginners guide when you are installing Arch.

Yeah, I've already printed it out for easy reference, although some things are linked from the wiki page, which means it just prints the link.  But I think I have all the info needed to install and get ethernet working so I can lookup other stuff on the web as needed.

> Open it in nano (imo, the easiest terminal editor of all of them, but not as feature rich as others either)

Yeah, I definitely prefer nano, because I'm used to pine from when I was in college.  I really can't deal with vi.  I learned it once, didn't really like it then, and have since forgotten everything I learned.  I know people love vi, I can even sort of see why, but I just hate it with a passion.

> partitioning, which I recommend using another disk for, like the GParted livecd, ,as at least for me, Arch's cfdisk doesn't work for partitioning, and when it does, it doesn't move partitions).

Thanks, but I have no worries in that regard.


As for your other answers, not entirely the answers I "wanted to hear", but very much appreciated.  Thank you.  Even knowing that I'll have to edit config files for most setup, which is something I suspected anyway, I'm definitely ready to give Arch a try.  I'm not an expert by any means, but I think I'm far enough into the "intermediate" user range that I think I can do it.  You'll understand when I say that the prospect of installing Arch is a little bit daunting...

The program I want from an .rpm is a V:TES CCG deckbuilder, so it's not going to be in the repositories - that's for certain.  It's too bad there isn't an alien-like tool.  Although alien is available in a .deb, so I wonder what the chances are that I could install it and then try to install the .rpm...  May not work, but I guess it's something to consider trying.  Will probably try building from source first.

I've tried E17 a little bit, and even though I completely hate the dock, I do like a lot of things about it.  The reasons I want Compiz are for the cube (gotta love the cube, and it's funny to have a full screen VM of WinXP on one cube side - though obviously not completely necessary), some of the useful window-switchers, and for a transparent desktop terminal.  I currently have a transparent terminal using devilspie (because I had problems with using compiz for it - which I've sinced resolved), but I'm not sure devilspie is available for arch, and even if it is, if I'm planning on using compiz, it's an added benefit to not have to throw another daemon on the pile.

So for right now, I guess it's a tossup between E17 (no Compiz), LXDE (not fully implemented, from what you're saying), and Gnome (same old same old, and a little bit heavy).  I might also try XFCE, although I have 0 experience with it at all.

---

### Post by smartboyathome on 2008-08-19
If you can find the source for that program, don't bother tryign to use the RPM. It will be a huge mess. You might be surprised how much stuff arch actually has, even if it is not officially packaged. If it isn't available, ask on the forums for someone to make an AUR for you, the community is really friendly.

About LXDE, it doesn't have every single part of it on Arch's repos yet, which is what I am saying. So you won't be able to fully use it like on Ubuntu (since the developer supports Ubuntu, not Arch). You can always install it and try it though, see if it works for you. :)

E17's "dock" can be easily customized. I have my E17 layed out in a windows-like style (see [here]("http://bbs.archlinux.org/viewtopic.php?pid=397843#p397843") for an older version of my desktop, which has the same layout). You can try Ecomorph from AUR and see if that works for you. Or you can try all the window managers/desktop environments you want and see which one fits you best.

---

### Post by mips on 2008-08-20
[http://lxde.org/wiki/ArchLinux](http://lxde.org/wiki/ArchLinux)

> Most of the latest LXDE packages are already in community repo of ArchLinux and maintained by trusted users. The rest might be found in AUR. **(The compability of LXDE and ArchLinux is guaranteed since the lead developer of this project is using Arch.) **
Please add community repo to your /etc/pacman.conf. If you have problems, read the [ArchWiki]("http://wiki.archlinux.org/index.php/Pacman"). There are nice articles for pacman. After adding community repository, execute the following commands with root access. 


---

### Post by mips on 2008-08-20
I'm actually very keen to try out LXDE as it looks nice.

EDIT: Very easy & small (about 7MB) to install over here. Actually damn nice. Obviously uses a bit more resources than say Openbox but on the other hand you have simplicity (in setting up) and a bit more usabilty if you want to call it that.

---

### Post by MisfitI38 on 2008-08-20
I am not currently using LXDE, but I am a strong supporter; I think it's a great way to get a quick OB system setup very expediently.

You can use ABS and makepkg to easily make an installable pkg.tar.gz for anything you need, as long as you can get the sources.

---

