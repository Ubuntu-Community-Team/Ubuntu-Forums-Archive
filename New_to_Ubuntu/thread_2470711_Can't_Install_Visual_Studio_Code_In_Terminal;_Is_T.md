---
title: "Can't Install Visual Studio Code In Terminal; Is Terminal Broken?"
date: 2022-01-08
forum: New to Ubuntu
---

### Post by jesus-pieces on 2022-01-08
I followed the instructions from the VSC website, and all three methods failed: 

1) [sudo] [dpkg] [-i] code_1.63.2-1639562499_amd64.deb
dpkg: error: cannot access archive 'code_1.63.2-1639562499_amd64.deb': No such file or directory

2) [sudo] [apt-get] [install] [-f] code_1.63.2-1639562499_amd64.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package code_1.63.2-1639562499_amd64.deb
E: Couldn't find any package by glob 'code_1.63.2-1639562499_amd64.deb'
E: Couldn't find any package by regex 'code_1.63.2-1639562499_amd64.deb'

3) [sudo] [apt] [install] ./code_1.63.2-1639562499_amd64.deb
Reading package lists... Done
E: Unsupported file ./code_1.63.2-1639562499_amd64.deb given on commandline

So, in the end I double clicked the .deb file, and it installed itself. I didn't see that method on the VSC website! In your face Computer Science! Should I have put a comma before Computer Science?

---

### Post by deadflowr on 2022-01-08
Duplicate thread
Please don't post multiple threads dealing with the same topic.
See other thread here: [https://ubuntuforums.org/showthread.php?t=2470675]("https://ubuntuforums.org/showthread.php?t=2470675")
This thread is now closed

---

