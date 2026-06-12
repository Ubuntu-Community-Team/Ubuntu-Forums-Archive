---
title: "Adding lines to init file"
date: 2012-10-15
forum: New to Ubuntu
---

### Post by kheal on 2012-10-15
I am very new to Ubuntu and am trying to install a program.  I have gotten through all the directions (ran a well-built .sh) and have gotten stuck with these directions:


Follow the steps below with care!!!

**************************************************
add one of the following lines to your init file
**************************************************
# bash users add to ~/.bashrc:
  alias arb=/usr/arb/bin/arb
# tcsh users add to ~/.cshrc:
  alias arb '/usr/arb/bin/arb'


These are the last steps.  I am not sure what they mean or how to access these files.  I have looked for them and cannot find them.  Any help would be greatly appreciated.


Katherine

---

### Post by wojox on 2012-10-15
Open a terminal (Ctrl+Alt+T)
```
echo "alias arb=/usr/arb/bin/arb" >> ~/.bashrc
```
```
source .bashrc
```

---

### Post by hakermania on 2012-10-15
All Operating Systems have the so-called hidden files. For linux, the hidden files start with a dot (.)

In order to make Nautilus able to show them you have to press the Ctrl+H keyboard-shortcut. You will find the .bashrc file at your home folder. It was always there, but you hadn't notice because it was hidden by Nautilus the whole time.

In order to hide at Nautilus the hidden files press again the same shorcut.

Note 1: Nautilus also hides the files that start with ~, although they are clearly visible with a terminal via the ```
ls
``` command, without any special options

Note 2: The ~ in the paths (e.g. **~**/.bashrc) represents your home directory.

---

### Post by kheal on 2012-10-15
Thank you for the quick responses.  I tried did your code but was still unable to run the program (ARB).  Now I get this string of errors.  Any suggestions?


katherine@katherine-ThinkPad-T400:~$ echo "alias arb=/usr/arb/bin/arb" >> ~/.bashrc
katherine@katherine-ThinkPad-T400:~$ source .bashrc
katherine@katherine-ThinkPad-T400:~$ arb
Environment Variable ARBHOME was empty
Using ARBHOME='/usr/arb'
Directory /home/katherine/.arb_prop not found - creating ...
Directory /home/katherine/.arb_prop/macros not found - creating ...
Please wait while the program ARB is starting .....
katherine@katherine-ThinkPad-T400:~$ /usr/arb/bin/arb: line 146: /usr/arb/bin/arb_ntree: cannot execute binary file
ARB done



Katherine

---

### Post by kheal on 2012-10-15
Okay, now I believe I have found the correct file to edit (the bash.bashrc file), but I do not have permission to edit it.  It says I am not the owner so I cannot change my permissions.  

I installed the program as root, but I cannot figure out how to edit the bash.bashrc file.  Also, the file I found was not under the ~/ but rather under ~/etc/  and hidden there - should that make any difference?

Thank you for your help, I have been trying to get this program going on various machines for a couple weeks now!

Katherine

---

### Post by drmrgd on 2012-10-15
Based on your post above, it seems that you were able to successfully add the line to your .bashrc file.  You don't want to edit any other .bashrc files on the system as they won't be used for you when you initiate a shell.  They are usually templates for when one needs to recover their .bashrc or wants to import one from scratch.  I think everything is correct.

The error you're getting looks more like it's a problem with the program itself.  If you did something wrong adding the line to .bashrc, when you ran 'source ~/.basrch' you would have gotten an error.  Instead, though, I can see that typing 'arb' is indeed launching the program as you would like, but something is not quite configured correctly with the program and it's failing.  By the looks of it, there's something wrong with the file /usr/arb/bin/arb_ntree.  

It could be one of several reasons.  The easiest to check would be that the file exists, and has the correct permissions to allow you to execute it.  Please list the output of:

```
ls -l /usr/arb/bin/
```

Alternatively, there could be something that was missed when you configured the program.  It's a bit hard to say what it is.  I would double check the README or INSTALL file that you got with the source code to make sure all your t's were crossed and what not if it's not a simple permissions or file missing issue.

---

