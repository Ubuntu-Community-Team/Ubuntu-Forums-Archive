---
title: "(Im) Requesting advice about boot-repair for an atypical system."
date: 2018-07-09
forum: New to Ubuntu
---

### Post by nothan on 2018-07-09
Background
i have used boot repair previously (in other ubuntu installations), and even if im a "noob", i have been testing on and off ubuntu os, maybe since version 10 or 12 (always returning to windows since a few programs i like wont run in ubuntu, but that has been changing and i hope i can remain in ubuntu longer).

Current issue(s) pt1
im trying dual boot for the first time, with few hickups. i know that changing recommended settings in boot repair can do more trouble than solving problems, but im also ignorant of how the recommended settings in auto-repair will affect my current system since i decided to try a custom installation and i dont like the idea of having to reinstall everything if something fails in a serious way after repairing boot. i have been having a booting issues at least two times now after turning off my computer (normal turn off), and in previous ocassion this was the sequence: computer starts in bios showing no booting options; i ran the live usb; turn off; turn on; windows "magically" boots; restart; somehow grub reappears, and i can login again. Im currently writing this in win8, in the laptop with the issue. 

The "snapshot" taken by boot-repair:
paste.ubuntu.com/p/bZR32rhRPB

Short description of my system
i created many partitions: one for boot, anothers for temp, swap, and also others for files and some programs (mostly games).

Current issue(s) pt2
im asking advice here, for the first time, since i would like to keep my current installation and settings. Most of it works properly, after a few issues with "nvidia vs the kernel version", and "kde desktop + ubuntu with a few gnome and gtk files": i installed current version of ubuntu studio 16.04 lts to try the low latency kernel + audio software, but since i found kde desktop looks nice and depends on a lot of files that dolphin file manager uses (and other kde apps), and which i also like, i decided to use that desktop enviroment. i had a few screen tearing issues from bad attempts to run nvidia drivers with my settings, but i finally managed to solved them after removing and reinstalling nvidia a few times. last time i also had a few screen issues,but only sometimes when starting firefox: a singe or two black bars appear over the area where cairo-dock is running (running with opengl "cairo-dock -o"). those bars or bar usually go away after closing firefox or starting something else. im not sure how to solve those, but since everything else looks to be working mostly fine, i dont want to keep fooling with nvidia drivers (its currently active and working; last time i switched to intel from the nvidia panel, i was later unable to switch back to nvidia and had to reinstall the drivers, so, im not interested in doing all that again). if there was a way to switch to intel graphics and nvidia, without having issues to switch back and forth, it would be nice,or ,even better, to keep intel as default and run nvidia only with a few games (steam, and free games like freedoom), and programs like blender, davinci resolve, natron, and lightworks (learning and finding ways to show what this programs can do could help people think more about linux).


Bonus problems (ignore this if you must):
A) if i run gimp (v2.8), gimp fails to change swap and temp folders, and also save other settings, except if i start it through "sudo gimp": is there a way to avoid doing sudo to keep settings, or is there a way to "auto sudo" through a desktop shortcut (so i only have to type the password, rather than opening a terminal to access gimp).

B) im also interested to have usb-key to boot my system, so it wont start without it; i have been searching a bit, but havent been able to read something that could be more or less straight-forward that could work for a dual-boot system. Also, if such usb-key could work only with a specific os (linux), is there a way to use the same usb-key to skip entering the password each time sudo is required? Any tips about how to investigate this, will also be appreciated.


I hope this "ramblings" didnt bored you to dead, or that if you were  dying, you left a message so someone else could keep reading where you  left: i really want to learn and use linux for "creative stuff" and  maybe make a few guides to help the projects (unrelated to programming,  which im very ignorant of, and im unsure how to learn the basics while  also studying previous video-related programs; also please forgive me  for my somewhat "broken english").

Thanks for reading.

---

### Post by yancek on 2018-07-09
Your link to the boot repair output is broken, try again.

You posted about several different issues.  Best to open separate threads for each since people who are familiar with Gimp may not be familiar with graphics card issues, boot issues, etc.  Additionally, posting about multiple problems in one thread gets confusing.

---

