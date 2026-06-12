---
title: "symbolic link to an executable"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by muteXe on 2008-09-09
Hello,
My mate has a program in his home folder that he runs by going to this folder and typing
```

./ProgramName

```


I can't seem to create a symbolic link on his desktop that works.
I've tried
```

ln -s /fullPathToExe /FullPathToWhereIwantLinkOnDesktop

```

Double-clicking this link doesn't run it for some reason.

I've even tried writing a little script on the desk top
```

#!/bin/bash
cd /PathToExe
./ProgramName

```

And that script doesnt do anything either.  Or it appears not to do anything.

Any ideas?  Someone at my work has suggested that the exe i'm trying to call is actually a script itself but i dont know how to check this.

Many thanks,

Tom

---

### Post by AndyCee on 2008-09-09
Perhaps try these:

```
$ file ProgramName
```
This will tell you what the program is (script, executable etc).

and

```
$ ls -l ProgramName
```
This will show you permissions on the file.

---

### Post by muteXe on 2008-09-09
file ProgramName
```
ProgramName: ELF 32-bit LSB executable, Intel 80386, Version 1(SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), not stripped
```

ls -l ProgramName

```
-rwxr-xr-x 1  tom tom 22686 2008-06-10  19:36 ProgramName
```

Thanks for the quick response btw.

---

### Post by kpatz on 2008-09-09
Try creating a launcher for the executable on the desktop instead of a symlink.

---

### Post by muteXe on 2008-09-09
tried that, same thing.  I double click the launcher and nothing appears to happen.
unless i run it with:

./ProgramName

it doesn't want to run.  Thank you for your reply tho.

---

### Post by AndyCee on 2008-09-09
I don't know why this is happening. Something else to throw in:

What happens if you double-click on the executable itself?

---

### Post by aeiah on 2008-09-09
have you set it to be an executible?

you should be able to set up an application launcher that does

/path/to/executible

if you trust the program you could put it in your /usr/bin or /usr/local/bin or wherever executible binaries go nowadays, set it as an executible and it'll be in your path. so you can launch it from the terminal with 'programname' or set it as a menu item or launcher by just calling it by 'programname' instead of specifying a path etc

---

### Post by muteXe on 2008-09-09
nothing :(

---

### Post by muteXe on 2008-09-09
> **aeiah said:**
> have you set it to be an executible?

you should be able to set up an application launcher that does

/path/to/executible



yep i've tried that.  I don't think moving the program anywhere is an option i'm afraid.


Looks like he'll have to cd to the folder and run manually :(

---

### Post by AndyCee on 2008-09-09
So - the program doesn't run when you double-click? It sounds like a terminal program. If it doesn't do anything when you double-click the actual program, it certainly won't change when you make a link to it.

I have to ask - What does it do? (when it works)

---

### Post by muteXe on 2008-09-09
It's a work colleague's program, so it's commercially sensitive i'm afraid.  it's to do with air traffic control monitoring.

Not sure i know what a terminal program is. Can I create a link to this type of program or is that a no-no?

---

### Post by bodhi.zazen on 2008-09-09
Run the program from a link in the terminal :

```
~/Desktop/Link_to_Program
```

See if you get any error messages.

You may also want to :

```
sudo ln -s /home/user/program /usr/bin/program
```

---

### Post by muteXe on 2008-09-09
I'll tell him to try this tomorrow, he's gone home now.

thanks for all the replies,

Tom

---

