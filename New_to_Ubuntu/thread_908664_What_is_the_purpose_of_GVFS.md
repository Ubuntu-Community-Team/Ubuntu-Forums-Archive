---
title: "What is the purpose of GVFS?"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by Frogbarf on 2008-09-02
I decided to copy my home directory to a Windows box as backup. Eeek! Tens of thousands of files! Gigabytes of information! And I only installed HH 8.04 last Saturday! Eeeeek!

Digging around, I discovered that my home directory includes a hidden directory .gvfs that itself includes all the stuff in the windows share I was going to copy to! That's where all those files & gigabytes were coming from. If I hadn't cancelled the copy, I'd have had two copies of everything on the Win98 box!

Evidently, all that stuff in the .gvfs directory isn't really there: it's just where the Windows share has been mounted without me realizing it. I was going to mount that same Windows share in my home directory via FSTAB and such, but hadn't completed deciphering the instructions and now I wonder if I have to bother.

Neither Google nor the Ubuntu forums have been able to answer a fundamental question: what problem(s) is this .gvfs and its associated demon solving? What is its purpose, in everyday language? The explanations I have found are written by people too close to the trees to see the forest.

Can I dispense with mounting the Windows share since I can always navigate to the .gvfs directory? Can I change the location of the .gvfs directory to, say, /media?

Does the existence of gvfs mean I can forget about running Samba? (I think I have to run Samba so the Windows boxes can see the Linux file system.)

Etc.

Thank you in advance for your carefully written reply that avoids jargon, abbreviations, and implicit assumptions about my knowledge of Linux.

---

