---
title: "Did i do something wrong (steam)"
date: 2024-05-23
forum: New to Ubuntu
---

### Post by yimtsuki on 2024-05-23
I didnt research properly i downloaded this OS and tried to open steam then it said so i wrote it directly will this be ok or should i do something to fix it. It said 32-bit nvidia driver files were not found and to install i should run
 sudo dpkg --add-architecture i386
sudo apt update
sudo apt install libnvidia-gl-535:i386
after i did that whenever i type a command it says: Ignoring file 'ubuntu.sources.curtin.orig' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

---

### Post by yancek on 2024-05-23
Check your grammar before you post as your first run-on sentence doesn't make any sense.
What specific OS did you download and which release version?  Your posting at an Ubuntu forum so I expect it is some Ubuntu release?
Did you install Steam yourself?

Is your hardware 32bit only?  A current release of Ubuntu does not have a 32bit version.  Open a terminal and run this command and post the output here:  uname -a

> after i did that whenever i type a command it says: Ignoring file  'ubuntu.sources.curtin.orig' in directory '/etc/apt/sources.list.d/' as  it has an invalid filename extension 		 

Go to /etc/apt/sources.list.d and copy the file in question 'ubuntu.curtin.orig' here.  

You might take a look at the suggestion toward the bottom of the page at the site below as it has a suggestion to deal with the problem.

[https://bugs.launchpad.net/curtin/+bug/2058741](https://bugs.launchpad.net/curtin/+bug/2058741)

---

### Post by currentshaft on 2024-05-24
a

---

### Post by ActionParsnip on 2024-05-24
All files you want to be processed in [COLOR=#E8E6E3]/etc/apt/sources.list.d must end in ".conf" to be processed in updates etc. This is what the message means.[/COLOR]

---

