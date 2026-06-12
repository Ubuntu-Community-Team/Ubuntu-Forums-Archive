---
title: "spaces in direcory names"
date: 2019-02-19
forum: New to Ubuntu
---

### Post by zak100 on 2019-02-19
Hi,
I created a folder "parallel processing programs" without quotes but t created 3 folders. Please guide me how to solve this problem. Can I have spaces in folder names?

```
  

@lc2530hz:~$ mkdir parallel processing programs
@lc2530hz:~$ cd parallel *
bash: cd: too many arguments
i@lc2530hz:~$ cd parallel*
@lc2530hz:~/parallel$ cd ..
@lc2530hz:~$ cd pARALLEL processing programs
bash: cd: too many arguments
@lc2530hz:~$ dir
aboutComputer                 forums\ url.odt  Public
android\ emulator\ installation.odt  Music          snap
Desktop                     parallel          Templates
Documents                 Pictures          Untitled\ 1.odt
Downloads                 processing       Videos
examples.desktop             programs          VirtualBox\ VMs
@lc2530hz:~$ cd "parallel processing programs"
bash: cd: parallel processing programs: No such file or directory
@lc2530hz:~$ cd processing
@lc2530hz:~/processing$ cd ..
@lc2530hz:~$ cd parallel\ processing\ programs
bash: cd: parallel processing programs: No such file or directory
@lc2530hz:~$ 



```

Somebody please guide me.

Zulfi.

---

### Post by CatKiller on 2019-02-19
Yes, you can have spaces in directory names.

In the shell, spaces and other wildcard characters can be escaped (not interpreted, but used verbatim) with \. ```
mkdir parallel\ processing\ programs
``` Or use ". 

I have no idea why, when you know you've created three different directories, you're trying to pretend that they're one directory.

---

### Post by The Cog on 2019-02-19
I can see that you tried to cd into that directory using both quotes and using backslash escapes. Either method is good. But it's too late, you already created three separate directories with the mkdir command. I suggest removing the three separates and creating the one like this:
```
rmdir parallel processing programs
mkdir "parallel processing programs"
```

---

### Post by zak100 on 2019-02-19
Hi,
I actually used the command:
$mkdir parallel processing programs

I thought the above would create one directory like in windows or in Unix but here in Ubuntu it created 3 directories i.e. parallel &  processing & programs. But my objective was to create only one directory. Thanks for your help.

Zulfi.

---

### Post by oldrocker99 on 2019-02-19
I always name things like_this,_so_there_are_no_spaces.

---

### Post by SeijiSensei on 2019-02-19
That command would create three directories in most *nix shells, not just bash.  Most every shell uses spaces as delimiters.  

If you embed a string in single quotes, it will be interpreted literally.  With double quotes environment variables will be replaced with their values.

```

MYHOME=/home/seiji

echo 'This is my home: $MYHOME'

This is my home: $MYHOME

echo "This is my home: $MYHOME"

This is my home: /home/seiji

```

If you have a filename with embedded spaces, you can use "[tab-completion]("https://spin.atomicobject.com/2016/02/13/bash-completion-tab/")" to expand the name by inserting the needed backslashes to escape the spaces for you.

---

### Post by The Cog on 2019-02-19
In case it's not clear:
This will create three directories (there are three space-separated arguments to the mkdir command):
```
mkdir parallel processing programs
```
But this will create one directory (there is just one argument):
```
mkdir "parallel processing programs"
```
And this will create three directories:
```
mkdir "parallel processing programs" "another name with spaces" foo
```
You can use backslashes in front of spaces rather than using quotes, but I find quotes easier to read.

---

### Post by QIII on 2019-02-19
In general, it is poor practice to create directories (and filenames) with spaces anyway - both in *Nix and Windows.  Microsoft's practice of "My Documents", "My Foo" and "This is my file name.doc" is a nightmare for software developers.

I would say that you simply should not do it: 

1.  There is no reason to.
2.  Doing so is a departure from long-established convention.
3.  Referring to them requires special handling to escape the spaces or the extra effort of adding quotes.  Extra keystrokes add to the likelihood of typographical errors.

---

### Post by koshamo on 2019-02-19
I would not recommend creating directories or filenames with spaces, but if you do:

```

mkdir this\ is\ a\ directory
mkdir "this is a directory"

```

---

### Post by col48 on 2019-02-20
In terms of good practice, I think there are two aims which sometimes collide at the margins.
1) Having meaningful and clear directory and file names.
2) Having names which are easy to make use of in future.

A name like "This is my personal directory" satisfies the first, but falls at the second unless access is through a file manager (just highlight and click) or through something hardcoded (eg typed into a parameter file).  This_is_my_personal_directory is a fair compromise for the first but is a pain to type quickly if the underscore requires use of the shift key.  Thisismypersonaldirectory has no problematic characters but mistakes in typing are hard to spot until the computer complains.

Since I routinely create and access files and directories through a GUI file manager, I am happy to have file and directory names with embedded spaces and other similarly awkward characters.
BUT, if I know I am likely to need to refer to them in a Terminal command, I use names with underscores; it is often convenient to use copy/paste if the name is more than a few characters long, and underscores are no problem where spaces would be, as vividly illustrated here.

---

### Post by CatKiller on 2019-02-20
> **col48 said:**
> BUT, if I know I am likely to need to refer to them in a Terminal command, I use names with underscores; it is often convenient to use copy/paste if the name is more than a few characters long, and underscores are no problem where spaces would be, as vividly illustrated here.

Tab-completion makes it really a non-issue. Maybe you need to remember whether it starts with a capital or not, but other than that you just type the first few letters and press Tab. Job done. I'm happy to use whichever characters might be useful in filenames. The only one you can't use is /.

---

