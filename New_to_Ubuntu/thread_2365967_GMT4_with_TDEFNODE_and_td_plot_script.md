---
title: "GMT4 with TDEFNODE and td_plot script"
date: 2017-07-12
forum: New to Ubuntu
---

### Post by blitzkrieg2 on 2017-07-12
I'm a very very new user to Ubuntu, and has a problem so far. I might explain it very carefully:

- I'm working on a software called TDEFNODE(a freeware) for scientific issues which is coded through Fortran. To run it, I've installed a virtual machine(VMare Workstation) on my Windows 10 OS and download the program.

- I don't know anything about Ubuntu, so I just installed 14.0 version of it in the virtual machine.

- One of my friends just compile the TDEFNODE program. To run the software, he installed "gfortran" and "tcsh", and add alias syntax to "bashrc" showing the full path of the folder, and run it through terminal.

- Afterwards, I've done the process, but the tricky part is that the output files after the process has to be drawen with a file called "td_plot" in the software's folder. This "td_plot" used by some syntax in the terminal to run some specific properties of GMT. So I've downloaded GMT as well.

- When I tried to plot some drawings, just say: 

td_plot -p map -m mode

 the most important part of the output is missing; means velocity vectors and so.

- When I examine this "td_plot" thing, I understood that this file is for "tcsh" but I've installed "tcsh" in the first place.

- I wonder if there's a way around to run this "td_plot" or say, compiling the orginal files somehow, etc.

I hope to explain the issue clearly.

Thanks anyway.

---

### Post by steeldriver on 2017-07-12
It's going to be hard to diagnose based on the description you have given

Can you provide any sample file that we can test, along with the expected output?

---

### Post by blitzkrieg2 on 2017-07-12
By this time, I've been searching through the web and as I understood, the file "td_plot" is having commands based on "tcsh", and starting like this:



#!/bin/tcsh -f


## set $TD_HOME to be the path to this directory
## creates and uses a scratch directory $TD_HOME/scratch/$USER




set TD_scratch = $TD_HOME/scratch/$USER
if ( ! -e $TD_scratch ) mkdir $TD_scratch


### where grid files are
# if using etopo2
set ETOPO2 = /ssd/gmt_data/etopo2/etopo2.grd
# if using SRTM
set SRTM   = /ssd/gmt_data/srtm


## RM's data directory
#set dn = '/home/mccafr/work/dn'   


## defaults
set pgm = 'map'
set w1 = 100 e1 = 120 n1 = 40 s1 = -40
set t1 = 2000 t2 = 2014 dt = 1 dtin = 0 tset = 0
set Jt = 0



The problem, I think, is that I run this file under bashrc. 

Actually, I've learned that there are two main ways to confront the problem:
1- Translate the commands in this file from "tcsh" to "bashrc"--> Which seems unlikely, because the file continues more than 600 lines.
2- I have to run this file with "tcsh" shell. I know that tcsh installed on my OS, but I have no idea how to change the shell and run this "td_plot" anywhere in the computer.

---

### Post by steeldriver on 2017-07-12
If you run it using (for example)

```

./td_plot foo bar

```

from the directory in which the file is located, OR with the full path

```

/path/to/td_plot foo bar

```

OR

by adding `/path/to/` to your (bash) shell's $PATH, then the "shebang" line 

```

#!/bin/tcsh -f

```

should ensure that it is executed using /bin/tcsh. There should be no need to "translate" it to bash.

---

### Post by blitzkrieg2 on 2017-07-12
Dear steeldriver,

I'm a real rookie about this shell thing, sorry about that. I really want to understand it clearly. Can you explain these issues to a real-noob, please?

- I can run td_plot command in an output folder, name like <blitz> with this, no problem: 
  
td_plot -p map -calc -obsv


- In the .bashrc file, there are some lines about the path of the file(I'm not sure if it's wrong):

export TD_HOME=/home/asdfgh/TDEFNODE
alias tdefnode='/home/asdfgh/TDEFNODE/tdefnode'
alias td_plot='/home/asdfgh/TDEFNODE/td_plot'

PATH=/home/asdfgh/TDEFNODE/td_plot:"${PATH}" -->This one I've written it.

- I have no idea about the "shebang" line and where to put it. So if you please explain all of them on my .bashrc file if it's no problem?




# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples


# If not running interactively, don't do anything
case $- in
    *i*) ;;
      *) return;;
esac


# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth


# append to the history file, don't overwrite it
shopt -s histappend


# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000


# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize


# If set, the pattern "**" used in a pathname expansion context will
# match all files and zero or more directories and subdirectories.
#shopt -s globstar


# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"


# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "${debian_chroot:-}" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi


# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac


# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes


if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
	# We have color support; assume it's compliant with Ecma-48
	# (ISO/IEC-6429). (Lack of such support is extremely rare, and such
	# a case would tend to support setf rather than setaf.)
	color_prompt=yes
    else
	color_prompt=
    fi
fi


if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt


# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac


# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'


    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi


# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'


# Add an "alert" alias for long running commands.  Use like so:
#   sleep 10; alert
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'


# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.


if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi


# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if ! shopt -oq posix; then
  if [ -f /usr/share/bash-completion/bash_completion ]; then
    . /usr/share/bash-completion/bash_completion
  elif [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
  fi
fi


export TD_HOME=/home/asdfgh/TDEFNODE
alias tdefnode='/home/asdfgh/TDEFNODE/tdefnode'
alias td_plot='/home/asdfgh/TDEFNODE/td_plot'


PATH=/usr/bin/gmt/:"${PATH}"
PATH=/etc/gmt/:"${PATH}"
PATH=/usr/lib/gmt/:"${PATH}"
PATH=/usr/bin/X11/gmt:"${PATH}"
PATH=/usr/share/gmt/:"${PATH}"
PATH=/usr/lib/gmt/bin/:"${PATH}"
PATH=/home/asdfgh/TDEFNODE/td_plot:"${PATH}"





- And lastly, I think I have to run the command on the terminal(or reboot the system):
  
 source ~/.bashrc

  Is it correct?

Thanks for your time.
Really.

---

### Post by vocx on 2017-07-13
> **blitzkrieg2 said:**
> Dear steeldriver,

I'm a real rookie about this shell thing, sorry about that. I really want to understand it clearly. Can you explain these issues to a real-noob, please?


First of all, whenever you write code or terminal commands in this forum you should use CODE tags. There is an opening tag and a closing tag. The word "```
" is the tag.
[PHP]
[CODE]
# example code
td_plot -p map -calc -obsv

```
[/PHP]

If you see post #4 in this thread, on the lower side to the right there is a "reply with quote" option. If you click that, you will see the source code of the post, and you will get an idea how to paste code correctly. Using code tags is preferable because it uses a monospace font, and maintains the formatting of the code, including any spaces.

> - I can run td_plot command in an output folder, name like <blitz> with this, no problem:

Okay, now back to your question. What is exactly the problem? You have not clarified exactly what you have, and what you want. You should say, "I have this, and I want to have this. How do I do that?" Specifying clearly the problem is important.

If you say, "my problem is that I don't get the correct vectors", maybe this is a problem with the specific TDEFNODE program, or its input files. Since most of us have no experience with that program, we cannot help you with that. We can only help you with general things, but not with the specifics of that program. Also, if you have trouble writing in English, get somebody to help you explaining your problem with as much detail as possible.

For the most part I think you've done your research so you are correct in many of your assumptions. I'll try to clarify a few things.

A "shell script" is basically a collection of commands in a file. The file is read by a "shell interpreter" and the commands are executed in sequence, from top to bottom. The style of commands depends on the shell interpreter. Two very common types of shell are the Bourne-type shells, and the C-type shells. So, "bash", which is commonly available in modern Linux distributions is a Bourne-shell, and "tcsh" is a C-shell. Personally, I've never used "tcsh". It seems it is not very popular nowadays, but plenty of documentation of all kinds of programs reference it. So, maybe it was more common in the 1990s and gradually lost popularity. Nevertheless, since things in Linux live forever, you can easily install it, which apparently you already did.

So, in order to run a script, you preface it with the shell executable
```

bash some_script
bash ./some_path/some_script
bash a/relative/dir/some_script

tcsh some_script_c
tcsh /a/full/path/some_script_c

```
This will run the scripts, in the current directory, or in their relative or full directory, using the specific "bash" or "tcsh" shell.

Another way of running scripts is by giving the relative path or the full path of the script
```

./some_script
some/relative/path/some_script
/home/user/mydir/some_script

```
The first line indicates "in the present directory (indicated by the point) run the file «some_script»".
The second line indicates "in the directory «some/relative/path» run the file «some_script»".
The third line indicates "run the file «/home/user/mydir/some_script»".

Using the full path will guarantee that it finds the file. In order to use a relative path you need to be in the correct top level directory, otherwise it will not be found.

Now, when you just give the script's name, you don't specify the shell to use. It just says "run this file". So, how does the system know which shell to run?
> 
- I have no idea about the "shebang" line and where to put it. So if you please explain all of them on my .bashrc file if it's no problem?


Inside the file, the first line in the script is the "shebang". This name comes from "hashbang". Popularly, the # is a "hash", and the ! is a "bang". This first line indicates which interpreter should be used to run this script.
```

#!/bin/tcsh -f

```

So, when you run
```

td_plot [options]

```
What the system actually runs is
```

/bin/tcsh -f td_plot [options]

```
You don't add a shebang to "bashrc", you add it to a script, such as "td_plot". In fact, you don't need to modify this file because it already has the correct shebang. It seems that when you run "td_plot" you don't get any errors, so actually it seems everything works as intended. You are already running "td_plot" with the correct shell (tcsh).

The "bashrc" file is a configuration file for the bash shell, which is the default for Ubuntu. In this file you add some useful options for your shell, and you also add environmental variables that you want to have available in all programs that you open through that shell.

```

export TD_HOME=/home/asdfgh/TDEFNODE
alias tdefnode='/home/asdfgh/TDEFNODE/tdefnode'
alias td_plot='/home/asdfgh/TDEFNODE/td_plot'

```
What this does is it creates a variable TD_HOME, assigns some directory and exports the variable.
It also creates some aliases, so "tdefnode" is equivalent to the full path of the program. I mentioned above that you need to give the full path of a program. If you create an alias like this, it will use the full path whenever you use the short name.

```

PATH=/usr/bin/gmt/:"${PATH}"
PATH=/etc/gmt/:"${PATH}"
PATH=/usr/lib/gmt/:"${PATH}"
PATH=/usr/bin/X11/gmt:"${PATH}"
PATH=/usr/share/gmt/:"${PATH}"
PATH=/usr/lib/gmt/bin/:"${PATH}"
PATH=/home/asdfgh/TDEFNODE/td_plot:"${PATH}"

```
Why exactly are you adding these directories to the PATH? Are you following some instructions that your colleagues gave you?

The default PATH includes standard directories where executables are usually found.
```

echo $PATH

```
```

/home/user/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin

```

In general, you only append non-standard directories to the PATH when you install programs manually, which seems to be your case. I have no experience with GMT, but if you installed it from the Ubuntu repository I think you should not need to modify PATH as probably it already places its executables in the usual directories like "/usr/bin". In particular, I don't understand why you need to add "/etc/gmt", "/usr/share/gmt", or "/usr/lib/gmt". You should only add to the PATH directories where actual executables reside. Directories inside "/etc", "/usr/share", or "/usr/lib" are mostly for configuration and support files, and don't have actual executables, so there is usually no reason for these directories to be included in the PATH variable.

By the way, you add **directories** to PATH, not the programs themselves. So, you could do
```

export PATH="/home/asdfgh/TDEFNODE:${PATH}"

```
to add the directory "/home/asdfgh/TDEFNODE". Inside this directory, you should find the programs "td_plot", "tdefnode", etc. There is no point in adding "/home/asdfgh/TDEFNODE/tdefnode" or "/home/asdfgh/TDEFNODE/td_plot" because these are the actual programs, not directories containing programs.

Also notice that you need to "export" the PATH, otherwise the variable is not propagated correctly to the other shells and processes.

One more thing, the PATH variable is there to look for executables. If you type "tdefnode" in the terminal it will search that program in the directories of the PATH.
```

/home/user/bin/tdefnode
/usr/local/sbin/tdefnode
/usr/local/bin/tdefnode
/usr/sbin/tdefnode
/usr/bin/tdefnode
... etc.

```
if it doesn't find it, you will get an error "command not found".

However, when you use the alias it will always substitute the short name for the long definition. So, it will not use PATH.
```

alias tdefnode='/home/asdfgh/TDEFNODE/tdefnode'

```

Here it will always substitute "tdefnode" with "/home/asdfgh/TDEFNODE/tdefnode".

So, if you use the alias, you don't need to modify the PATH to find this program. On the other hand, if you correctly set up the PATH, you do not need the alias. It seems you are setting both at the same time. Personally I find that using an alias is a dirty trick, while changing the PATH is better. If you see most guides online they will tell you to "add this directory to PATH", but none will tell you to create aliases for commands. So, I would suggest you to delete the alias lines, and just make sure the PATH variable is correct.

> 
- And lastly, I think I have to run the command on the terminal(or reboot the system):
  
 source ~/.bashrc

  Is it correct?

Thanks for your time.
Really.

Yes, when you modify "bashrc" and you want to see the changes, you have to import (source) again that file. The file is imported automatically whenever you start up your system, or when you open a new terminal. Rebooting is usually not necessary.

---

### Post by blitzkrieg2 on 2017-07-13
```

    PATH=/usr/bin/gmt/:"${PATH}"
    PATH=/etc/gmt/:"${PATH}" 
    PATH=/usr/lib/gmt/:"${PATH}"
    PATH=/usr/bin/X11/gmt:"${PATH}"
    PATH=/usr/share/gmt/:"${PATH}"
    PATH=/usr/lib/gmt/bin/:"${PATH}"

```

Actually, the codes in the .bashrc is for another software, GMT, and td_plot uses this program to draw.


```

    export TD_HOME=/home/asdfgh/TDEFNODE
    alias tdefnode='/home/asdfgh/TDEFNODE/tdefnode'
    alias td_plot='/home/asdfgh/TDEFNODE/td_plot'

```

When I remove the 2nd and 3rd lines and source the .bashrc, td_plot or tdefnode could not be executed(command not found error).


Finally, you explained that the td_plot script is running properly because of the first line in the file. There are no errors in the output, except a command:

```

rm: No match

```

Which I believe another command about deleting a folder or something, irrelevant.


In this case with all your information, it seems impossible to solve the problem or whatever is going on with this software.

Thanks anyway.

---

### Post by vocx on 2017-07-13
> **blitzkrieg2 said:**
> ```

    PATH=/usr/bin/gmt/:"${PATH}"
    PATH=/etc/gmt/:"${PATH}" 
    PATH=/usr/lib/gmt/:"${PATH}"
    PATH=/usr/bin/X11/gmt:"${PATH}"
    PATH=/usr/share/gmt/:"${PATH}"
    PATH=/usr/lib/gmt/bin/:"${PATH}"

```

Actually, the codes in the .bashrc is for another software, GMT, and td_plot uses this program to draw.

I know. You mentioned that you installed GMT. But how did you install it? There is a package in the Ubuntu repository called "gmt". I assume it is this package. Usually, if you install packages from the repositories you don't need to alter the PATH variable because the program's files are placed in the correct directories, and the executables will be found in their normal locations, normally, "/usr/bin".

But if you downloaded the GMT software, and manually installed it (extracted it into a directory), then yes, maybe you need to manually modify the PATH variable. But this is not recommended. The recommended way to install programs in a modern Linux distribution is to use a package manager, which in Ubuntu is accessed through the "apt" command.

```

apt show gmt

# to install
sudo apt install gmt

```

> 
```

    export TD_HOME=/home/asdfgh/TDEFNODE
    alias tdefnode='/home/asdfgh/TDEFNODE/tdefnode'
    alias td_plot='/home/asdfgh/TDEFNODE/td_plot'

```

When I remove the 2nd and 3rd lines and source the .bashrc, td_plot or tdefnode could not be executed(command not found error).

You will have that error if the PATH is not correctly set. So, delete the two alias lines, but add the proper directory to PATH.
```

    export TD_HOME=/home/asdfgh/TDEFNODE

    # Remove these
    #alias tdefnode='/home/asdfgh/TDEFNODE/tdefnode'
    #alias td_plot='/home/asdfgh/TDEFNODE/td_plot'

    # Add the correct directory
    export PATH="${TD_HOME}:${PATH}"

    # This is the same as
    #export PATH="/home/asdfgh/TDEFNODE:${PATH}"

```

> 
Finally, you explained that the td_plot script is running properly because of the first line in the file. There are no errors in the output, except a command:

```

rm: No match

```

Which I believe another command about deleting a folder or something, irrelevant.

This could mean that the script is trying to remove a file that doesn't exist. If it does not seem to stop the execution of the script, then it's probably not a major issue, just some case that doesn't affect the result.

> 
In this case with all your information,** it seems impossible to solve the problem** or whatever is going on with this software.

Thanks anyway.
This is my main concern. **You have not explained what the problem is**. You said "td_plot" runs. Then, what's the problem exactly?

If everything runs okay, then this means you need to read the documentation of your software, "tdefnode" and "td_plot", and figure out exactly what it expects as input and what kind of output it generates.

Since this is a Fortran program, I will just assume it's some sort of finite element solver for hydraulic or structural engineering, or that it does numerical calculations on some sort of input file. With these types of technical software, if your input is not adequate (bad definition of boundary conditions, simulation speed, material parameters, etc.), you will find a strange or non-existent output. That is, the program will run properly, as intended, but the output will not be a good solution. This is just my guess.

---

### Post by blitzkrieg2 on 2017-07-13
Actually you're correct of your assumptions. This program is about tectonics and resolves the relative block movements, written by one person, and he seems very busy to fully help.

The problem is that the output files are in the expected format(txt files including rows with some values) and seems fully "drawable"(actually, TDEFNODE cannot provide any output file if there's a problem through the process). Here,  final output should be a map of some continent or region, and there should be vectors showing the velocities on certain points. But the only thing we've got is certain base maps produced by GMT(I've installed GMT not manually). The vectors are not shown. For me, that may refer that some part of this td_plot draws the base map; but cannot draw the vector inputs. 

I have a test file from the producer of the software, also. And there's a proper final output in the PDF file. The interesting part is that I cannot even plot the test file correctly. 

I'm not sure but there might be another possibility. The orginal software was processes with Fedora 23 on a desktop, but I'm trying to run it on Ubuntu 14 on a virtual machine. Some compatibility issue might arise this problem. 

One last thing, a long shot but if it is possible to run this td_plot script under tcsh shell somehow, might be a solution. Other than that, it's impossible to dig in the codes of td_plot or translate it from tcsh to bash correctly.

---

### Post by steeldriver on 2017-07-13
Nothing you've told us suggests it **isn't** being run under tcsh - it almost certainly would **not run at all** under any other shell (with the possible exception of the - original - csh) since the syntaxes would be incompatible

If you try to run it in bash or sh for example it will immediately crash out with syntax errors

Really IMHO you are barking up the wrong tree here - if td_plot isn't giving the output that you expect, it's **not **because of your shell

---

### Post by vocx on 2017-07-13
> **blitzkrieg2 said:**
> Actually you're correct of your assumptions. This program is about tectonics and resolves the relative block movements, written by one person, and he seems very busy to fully help.

The problem is that the output files are in the expected format(txt files including rows with some values) and seems fully "drawable"(actually, TDEFNODE cannot provide any output file if there's a problem through the process). Here,  final output should be a map of some continent or region, and there should be vectors showing the velocities on certain points. But the only thing we've got is certain base maps produced by GMT(I've installed GMT not manually). The vectors are not shown. For me, that may refer that some part of this td_plot draws the base map; but cannot draw the vector inputs. 

I have a test file from the producer of the software, also. And there's a proper final output in the PDF file. The interesting part is that I cannot even plot the test file correctly. 

Okay, so this seems to be the problem. The script "td_plot", which internally uses the GMT software, does not plot correctly the files, not even the test file.

> 
I'm not sure but there might be another possibility. The orginal software was processes with Fedora 23 on a desktop, but I'm trying to run it on Ubuntu 14 on a virtual machine. **Some compatibility issue might arise this problem. **

First, that it is in a virtual machine should not be a problem. However, the version of Ubuntu may in fact affect the version of the GMT software under use.

Basically, each Linux distribution has repositories with software. In Ubuntu, the software is "frozen in time" in a particular version. For example, it may be the case that Fedora 23 has GMT version 5.2, while Ubuntu 14.04 has GMT version 4.9. So, maybe the author of "tdefnode" expects you, the user, to use GMT version 5.2 with his code, and maybe you don't have the correct version.

Ubuntu distributions have a version number, the first number is the year, and the second the month. So Ubuntu 14.04 was released April 2014. That is quite an old version, in Linux terms, of course. Three years pass fast in the Linux world. The current Ubuntu version is 17.04, released in April 2017.

Since you don't seem to care about Ubuntu other than to run the "tdefnode" software, I would suggest you to install Ubuntu 17.04. In this way, your software repositories will be more recent, and maybe you will notice that now "td_plot" works. You could try this, unless you have a particular reason for sticking to 14.04.

There is one case that is also possible. Say, Ubuntu 17.04 is the latest version, and it has GMT 5.2. But, the "tdefnode" software actually requires GMT 5.5. So how do you install the newest GMT? Well, this would warrant a separate thread. You would have to get the GMT source, and install it in your system. This happens sometimes in Linux. The software that is in the distribution repositories (Ubuntu in this case) usually is older (frozen in time) than the most recent version available by the developers. In many cases using a slightly older version is not a problem, and other times you are forced to have the latest version for other programs to work. This is just speculation, but it's a possibility.

So, my suggestion is to install Ubuntu 17.04 in the virtual machine, and test again the "tdefnode" and "td_plot" programs.

> 
One last thing, a long shot but if it is possible to run this td_plot script under tcsh shell somehow, might be a solution. Other than that, it's impossible to dig in the codes of td_plot or translate it from tcsh to bash correctly.
Remember, because of the shebang, you are already running "td_plot" with "tcsh" when you run
```

td_plot -p map -m mode

```

It is definitely not impossible to translate the "td_plot" to bash, but you do need some experience with the shell. You need to know what is going on, and understand the way the script is using the GMT program. I presume the "td_plot" script basically reads the input file, and then it uses GMT to draw the respective map and vectors from the read data. In your post #3, you posted the initial lines from "td_plot" and it does not look very complicated. It basically runs commands in sequence, setting some variables. If it had many conditional branches, like "if", "then", "else" clauses, then it could be hard to know what it does.

```

#!/bin/tcsh -f
## set $TD_HOME to be the path to this directory
## creates and uses a scratch directory $TD_HOME/scratch/$USER
set TD_scratch = $TD_HOME/scratch/$USER
if ( ! -e $TD_scratch ) mkdir $TD_scratch

### where grid files are
# if using etopo2
set ETOPO2 = /ssd/gmt_data/etopo2/etopo2.grd
# if using SRTM
set SRTM   = /ssd/gmt_data/srtm

## RM's data directory
#set dn = '/home/mccafr/work/dn'   

## defaults
set pgm = 'map'
set w1 = 100 e1 = 120 n1 = 40 s1 = -40
set t1 = 2000 t2 = 2014 dt = 1 dtin = 0 tset = 0
set Jt = 0
...

```

One thing you can try, open your terminal, then run "tcsh",
```

tcsh

```
once you are inside "tcsh", you can actually run each line of "td_plot". That is, open "td_plot" in a text editor, and copy and paste one line to the terminal running "tcsh", hit enter and see the result. Do this until you find an error, or something that doesn't seem right. If "td_plot" is really 600 lines long, this will be tedious, but it's a way to debug the problem.

I suspect the problem is with the GMT program. Maybe it is not correctly accepting the input file, and thus not drawing the vectors that you want. But it does become difficult to troubleshoot if you don't have enough knowledge on GMT or the shell.

So my advice still stands. Install Ubuntu 17.04, install GMT, install "tcsh", and try again, and hope it works. If it doesn't, contact the author of the program and ask him for more advice. Or, also try installing the same version as him. If he is using Fedora 23, maybe you should try using the same in the virtual machine.

---

### Post by blitzkrieg2 on 2017-07-13
It seems the most plausible action is to fit the orginal conditions, which includes Fedora 23, GMT 4, and compiling the TDEFNODE for Fedora. 

I presume it will take ages (with my ignorance on Linux), but I'll keep this topic updated if possible. I have to start from somewhere.

Thanks for your help all.

---

### Post by blitzkrieg2 on 2017-07-24
Finally, I figured out to work with these softwares. I don't want this topic to be a dead end, so I'll simply explain the installation process. Maybe it'll be useful somehow:


1- Installation and next process seems to rely on the versions of the softwares. 
2- I installed Ubuntu 16.04 on a VMware virtual machine(4 CPUs, 4 GB RAM).
3- Install netcdf(libnetcdf-dev) and gdal(libgdal1-dev).
4- Download GMT-4.5.14, GSHHG-GMT-2.3.4, GMT4param.txt, and install_gmt4.sh
5- Change the parameters on GMT4param.txt: 
   GSHHG_ftp=n
   GSHHG_path= (installation path)
   GMT_ftp=n
   GMT_prefix= (installation path)
   GMT_delete=n
6-Install these files, using: 
   sudo sh install_gmt4.sh GMT4param.txt
7-Add PATH of GMT to your .bashrc file.


These steps are for GMT. 


For TDEFNODE:


1-Download and compile TDEFNODE.
2-Put all the files in a directory.
3-Specify the PATHs for TDEFNODE and td_plot in .bashrc
4-Install tcsh package.


Now the software runs and works with GMT. Seems no error so far.

---

### Post by vocx on 2017-07-24
> **blitzkrieg2 said:**
> Finally, I figured out to work with these softwares. I don't want this topic to be a dead end, so I'll simply explain the installation process. Maybe it'll be useful somehow:

1- Installation and next process seems to rely on the versions of the softwares. 
2- I installed Ubuntu 16.04 on a VMware virtual machine(4 CPUs, 4 GB RAM).
3- Install netcdf(libnetcdf-dev) and gdal(libgdal1-dev).
4- Download GMT-4.5.14, GSHHG-GMT-2.3.4, GMT4param.txt, and install_gmt4.sh
5- Change the parameters on GMT4param.txt: 
   GSHHG_ftp=n
   GSHHG_path= (installation path)
   GMT_ftp=n
   GMT_prefix= (installation path)
   GMT_delete=n
6-Install these files, using: 
   sudo sh install_gmt4.sh GMT4param.txt
7-Add PATH of GMT to your .bashrc file.

These steps are for GMT. 

For TDEFNODE:
1-Download and compile TDEFNODE.
2-Put all the files in a directory.
3-Specify the PATHs for TDEFNODE and td_plot in .bashrc
4-Install tcsh package.

Now the software runs and works with GMT. Seems no error so far.
This is great. Thanks for the follow up. In support forums it is typical that a user asks a question, then just disappears without a conclusive solution. That you documented your solution will be helpful for future researchers that are having a similar problem. It shows you are a true scientist.

So, basically the solution is to install a particular version of the GMT software from source, as it appears the available GMT in the Ubuntu repositories does not work with your version of the TDEFNODE program.

---

### Post by blitzkrieg2 on 2017-07-24
> **vocx said:**
> This is great. Thanks for the follow up. In support forums it is typical that a user asks a question, then just disappears without a conclusive solution. That you documented your solution will be helpful for future researchers that are having a similar problem. It shows you are a true scientist.

So, basically the solution is to install a particular version of the GMT software from source, as it appears the available GMT in the Ubuntu repositories does not work with your version of the TDEFNODE program.


That's correct. Seems offline installation working properly, at least for these versions.

Thanks for your help.

---

### Post by vocx on 2017-07-24
> **blitzkrieg2 said:**
> That's correct. Seems offline installation working properly, at least for these versions.

Thanks for your help.
By the way, I realize now that the title of this thread is not very descriptive. You should go to the first post of this thread, edit the post, and change the title to something like "help getting TDEFNODE work with GMT" or something more accurate. Also, in this first post you can use the "thread tools" to mark the thread as SOLVED.

---

