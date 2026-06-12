---
title: "How can this be?"
date: 2012-07-29
forum: New to Ubuntu
---

### Post by Langstracht on 2012-07-29
I have not been able to find a post anywhere that complains about "rename".  But I have one.  Actually - in terms of instances - many more than one.

If I want to, say, rename some audio files in a folder from:

cher - file1.mp3
cher - file2.mp3
cher - file3.mp3

to:

Cher - File1.mp3
Cher - File2.mp3
Cher - File3.mp3

more often than not, it will NOT let me - claiming a file by that name already exists.  I have to, for instance change cher - file1.mp3 to Cher - File1 A.mp3 to get it to work.

Anyone know what's going on?  And how to stop it from doing this?

TIA

---

### Post by steeldriver on 2012-07-29
what replace string are you using exactly? I just tried

```
rename -v 's/cher - file/Cher - File/' cher*.mp3
```

(after creating some dummy 'cher - file1.mp3' etc files) and it seemed to work fine

---

### Post by hil4vitkutin on 2012-07-29
Wondering, just like you.

I have this same issue... It seems to have something to do with capital letters? This issue occurs for me only when changing lower-case letters to upper-case and vice versa.

I'm sorry for not knowing any solutions for this, just got to live with it :D Just saying you're not alone with this. It's annoying and I hope it could be fixed.

---

### Post by hil4vitkutin on 2012-07-29
Woops... didn't refresh the page.

Is there any other way to fix this than the terminal-way?

---

### Post by ajgreeny on 2012-07-29
Are these files on a fat32 or ntfs filesystem?  Only linux filesystems are case sensitive, fat and ntfs are not so on those cher=Cher.

---

### Post by hil4vitkutin on 2012-07-29
Oh :D Yes, my files are on FAT, and the error occurs only on FAT/NTFS filesystems. Thanks for helping this out.

---

### Post by steeldriver on 2012-07-29
well done ajgreeny! nice bit of deduction

---

### Post by Langstracht on 2012-07-29
I have not been using CLI - relying totally on "F2".

Filesystem?  vfat.

So!  What to do?  Grin and bear it like hil4vitkutin opines ...

---

### Post by spjackson on 2012-07-29
> **Langstracht said:**
> I have not been using CLI - relying totally on "F2".

Filesystem?  vfat.

So!  What to do?  Grin and bear it like hil4vitkutin opines ...
I don't think that you can do it in a straight-forward manner on vfat.

I think you should be able to do a 2 stage rename, e.g. first rename them to say
ZZZCher - File1.mp3
ZZZCher - File2.mp3
ZZZCher - File3.mp3
then rename them again to remove the ZZZ.

---

### Post by Langstracht on 2012-07-30
I think I understand that "linux" thinks "Cher" is the same as "cher".

I do NOT understand why that is interpreted as a problem when "cher" will not exist after it's renamed "Cher".

Is this a bug that needs reporting?

---

### Post by muteXe on 2012-07-30
I think my machines would complain if they found anything by Cher on any of my partitions :)

---

### Post by jtarin on 2012-07-30
Open a terminal and type ```
man rename
``` and you will have your answer about upper and lower case.

---

