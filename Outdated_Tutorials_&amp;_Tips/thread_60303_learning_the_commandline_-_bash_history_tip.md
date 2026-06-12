---
title: "learning the commandline - bash history tip"
date: 2005-08-27
forum: Outdated Tutorials &amp; Tips
---

### Post by ssam on 2005-08-27
If you are learning to use the commandline (or even if you are a linux guru) then bash history is a very useful feature you should get to know.

so open a terminal and try these tips:

the simplist way to use it is to press up and down. you will be shown the last commands that you used.

suppose you had a great command that you used last week, but can't quite remember. to save you from repetitive strain injury try the **history** command:

```
sam@titania:~$ history
<trimmed>
  556  ls
  557  history
sam@titania:~$

``` 

that gives you a big list of what you have done in the past.

now you probably don't want to read through all of it, so we must filter it. For this we use the wonderful **grep**. for example if you want to find that wget command you used

```
sam@titania:~$ history | grep wget
  544  wget -c http://kent.dl.sourceforge.net/sourceforge/inkscape/Inkscape-0.42.2-0.dmg
```

Now we have something useful. but a bit fiddly to type. The solution is to set an alias. (like a sortcut). I have mine set to **h**. To do this type
```

alias h="history|grep"
```

now you only need to do

```
h wget
```

if you like this you can make it perminant by putting it into you **.bashrc** file

```
gedit .bashrc
```
or
```
vim .bashrc
```

and put
```

alias h="history|grep"
```

at the end. this will take effect next time you open a terminal.

---

### Post by heimo on 2005-08-27
And here's one more tip for using command line history. Hit ctrl+r and start typing part of the command you're searching from history. It'll automagically appear and you can accept it by hitting enter, or edit first. :) Very, very convenient. Love it, saves lots of time.

---

### Post by essexman on 2005-08-27
[QUOTE=ssam]

```
h wget
```

if you like this you can make it perminant by putting it into you **.bashrc** file

```
gedit .bashrc
```
or
```
vim .bashrc
```

and put
```

alias h="history|grep"
```

at the end. this will take effect next time you open a terminal.[/QUOTE]
Sam

Thanks for the post - one question?

my .bashrc (standard installtion) contains this:
```
# Define your own aliases here ...
#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi
```

Where do I put the alias line?
[list]
[*]after the code?
[*]Commented or uncommented?
[*]Or in a new .bash_aliases file?
[*]Or somewhere else?
[/list] 

I would like to learn more, and I find it very useful when a simple Howto has 'what goes where and why'.

Hope you will oblige.

Cheers

Essexman O:)

---

### Post by ssam on 2005-08-27
i put
```
alias h="history|grep"
```
as the end of .bashrc

it does not make much difference. if you had a lot of aliases it may be neeter to put thme in a seperate file.

also i recomend that you uncomment (remove the #s) from the
```
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi
```block. then you get very sweet tab completion.

my .bashrc looks like
```

# .bashrc
# User specific aliases and functions

# Source global definitions
if [ -f /etc/bashrc ]; then
        . /etc/bashrc
fi

if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

export PATH=$PATH:/home/sam/bin
alias playdvd="xine --no-splash --fullscreen --hide-gui --auto-play=d"
alias ls="ls --color"
alias h="history|grep"
```

---

### Post by FLeiXiuS on 2005-08-27
[QUOTE=heimo]And here's one more tip for using command line history. Hit ctrl+r and start typing part of the command you're searching from history. It'll automagically appear and you can accept it by hitting enter, or edit first. :) Very, very convenient. Love it, saves lots of time.[/QUOTE]

Now that is sexy!  :-)

---

### Post by arnieboy on 2005-08-27
[QUOTE=ssam]```

alias h="history|grep"
```[/QUOTE]
Sweeet! Thanks for the tip :D

---

### Post by Wolki on 2005-08-29
[QUOTE=heimo]And here's one more tip for using command line history. Hit ctrl+r and start typing part of the command you're searching from history. It'll automagically appear and you can accept it by hitting enter, or edit first. :) Very, very convenient. Love it, saves lots of time.[/QUOTE]

Hehe, tthat one's a great and often under-appreciated feature. You can do so many cool things with the command line, but i can understand that people hate it when often they don't even know about tab completion or history search...

Anyway, here's another tip. Not quite as useful as the last one, but it helps.

Let's say you have just entered a command with an argument...

$ mv demo.txt ~/really/long/path/so/you/absolutely/do/not/want/to/enter/it/again/

ok, you moved the file there. then you want to cd there. Instead of typing that awfully long path again, just do

$ cd <escape>-<.>

and the shell will automatically extend that to

$ cd ~/really/long/path/so/you/absolutely/do/not/want/to/enter/it/again/

In short, if you enter <escape>-<.>, it will copy the last argument and paste it there. Can save quite some time, try it out! :)

---

### Post by mikedtemple on 2005-08-30
[QUOTE=ssam]
```

alias h="history|grep"
```

at the end. this will take effect next time you open a terminal.[/QUOTE]


Now that is awesome, especially for a noob like me.  Even for an old DOS head, the linux command line can be daunting.  Does anyone have any recommendations for a good command line book??

---

