---
title: "how can I execute shell script from everywhere?"
date: 2007-06-24
forum: Programming Talk
---

### Post by frischi on 2007-06-24
I've been reading a tutorial about shell script.

There was written that by making the directory ~/bin and putting the shell script in there you could execute it from everywhere without having to give a path. That did not work.

There's also written that this is like that because of the PATH settings.

Should this work on ubuntu?
Where are this PATH settings (and can a beginner change them)?

---

### Post by mattg89 on 2007-06-24
Try adding

```
PATH=$PATH:$HOME/bin
``` to the end of .bash_profile.
Then to check it's worked, restart, and do
```
echo $PATH
```
This should have /home/<username>/bin on the end

---

### Post by frischi on 2007-06-24
where is .bash_profile stored?

---

### Post by mattg89 on 2007-06-24
in your home directory

either

gksudo gedit ~/.bash_profile

or if you prefer the commands line

sudo nano ~/.bash_profile

---

### Post by frischi on 2007-06-24
doesn't work. 

i suppose i make a very noobish fault.

here what the file looks like now:






# ~/.bash_profile: executed by bash(1) for login shells.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/login.defs
#umask 022

# include .bashrc if it exists
if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

PATH=$PATH:$HOME/bin

---

### Post by frischi on 2007-06-24
i wonder whether the second last line of what was already there doesn't mean exactly the same.

---

### Post by rax_m on 2007-06-24
> 
# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
PATH=~/bin:"${PATH}"
fi


This block of code checks whether a bin directory exists in the users home directory, and if it does, adds that directory to the PATH. So no need to add the last line you have. 

You have to logout and log back in for it to work. Restart shouldn't be necessary. 

If you then do a ```
whereis <commandname>
```

it should show you /home/<yourusername>/bin

Rax

---

### Post by frischi on 2007-06-24
silvio@ubuntutest:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
silvio@ubuntutest:~$ sh bin/knowledge
Knowledge is Power
silvio@ubuntutest:~$ knowledge
bash: knowledge: command not found

---

### Post by frischi on 2007-06-24
and by the way how do you make this this blocks you write the code in?

---

### Post by rax_m on 2007-06-24
ok.. i tested this on my system and it doesn't work from within Gnome for some reason.. 
However if I open a console (Ctrl-Alt-F1) then the command works fine. BTW Ctrl-Alt-F7 to get back to X. 

Also, to quote something in the forums you use [ quote ] Some stuff [\ quote ]
But don't put in the spaces between the brackets and the words. I had to do that so you could see the tags. 

Or change the words quote for code to show some code.

---

### Post by frischi on 2007-06-24
that works! thank you very much!

---

### Post by rax_m on 2007-06-24
found a solution:

Add ```
 export PATH=$PATH:~/bin 
```

to your .bashrc file found in your home directory. 
This will then be available when you start a new terminal window. No need to even logout :)

---

### Post by frischi on 2007-06-24
ok works as well thank you

---

### Post by Mr. C. on 2007-06-24
> **frischi said:**
> silvio@ubuntutest:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
silvio@ubuntutest:~$ sh bin/knowledge
Knowledge is Power
silvio@ubuntutest:~$ knowledge
bash: knowledge: command not found

You have not added ~/bin to your PATH variable, so the shell cannot find your knowledge command.

You need PATH=$PATH:~/bin

and then it will work.

Read up on how Unix/Linux shells find commands via PATH:

[http://cis68a.mikecappella.com/files/lecture5.pdf](http://cis68a.mikecappella.com/files/lecture5.pdf)

starting at slide 35.

MrC

---

### Post by peterx14 on 2007-07-07
I think this problem is the same as discussed in another thread. I believe I have a solution here:
[http://ubuntuforums.org/showthread.php?p=2981327#post2981327](http://ubuntuforums.org/showthread.php?p=2981327#post2981327)

---

