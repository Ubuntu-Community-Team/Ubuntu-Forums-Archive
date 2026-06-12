---
title: "Create file add text to it in one command"
date: 2008-09-20
forum: Outdated Tutorials &amp; Tips
---

### Post by twizler on 2008-09-20
Create file,  add text to the file in one command

open a terminal window type:

>  echo  "The text you want added to a new file"  >>                     the_file_name

so simply put --
use echo command with quotes around the text " " then the >> tells the text to be put into a file name. 


Nice way to create a quick note - or make a super simple bash script. 

I use it this when i create a junk account on 10min mail so i dont forget the user name and password. 

Example: I just created the account on website forumpost.com bartsimpson with a password of 12345678: Now i want to quicky make a text file with that info in it. 


> EXAMPLE:
echo "Site name forumpost.com user: bsimpson password: 12345678" >> forum_account.txt

Now you have a file w/ this info in it. SIMPLE AS PIE


**

---

### Post by jpeddicord on 2008-09-20
Another way to do it is to use cat:

```
cat > filename
```

Run it, type the text you want to put into the file, then hit Ctrl-C to save & quit.

---

