---
title: "computer search tools"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by JBA2337 on 2008-05-25
In Ubuntu, I noticed that there are several different search tools that can be used to search for files or folders on my computer. Having used Windows before (which only has one search tool) I am a bit confused by all of this. in Ubuntu, which search method is the fastest and the best choice to use when I am looking for a specific file or a set of files on my computer?

The following search tools are in my Ubuntu 8.04 Hardy Heron installation. Some use indexing, and some don't.

(1) Desktop Search (beagle search)...uses indexing
(2) Tracker Search...uses indexing
(3) Search for Files (gnome search tool)...don't
    know if this one uses indexing
(4) Search for files as root, using Nautilus file
    browser...don't know if this one uses indexing
(5) Deskbar Applet ("Show Search Entry")...don't
    know what this one is or what it is used for


JBA2337

---

### Post by sayakb on 2008-05-25
Use catfish. It is versatile.

---

### Post by JBA2337 on 2008-06-01
Thanks for your help. I tried Catfish and I like it. By the way, does Catfish use indexing?

Do you ever use, or need to use any of the other search tools that come with Ubuntu?

JBA2337

---

### Post by sayakb on 2008-06-01
I don't use any search tools. I have my documents organized, and use the banshee music player library to search for music.
More about [Catfish.]("http://software.twotoasts.de/?page=catfish")
Catfish just provides a GUI of the commands you issue in the terminal.

---

### Post by unutbu on 2008-06-01
There are also two command-line tools: locate and find.

```
locate menu.lst
```
finds all files on your system whose filename contains the string "menu.lst" anywhere in its name. It uses an index, /var/lib/slocate/slocate.db

```
find / -name menu.lst
```
find is slower because it is not indexed. The command above finds files whose filename exactly matches menu.lst. find is a very useful command to learn if you ever want to write bash scripts or do more complicated searches.

For example:

```
find $HOME -mtime 0
```
finds every file in your home directory or subdirectories which has been modified in the last 24 hours.

```
sudo find /  -mmin -60 | grep -v '^/sys' | grep -v '^/dev' | grep -v '^/proc' 
```
finds all files modified in the last 60 minutes.

```

find . -type f -exec grep "Top Secret" /dev/null {} \; 
```
finds every file which contains the string "Top Secret". It searches the current directory and all its subdirectories.

For more information, type
```
man locate
man find
```

---

