---
title: "Curious about writing to file"
date: 2007-12-18
forum: Programming Talk
---

### Post by Kenchu on 2007-12-18
I'm pretty new to Ubuntu and linux. I've noticed that usually all programs save their stuff @ homefolder with . (dot) appname. Just wondering if this "feature" is in the OS itself, or something programmers choose to implement themselves? Because I've got a Java IRC client, and it is saving stuff to a hidden folder in home. That made me think how it was implemented. Because java programs work on practically all OS. So was that part with writing files specialized, or is it something the OS handles itself?

Thx

**EDIT**

I must've explained myself confusingly. I meant more like the path to the file. Does the program have different implementations for each OS (with different paths), or is it the same for each (kinda like "save to user docs" or something, that results in My Documents if in windows, or Home if in linux, for example).

---

### Post by Majorix on 2007-12-18
It is programmers who specify to save files that start with a dot. It is NOT the OS.

---

### Post by ghostdog74 on 2007-12-18
the "dot" in front of a file name/dir is supposed to be *nix way of specifying hidden files. IT IS an OS "feature". But whether to save files as hidden, is entirely up to whoever.

---

### Post by Kenchu on 2007-12-18
I must've explained myself confusingly. I meant more like the path to the file. Does the program have different implementations for each OS (with different paths), or is it the same for each (kinda like "save to user docs" or something, that results in My Documents if in windows, or Home if in linux, for example).

---

### Post by cwaldbieser on 2007-12-18
> **ghostdog74 said:**
> the "dot" in front of a file name/dir is supposed to be *nix way of specifying hidden files. IT IS an OS "feature". But whether to save files as hidden, is entirely up to whoever.

Isn't it more of a feature of the "ls" command and some window managers, rather than the OS?

---

### Post by ghostdog74 on 2007-12-18
> **cwaldbieser said:**
> Isn't it more of a feature of the "ls" command and some window managers, rather than the OS?

you can put it that way since you can use ls to see hidden files w/o using -a. however, if you have hidden files in a directory and you do a rm *, normally, those hidden files won't get deleted.

---

### Post by Majorix on 2007-12-18
> **Kenchu said:**
> I must've explained myself confusingly. I meant more like the path to the file. Does the program have different implementations for each OS (with different paths), or is it the same for each (kinda like "save to user docs" or something, that results in My Documents if in windows, or Home if in linux, for example).

Sorry I got you wrong.

Yes there are different implementations for each OS in cross-platform programs. Usually, in the sourcecode, there is something that creates a folder in the user's home or Program Files folder or wherever. If you would like, consider this pseudo-code example:

```
if OS is Windows
   install to Program Files\program name
else if OS is Linux
   install to users_home/.program_name
.
.
.
```
You get the idea.

You can see a sourcecode for a cross-platform program to see the idea I explained here in action.

It is nice of you to try to learn the insights to your OS :)

---

### Post by tyoc on 2007-12-18
mmmm... :S.

It is a convention that if you will only store a single file, then you do it in home in a file for your app ~/.appname if you gona have more than 1 file for your app configuration, then it should be inside a hiden folder.

Like I know the dot file is also a convention between one of this: tools accessing FS or the FS.

---

### Post by LaRoza on 2007-12-18
> **Kenchu said:**
> I'm pretty new to Ubuntu and linux. I've noticed that usually all programs save their stuff @ homefolder with . (dot) appname. Just wondering if this "feature" is in the OS itself, or something programmers choose to implement themselves? Because I've got a Java IRC client, and it is saving stuff to a hidden folder in home. That made me think how it was implemented. Because java programs work on practically all OS. So was that part with writing files specialized, or is it something the OS handles itself?


The languages that have an interpreter or a virtual machine (Java, Python, etc) have the implementation of the file and directory handling internally so the programmer doesn't have to think about it.

In Python (for example) you can specify a path without worrying if the slashes are right. 

As for the programs themselves, it is the programmer who choses to follow the convention. I have a few GNU Software ported to Windows, and they have .something files in my "home" directory, so it is not a feature of the OS.

---

### Post by Kenchu on 2007-12-18
Thx. I got what I was looking for. :)

---

