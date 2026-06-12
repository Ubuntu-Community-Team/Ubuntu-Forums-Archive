---
title: "Cd command no worky?"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by dhinderliter on 2008-09-03
danielle@danielle-laptop:~$ cd desktop
bash: cd: desktop: No such file or directory
danielle@danielle-laptop:~$ ls
Desktop    Examples  Photos    Public     Videos
Documents  Music     Pictures  Templates
danielle@danielle-laptop:~$ cd music
bash: cd: music: No such file or directory
danielle@danielle-laptop:~$ cd photos
bash: cd: photos: No such file or directory
danielle@danielle-laptop:~$ cd videos
bash: cd: videos: No such file or directory
danielle@danielle-laptop:~$ 



heres what it says when i try to use cd command. am i doing it wrong?
i'm reading this [tutorial]("http://ubuntuforums.org/showthread.php?t=73885&highlight=linux+commands").

---

### Post by Tatty on 2008-09-03
Linux is case-sensitive, so you must use the proper capitalisation of the folder you are trying to reach, try:

```
cd Desktop
```

---

### Post by OutOfReach on 2008-09-03
The command line is case sensitive, so try Desktop, Music, Videos, etc...

EDIT: Darn, Beaten by a second. :)

---

### Post by Tatty on 2008-09-03
> **OutOfReach said:**
> EDIT: Darn, Beaten by a second. :)


I win!  lol :popcorn:

---

### Post by Presto123 on 2008-09-03
Remember that it is case sensitive for one.

Second, you need to navigate to the whole file:
```
blah@blah-desktop: cd Desktop/pictures
```

Try that and see what it gives you.

---

### Post by Presto123 on 2008-09-03
Har har...Quickdraw McGraw :P

---

### Post by OutOfReach on 2008-09-03
> **Tatty said:**
> I win!  lol :popcorn:

By a second. ;)

---

### Post by jemate18 on 2008-09-03
> **dhinderliter said:**
> danielle@danielle-laptop:~$ cd desktop
bash: cd: desktop: No such file or directory
danielle@danielle-laptop:~$ ls
Desktop    Examples  Photos    Public     Videos
Documents  Music     Pictures  Templates
danielle@danielle-laptop:~$ cd music
bash: cd: music: No such file or directory
danielle@danielle-laptop:~$ cd photos
bash: cd: photos: No such file or directory
danielle@danielle-laptop:~$ cd videos
bash: cd: videos: No such file or directory
danielle@danielle-laptop:~$ 



heres what it says when i try to use cd command. am i doing it wrong?
i'm reading this [tutorial]("http://ubuntuforums.org/showthread.php?t=73885&highlight=linux+commands").

It is case sensitive ... Try (Assuming you are in home directory)
danielle@danielle-laptop:~$ cd Desktop

or

danielle@danielle-laptop:~$ cd Music

or

danielle@danielle-laptop:~$ cd Videos

---

### Post by iaculallad on 2008-09-03
Say, when you're outside of your HOME directory (Assuming you're in the / directory) and want to CD to your Desktop, you could just do:

```
cd ~/Desktop
```

The ~ (tilde) sign represents your HOME directory.

---

### Post by dhinderliter on 2008-09-04
ah case sensative....well that works!! 

jeeze so much to remember. now i feel really blond...thanks for the help quickdraw! :lolflag:

---

### Post by jemate18 on 2008-09-04
> **dhinderliter said:**
> ah case sensative....well that works!! 

jeeze so much to remember. now i feel really blond...thanks for the help quickdraw! :lolflag:

Please mark this thread SOLVED

---

### Post by Corrupt3d on 2008-09-04
btw, when your listing directories or navigating the file system throught the terminal, you can use "tab" to autocomplete, most of the time you can just type the first few letters, great way to avoid typos or avoid writing out long cryptic names.
If it doesn't auto complete, then check your spelling, or hit tab again to see all files that begin w/ the same name.

---

