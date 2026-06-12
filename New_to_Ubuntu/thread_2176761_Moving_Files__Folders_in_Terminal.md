---
title: "Moving Files / Folders in Terminal"
date: 2013-09-25
forum: New to Ubuntu
---

### Post by aaron-huddleston30 on 2013-09-25
Yeah I am a beginner lol.  Just a quick question.

I have read up on all the ways to move files and directories in the Terminal but for some odd reason nothing is ever working for me.  Here is the current situations I am running into.

I created a folder called GPU Test onto my Desktop.  Problem is when I try to cd /user/me/Desktop/GPU Test 
it will say that there is no such directory.

Same is happening when I try to move files.  Say I created a file inside the Documents folder and want it moved to the GPU Test folder.

if I try 

> mv user/me/Documents/[I]documentname
 
[/I]then what?  Do I just use a space betw*een **documentname* and the folder I want to send it to?  All the examples so far have been ... for some reason using ............. type syntax all over the actual code line so its impossible to read what they actually mean.

would the end line read: > mv user/me/Documents/*documentname* user/me/Desktop/GPU Test
?

Or is there something I have to put between the 2 directories?

Then of course I have to figure out why I simply can't even go into the GPU Test folder on my desktop from the Terminal.  That one is really confusing me.

---

### Post by whitesmith on 2013-09-25
If only all problems were so simple! The issue is that unadorned cd parses your command as if you had written```
cd /user/me/Desktop/GPU
```In other words, it sees the space as a separator and naturally can't find the nonexistent directory (GPU). You need to do this ```
cd '/user/me/Desktop/GPU Test'
``` Try it with single (or double) quotes and let me know the result.

---

### Post by Impavidus on 2013-09-26
All those command like cd, mv, cp, rm etc. use space as a separator. In fact, it's a property of the shell, not of the commands themselves. To use files or directories with space in their names you either quote the name ("like this" or 'like this', there's a slight difference between them) or you escape\ all\ spaces\ with\ backslashes.

---

### Post by oldos2er on 2013-09-26
```
mv user/me/Documents/*documentname* user/me/Desktop/GPU Test
``` For this to work you'd need a couple small changes. As mentioned, use \ to escape the space in GPU Test. If you use tab completion the shell will do this for you.

When moving a file to a certain folder, always use a trailing /. Here's what I mean: ```
mv user/me/Documents/*documentname* user/me/Desktop/GPU\ Test/
``` Reason being that mv can also function as a rename command, so in your original command above the shell would move *documentname* to the Desktop folder and rename it to GPU Test. The trailing / tells the shell to move the file to the existing folder GPU Test and nothing more. Hope that's clear.

There's a free PDF [here]("http://sourceforge.net/projects/linuxcommand/files/TLCL/13.07/TLCL-13.07.pdf/download"), it's a good tutorial on learning the command line and I think you would benefit by taking a look at it. I've been using Linux for six years and I still refer to it quite a bit myself.

---

