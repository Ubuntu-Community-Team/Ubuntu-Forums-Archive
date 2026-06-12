---
title: "Guide on Terminal"
date: 2014-05-30
forum: New to Ubuntu
---

### Post by majk2 on 2014-05-30
I recently dumped Windows off my laptop and installed Ubuntu. I was just getting irritated with the notice interruptions and unsolicited software and spam on Windows. So I can repport after a few weeks I am just loving the freshness and direct functionality of Ubuntu.

I am even coming to grips with the need to use Terminal, while  not entirely sure why a GUI method of doing tweaks has not yet been created for Ubuntu. I am sure that the uptake of Ubuntu would be so much more widespread if a GUI system was available. I suppose it has something to do with there being more exceptions than rules as far as Linux software goes and I suppose this is the price you pay for so much Freedom and Free stuff.

Anyway, as I said I am not personally frightened of the Terminal, just a little cautious. I realise that most posts with solutions are helpful and copying and pasting their terminal command tips and helps into terminal and executing these commands are generally helpful or harmless. But I also realise that you can do great harm and open yourself up to big breaches in security if you trustingly just execute some strangers posted commands.

So I guess my question is, is there some sort of help-file or guide to help understand what commands are safe and which to stay away from or at least double check with another source before using?

---

### Post by whitesmith on 2014-05-30
Check out the second reference in my sig line. There is a "GUI method of doing tweaks" for Ubuntu, it's just that the CLI can do much more, much quicker, much easier. Read reference #1 while you're at it, please! You'll thank me later.

---

### Post by TheFu on 2014-05-30
Read the man page for every command, learn to understand what each option does and have a complete understanding of file/directory permissions.

To get started, **man man** to learn about the manpages.  Pretty much every command on Linux/UNIX has a manpage.  The ssh, sudoers and fstab manpages are especially good, BTW.  I learn something new every time and I've been doing Linux since 1993.

---

### Post by Impavidus on 2014-05-30
A place to start: [https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

Most commands you see here are only diagnostic tools. They are meant to pinpoint the problem, but don't do anything to your system. Most other commands are safe too, at least in the context for which they were given. Of course there are exceptions, so always try to understand the commands before you run them. The man pages are a good way to find out.

Most things can be done through the GUI, but we prefer the command line because the command line is the same in all flavours of Ubuntu and because it's easier to give instructions that way.

Sometimes some options, accessible from the command line or via config files, are left out of the GUI to simplify the GUI. This is to make things easier for beginners, provided they're not interested in those options anyway. Some proprietary systems, with everything accessible from the GUI, may have less options to begin with. Also, underneath Linux is based on the command line, the GUI is a layer on top of that. Therefore the GUI can never provide options not accessible through the command line, but the reverse is possible. When development of the GUI lags a bit, functionality can already be made available through the command line.

If Ubuntu wants to have a market share comparable to Windows it has to become more like Windows. More dumbed down. The day when that happens will be the day when I leave for some other Linux distro.

---

### Post by slickymaster on 2014-05-30
Another good place to start: [http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

---

### Post by Rob Sayer on 2014-05-30
You're right to be concerned about making your system less safe or stable.  But I wouldn't be so concerned about CLI in general, more the quality of information.

It'd probably be a good idea to stick mostly to this forum or askubuntu for now.  Askubuntu is particularly good because it has user reputation based on votes.  On this forum it's tempting for newbies to judge users by the # of posts/beans.

Don't.  I've seen users with 1500 or more beans who IMO don't really know what they're talking about.  And I've seen ones with 10 who are clearly experts.

That said, I don't want to scare you re. ubuntu support.  It's the best there is.  There's support out there that you *pay* for that isn't as good.

Of more concern IMO is that newbies tend to load up on programs that aren't in the official ubuntu repos.  This is a bad idea if you don't know what you're doing.  At first you should stick to the tested programs from the repos.

---

### Post by bapoumba on 2014-05-30
Sometimes, I prefer to read man pages from a web page. Always check what a command does, and the appropriate syntax before using it, even if someone gives the whole command tht you just need to copy/paste. Ubuntu has a dedicated resource as pointed out.
I also use these ones :
[http://manpages.ubuntu.com/manpages/trusty/](http://manpages.ubuntu.com/manpages/trusty/) < you get the man pages for each release, you can choose it at the top of the page.
[http://linux.die.net/man/](http://linux.die.net/man/) < a general Linux one, my favorite from the old days, but it can differ now from Ubuntu setups.

---

### Post by whitesmith on 2014-05-30
> **Impavidus said:**
> If Ubuntu wants to have a market share comparable to Windows it has to become more like Windows. More dumbed down. The day when that happens will be the day when I leave for some other Linux distro.Mark Shuttleworth is quoted somewhere as saying--this is not verbatim, but close--that Problem One with Ubuntu is becoming king of the desktop. We both seem to disagree. Drive down any highway in the USA. You will find more Fords than Bugattis by a wide margin, but most people would rather drive  Bugattis, if only they could afford to. Pursuing market share with any FOSS product is utterly pointless. Quality is the only determinant. I, too, am waiting for pressure gauges to be replaced by idiot lights. When they appear I will be gone as well.

---

### Post by TheFu on 2014-05-30
> **whitesmith said:**
>  I, too, am waiting for pressure gauges to be replaced by idiot lights. When they appear I will be gone as well.

For the first 6 months I was learning UNIX, the first question that my peers asked was if I'd RTFM'd already. If I didn't say yes (and showed it was true), they'd send me away to RTFM.  It sucked. I remember it, but it taught me how to read AND understand manpages.  

In the beginning, the hardest part is asking questions that get good answers. Start with **whatis**, then use **apropos**, then **man** - ask each the same question and see where it leads.  This is google from before google (or altavista) existed.

I've left the stock Ubuntu GUI since 11.04 when Unity was made default. Load up "server", then add the UI you like whatever that may be. This keeps the bloat down AND the tracking that was introduced in 13.xx out.  There are still many things to like about Ubuntu, especially the LTS releases. I haven't found any other distro that does it as well.

I don't use many GUIs to manage configurations.  Point-n-click is too slow and hard to reproduce later.  By managing the config files directly, things can be automated easily. This is my preferred way to handle this stuff.  OTOH, I'm not managing 1 machine - more like 30 and most of those do not have any GUI.  Getting a GUI back exactly the way it was is relatively easy when moving from 1 box to another, it just takes knowing where the config files are stored and replicating those items on the new machine.

Honestly, I don't want Linux to be as popular as Windows. That will convert most well-paying Linux jobs into "desktop support" jobs for 80% less money.

---

### Post by Habitual on 2014-05-30
[ATTENTION ALL USERS: Malicious Commands]("http://ubuntuforums.org/announcement.php?f=326")

---

### Post by majk2 on 2014-06-13
Well thanks guys you have all jumped in and given some valuable information. 

Yes I do understand how being able to use terminal gives so much more tweaking ability as I am a web developer and while I do use CMS packages like Joomla I find I get my best work done under the bonnet using PHP. I love the Gauges and warning lights analogy buy the way.
Anyway thanks for all the input much appreciated guys.

---

### Post by TheFu on 2014-06-13
> **majk2 said:**
> Well thanks guys you have all jumped in and given some valuable information. 

Yes I do understand how being able to use terminal gives so much more tweaking ability as I am a web developer and while I do use CMS packages like Joomla I find I get my best work done under the bonnet using PHP. I love the Gauges and warning lights analogy buy the way.
Anyway thanks for all the input much appreciated guys.

You realize that "terminal" is just a program. There are many, many different terminals - some are fancy, sucking RAM and CPU, others are lighter but don't support every characterset.  I prefer the old-school xterm, but many people like rxvt, lxterms, gnome-terminal. Don't forget about all the lovers of running a shell from emacs or using screen to keep them alive and being able to reconnect from a different terminal session later.  I think what you really want to learn is CLI or "the shell" or the thousands of commands that most UNIX/Linux systems have in /bin/ or /usr/bin/.

The terminal programs themselves really aren't all that difficult. The settings possible for an xterm are nearly unlimited, but most people only know it as a simple black box with white text that doesn't have a menu.  It does have 3 menus and even more control is possible through either startup parameters or the .xtermrc or the .Xresources files.

Sorry to head down a rabbit hole - that is the nature of Linux/UNIX.  Just when you think you understand something, you learn that you've got only 10%.

Oh - and putty is the terminal most used from Windows to Linux/UNIX systems over ssh. I suppose there are others - teraterm used to be a favorite in the late 1990s - but that project died when ssh2 was released closing some serious security holes.

Anyway - have fun in the shell today!

---

### Post by majk2 on 2014-06-13
:popcorn: I will Thanks!

---

