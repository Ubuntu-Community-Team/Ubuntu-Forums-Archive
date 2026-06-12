---
title: "[SOLVED] Searching for files!!"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by NikS on 2008-06-29
Hi everyone,

M basically a refugee from Windows,
So unaware how to search for files when u dont know the exact filename!!
Like in windows if i search for fir*.* it returns me all files starting with fir n all file types as well!!

So how do i do it in Linux?? Esp. ubuntu???

-----------------------------------------------------------
Thanks ubuntu community!!
:lolflag:

---

### Post by wormser on 2008-06-29
The same rules apply for wildcards (*) in Linux.  Applications> Accessories> Terminal.

First update the DB
```
sudo updatedb
```
```
locate fir*.*
```

Another method is with the find command.
```
find / -name fir*.*
```

The / is for searching from the root directory.  You can specify other directories like /home/user.

---

### Post by NikS on 2008-06-29
Oh thanks!!!

That worked!
But How do I use it in browser??
There's a search option there....
But...
:confused:

---

### Post by Canis familiaris on 2008-06-29
GUI way:
Places->Search for Files

---

### Post by NikS on 2008-06-29
Thats wat the problem is!!!

I have a file say 'new file.txt' in drive.
I search for 'new file', 'new*', 'new*.*'!!!
It always says: No files found!!!!

---

### Post by linuxisfree on 2008-06-29
> **NikS said:**
> Thats wat the problem is!!!

I have a file say 'new file.txt' in drive.
I search for 'new file', 'new*', 'new*.*'!!!
It always says: No files found!!!!

i think i know the problem... you said, for example, you're looking for New File.txt? make sure you type in the search New *.* (please take note of the space between New and *)
That should work:D

---

### Post by NikS on 2008-06-29
Yes it sure did mate!!!

Thanks!!!
:)

---

