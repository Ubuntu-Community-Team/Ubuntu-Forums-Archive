---
title: "[SOLVED] This is a major failure of your software management system..."
date: 2008-11-13
forum: New to Ubuntu
---

### Post by noseovertail27 on 2008-11-13
Hey,

I had tried to install a program through the add/remove feature, and upon completion, I had received this message:

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

When I had went to the synaptic program, I had received this message then:

E: Type 'sudo' is not known on line 66 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.



I have been trying to fix this for over a half hour. Any information whatsoever would be greatly apreciated. Thanks so much.

-Jordan

---

### Post by aysiu on 2008-11-13
**Step 1**
Close Add/Remove and Synaptic completely

**Step 2**
Paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
gksudo gedit /etc/apt/sources.list &
``` This will open the /etc/apt/sources.list file in a text editor. Find line 66 and delete it completely. Then save and close the text editor.

**Step 3**
Paste these commands into the terminal: ```
sudo apt-get update
sudo apt-get -f install
```

---

### Post by noseovertail27 on 2008-11-13
Wow, thank you so much. This is an outstanding forum.

---

