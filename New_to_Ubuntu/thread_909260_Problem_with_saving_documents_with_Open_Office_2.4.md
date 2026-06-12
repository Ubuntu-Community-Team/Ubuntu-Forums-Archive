---
title: "Problem with saving documents with Open Office 2.4"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by pkj on 2008-09-03
Hi,

Whenever i create a new document and try to save it, i get the following error message

Due to an unexpected error OpenOffice.org crashed. All the files you were working on will now be saved. The next time Openoffice.org will be launched, your files will be recovered automatically.

How to resolve this problem

pkj

---

### Post by philinux on 2008-09-03
Open a terminal and use this.

ooffice -writer %U

Post the errors.

---

### Post by pkj on 2008-09-03
Gives the following error

/home/pradeep/%U does not exist

pkj

---

### Post by philinux on 2008-09-03
Run it from the terminal without the %u

Try saving a doc and see what error spits out.

---

### Post by gjoellee on 2008-09-03
I have had the same error, but I noticed that I didn't named the documents anything...

---

### Post by pkj on 2008-09-03
Running the command without %u gives the same error...

Saveas option also gives the same error...

pkj

---

### Post by philinux on 2008-09-03
```
ooffice -writer
```

Copy and paste into a terminal.

On my system this just fires up open office.

Copy and paste all messages following this command.

---

### Post by pkj on 2008-09-03
ooffice -writer

Command opens OpenOffice2.4
Takes me directly to the recovery option (for the last closed document)
After recovery...Opens OpenOffice Writer
I type in something
Again Trying to save gives the error
Due to an unexpected error OpenOffice.org crashed. All the files you were working on will now be saved. The next time Openoffice.org will be launched, your files will be recovered automatically.

pkj

---

### Post by philinux on 2008-09-03
Were there no other error messages in the terminal?

Make sure Open office is not running. 

Go to your home folder. Press ctrl h to show hidden files.

Delete this file.

.openoffice.org2

It just contains config files and will be recreated when you fire up open office.

---

### Post by pkj on 2008-09-03
Dont exactly know how to reach the home folder

tried /home

ctr h however does not shou anything...

pkj

---

### Post by Tatty on 2008-09-03
> **pkj said:**
> Dont exactly know how to reach the home folder

tried /home

ctr h however does not shou anything...

pkj

Clicking Places->Home will give you your home folder, and is the best option for this task.

Though if you want to navigate to it via the terminal the "cd" command will change directory, so:
```
cd /home/[your-user-name]/
```
will take you to your home folder

However the ~ symbol acts as a short-hand method of saying "my home folder", so you would type:
```
cd ~/
```
and that would also take you to your home folder.

---

### Post by giosimar on 2008-09-07
I have the same problem ALSO with evince and evolution.

everytime a trie to save something, the application crashes.
in evolution is impossible to save any attachment.

using the same softwares in kde this problem disappears.

---

