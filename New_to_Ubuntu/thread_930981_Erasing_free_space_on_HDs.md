---
title: "Erasing free space on HDs"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by newbietuna on 2008-09-26
MS Windows has a freeware product called "eraser" that can erase deleted file data from hard disks (ie makes it impossible to recover deleted files). Is there anything equivalent for HDs on ubuntu systems? How can one write over freespace on a HD? (Like deleted files in the temp or any other directory, etc.)

---

### Post by phidia on 2008-09-26
Read the guide [here]("http://linuxhelp.blogspot.com/2006/06/how-to-securely-erase-hard-disk-before.html"). Hope that helps.
The command if you just want the quick and dirty is: > shred -vfz -n 100 /dev/(your drive designation) you probably always want to use that from a live cd, but if you were just deleting a partition, and wanted this level of security, you would need to use "sudo" in front of that command if you were running it from an installed system.

---

### Post by Fixman on 2008-09-26
Anyway, once you delete a program (unless you send it to Trash) you can automatically write over it, the other program only serves is you have a file you want to have "securetely deleted", like a credit card number or something).

---

### Post by newbietuna on 2008-09-27
Thanks, Phidia and Fixman. As I am newbie, I can ask dumb questions (right?). I am looking to leave my program files intact. I only want to write over the free space of the HD which may have images or remnants of deleted files on it. Does your suggested shred command do that? I get the impression that it wipes out everything!

---

### Post by lucasl on 2008-09-27
Don't run that shred command, that wipes everything.
When you delete a file or folder, the leaves the data there, but marks it as deleted. This means that even though the 1s and 0s are there, the space is freed and other programs will write over it.
What eraser does is as well as delete the file, it writes over the 1s and 0s with just 0s, so that you can't 'undelete' the data with a special program.

What's the point? Like fixman said, if you have sensitive information (credit card details, bank account details, witness protection details, etc.), then eraser makes it very hard to impossible to get that data back, even by top FBI teams. It isn't reall nessesary unless you are paranoid or you throw your hard drive in a bin or something.

---

### Post by alphacrucis2 on 2008-09-27
A search came up with this thread that might be useful:

[http://ubuntuforums.org/showthread.php?t=281480](http://ubuntuforums.org/showthread.php?t=281480)

---

### Post by bumanie on 2008-09-27
> **newbietuna said:**
> Thanks, Phidia and Fixman. As I am newbie, I can ask dumb questions (right?). I am looking to leave my program files intact. I only want to write over the free space of the HD which may have images or remnants of deleted files on it. Does your suggested shred command do that? I get the impression that it wipes out everything!

That command wipes the entire hard drive. Don't use it unless you want a blank drive/partition.

---

### Post by hyper_ch on 2008-09-27
if you are worried about the data on the drive then use full disk encryption.

---

