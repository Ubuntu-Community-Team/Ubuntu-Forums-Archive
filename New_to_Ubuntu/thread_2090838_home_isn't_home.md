---
title: "home isn't home"
date: 2012-12-03
forum: New to Ubuntu
---

### Post by Elect GMax on 2012-12-03
The "home" folder in the GUI has lots of other folders in it like Desktop and now my un-tarred NDISwrapper folder. However, when I'm in the terminal at GMax@Waterwalker-II/home:~$ or whatever, typing "cd desktop" or "cd ndiswrapper-1.58rc1" gives me Bad Command or File Name (or whatever the Linux equivalent is).

Look, I get the "not user friendly" bit, but is "at least as user-friendly as DOS" really so much to ask? What's going on here?

---

### Post by Tony Flury on 2012-12-03
File names and folder names are case sensitive under Linux. 

So "desktop" and "Desktop" are two different things 

Use the "ls" command to see the files that exist in your current directory. 

You can also use Tab completion : for instance type "cd D" and press TAB - the command line will then complete the name of the folder if one exists beginning with a capital D.  Pressing TAB twice will give you a list of all matching file names. 

TAB completion doesn't just work with the cd command.

---

### Post by linux4me on 2012-12-03
Home typically has a number of folders in it even in a clean installation, including Desktop, Documeents, Downloads, Music, Pictures, etc.

Your failed commands are probably because Linux is case-sensitive, so using "cd desktop" will get you a:
```
bash: cd: desktop: No such file or directory
```
error if you're trying to change to the Desktop directory and you don't have a "desktop" directory in the current folder.

Try:
```
cd Desktop
```
from your /home directory prompt, or:
```
cd ~/Desktop
```
to go to the Desktop folder in your current user's /home directory from elsewhere in the file system.

---

### Post by Elect GMax on 2012-12-03
Typing "cd Desktop" didn't work any better than "cd desktop" did.

There are no capital letters in my ndiswrapper directory.

WHY LINUX HATE ME?

EDIT: this works:

> **linux4me said:**
> ```
cd ~/Desktop
```to go to the Desktop  folder in your current user's /home directory from elsewhere in the file  system.

Absolutely NOTHING else opens with the cd command, but the above command works. Thanks!

I can now get Internets with Ubuntu. This is the first post that I'm making from my Ubuntu installation.

YAAAAAAY

---

### Post by linux4me on 2012-12-03
> **Elect GMax said:**
> WHY LINUX HATE ME?

Maybe it's something you did? :P

Seriously, if you copy-and-paste the output of Terminal when you're trying the commands so we can see the command prompt (your location) and the exact error message, maybe someone can help you.

---

### Post by deadflowr on 2012-12-03
> Absolutely NOTHING else opens with the cd command

It's not suppose to open anything, cd only changes where you're sitting/standing in the file system at that time.

You can use the ls command to see what is in the directory you're in at the moment.
If you use ls, look to see if you have both a desktop and a Desktop.

You can always man the command to get even better understandings.

```
man commandname
```

---

### Post by Elect GMax on 2012-12-03
Okay, well, I WAS getting Internet a while ago. Now I have to go back to  Windows if I want to Internet because Ubuntu keeps trying and failing  to connect :(

But whatever. The tars got un-tarred correctly, the  drivers got ndiswrapped correctly, and now I just have to ask Starbucks  to make their signal strength suck less, I guess.

> **linux4me said:**
> Seriously,  if you copy-and-paste the output of Terminal when you're trying the  commands so we can see the command prompt (your location) and the exact  error message, maybe someone can help you.

As long as I'm having wi-fi problems, this isn't going to be a reliable option.

> **deadflowr said:**
> It's not suppose to open anything

It opens directories.

Also, the word is "supposed".

---

