---
title: "Environment variables unset?"
date: 2008-10-16
forum: Programming Talk
---

### Post by smartboyathome on 2008-10-16
Hi, I'm working on a script and it seems to be unsetting my environment variables. I know this because I named a random variable (in this case prgmnm) with the same content as another variable I want to use, and when I echoed it during the last part of my script, it came back with nothing. Can you guys help me find where the variables are unset and stop it from unsetting them? I underlined where I wanted the variable to be accesible. Is it not accesible in that position for some reason, and if so is there a way to make it accessible there? I posted the script below. The portion in which I found the variables to be unset is bolded.

```
cd \$tmpdir/makeself-mod/ &&_ ./makeself-mod-light_
```

Thanks to everyone who helps.
Smartboy

---

### Post by mssever on 2008-10-16
It's hard to know exactly what you're trying to do, since you posted a very long bit of code that isn't particularly easy to read. Of course, that means I only skimmed it. Plus, you didn't give a precise example of where the program isn't behaving as expected (you bolded too much code). However, I noticed that you're doing \$somevar a lot instead of $somevar. In at least some cases, I question whether that's what you really should be doing, though your code is sufficiently difficult to follow that I'm not always sure just what you're trying to accomplish.

If you narrow your code down so I can better tell what's going on, I might be able to provide some better help.

---

### Post by smartboyathome on 2008-10-16
Sorry, this isn't all my code, I'm borrowing someone else's code and modifying it to suit my needs. I was able to shorten it to one line in the script where the variables don't stick. Its the underlined portion of the code box which doesn't seem to hold the variables. What I'm trying to do is get it so that the variables transfer over to that underlined script I run at the end so that I can use it in that script. I tried echoing the variables right before that line and it doesn't echo anything back, so I'm guessing its a problem with the &&.

I then tried to put the script on a separate line, but it still doesn't work, as the script STILL doesn't get the variables. I guess I want to know if there is any way to carry over the variables from the first script to the second one.

---

### Post by dwhitney67 on 2008-10-17
I may be wrong, but I do not think it is possible to define a variable in one script, and use it in another.  When you run a script, you are in essence running a sub-shell.  This sub-shell is capable of reading environment variables that you have set within the parent shell, but the other way around is not possible.

If you have a script that is formulating the value of a variable, what you could do is echo the value to the terminal, and let the second script accept it as a command-line argument.

For example, here are two scripts:

s1.sh:
```

#!/bin/sh

FOO="Hello World"
echo $FOO

```

s2.sh:
```

#!/bin/sh
echo FOO = $1

```

To test:
```
sh s2.sh `sh s1.sh`
```

You could also do this within your parent (main) shell:
```
export FOO=`sh s1.sh`
```

Then s2.sh could be:
```

#!/bin/sh
echo $FOO

```
which would obviate the need to look at the command-line arguments.

---

### Post by mssever on 2008-10-17
> cd \$tmpdir/makeself-mod/ &&_ ./makeself-mod-light_Do you mean that you want to access $tmpdir from makeself-mod-light? The code you posted won't work unless you're cd-ing to a directory named '$tmpdir' (i.e., that literal name, not a variable reference). I'm guessing that's not what you want, in which case you need to drop the backslash. 

Assuming that $tmpdir is the variable you want, you need to export it for it to be visible to subprocesses. So: ```
export tmpdir=whatever
cd "$tmpdir"/makeself-mod && ./makeself-mod-light
```
If you're trying to get variables from one program that's already exited and use them in another program, you can't. At least not in Bash.

---

### Post by smartboyathome on 2008-10-17
Thanks guys. What I'm trying to do is create a portable, single archive runnable file which houses portable linux apps. I got it fine, except I can't get Linux apps to save without repackaging them in the same way they were created. To do this, I have to chain a lighter version of the original script so that I can create it again. Because of how this works, I need to export some of the info from the script which is attached to the archive to the script which I run to make the archive again with the saved stuff. I can't export the variable because it is a random directory which would change when I try exporting it, but I tried exporting the freshly created tmpdir variable (which gets set before the directory for the program gets made), and made the fixes you suggested, but I now get this error:

cd: can't cd to /makeself-mod/

How come its doing this? Is the variable not setting for some reason? I don't get any other error other than this, and I didn't get this error before I changed the stuff.

EDIT: Getting rid of the quotes and adding the \ back in makes it work, but the variable still isn't carrying over to the new script.

---

### Post by dwhitney67 on 2008-10-17
> **smartboyathome said:**
> ... I now get this error:

cd: can't cd to /makeself-mod/

...
As you figured out, tmpdir is not making it into the script.  As I stated earlier, it will only make it into the script if it is defined in the parent shell where the script is run.

So set it (tmpdir) first, and then run the script that expects it.

```

export tmpdir=/some/path

```
Once you set tmpdir, you should be able to access it as $tmpdir.

Be aware that if there are spaces in the pathname assigned to tmpdir that there may be other issues that crop up.

---

### Post by mssever on 2008-10-17
> **smartboyathome said:**
> Thanks guys. What I'm trying to do is create a portable, single archive runnable file which houses portable linux apps. I got it fine, except I can't get Linux apps to save without repackaging them in the same way they were created.You mean, something like [Autopackage](http://www.autopackage.org/)?

> I can't export the variable because it is a random directory which would change when I try exporting itSo export it after you've determined the name of the random directory.

> EDIT: Getting rid of the quotes and adding the \ back in makes it work, but the variable still isn't carrying over to the new script.
I'd like to see your code for that. If that works, then you must be evaluating the command an extra time, which is probably a problem.

If you're trying to get two bash scripts to communicate, I can only think of two options: Set up a pipeline, and/or use one program to call the next with the appropriate input. If you were using a different, language (such as Ruby or Python), you'd have a few more options available.

---

