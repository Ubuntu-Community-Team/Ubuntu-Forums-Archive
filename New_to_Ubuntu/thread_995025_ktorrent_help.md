---
title: "ktorrent help"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by nynoah on 2008-11-27
I had some problems with Ktorrent in the past.  So I stopped using it.  I am trying to get Kubuntu working well now.  I had a lot of torrents on Ktorrent from before that I have deleted the files for or moved.  I am wondering how I can clear cash for Ktorrent so it just opens up with no jobs.  As it is now.  It tries to recreate like 30 torrents that no longer exist and it just crashes because of the load of those errors.

Anyone know how to clear the memory for Ktorrent so I start from scratch?

---

### Post by echo314 on 2008-11-27
Check in your home directory for a hidden folder named .ktorrent. If you delete this folder (as with almost any hidden folder related to a program), a new one with default settings will automatically be created the next time you run the program.

If you look around inside the folder, you may even be able to see which specific file has the links to the torrents its trying to load, depending on how cryptic everything is. That way, it does not clear all the settings, such as any personal ports, schedules, etc. you may use.

---

