---
title: "File/folder permissions help!!!"
date: 2009-07-19
forum: Programming Talk
---

### Post by oscurochu on 2009-07-19
I am creating a script that uses modules. I want to put the modules all in a directory called "~script-path/modules"

All the modules I want enabled will be in that directory, and all the disabled modules will go into a subdirectory "~script-path/modules/disabled"

What permissions must I give the folder(s) to ONLY allow php to read/execute the php scripts in those two directorys, and move files from the subdirectory in to the parent directory, and files from the parent directory into the  subdirectory to easily disable (or enable) certain modules? I do not want to allow any other types of permissions that could put the system or php script at risk.

---

