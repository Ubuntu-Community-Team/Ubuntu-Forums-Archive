---
title: "Copying files to new destination with same realative path?"
date: 2011-03-16
forum: Programming Talk
---

### Post by viggen on 2011-03-16
I wonder, if a recursive copy is performed from place A,** is it possible to place the copy in a new destination B that is similar in structure where the file was copied from?**
  
**MUST CRITERIA 1:** Note that only the files of specific type will be copied (here *.txt)
** MUST CRITERIA 2:** Note that there is files and folders in both structure A and B that must not be copied or changed.
  [B]
[/B]
[B]From structure A:
[/B]**/home/A/**rootA1.txt
** /home/A/**rootA2.txt
** /home/A/**oldA.xx 
** /home/A/foo/**fA1.txt
** /home/A/foo/**fA2.txt
** /home/A/foo/**oldfooA.xx
** /home/A/bar/**barA1.txt
** /home/A/bar/**barA2.txt
** /home/A/bar/**oldbarA.xx

[B]From structure B:
/home/B/[/B]newB.xx 
** /home/B/foo/**newfooB.xx 
** /home/B/bar/**newbarB.xx


  **Result:**
** /home/B/**rootA1.txt
** /home/B/**rootA2.txt
** /home/B/**newB.xx [COLOR=Blue]<- not changed in B, even if the file names would be the same.[/COLOR]
** /home/B/foo/**fA1.txt
** /home/B/foo/**fA2.txt
** /home/B/foo/**newfooB.txt [COLOR=Blue]<- not changed in B[/COLOR]
** /home/B/bar/**barA1.txt
** /home/B/bar/**barA2.txt
** /home/B/bar/**newbarB.txt [COLOR=Blue]<- not changed in B[/COLOR]
  I have tried with rsync but this will remove the destination folders when using rsync -zvr --existing

---

### Post by Arndt on 2011-03-16
> **viggen said:**
> I wonder, if a recursive copy is performed from place A,** is it possible to place the copy in a new destination B that is similar in structure where the file was copied from?**
  
**MUST CRITERIA 1:** Note that only the files of specific type will be copied (here *.txt)
** MUST CRITERIA 2:** Note that there is files and folders in both structure A and B that must not be copied or changed.
  [B]
[/B]
[B]From structure A:
[/B]**/home/A/**rootA1.txt
** /home/A/**rootA2.txt
** /home/A/**oldA.xx 
** /home/A/foo/**fA1.txt
** /home/A/foo/**fA2.txt
** /home/A/foo/**oldfooA.xx
** /home/A/bar/**barA1.txt
** /home/A/bar/**barA2.txt
** /home/A/bar/**oldbarA.xx

[B]From structure B:
/home/B/[/B]newB.xx 
** /home/B/foo/**newfooB.xx 
** /home/B/bar/**newbarB.xx


  **Result:**
** /home/B/**rootA1.txt
** /home/B/**rootA2.txt
** /home/B/**newB.xx [COLOR=Blue]<- not changed in B, even if the file names would be the same.[/COLOR]
** /home/B/foo/**fA1.txt
** /home/B/foo/**fA2.txt
** /home/B/foo/**newfooB.txt [COLOR=Blue]<- not changed in B[/COLOR]
** /home/B/bar/**barA1.txt
** /home/B/bar/**barA2.txt
** /home/B/bar/**newbarB.txt [COLOR=Blue]<- not changed in B[/COLOR]
  I have tried with rsync but this will remove the destination folders when using rsync -zvr --existing

Look at 'find', 'tar' and 'cpio'.

---

### Post by viggen on 2011-03-17
Thanks!

---

