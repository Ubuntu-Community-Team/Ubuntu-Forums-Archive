---
title: "How to view/convert surveillance dvr files (.dmd)"
date: 2016-11-12
forum: New to Ubuntu
---

### Post by laurag98107 on 2016-11-12
I have a hard drive from my surveillance dvr, which doesn't work anymore.  My computer running Windows 7 won't even recognize the hard drive, but when I boot into Ubuntu, I can see the hard drive and the files.  There are several folders with numeric names (00000507 for example) and inside the folders are files with .dmd extension.  There is also a file named "backup player.exe" but it gives an error message when I double click it.

The DVR is a Prestige 16 channel- it's a pretty generic dvr.  I have the hard drive hooked up to my laptop with a usb adapter.  I'm really new to Ubuntu and Linux, so this might seem like a dumb question, but hopefully someone can point me in the right direction.

Thanks,
Laura

---

### Post by yetimon_64 on 2016-11-13
> **laurag98107 said:**
> ...  There is also a file named "backup player.exe" but it gives an error message when I double click it.

The DVR is a Prestige 16 channel- it's a pretty generic dvr.  I have the hard drive hooked up to my laptop with a usb adapter.  I'm really new to Ubuntu and Linux, so this might seem like a dumb question, but hopefully someone can point me in the right direction.

Thanks,
Laura

Windows executables (.exe files) only work on windows, not on linux. It maybe possible to use it under Wine (a windows code compatibility layer for linux), but with no guarantee it will work. Wine tends to be a bit of a "hit and miss affair" with respect to windows exe files.

After a bit of searching those "dmd" files appear to be "SQL Developer Data Modeler files". I have not been able to dig up any "easy" means of converting such files, but I will put a couple of links in for you to look at...

A description of the file type is [[COLOR=#0000ff]--here--[/COLOR]]("http://www.file-names.com/file-extension-dmd/").

The next link on a gamers forum (read post #7) asking about opening dmd files got a response about using md2tool and blender to convert and open such files [[COLOR=#0000ff]--the gamer forum link--[/COLOR]]("https://forums.duke4.net/topic/879-dmd-files-how-can-openedit-them/") (from 2009).
Note the tool (md2tool) on sourcforge is dated to 2004 (very old). I have never used this tool, or even blender for that matter, and have no idea if it works or not; I just ran across these links from a bit of googling on your problem.

Hope someone else here actually has some first hand experience with such files and can help you further.
Good luck, yeti.

---

