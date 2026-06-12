---
title: "Goofed up Zim installation can't reinstall &amp; work"
date: 2011-12-01
forum: New to Ubuntu
---

### Post by Denver Dave on 2011-12-01
I've been looking for linux PIM and am trying out Zim under windows and ubuntu 11.10.   Zim is in the software center and I initially installed it fine and it ran.

However, I tried out the calendar widget, could not seem to get rid of it and I went a little nuts, deleting pages, zim notebook files and folders.

Now I can uninstall and reinstall Zim, but when I launch the program it just goes to the left bar for a while and then disappears.

I've tried uninstalling and reinstalling from the software center multiple times with the same result.   I don't have any data in Zim and I suppose I could reinstall ubuntu 11.10 to the flash drive.

Any suggestions on how to resurrect the ability to install Zim in a less drastic way than reinstalling ubuntu 11.10?

Thanks.

---

### Post by Elfy on 2011-12-01
Try searching for a zim folder in your home and removing that, purge and reinstall zim - see if that helps. When you uninstall an app config files in your home do not get removed.

---

### Post by SteveDee on 2011-12-01
> **Denver Dave said:**
> ...Any suggestions on how to resurrect the ability to install Zim in a less drastic way than reinstalling ubuntu...

I'd remove zim via Synaptic, then search the system for "zim" files & folders and remove them.

On my system there are zim files in /home/{user}/.config/zim.

You could try creating a second user account and see if you have the same problem.

Could you have accidentally trashed some others files? (e.g. not part of zim, but required by zim).

For what its worth I've stopped using Zim because some of my links broke and I can't recover them. WikidPad is a much more stable application.

---

### Post by Denver Dave on 2011-12-01
Thanks for the tip.  I had searched for notes and notebook, but not Zim.

Nothing in the home directory for Zim left, but did find when searching the filesystem:

zim.list
zim.png
zim.postrm
zim_0.52-1_all.deb
Zim Desktop Wiki

Two files have been modified in the last 2 days - both are read-only
zim.list in /var/lib/dpkg/info
and "zim Desktop Wiki" in /usr/share/app-install/desktop

double checked and with the home button - I'm not seeing a config directory or one under share.   under file system, no config folder, but is a usr, under that, I don't see my user "denverdave", just bin, games, include, lib, local, sbin, share, src.

I could have trashed other files - we'll see - more of a learning experience, wouldn't hurt me to practice reinstalling ubuntu (I'm sure I'll get other chances).  In my frustration to get rid of the calendar, I deleted the notes and notebooks directories.

With sudo nautilus I've renamed the zim.list, which seemed to be empty and am reinstalling Zim - will report back.  Renaming zim.list did not allow zim to run, but might be on the right track.  

= = = 
Zim is an interesting application.  Very nice design layout.   But seems to be somewhat possessed.   Thought I might need an excorcism to get rid of the calendar when added to a page on the ubuntu version, which is how I got into the above issue.  On the windows version, which is still running, once I do fullscreen, whether I do full screen or not, the screen takes up my entire 24" monitor and I can't seem to resize and f11 does not fix (haven't reinstalled yet on windows).    I digress - Zim would much benefit from a discussion forum - which I haven't found.

---

### Post by SteveDee on 2011-12-01
> **Denver Dave said:**
> ...Zim is an interesting application.  Very nice design layout....

I agree. And I was hoping to promote it at work (on Windows) as its easier to drive than WikidPad. But if you invest your valuable time in adding information, it needs to be kept safe. I've never liked the idea of these kind of apps keeping stuff in a collection of files, and this bad experience has just reinforced my view.

WikidPad keeps your notes in a single database. It works great on Windows, but you need to remember to close it before shutting your system down (especially on Linux). You can generally move wikis between Windows<>Linux so long as you keep the WikidPad version the same.

Anyway, I wish you luck with Zim.

---

