---
title: "File locking shell script"
date: 2008-02-22
forum: Programming Talk
---

### Post by adza on 2008-02-22
Hi There, i'm currently having some issues trying to resolve what i think should be a fairly simple issue... i'm currently working on a project where we are creating an EDI connection with one of our customers. I have a samba shared directory on my unix machine (the ERP platform) where the EDI process writes to a file full of orders, until i come and pick it up and move it elsewhere in the file structure.. What i want to know is, can i use a unix command to check to see if anyone is writing to that file before i grab it (or can i apply an exclusive lock to that file)? I can't grab the file with half an order being written to it at the moment i grab it.. am i being niaive here? this sounds like it should be really simple....

---

### Post by Zwack on 2008-02-22
There are multiple ways of locking a file unfortunately.  And unless you know the mechanism that the ERP system is using then you can't guarantee that you are using the same system.  Not all of these are available from the shell as far as I know.

You  could use fuser to see what has the file open but beware of potential race conditions.

It's also possible that the ERP opens the file once and keeps the file handle in which case there isn't much that you can safely do.

I'd suggest trying fuser yourself to make sure that the file is normally closed, and then consider something like this...
[code]
while `fuser ${file}`
do
  echo "the file is in use"
done
cp ${file} ${file2}
echo > ${file}
[\code]

Now $file2 is yours to do what you want with.  This has a race condition, but without knowing what file locking is being done on the file, and given that you are doing this within a shell, it's as good as you're likely to get...  Any improvements I can think of still have race conditions... 

Z.

---

### Post by lnostdal on 2008-02-22
this sounds like a good time to switch to a storage system that supports concurrency .. PostgreSQL for instance

---

