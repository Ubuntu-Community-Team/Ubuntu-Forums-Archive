---
title: "Unable to rename files in Terminal..."
date: 2008-08-03
forum: New to Ubuntu
---

### Post by mingle on 2008-08-03
Hi,

I'm trying to rename a file using the following command in the Ubuntu terminal:

user@D515-desktop:/boot/grub/splashimages$ sudo rename splash.xpm.gz splash.temp

But get the following errors:

Bareword "splash" not allowed while "strict subs" in use at (eval 1) line 1.
Bareword "xpm" not allowed while "strict subs" in use at (eval 1) line 1.
Bareword "gz" not allowed while "strict subs" in use at (eval 1) line 1.

Obviously I'm doing something fundamentally wrong!

Also, on a similar thread - how do I enable things like rename, copy and move from within the Ubuntu file-manager, so I don't have to use "sudo" from a terminal window?

Cheers,

Mike.

---

### Post by marshal_mellow on 2008-08-03
Try 
```
sudo mv splash.xpm.gz splash.temp
```

---

### Post by BennBuntu on 2008-08-03
I've never used rename, but seems it's for renaming multiple files.```
man rename
``` will give you a description with an example. Normally just use mv as above


You can already rename in the file manager, but if you want root permissions, letting you change all files, launch it from terminal with gksudo.

```
gksudo nautilus
```
or
```
gksudo nautilus /home/whatever
```

---

### Post by ingeva on 2008-08-03
> **mingle said:**
> 
Also, on a similar thread - how do I enable things like rename, copy and move from within the Ubuntu file-manager, so I don't have to use "sudo" from a terminal window?


In nautilus file manager it's just like in Windows. Cut, copy and paste are the same. Use CTRL-C/X/V, or if you want me to confuse you, the Insert/Delete keys with CTRL and CTRL+SHIFT.

To rename, click on the icon of the file or directory, and press "F2". Just like in that old deprecated W-system.

---

### Post by ET! on 2008-08-03
use mv command it works for sure...

---

### Post by sisco311 on 2008-08-03
the rename command is for bulk rename files.
use the mv command as suggested above.

just for fun:
```
rename 's/splash.xpm.gz/splash.temp/' ./*
```

---

### Post by Elep.Repu on 2009-07-08
> **ingeva said:**
> In nautilus file manager it's just like in Windows. Cut, copy and paste are the same. Use CTRL-C/X/V, or if you want me to confuse you, the Insert/Delete keys with CTRL and CTRL+SHIFT.

To rename, click on the icon of the file or directory, and press "F2". Just like in that old deprecated W-system.

deprecated?
At least DOS stopped using "mov" for rename, and actually gave a Rename command.
[http://www.computerhope.com/renamehl.htm#01](http://www.computerhope.com/renamehl.htm#01)

---

### Post by Celauran on 2009-07-08
> **Elep.Repu said:**
> 
At least DOS stopped using "mov" for rename, and actually gave a Rename command.
[http://www.computerhope.com/renamehl.htm#01](http://www.computerhope.com/renamehl.htm#01)

At least? There's really no difference between renaming foo to bar and moving foo to bar. No need for an additional command to do the same thing IMO.

---

### Post by Mornedhel on 2009-07-08
For the curious, rename is an extremely powerful command-line bulk renamer. It's used thus :

```
rename 'how' what
```

Where <what> is a list of files, and <how> is actually Perl code. Any valid Perl expression can be used, which includes regular expressions. For instance, if you have a bunch of files named ep01.avi, ep02.avi, ep03.avi, etc., and you want to give them nice names, do this :

```
rename 's/ep([\d]+)/Some TV Series - $1/'
```

And the files will be moved to Some TV Series - 01.avi, etc. Obviously this is a trivial example and awesome things can be achieved. Since any code can be run, including module imports, you could even fetch data from the Internet, or local databases, or perform arithmetic operations, or access the file to rename it based on its contents, etc., although for more advanced stuff you end up writing the script anyway. For the Perl coders around here, this works with the help of the magical variable $_, which is set to each filename in turn.

The -n option can be used to have rename perform dry runs (print what should happen, but don't actually rename anything).

---

