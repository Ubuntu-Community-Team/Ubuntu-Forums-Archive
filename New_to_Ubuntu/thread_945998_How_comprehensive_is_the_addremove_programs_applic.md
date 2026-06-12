---
title: "How comprehensive is the add/remove programs application?"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by a_weasel on 2008-10-12
I've been going through it, and it seems like theres a LOT of programs. Are there others hiding on the internet waiting for me to find, or do the programs found in the add/remove programs thing constitute most of what people use?

also, if you happen to know, what program would i use to import songs from my ipod to my computer?

also also, how good is the wine windows emulator? i tried it on starsiege: tribes (of all things!) and it worked. like, I had planned to install XP so I could do windows things, but if wine pretty much always works i guess theres no point...

---

### Post by Jackelope on 2008-10-12
Most everything you need is in the repos, yes. But now and then you'll find a newer program that's not. The versions in the repos are also a little older than the current one, but tested and stable.

Rhythmbox should work fine for ipod imports from what I hear. You should have it already...its the default music player.

Wine is alpha software, still in heavy development. While it works great with more popular apps, some others run weird or not at all. But if you can ditch windows for wine and it works with all your programs, go for it!

By the way, usually only one question should be posted per thread...it gets you a faster response if everything's divided up accurately.

---

### Post by nateperson on 2008-10-12
The add/remove is pretty encompassing...  Debian (and by that Ubuntu) have pretty strict requirements for getting into an official repository... That being said, there are many other repositories, that are not included by default, such as medibunutu.org where I have find just about whatever I wanted that wasn't included by default.  > sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list  should get it added.

---

### Post by namegame on 2008-10-12
I would like to add that not *all* programs you might need are in the repositories. For example, the version of VirtualBox that is in the repositories is a bit buggy for me. I just download the newest one from their website.

There are other ways to install programs other than add/remove programs or synaptic.

In Ubuntu, some .deb packages are actually installers. You can find examples here: [http://www.getdeb.net](http://www.getdeb.net)

---

### Post by pytheas22 on 2008-10-12
> 
also, if you happen to know, what program would i use to import songs from my ipod to my computer?

gtkpod can do that.  It's in the repositories, of course.

wine works pretty well these days for most applications, but it's far from perfect.  You can take a look at the [wine database]("http://appdb.winehq.org/") to look up how well the programs that you need work in wine (also keep in mind that for most programs, you can find free equivalents that run natively on Linux).

You may want to create a Windows virtual machine inside Ubuntu instead of dual-booting; it's a lot more convenient because it doesn't require you to reboot the computer in order to run Windows applications.  The only major downside is that you can't use hardware acceleration inside your virtual machine, meaning that 3D games won't work.  Older games and everything else will work flawlessly, though.  [Here]("http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/")'s a quick guide to installing Windows inside Ubuntu using Virtual Box.  It may be a bit outdated, but you can find plenty of other documentation online if you search.

---

