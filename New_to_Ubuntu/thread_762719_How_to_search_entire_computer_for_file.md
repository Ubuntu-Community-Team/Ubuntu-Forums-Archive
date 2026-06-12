---
title: "How to search entire computer for file"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by billmik on 2008-04-22
Whats the best way to search all of ubuntu drive for a particular file? Tracker search tool doesn't seem to search everywhere. Is there another search tool like the one windows uses?

---

### Post by philinux on 2008-04-22
> **billmik said:**
> Whats the best way to search all of ubuntu drive for a particular file? Tracker search tool doesn't seem to search everywhere. Is there another search tool like the one windows uses?

Places - down the bottom > search for files.

---

### Post by Joeb454 on 2008-04-22
Using the method **philinux** mentioned you will need to change "Search in folder" to be "Filesystem" :)

---

### Post by billgoldberg on 2008-04-22
> **billmik said:**
> Whats the best way to search all of ubuntu drive for a particular file? Tracker search tool doesn't seem to search everywhere. Is there another search tool like the one windows uses?

 The only files I need to search for are music files (to much to navigate properly). I use "places -> search for files" and it always find the files in seconds.

There is the "deskbar applet" but I never used it.

You can use the terminal to search for files. Google for it as I've never used this.

According the the [ubuntu wiki]("https://help.ubuntu.com/community/MetaTracker#head-bfed826323f0fb1789b955aad48bef80111a2163") there are other search applications.

- beagle (I've heard this one isn't friendly on resources, but I never used it)
- strigi
- recoll

---

### Post by sayakb on 2008-04-22
I use catfish (I find it versatile)
```
sudo apt-get install catfish
```Then goto Applications->Accessories->File Search

---

### Post by enigmaniac23 on 2008-04-22
from the terminal:

cd /
sudo find -name file_name -print



Using this, you can also find the hidden files.  I don't think that searching from Places-->Search for files will show hidden files.

Example:
cd /
sudo find -name .bash_history -print
[sudo] password for user: 
./home/user/.bash_history

---

### Post by billgoldberg on 2008-04-22
> **enigmaniac23 said:**
> from the terminal:

cd /
sudo find -name file_name -print



Using this, you can also find the hidden files.  I don't think that searching from Places-->Search for files will show hidden files.

Example:
cd /
sudo find -name .bash_history -print
[sudo] password for user: 
./home/user/.bash_history

"Search for files" can look for hidden files. But you'll need to enable it in the "select more options" drop-down menu. This will take longer than normal searches.

---

### Post by billmik on 2008-04-22
Thanks catfish is exaxtly what i was looking for

---

### Post by tyroeternal on 2008-04-22
I've always been a big fan of slocate.

> Secure Locate provides a secure way to index and quickly search for  files on your system. It uses incremental encoding just like GNU locate to compress its database to make searching faster, but it will also store file permissions and ownership so that users will not see files they do not have access to.

It searches quickly, and can be updated quickly if you are searching for something you just saved with.
```
sudo updatedb
```
Then you can just use:
```
slocate nameOfFile
```
which views all the files you can see.  Or if you want to search all the files in the system just use sudo along with it to see everything.

---

