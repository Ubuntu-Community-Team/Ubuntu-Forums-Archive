---
title: "Rename Program Do you know any?"
date: 2012-09-11
forum: New to Ubuntu
---

### Post by Pletched on 2012-09-11
So I'm looking for a rename program similar to the [antRename]("http://www.antp.be/software/renamer") on Windows. I use the enumerate feature a lot to rename a batch of files. 

Anything close to that program with an enumerate function will do. 

I don't want suggestion. Leave those out. I want something you've tested, used and found useful.

---

### Post by sisco311 on 2012-09-11
GUI:
[list]
[*]thunar (file manager)
[*]**gprename** 
[*]gnome-commander (file manager)
[*]purrr 
[*]pyrenamer 
[*]gwenrename 
[*]**krename** 
[/list]

CLI:
[list]
[*]rename 
[*]prename #aka rename on Debian and Debian based distos
[*]mmv
[*]<bash/csh/dash/ksh/zsh/any other shell> #you can write your own shell script :evil:
[/list]

---

### Post by varunendra on 2012-09-12
+1 to **krename** for GUI and **rename** for CLI. I've been using both and both are powerful and flexible.

> **sisco311 said:**
> 
[LIST]
[*]<bash/csh/dash/ksh/zsh/any other shell> #you can write your own shell script :evil:
[/LIST]
:lolflag:

---

### Post by dargaud on 2012-09-12
I second the krename and rename choices, but a word of warning: there are actually 2 different command line programs called 'rename', depending on the version of Linux:
```
RENAME(1)   Perl Programmers Reference Guide
NAME       rename - renames multiple files
SYNOPSIS   rename [ -v ] [ -n ] [ -f ] perlexpr [ files ]

```
```
RENAME(1)  Linux Programmer’s Manual
NAME       rename - Rename files
SYNOPSIS   rename from to file...

```

---

### Post by Grenage on 2012-09-12
For renaming with substitution, I've always used a *for* loop, with sed.  It's not a nice GUI package, but I do most of my file management over SSH:

```
for in *
do
  mv "$f" $(echo "$f" | sed 's/lalalalala\.\([0-9][0-9]\).*/rararara\.\1\.things')
done
```

A rough, if inelegant example of what I do.

---

### Post by Pletched on 2012-09-12
> **Grenage said:**
> For renaming with substitution, I've always used a *for* loop, with sed.  It's not a nice GUI package, but I do most of my file management over SSH:

```
for in *
do
  mv "$f" $(echo "$f" | sed 's/lalalalala\.\([0-9][0-9]\).*/rararara\.\1\.things')
done
```A rough, if inelegant example of what I do.

That is a nice script! Though I don't know how it completely works. :D I now the basics of mv and sed (just the substitution part).

I've picked Purrr. It's simple, fast, but no documentation. I tried krename and gprename, none of them are what I wanted. gprename doesn't add zeros before numbers, which is what I wanted. example, 001, 002, 003.

I need documentation for purrr. I searched wiki and purrr's website. I didn't find anything. A picture on software center helped a little. I grasped the basics of renaming from that.

---

