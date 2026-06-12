---
title: "BlueJ Stopped Working"
date: 2007-02-09
forum: Programming Talk
---

### Post by Catsworth on 2007-02-09
Hi Guys,

BlueJ has recently stopped working, and I've got no idea why.

I haven't installed anything new, or changed anything that I can recall, all I've done is install the recommended updates (can't remember what they were) that have popped up on my screen whilst I've been using Ubuntu.

Ok, here's what happens.

When I click on the BlueJ entry in the menu (or type BlueJ in a terminal) BlueJ opens as usual, except it opens with a 'project' already open.  When I double click on a class, or right-click and select the Editor option, BlueJ hangs and I can't find any way to close it or clear it - I end up resorting to pressing Ctrl+Alt+Backspace and logging in again.

I'd be really greatful if anyone can help, I need this to be working for my University studies.

Thanks.

---

### Post by Catsworth on 2007-02-12
Anybody? :(

---

### Post by jblebrun on 2007-02-12
I don't use BlueJ, so this is a total shot in the dark, but try removing the BlueJ configuration stuff from your home directory.

I imagine there's a directory called ".bluej" or something. Move it away from that location, to something like bluej.bak

Then see if BlueJ works properly again. This has done the trick for me with other programs exhibiting similar behavior.

---

### Post by steve.horsley on 2007-02-12
What does the bluej launch script say if you launch it from a console? 

I wonder if a Ubuntu update has replaced your JVM with a different version, or at least, replaced a symlink to a JVM/JDK.

---

### Post by Catsworth on 2007-02-13
It doesn't say anything, it just loads BlueJ.  Then, when I try to open any project, everything hangs and the only way to get out of it is to Ctrl+Alt+Backspace.

I'll try removing the config information and see if that helps.

Thanks.

---

### Post by Rizado on 2007-03-13
Do "cat /path/to/bluej/bluej". Is the java path right? If not change it. Also I have had problems with some projects that bluej cannot open anymore. If will do nothing at all trying to open them and if you got bluej autoopening that project it wont start.

---

### Post by Jonwenger on 2009-12-16
I recently had a similar problem that appeared after I upgraded to Karmic. I cannot use any buttons in BlueJ. Neither can I load projects. The Error code I am getting when I run BlueJ from the terminal is: ```
class Boot: tools.jar not found. Potential problem for execution.
```

---

### Post by Zugzwang on 2009-12-17
@Jonwenger: Check that the package "sun-java6-jdk" is installed.

---

### Post by SigmaSanti on 2009-12-17
I had this problem before (among several others) with bluej.
I would run bluej from my computer and open a project on my flash drive, later when I would run bluej without my flash drive plugged in it would try and go to the last folder location/dir it had opened files at. This location no longer existed since the drive was not plugged in, so bluej would crash. 
Deleting it and all the its files, then reinstalling should fix this.

---

### Post by Jonwenger on 2009-12-19
@Zugzwang

Thank you. Worked perfectly.

---

