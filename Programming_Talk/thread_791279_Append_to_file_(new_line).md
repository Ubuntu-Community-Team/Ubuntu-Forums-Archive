---
title: "Append to file (new line)"
date: 2008-05-12
forum: Programming Talk
---

### Post by ccc0219 on 2008-05-12
Hi, I'm trying to create a script that asks for directories to exclude in a system backup.  I was trying to have the input as space separated and append to an exclude file with each directory as a new line in the exclude file.  What's the easiest way to do this or am I going about this the wrong way?  Here is what I have so far with it appending it as space separated in the exclude file.  


[I]echo -n "Enter directories to be excluded in the backup... :"
read response4
for i in "$response4"; do
	echo "$i" >> /tmp/backuptmp.lst
done[/I]

---

### Post by ccc0219 on 2008-05-12
wow.. just realized tar accepts space separated lists... sorry for the stupid post

---

