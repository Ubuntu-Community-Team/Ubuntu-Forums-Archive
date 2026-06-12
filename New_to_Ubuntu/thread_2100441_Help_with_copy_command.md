---
title: "Help with copy command"
date: 2013-01-01
forum: New to Ubuntu
---

### Post by GMHilltop on 2013-01-01
I am still fairly new to the command line thing in Terminal.  Could  someone expand on the 'asterisk'  for me please.  Is it needed to make  the recursive or archive copy capture ALL the directories?

**cp -a /directory/* /here**
or
**cp -r /directory/* /here**

would this produce the same results:

**cp -a /directory /here**
or
**cp -r /directory /here**

If someone could comment, or give me some "Best Practices" guidance on this, that would be terrific.
I understand that here:  [http://en.wikipedia.org/wiki/Cp_%28Unix%29](http://en.wikipedia.org/wiki/Cp_%28Unix%29)
...  thre was mentioned that there is some difference between GNU and BSD  systems and what would actually happen with regards to that command.

It  is under the examples . . . just search for, ". . . on a GNU system it  behaves as expected; however, on a BSD system . . ." and you will see it  there.

Thanks.

---

### Post by oldos2er on 2013-01-01
Post moved to its own thread.

---

### Post by Cheesehead on 2013-01-01
> **GMHilltop said:**
> Could  someone expand on the 'asterisk'  for me please.  Is it needed to make  the recursive or archive copy capture ALL the directories?

No. The [FONT=Courier New]-r[/FONT] or [FONT=Courier New]-R[/FONT] flag makes it recursive.
The [FONT=Courier New]*[/FONT] makes it capture everything in the directory. That's different.

For example, let's create two directories, A and B. A will remain empty, B will have two files in it, 1 and 2.
```
mkdir a
mkdir b
touch b/1
touch b/2
```Let's do a recursive copy. 'Recursive' means everything inside the folder, too.
```
ls -R b
b:
1 2

cp -r /path/to/b /somewhere/else/

ls /somewhere/else/
b:
1 2
```See how 1 and 2 traveled with b? That's a recursive copy.

Now, lets do a wild card ([FONT=Courier New]*[/FONT])copy instead. The wild card simply matches all characters.
```
ls b/*
b/1  b/2

cp /path/to/* /somewhere/else/
cp: omitting directory `a'
cp: omitting directory `b'

ls /somewhere/else/
(blank result)

```See how the wild card captured both a and b, but none of b's contents?
Without recursion, cp viewed b as an empty directory. cp balked rather than copy an empty directory. It also balked at a for the same reason.

Your example used both.
> cp -r /directory/* /hereThis command will capture everything the thedirectory (wild card), plus all of their subdirectories and contents (recursion), and copy the entire tree to the new location.

See [FONT=Courier New]man cp[/FONT] for the difference between -a and -r. Briefly, the way the new copy treats links, mode, ownerships, and timestamps is different. -a (archive) keeps originals as much as possible, while -r tries to cleverly adapt to the new environment the copy is being grafted into. If in doubt, try -r first.

---

### Post by MG&amp;TL on 2013-01-01
> I am still fairly new to the command line thing in Terminal. Could someone expand on the 'asterisk' for me please.The '*' is a wildcard. Wildcards are special characters that are expanded by the shell (a program you type your commands into) into their appropriate meanings. "*" means "everything". You can find a good explanation here: [http://www.tuxfiles.org/linuxhelp/wildcards.html](http://www.tuxfiles.org/linuxhelp/wildcards.html)


>  Is it needed to make the recursive or archive copy capture ALL the directories?Almost. It will make the copy capture EVERYTHING in the path given. For instance:

```
cp /path/to/source/directory/* /path/to/destination/
```is a lot faster than:

```
cp /path/to/source/directory/file1 /path/to/destination/file1
cp /path/to/source/directory/file2 /path/to/destination/file2
cp /path/to/source/directory/file3 /path/to/destination/file3
...
```> cp -a /directory/* /here
or
cp -r /directory/* /here

would this produce the same results:

cp -a /directory /here
or
cp -r /directory /here

I think so, yes.

> If someone could comment, or give me some "Best Practices" guidance on this, that would be terrific.There isn't really any "best practices" for this other than be careful.  Wildcards are extremely powerful, but equally very dangerous. For instance, using the remove command (rm) with wildcards could very easily wipe out entire chunks of data.

I can't really comment on the differences with GNU/BSD as I've never used a BSD version of cp. Hope the rest helped though.

---

### Post by t0p on 2013-01-01
I suggest you play with **cp** a bit, in a new directory, with expendable files.  That way you won't cause any damage if you word a command incorrectly.

[LEFT]Oh, and don't use the commands as root (ie with **sudo**) until you're sure you understand what you're doing.  Better safe than sorry, eh!
[/LEFT]

---

### Post by mamamia88 on 2013-01-01
Well * usually means all.  so if you did cp * /home/user/ it would copy all files and folders in the current working directory to /home/user.

---

### Post by garyed on 2013-01-01
> **GMHilltop said:**
> 

**cp -a /directory/* /here**
or
**cp -r /directory/* /here**

would this produce the same results:

**cp -a /directory /here**
or
**cp -r /directory /here**


Both commands copy all the contents & all subdirectories to the target directory. The basic difference is the second set of commands will copy the parent directory name also where the first set of commands don't. 
In the first instance the "here" directory will show all of the files but in the second instance the "here" directory will show the "directory" directory & all the files will be inside it just like the original setup.

---

