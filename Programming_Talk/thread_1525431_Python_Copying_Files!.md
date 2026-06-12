---
title: "Python: Copying Files!"
date: 2010-07-06
forum: Programming Talk
---

### Post by Sailor5 on 2010-07-06
Ahoy Sailor!

So I've been altering my Python Twisted project slightly so it's ready for windows, There is one job I used os.system for, However this can't be done with CMD, As it lacks some functions I needed (Bash is way better)

In short, I need to copy up to four files (Varying on the computer, There may be less) to another DIR, If I use shutils to try copy all the files, And it doesn't find one, Then it breaks the connection between Client & Server. So is there any way we could copy files without breaking or to check if the files exist beforehand?

Thanks Bye!

---

### Post by StephenF on 2010-07-06
First thought, to install an ssh server on the remote machine, then use a combination of ssh and sftp.

---

### Post by wmcbrine on 2010-07-07
os.listdir()
os.path.exists()
os.path.isfile()

among other helpful functions. Without seeing what you have now, it's hard to be more specific.

---

### Post by ashishanand19 on 2010-07-07
os.system() should work for windows too. You just need to give the commands right in windows because **cp** won't work for copying instead you need to use **copy** for windows.
So if you are writing the script to run on both windows and unix at the same time you need to have a check before.
import platform 
platform.platform()
will give you the details of the operating system.

OR else try using the subprocess module
subprocess.popen() should be helpful.

---

### Post by wmcbrine on 2010-07-07
os.system() would work, yes, but it's silly to use it just for copying files. It's needless overhead -- making Python launch a whole other shell for something it can easily do itself.

From the OP's vague description, he could probably get by with just putting his copy call in a try/except loop (and "pass" on the except). But I'd really prefer to see his code before making such a suggestion.

---

### Post by Sailor5 on 2010-07-07
> **ashishanand19 said:**
> os.system() should work for windows too. You just need to give the commands right in windows because **cp** won't work for copying instead you need to use **copy** for windows.
So if you are writing the script to run on both windows and unix at the same time you need to have a check before.
import platform 
platform.platform()
will give you the details of the operating system.

OR else try using the subprocess module
subprocess.popen() should be helpful.
It's not that I don't understand CMD, It's some of the functions I would use are not there in cmd, For example if you want to specify more then one command on one line, You would use two ampersands, However if one of the commands fails, The entire line breaks

```
os.system('copy 1.exp C:\&&copy 2.exp C:\&&Echo Done!')
```So first we try to copy 1.exp, But if that file isn't there then it would break the entire operation, And therefore not perform any other actions. So that's why I stopped using os.system. That and also you can't use wildcards when copying is a bit of a draw back.

> **wmcbrine said:**
> os.listdir()
os.path.exists()
os.path.isfile()

among other helpful functions. Without seeing what you have now, it's hard to be more specific.
Thanks I didn't know of the os.path.isfile() command before, I'll check to see if the comeback is True and then copy the file using shutils if so!

---

### Post by soltanis on 2010-07-07
You should use shutil and not os.system to perform copying; trying to use the cmd.exe shell inevitably leads to frustration. If you want wildcard functionality, then what you are looking for is the glob module (look it up; part of the standard python distribution) which allows you to iterate over files which match a very restricted form of regular expressions:

[php]
import shutil, glob

dest_dir = "C:\\"
for f in glob.glob("*.dat"):
    shutil.copy(f, dest_dir)
[/php]

---

### Post by evstevemd on 2010-07-08
And.. avoid system specific suffs when you plan to code for X-Platform :P

---

