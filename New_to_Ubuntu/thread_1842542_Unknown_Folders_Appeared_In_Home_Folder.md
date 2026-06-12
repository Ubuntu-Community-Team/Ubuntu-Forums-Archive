---
title: "Unknown Folders Appeared In Home Folder"
date: 2011-09-11
forum: New to Ubuntu
---

### Post by johnsmoke on 2011-09-11
Today when I went into my home folder I noticed that there were 7 folders in there that appeared out of nowhere. They all start with lua_ and then a variation of letters and numbers. One is lua_E8lJZ9 another is lua_A3lM1a and so on..... Not sure how these got there. The folders contain nothing inside them. I was learning to use code in Terminal to install some drivers and a software package... Maybe this did it? Not sure what these are... Can I safely delete them with no worries?

---

### Post by audiomick on 2011-09-11
Hi.
I can't say for absolute sure, but I would probably delete them and see if they stay away. The stuff in your home folder is all to do with you. I am not aware of anything in there that will kill you system if it disappears. In my experience, the configuration files in there (which generally have a dot before the name like .filename and are hidden) get created again if you erase them. Your preferences for the application in question are gone, but the application still runs.

---

### Post by Old_Grey_Wolf on 2011-09-11
You may what to look at this site [http://www.lua.org/about.html](http://www.lua.org/about.html). Something you were attempting to installing may use lua; however, it shouldn't be putting things like that in your home folder. In Linux, you have to be careful what directory you are in when you execute a command or what you type for the path. If you don't, you may get things put where you didn't intend them to be. You said you are learning so I wouldn't disregard the possibility. The folders can probably be deleted.

---

