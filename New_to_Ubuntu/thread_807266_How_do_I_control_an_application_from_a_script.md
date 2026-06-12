---
title: "How do I control an application from a script?"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by CRISM on 2008-05-25
I've done a few simple scripts, and I know how to get a program started and running in either foreground or background. I would like to open Audacity and have it play a WAV file automatically. Of course, I can use another app such as aplay or totem, but as a learning experience, I'm interested to find out if I can do it with audacity, which doesn't automatically begin playing a file. So far I've been able to use the script to open audacity and load the WAV file. But I can only start it playing by manually hitting the spacebar on the keyboard. Is there a way to do this in the script?

---

### Post by mbarak on 2008-05-25
try 
```
man audacity
```
or
```
audacity --help
```
to see a list of command options

You might just have to change the settings (within the program) to start playing automatically

---

