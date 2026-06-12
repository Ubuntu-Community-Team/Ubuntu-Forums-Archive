---
title: "Desktop Problem"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by xfalcon on 2008-10-11
I am new to Linux, I just installed xubuntu yesterday and I was able to login and go to my desktop. I then was able to use my wireless to go online and installed some updates including some codec update for Totem Player.

Today, I tried using Totem Player to run a DVD, but it hang up. So I figured, I will just restart the computer. After restarting  and logging in, My desktop looked different, it has icons in the middle like Home, Floppy, File  Manager, etc but it don't have the top bar or the bottom bar. I tried right click to change the setting for desk top and after changing the setting, etc.. I ended with no icons in the desktop, just the background on the desktop and nothing else, right click and left click don't do anything. restarting the computer still give me the same result after logging in. 

After looking at the forum and trying some of the suggestions, nothing help.. so I decided to just reinstall the xubuntu instead of looking for a solution.

I would appreciated if somebody tell me what happened and if there was a quick fix. Is there a quick way to stop a nonresponsive program in Linux ? (like the one in Windows Ctrl-Alt-Del). Is there a way to prevent this from happening in the future?

---

### Post by sumguy231 on 2008-10-11
It sounded like some of your desktop config got screwed up, and deleting the configuration files may have helped. Most are located in .config/xfce4 in your home directory.

As for ending a nonresponsive program, try xkill. When you run it, it gives you a cursor shaped like an x, and the first application you click on will immediately terminate. (Press Esc to cancel).  You might find it handy to enter the keyboard settings and map it to a shortcut like Ctrl+Alt+Esc. There is also a system monitor in the system menu if you want a tasmanager-like application.

Oh, and as for prevention, I would recommend backing up at least your config stuff in case something like this were to happen again.

---

### Post by randcoop on 2008-10-11
To end a non-responsive program in Xubuntu, you might want to try using htop.  Click System in the menu and then choose htop.  It will give you a list of all running programs.  Hit the F3 key to search for a particular program.  Once it's highlighted, hit the F9 key to kill it.

---

