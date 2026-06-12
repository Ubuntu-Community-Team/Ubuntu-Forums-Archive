---
title: "Bash problem"
date: 2007-02-17
forum: Programming Talk
---

### Post by jingo811 on 2007-02-17
I'm trying to learn BASH scripting by following this tutorial
[http://www.linuxcommand.org/wss0010.php](http://www.linuxcommand.org/wss0010.php)
I did everything except add the directory path.  I just created home/bin and test my scripts by changing to that directory.
The thing is that trick wored a few days ago.  Now when I try to run my_script it won't run.
Can you see what's wrong?
```
mike@sanka:~/bin$ **ls -la**
total 12
drwxr-xr-x  2 mike mike 4096 2007-02-12 09:56 .
drwxr-xr-x 55 mike mike 4096 2007-02-17 18:34 ..
-rwxr-xr-x  1 mike mike   51 2007-02-12 09:24 my_script
mike@sanka:~/bin$ **chmod 755 my_script**
mike@sanka:~/bin$ **ls**
my_script
mike@sanka:~/bin$ **my_script**
[COLOR="Red"]bash: my_script: command not found[/COLOR]
mike@sanka:~/bin$

```

```
mike@sanka:~/bin$ **less my_script**

#!/bin/bash
# My first script

echo "Hello World!"
my_script (END)
```

---

### Post by nereid on 2007-02-17
I think that your personal bin folder isn't in your path. So you have to call this script like this

```

./my_script

```

Notice the dot and the slash in front of the script, to tell bash that it should look in the current directory to find the script.

---

### Post by thomasaaron on 2007-02-17
The error message you are receiving is not referring to the location of your script.

It is referring to the last line of your script, which starts with "my_script"

It is telling you that "my_script" is not a valid command.

You can delete that line altogether from your script and everything should work fine.

Best,
Tom

---

### Post by jingo811 on 2007-02-17
Tnx  ```
./my_script
``` solved it!

---

### Post by thomasaaron on 2007-02-17
Ok.
My bad.
T

---

### Post by jingo811 on 2007-02-17
OK new problem.  Instead of me posting a new thread for every new BASH question I'm gonna make all my future BASH problems in here. (OK moderators!?)
I got stuck already on lesson 2 [http://www.linuxcommand.org/wss0020.php](http://www.linuxcommand.org/wss0020.php) and part of the previous lesson were you were supposed to add your directory into .bash_profile file.

```
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

[COLOR="DarkOrange"]# My custom commands 
export PATH=$PATH:home/mike/bin
alias l='ls -l'[/COLOR]

```

I restarted my PC and doing all the commands in terminal I can't make anything work.  What have I done wrong this time?

```
mike@sanka:~$ **./my_script**
bash: ./my_script: No such file or directory
mike@sanka:~$ **echo $PATH**
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
mike@sanka:~$ **l**
bash: l: command not found
mike@sanka:~$ **cd bin**
mike@sanka:~/bin$** ./my_script**
Hello World!
mike@sanka:~/bin$

```

---

### Post by WW on 2007-02-17
Put your custom commands in ~/.bashrc, not in ~/.bash_profile.  .bash_profile is for "login shells"; when you open up a terminal, you are not starting a new login shell.

Also, I think you are missing a / in your command to change PATH:
> export PATH=$PATH:**/**home/mike/bin

---

### Post by WW on 2007-02-17
One more comment: Once you have correctly set your PATH to include /home/mike/bin, you can use the command **my_script** anywhere.

When you put **./** in front of a command, you are explicitly telling the shell to look for the command in the current directory.  So the command **./my_script** will not work when run in your home directory, no matter what your PATH is set to (unless you happen to have a copy of my_script in your home directory).

---

### Post by jingo811 on 2007-02-17
When I do my changes in .bashrc is it enough that I do [Ctrl-Alt-Backspace] to enable the changes or do I need to do a reboot for every change in this file?
Second question is it I who read and interpreted the Tutorial lesson 1 wrong or did the author not know that editing the .bash_profile won't work in Ubuntu like on his distro?

---

### Post by WW on 2007-02-17
No need for ctrl-alt-backspace, and definitely no need to reboot!  Just start a new terminal, and start using it.

---

### Post by po0f on 2007-02-17
jingo811,

```
[FONT="Courier New"]$ ln -s ~/.bash_profile ~/.profile[/FONT]
```

GDM will source ~/.profile on login, and ~/.bash_profile (through the symlink) will source ~/.bashrc.  At least it works for me.  :)

And to answer your other question, it might have slipped the author's mind that someone might be doing this from a terminal emulator.  If you try it from a virtual console (Ctrl-F(1,6)), you'll see that it works the way the author presented it.

Also, most terminal emulators (gnome-terminal, urxvt, etc) usually have an option to set whether it should behave like a login terminal, ie it will source the proper files upon opening.  I know with urxvt the resource is "urxvt.loginShell: <bool>".  I'm sure gnome-terminal has this option as well, I just can't recall exactly how to set it.

---

