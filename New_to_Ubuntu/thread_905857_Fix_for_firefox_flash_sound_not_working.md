---
title: "Fix for firefox flash sound not working"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by wesag on 2008-08-30
I have a feeling the question I'm about to ask is very basic---so I'll post it here, hope someone can help. 

I'm trying to get sound to work in flash videos in Firefox 3.0.1 running Ubuntu 8.04--I found a fix in one of the forums and followed it--reinstalled/updated flashplugin-nonfree.

Then I installed alsa (I think...) with the command 
sudo apt-get install alsa-oss
used the command gksudo gedit /etc/firefox/firefoxrc

This brings up a blank text document---I've tried both typing the next command--firefox_dsp="aoss" into the blank text document, and into the terminal itself. In both cases when I go to close the text document, an error comes up that reads could not save the file etc/firefox/firefoxrc
unexpected error, file not found. Any help would be much appreciated, thanks!

---

### Post by alienexplorers on 2008-08-30
Try disabling from firefox addons>extensions Ubuntu Firefox Modifications.  Found that disabling that got rid of alot of my flash problems.  Also make sure you are using the latest flash 10 program.

---

### Post by RequinB4 on 2008-08-30
try:

```
sudo apt-get install libflashsupport
```

---

