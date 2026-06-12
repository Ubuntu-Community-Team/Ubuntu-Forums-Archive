---
title: "Slax customization - what would you add?"
date: 2008-08-31
forum: Other OS Talk
---

### Post by barkalot on 2008-08-31
So I stripped down a 6.0.7 Slax .iso, planning to customize it and use it for, well, something :) I'm not sure yet. I'm just doing this for fun, and I'm gonna keep my Frankenslax to myself. But since I'm not sure what kind of Slax remix to make, I'm posting here.

What would you do? Would you leave it without a GUI and add some more console apps? Would you add a flashy GUI? But that wouldn't make it special, since the original Slax uses KDE, and there's an older variant using Xfce. Maybe Openbox with transparency, or Gnome with Compiz? Not sure how that could be useful, but still.

So, what would you add?

EDIT: (You can skip this part, I'm just ranting about my failure ;) )Well, my first foray into 'distro' creation has failed. After deleting the base modules 003-006 and converting all the necessary .tgz files to .lzm ... I deleted all the modules because of a misplaced wildcard('rm * .tgz', anyone).

After starting over and finally getting that part done, I used the make_iso.sh file. Which included every file found in the base slax directory in the new .iso. After I started burning the CD, I began wondering just why the .iso was 290 MB large. Having the original .iso in the new one didn't help matters.

So after burning another CD with the correct, 100 MB .iso file, I booted the computer with the new CD inside. For my troubles, I got a "can't use runlevel 4 without *DM" loop. I think I need to change it to runlevel 3, but I'm not sure yet. I always forget just which runlevel does what. I'll have to find out some other time, though, 'cos I'm quite exasperated right now.

Of course, I'd still like to hear what you would add. Or maybe some of you've already done something like this before. I'd love to hear about it.

---

### Post by DeadSuperHero on 2008-08-31
I'd set up mostly command line tools and stuff that uses NCurses frontends. Absolutely love ncurses.

Some tools I used that you might find useful:

-Screen. It's a great app for switching between tasks without a GUI.

-eLinks: a Simple enough browser, but packed with functionality. Was useful for getting into Gmail, Myspace, and Twitter. Nice.

-IRSSI: Great IRC client.

-Cplay: A simple music player frontend. Very nice.

-Nano: My preferred CLI text editor. Most die-hards will say VIM or Emacs, but Nano is nice in its simplicity.

-BSDGames: For those who get bored.

I never could really find a mail client that I liked, lucky thing that eLinks supports rudimentary web interfaces.

---

