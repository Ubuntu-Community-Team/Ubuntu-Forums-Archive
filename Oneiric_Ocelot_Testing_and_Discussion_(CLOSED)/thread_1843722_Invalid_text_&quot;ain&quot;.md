---
title: "Invalid text &quot;ain&quot;"
date: 2011-09-13
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by PaulInBHC on 2011-09-13
I added wine ppa to my list to try to get the latest beta build. It doesn't work because natty is the last build.

Meanwhile now I cannot run Update Manager, Synaptic, Software center. I get an error and one of them states an error in a text file with ain in line 3. I opened the file and cannot edit and save the file because I do not have permission.

I am back on XP or I would post the correct message. Should I just reinstall OO?

---

### Post by mdhollis on 2011-09-13
> **PaulInBHC said:**
> I added wine ppa to my list to try to get the latest beta build. It doesn't work because natty is the last build.

Meanwhile now I cannot run Update Manager, Synaptic, Software center. I get an error and one of them states an error in a text file with ain in line 3. I opened the file and cannot edit and save the file because I do not have permission.

I am back on XP or I would post the correct message. Should I just reinstall OO?

I had the same exact issue with the rictoz ppa.  You need to edit the ppa and remove the ain and everything will be fine.  If you run:

> sudo apt-get update

It should give you the path to the source causing the problem.

---

### Post by jbicha on 2011-09-13
This is actually a pretty important bug but I never got around to tracking it down or reporting it (sorry!). Please go ahead and report it, maybe against aptdaemon. How exactly did you add the PPA immediately before seeing the bug?

Like mdhollis said, you need to look through /etc/apt/sources.list.d (or possibly /etc/apt/sources.list itself) for a file with an extra "ain" line and remove it.

---

### Post by PaulInBHC on 2011-09-13
I found the file, opened it with gedit, but I could not save or save as... because it states that I don't have permission.

---

### Post by mdhollis on 2011-09-13
open a terminal and type:
```
 gksudo gedit *wherever that source is*
``` 

Then edit and save

---

### Post by PaulInBHC on 2011-09-14
Thanks that did it. I've been away from ubuntu too long to remember all the terminal stuff.

@Jeremy I don't know what I did exactly but I copy and pasted the text from the winehq page about adding to update manager. The ppa for OO was already checked.

---

### Post by mdhollis on 2011-09-14
> **jbicha said:**
> This is actually a pretty important bug but I never got around to tracking it down or reporting it (sorry!). Please go ahead and report it, maybe against aptdaemon. How exactly did you add the PPA immediately before seeing the bug?

Like mdhollis said, you need to look through /etc/apt/sources.list.d (or possibly /etc/apt/sources.list itself) for a file with an extra "ain" line and remove it.

I added the ricotz ppa and received this error.  I added it with:

```
sudo add-apt-repository ppa:ricotz/testing
```

---

