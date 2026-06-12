---
title: "Creating a bash file"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by SheepIsOp on 2012-01-19
I have no prior knowledge of Linux so yeah... i'm trying to run a in wine program then the next 1 afterwards

what command should I use for this?

wine after file location? 

It's essentially a text file, i could just double click it?  Is it a bash file or sh idk if theres a difference?

~/Desktop/Link to League of Legends/lol.launcher.admin.exe 
~/Desktop/Link to League of Legends/RADS/projects/lol_launcher/releases/0.0.0.33/deploy/LoLLauncher.exe

idc if my grammar is not perfect.  if it's not don't bother saying i'll answer, "if you make it grammatically correct", i won't change it and that's not very constructive in general..

---

### Post by I8NY on 2012-01-21
a sh (shell script) is just a text file with *.sh at the end. ubuntu will let you choose how to open it when you click on it.  since you are making it it is best to drag the file into the terminal and press enter to launch to see the errors that might come out. so the first problem with you code is spaces are not allowed. either put a "\" right before the space or put the whole destination in " ". also you need the wine command at the begining of the designation. Example: ```
wine "~/Desktop/Link to League of Legends/lol.launcher.admin.exe"
wine ~/Desktop/Link\ to\ League\ of\ Legends/RADS/projects/lol_launcher/releases/0.0.0.33/deploy/LoLLauncher.exe
```
now i'm not entirely sure that both will run a the same time. you might have to make them launch in separate screens or just click on two files. i hope this helps.

---

