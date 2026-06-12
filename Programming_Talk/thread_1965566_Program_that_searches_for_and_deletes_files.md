---
title: "Program that searches for and deletes files"
date: 2012-04-26
forum: Programming Talk
---

### Post by keeganxvx on 2012-04-26
So, I don't have any experience with programming, but I'm looking to write an .exe file.

What I want it to do is automatically search for files/folders with certain keywords and delete them. So for example, the program is run and it searches in your computer for things containing the words: video, blah, blah2, etc and deletes those files.

I would also want it to display an image in the background, and then have a loading bar while it deletes the files.

How do I go about this?

---

### Post by Tony Flury on 2012-04-26
Firstly : 

You say you want a ".exe" file - can I assume then you want to write a program for Windows ? The reason i ask is that linux does not have .exe files - it has executable files (which can have any suffix you want).

Secondly : 
what language are you planning to write this in - in some languages this will be a lot easier than others.

Thirdly : 
I would imagine when you delete files based on such criteria, you would probably want to have a capability to confirm the file you are about to delete with the user - to prevent an accidental deletion.

---

### Post by coldraven on 2012-04-26
Maybe learn to program in Python, there a loads of tutorials out there.
Here's one you can download, Volumes 2 and 3 are also available .
[http://fullcirclemagazine.org/issue-py01/](http://fullcirclemagazine.org/issue-py01/)

---

### Post by keeganxvx on 2012-04-26
Yeah, it would be for Windows.

The language I know anything about would be c++, so I guess that? Would there be anything easier?

I might use Python, I had used it a little bit for game developing before.

---

### Post by ofnuts on 2012-04-26
> **keeganxvx said:**
> So, I don't have any experience with programming, but I'm looking to write an .exe file.

What I want it to do is automatically search for files/folders with certain keywords and delete them. So for example, the program is run and it searches in your computer for things containing the words: video, blah, blah2, etc and deletes those files.

I would also want it to display an image in the background, and then have a loading bar while it deletes the files.

How do I go about this?You are looking for the keywords in the file contents or in the file name?

In Linux (or with a Unix shell for Windows, suh as cygwin or msys) this is as simple as 
```

find . -exec grep "keyword" {} \; -delete
find . -name "*keyword*" -delete

```

---

### Post by keeganxvx on 2012-04-26
> **ofnuts said:**
> You are looking for the keywords in the file contents or in the file name?

In Linux (or with a Unix shell for Windows, suh as cygwin or msys) this is as simple as 
```

find . -exec grep "keyword" {} \; -delete
find . -name "*keyword*" -delete

```

So if I made that into a program and opened it in Windows would it work?

---

### Post by ofnuts on 2012-04-27
> **keeganxvx said:**
> So if I made that into a program and opened it in Windows would it work?Not really a "program" but more accurately a shell script. Note that the "find" command above isn't the Windows one (it's closer to a "dir /s"), but a Unixish one (provided in the mentioned Unix shell environments  for windows)

---

### Post by snowz on 2012-04-28
Btw, your app should be limited somehow, so that it would only search and delete files that are safe to be deleted. By that i mean, make sure that it doesn't screw up your OS or applications.

Example: It deletes some file from the gimp folder and gimp can't work properly after

---

