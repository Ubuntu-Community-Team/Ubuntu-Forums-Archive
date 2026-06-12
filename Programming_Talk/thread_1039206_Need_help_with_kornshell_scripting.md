---
title: "Need help with kornshell scripting"
date: 2009-01-14
forum: Programming Talk
---

### Post by DFord425 on 2009-01-14
I want to make a program that will tar a whole directory. I did that but when testing, i ran into a problem with files owned by root and since this will be used by people other than root, i cannot get permission to those files. What i want to do is make an exclude list for the tar command, so I use the ls -la to list all the files and i use a grep to find the ones owned by root, and a redirect that to another file. 
My question is, how to I parse the file for just the file names, and get past the rest of the ls -l output?

Thanks in adavance

---

