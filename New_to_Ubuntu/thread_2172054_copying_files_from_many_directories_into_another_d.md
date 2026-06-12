---
title: "copying files from many directories into another directory"
date: 2013-09-03
forum: New to Ubuntu
---

### Post by peragrate2 on 2013-09-03
Hi, I have a lot of pdfs in location /storage/books. Within the books directory are thousands of subdirectories, some with their own subdirectories. I've scowered the Internet to find a solution, but none of them seem to work. I'm using 10.0.4 lucid. Can some tell me how to copy all of these books, including the ones in multiple subdirectories, into another directory, say.../storage/a for simplicity.

Thank you and sorry if this is the wrong forum, I'm not sure where to put this one.

---

### Post by carl4926 on 2013-09-03
right click the folder books in /storage
go to /storage/a
right click paste

---

### Post by CaptainMark on 2013-09-03
I'm going to assume you don't want to manually select al the pdf's because of the mention of thousands of subdirectories, so the best way is to release the power of your terminal, search in the menu/dash for terminal and open it then type ```
find /storage/books -iname *.pdf -exec mv {} /new/location/ \;
```You just need to swap out the part /new/location/ with the end location of your choice and it must be an already existing directory.
This makes the assumption that 1) all pdfs are named with the .pdf extension 2) you have write access to the /storage directory (if not you'll need to prefix the command with sudo)

---

### Post by eternal243 on 2013-09-03
> **peragrate2 said:**
> Hi, I have a lot of pdfs in location /storage/books. Within the books directory are thousands of subdirectories, some with their own subdirectories. I've scowered the Internet to find a solution, but none of them seem to work. I'm using 10.0.4 lucid. Can some tell me how to copy all of these books, including the ones in multiple subdirectories, into another directory, say.../storage/a for simplicity.

Thank you and sorry if this is the wrong forum, I'm not sure where to put this one.

Just to be sure, as I understand it, you want to copy **"only"** the pdf-files and not the thousands of folders and subfolders that they are stored in? In that case use the suggestion above by CaptainMark.

Or do you want to copy the whole /storage/books/ directory including folders and subfolders?
If it is the second option you could simply copy the folder with copy paste, or if you need permissions I would use the rsync command with sudo.

Here is more information on rsync [http://www.the-tech-tutorial.com/?p=1242](http://www.the-tech-tutorial.com/?p=1242)

and here is an example that should work. 
```
sudo rsync -r /storage/books /storage/a
```

---

### Post by peragrate2 on 2013-09-03
> **CaptainMark said:**
> I'm going to assume you don't want to manually select al the pdf's because of the mention of thousands of subdirectories, so the best way is to release the power of your terminal, search in the menu/dash for terminal and open it then type ```
find /storage/books -iname *.pdf -exec mv {} /new/location/ \;
```You just need to swap out the part /new/location/ with the end location of your choice and it must be an already existing directory.
This makes the assumption that 1) all pdfs are named with the .pdf extension 2) you have write access to the /storage directory (if not you'll need to prefix the command with sudo)

Thank you CaptainMark, you knew exactly how to do what I needed, and saved me a great headache! Thanks again.

---

