---
title: "gEdit and the temp files it leaves behind"
date: 2007-05-18
forum: Programming Talk
---

### Post by Unterseeboot_234 on 2007-05-18
I wanted to ask this in programming. 

I'm coding java to read XML. As a roadmap as to what my code is supposed to be accomplishing, I will view my XML file(s) using the Text Editor that comes with Ubuntu -- gEdit. What I discovered is when I tell my java program to go back into that data folder of XML to get a list of the files is I have hidden files. gEdit opens a file and immediately makes a copy with fileName.xml~. (appends a tilde). This copy is not visible on the Linux desktop folder's contents unless I use the Natilaus View Menu --> Show Hidden Files (Ctrl-H).

I mean, I don't have to edit one keystroke of my XML text docs. Just open a doc and quit gEdit.  I have multiple, new files. At least one duplicate of every file I touched.

1. Should gEdit be housecleaning after itself?
2. Is there a Option setting I'm missing in gEdit?
3. Do I have to write java code to search for Linux trash that MAY be inside a folder?
4. Do the other languages/scripting coders see these hidden files?

Any ideas and opinions appreciated.

---

### Post by yatt on 2007-05-18
2. Gedit->Edit->Preferences->Editor->Create a backup of files before saving.

---

### Post by Unterseeboot_234 on 2007-05-19
Well, DOH! Now I feell silly for ranting. I admire Linux and gEdit even more. Maybe I was too involved with the code to visualize the simple. I say I admire Linux more, I woke up this morning with 2 lines of code that would filter fileName.xml~.

:)  thanks for the reply, yatt

---

