---
title: "[SOLVED] associate path with command line"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by orad on 2008-07-19
Hey all!

I just registered for the forums, but make no mistake - there have been plenty of times when I solved problems by just browsing. It's how I got my wireless card to work (thanks!!)

I've been fiddling with ubuntu since 7.04 (not much, though - I still dual-boot to Windows) and have lately been using some linux-only programs for work. I've just installed matlab (new program) for work, and I can get it to run, but only if I navigate to a certain path to call the program. That is, if I just type 'matlab' in the command line, the program won't work. Is there a way I an perminantly associate that command with the path? (I'm pretty sure I'm using completely wrong terminology, and so i apologize).

I'd also like for the program to appear in the "Applications" menu, but I've read up on it in the forum, and it seems to be hard, if not impossible, unless the program comes installed in a package with ubuntu (right?) so i'll settle for a command line hack.

I'm running 8.04 on an Hp Pavilion laptop.

Thanks!

---

### Post by hyper_ch on 2008-07-19
adding it to applications menu:
run
```

alacarte

```
and make a manual entry

---

### Post by Locutus_of_Borg on 2008-07-19
fast sloppy way to do it is
```
 sudo ln -s /path/to/matlab /usr/bin/matlab
```

thats assuming /usr/bin is already in your path

i do not recall the proper way to add a directory to your path, and so have been using that method for some time now with no problems

right clicking on your menu should allow you to add new items

---

### Post by t0p on 2008-07-19
You could add an alias to your .bashrc file. Something like
```
alias matlab='/path/to/matlab'
```

---

### Post by orad on 2008-07-19
both alacarte and right-clicking the menu worked. Thanks for that, it'll have to do for now, since I haven't figured out the rest of Locutus' advice.

Is it strange that I have matlab installed in a path something like this:

[PHP]usr/bin/matlab/bin/matlab[/PHP]
Thats what I need to type to run it.

So I tried 
[PHP]sudo ln -s /usr/bin/matlab/bin /usr/bin/matlab[/PHP]

and
[PHP]sudo ln -s /path/to/matlab /usr/bin/matlab[/PHP]
like a genius, and several permutations of the above. In all cases "bash: matlab: command not found".

What am I doing wrong?

---

### Post by erfahren on 2008-07-19
> **orad said:**
> 
Is it strange that I have matlab installed in a path something like this:

[PHP]usr/bin/matlab/bin/matlab[/PHP]
Thats what I need to type to run it.

So I tried 
[PHP]sudo ln -s /usr/bin/matlab/bin /usr/bin/matlab[/PHP]

and
[PHP]sudo ln -s /path/to/matlab /usr/bin/matlab[/PHP]
like a genius, and several permutations of the above. In all cases "bash: matlab: command not found".

What am I doing wrong?
I see what you did wrong - but first you need to remove that first symbolic link you made - so do:
```

sudo rm /usr/bin/matlab

```
then make it like:
```

sudo ln -s /usr/bin/matlab/bin/matlab /usr/bin/matlab

```
that should do it

EDIT: oops! Zack is right. That remove line I wrote should have spit out an error message though - sorry!

---

### Post by Zack McCool on 2008-07-19
neither of those will work, for the following reasons:
```

ln -s /usr/bin/matlab/bin /usr/bin/matlab

```

a) you have not named the object.  /usr/bin/matlab/bin is the directory, you want to link to the executable.  BUT
b) /usr/bin/matlab already exists (as a directory).  You cannot create it as a link, as that is a conflict.

You could do this:
```

ln -s /usr/bin/matlab/bin/matlab /usr/bin/matlab1

```

Then execute matlab1.  OR, you could do:
```

ln -s /usr/bin/matlab/bin/matlab /home/YOURUSERNAME/matlab

```

and run ./matlab when you log in...

---

### Post by orad on 2008-07-19
Did I install the program wrong that it looks like bin/matlab/bin/matlab? it asked for a directory, so I specfied usr/bin/matlab so that it would be in its own directory. I did some searching, it said that usr/bin is the closest thing to "Program files" in Windows, although not exactly. If I had it install directly to just /usr it would have sorted all the files to the right places and associated the command "matlab" with the program, right?

Well, you make a mistake only once. Are programs easy to un-install? I know how to re-install...

Anyhow, thanks zack, I've done what you said, and it worked. To see if I understand properly, though:

ln: makes a link between 2 paths (a windows "shortcut" if you will).
-s: symbolic link. I don't know exactly what this means.
/usr/bin/***: whatever *** is the program that gets run in bash. but if I have another program with that same name in the directory I'm in, I'd run ./*** instead, right?

Thank you!!

---

