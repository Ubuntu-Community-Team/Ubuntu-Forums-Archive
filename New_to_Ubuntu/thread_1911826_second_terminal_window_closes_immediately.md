---
title: "second terminal window closes immediately"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by qgroff on 2012-01-19
Hi all, just installed ubuntu last night so I'm totally new.  Have used Unix and Linux a fair bit before but never had to deal with setup or being in control of things.

My problem is, I can open a terminal just fine, use it, whatever.  When I then try to open a second terminal, it opens for a moment, displays nothing, then closes after about a second.  This happens regardless of how I try to open it: Ctrl-Alt-T, Ctrl-Alt-F2 and typing terminal, "xterm" or "xterm &" from the open terminal... all behave the same.  Knowing the way I function I'm going to want many terminal windows open so this is really cramping my style.

Thanks very much!

---

### Post by mcduck on 2012-01-19
That's strange. What happens if you open a new terminal directly from the old one (File/Open Terminal from the menu, or Shift-Ctrl-N). Or if you launch another gnome-terminal from the old one (or the Alt-F2 dialog)?

Since it seems to affect many different terminals (gnome-terminal and xterm, at least) it can't be a problem with a certain program's configuration. So that would point towards your Bash config files, ~/.bashrc and ~/.profile. Have you made any changes to either one?

...of course if nothing works, then using [Terminator]("apt:terminator") might be a decent workaround, giving you multiple terminals in one window...

---

### Post by kellemes on 2012-01-19
> **mcduck said:**
> ...of course if nothing works, then using [Terminator]("apt:terminator") might be a decent workaround, giving you multiple terminals in one window...

Indeed that's a nice app.. I think it's a little heavy on the resources but i'v been using it for some time now and it works just fine.

---

### Post by mcduck on 2012-01-19
> **kellemes said:**
> Indeed that's a nice app.. I think it's a little heavy on the resources but i'v been using it for some time now and it works just fine.

More lightweight alternative would of course be using [screen]("https://help.ubuntu.com/community/Screen"), or [Byobu]("https://help.ubuntu.com/community/Byobu"). But Terminator sure is easier to learn.

---

### Post by qgroff on 2012-01-20
Nope, fresh install, I'd barely done anything before I started having this problem.  I was going to edit those files, actually, but never so much as opened it because I wanted a second terminal before I did (so I could ssh in to a remote machine where I could look at my .bashrc and .profile there).

Since closing that one terminal I had open (and restarting) I now cannot open ANY terminals.  Both gnome-terminal and xterm do what I described before.  Open for about 1 second, blinks an underline cursor once, then closes.  I guess I'll try to install Terminator and see if I have any luck there.  If not I may just have to reinstall; functioning without terminals is out of the question.

Edited to add: Installed Terminator, it behaves the same.  Firefox opens.  System Settings and Dash Home both open.  Terminals open, then close.  The whole program is exiting out, because the menu bar disappears as well.  So weird.  Unless anyone has a brilliant idea I'll have to reinstall...

---

### Post by qgroff on 2012-01-22
Resolved: I just deleted my .bashrc and .profile entirely and things started working.  I'm quite sure I never edited them, and when I went in and looked at them I couldn't see anything out of place, but they were clearly making the terminal unhappy somehow.

---

### Post by rwlanger on 2012-01-27
Ubuntu 10.04, which I had used for a year and a half or so, recently got fouled up so badly that I couldn't eveb boot from the 10.04 CD.  I finally was able to install 11.10 without any apparent problem. However, now I cannot open a second terminal at all, which I thought I could do with 10.04. It seems to me that I ought to be able to have Sage (math) running in one terminal and have another terminal open to move some files. Also, I can't open a second instance of the Home Folder in the Unity interface, something which is also useful for the way I'm accustomed to moving files. I'm willing to study if I know where to look.

---

### Post by mcduck on 2012-01-27
> **rwlanger said:**
> Ubuntu 10.04, which I had used for a year and a half or so, recently got fouled up so badly that I couldn't eveb boot from the 10.04 CD.  I finally was able to install 11.10 without any apparent problem. However, now I cannot open a second terminal at all, which I thought I could do with 10.04. It seems to me that I ought to be able to have Sage (math) running in one terminal and have another terminal open to move some files. Also, I can't open a second instance of the Home Folder in the Unity interface, something which is also useful for the way I'm accustomed to moving files. I'm willing to study if I know where to look.

How are you trying to open the second terminal?

What comes to opening a new file manger window from Unity's launcher, that's done by middle-clicking the launcher icon. Or of course you can open a new window from the existing one, Ctrl-N is the common shortcut used for this purpose in pretty much every program on every operating system (well, of course it's Cmd-N on OSX instead).

---

### Post by rwlanger on 2012-01-27
Thank you! I had to think a bit about what you meant by "middle click," but sure enough the wheel on my mouse clicks. I've apparently also missed Ctrl-N, which works for the Home Folder but not for a second terminal.

---

### Post by mcduck on 2012-01-28
> **rwlanger said:**
> Thank you! I had to think a bit about what you meant by "middle click," but sure enough the wheel on my mouse clicks. I've apparently also missed Ctrl-N, which works for the Home Folder but not for a second terminal.

Yeah, terminals use a bit different keyboard shortcuts than most programs, as the usual ones often already have another special uses on command-line interfaces.

If you are using Gnome-terminal, try Shift-Ctrl-N, or just select File->Open Terminal from it's menu. And of course the same middle-click works as well, if you've added the terminal  to your launcher.

---

