---
title: "compare Linux distros by exporting directories and files to excel"
date: 2015-02-13
forum: New to Ubuntu
---

### Post by bill78 on 2015-02-13
Hi all, new to the forum, and I'm a beginner.  I have two versions of Linux distros. I'd like to do a side-by-side comparison by exporting all of the directories and files with each directory to Excel and see the delta.  I've read many threads but they don't seem to be pertaining to what I'm looking for. Any suggestions? Thank you.

---

### Post by nerdtron on 2015-02-13
I don't know what you are trying to achieve but if you want to list all files and folder (which is too many I think) you can do so.
from the terminal:
```
 sudo find / > listingA.txt 
```

It will take a while to output all filenames, but in the end, you will have a list of all files on the file "listingA.txt". You can import this in excel.
If there are too many files, perhaps you can define which directories you want to compare?

---

### Post by ian-weisser on 2015-02-13
Nerdtron is right. That's not a useful exercise for a beginner.
The output will be enormous, cryptic, and unhelpful.

Rather like comparing two bicycles by comparing rim sizes and spoke counts and gear ratios. It tells you little about which bike is more enjoyable to ride.
If you really want to compare two distros, *use* each of them for a few months.

---

### Post by bill78 on 2015-02-18
Thanks for the input.  I got ahold of a foreign Linux OS which I believe is 90% based on Ubuntu. I'd like to find out the rest of the 10% of the directories and files. I thought I can compare the directories and files and come up with the variances.

---

### Post by tgalati4 on 2015-02-19
I agree, not helpful for a new user, but since you asked:

Install *tree*.  

```
sudo apt-get install tree
man tree
cd
tree > my_huge_directory_tree_listing_while_I_am_trying_to_learn_linux.txt
```

You can change the output file to something shorter:  my_huge_directory_tree_listing_while_I_am_trying_to_learn.txt

---

### Post by grahammechanical on 2015-02-19
Slightly more useful, in my opinion, for your task is to use either,

```
dpkg --list
```

or

```
apt-cache pkgnames
```

The first command lists all the installed packages a Debian/Ubuntu based distribution. The second command, I think, lists all the packages in system. Do you not think that a comparison of installed packages is more educational than comparing folders and files?

[http://www.cyberciti.biz/faq/howto-display-list-of-all-installed-software/](http://www.cyberciti.biz/faq/howto-display-list-of-all-installed-software/)

Regards.

---

