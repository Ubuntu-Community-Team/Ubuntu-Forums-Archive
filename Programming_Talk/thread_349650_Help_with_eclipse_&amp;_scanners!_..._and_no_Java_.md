---
title: "Help with eclipse &amp; scanners! ... and no Java_home file?"
date: 2007-01-30
forum: Programming Talk
---

### Post by littleman54321 on 2007-01-30
To start out, I followed these 2 threads, and it's still not working properly for me.
[http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378)
[http://ubuntuforums.org/showthread.php?t=332674&highlight=move+directory](http://ubuntuforums.org/showthread.php?t=332674&highlight=move+directory)

Eclipes starts and runs. It read my workspace, and displays my code all nice and pretty and everything. Yay, all is well, except not. It's not recognizing the freakin' scanner package. There's also an "append" command that it is not liking.

```

matt@matt-laptop:~$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

```

Just for reference, that's my java version. When I type $JAVA_HOME, I get tihs:

```

matt@matt-laptop:~$ echo $JAVA_HOME
/home/matt/Desktop/Java6

```

I've also read in one of those threads that I would need to modify the JAVA_HOME file. Well, call me old fashioned, but that file has to exist for me to modify it, and I swear to god I cannot find it. 

When I right click on the existing project, I CAN change the compiler to 5.0 (and even 6.0), but it STILL doesn't like me using scanners. This EXACT code works perfectly on my windows machine. I don't know what else to do at this point.

Any thoughts? I *really* need to get this working so I don't have to keep switching to my windows box to write my programs for class, and so I can write code on my lappy while in class (not gonna mess with dual booting on this thing). Thanks in advance for any help :)

---

### Post by Tomosaur on 2007-01-30
$JAVA_HOME is an environmental variable rather than a file - you need it to point to the top level of the JDK directory:

/home/me/development/JDK


It sounds to me like you're not running the correct JDK. I only used the 'free' version of the JDK once, and immediately got rid of it when I saw how certain things were named differently, and it was just generally horrible.

You need to download and install the official sun JDK. The thread you linked to does tell you to download the right one, but I'm thinking your JAVA_HOME is pointing to the wrong place.

---

### Post by littleman54321 on 2007-01-30
> **Tomosaur said:**
> $JAVA_HOME is an environmental variable rather than a file - you need it to point to the top level of the JDK directory:

/home/me/development/JDK


It sounds to me like you're not running the correct JDK. I only used the 'free' version of the JDK once, and immediately got rid of it when I saw how certain things were named differently, and it was just generally horrible.

You need to download and install the official sun JDK. The thread you linked to does tell you to download the right one, but I'm thinking your JAVA_HOME is pointing to the wrong place.

Well, I got it from the sun website, so it's pretty much gotta be the right one. Here is what I added into the bashrc thingy

```
#BEG Copy and Paste
#Copy and Paste at the bottom of your .bashrc file
# ~~~~~~~~~~~~~~~~~ JAVA (JDK,JRE) ~~~~~~~~~~~~~~~~~~~~~ 
export JAVA_HOME='/home/matt/Desktop/Java6'
PATH=$JAVA_HOME:$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH
# 
# The eclipse alias below assumes that you have extracted the eclipse folder
# to your desktop. It can be anywhere. Edit path as necessary
#
alias eclipse='java -jar /etc/eclipse/startup.jar'
#END Copy and Paste
```

The java6 folder is on my desktop. Maybe the Path= part is wrong?

---

### Post by Tomosaur on 2007-01-30
try adding these instead:
```

export JAVA_HOME=/home/matt/Desktop/Java6/bin
export PATH=$PATH:$JAVA_HOME

```

Then reload your terminal app.
That *should* work, but you may find some conflicts between the 'real' java executables as opposed to the 'free' ones (which may already be in your /bin) folder. If this is the case, you can convert the free executables in /bin to symbolic links to the real ones in the Java6/bin dir.

Don't forget to update $JAVA_HOME and $PATH if you move/delete/rename the Java6 folder.

---

### Post by Ramses de Norre on 2007-01-30
Enter the right JRE in window>properties>java>installed JRE's and set your compiler default compliance level to 5.0. Scanner is supported since java5 only.

---

### Post by littleman54321 on 2007-01-30
How do I find where this file is? Or do I have to download it from somewhere? or...
It should have been downloaded and installed with the JDK, right?

---

### Post by phossal on 2007-01-30
lol Hey! I recognize what you added to your .bashrc.  ;)

---

### Post by phossal on 2007-01-30
Ramses is right, by default, once you've set the compiler correctly:

```
import java.util.Scanner;

public class Scan {

}
```

---

### Post by littleman54321 on 2007-01-30
> **phossal said:**
> lol Hey! I recognize what you added to your .bashrc.  ;)

=D
I added the other JRE, and the thing compiles now! YAY! But.....

Why don't I want to export PATH that way?

And another thing, when I type sudo -b gedit ~/.bashrc, it tells me file doesn't exist.... 
And when I open a new terminal window, I get this right before I get the "matt@matt-laptop:~$ "
```
bash: export: `/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/home/matt/Desktop/Java6/bin': not a valid identifier

```

Hmmmm.

---

### Post by phossal on 2007-01-30
Yeah, because every time you open a terminal window, it's going to "export" your path. lol That's one reason why you don't want to do that. In addition, if you include $PATH (even though I say to do it, you *shouldn't****) in its own definition, each time you *open a terminal window* path will add its definition to itself again. lol That's kind of stupid, isn't it?

Instead, once you understand how it works, you should add your *real path.* For example, here is how I actually have mine set up:
```
export JAVA_HOME='/usr/lib/Java6'
export CATALINA_HOME='/home/phossal/Desktop/Tomcat6'
PATH=$JAVA_HOME:$JAVA_HOME/bin:$JAVA_HOME/jre/bin:'/usr/local/sbin:/usr/local/bin:/usr/bin:/usr/sbin:/bin:/sbin'
```

Every time you open a terminal, it executes .bashrc. So, the way I have mine set up is so that $PATH stays exactly the same, but includes changes to my $JAVA_HOME variable. That way, I can change "homes" on the fly, without having my $PATH grow to include files it shouldn't.


[COLOR="Gray"][SIZE="1"]***I want everyone to succeed, so I try to make it as easy as possible. People inevitably *learn* and correct my intended mistakes.[/SIZE][/COLOR]

---

### Post by littleman54321 on 2007-01-30
so...i guess my question now is, how the hell do i get to that file to edit it, if the terminal is telling me it doesn't exist. o.O

---

### Post by phossal on 2007-01-30
> **littleman54321 said:**
> And another thing, when I type sudo -b gedit ~/.bashrc, it tells me file doesn't exist.... 

This works correctly for me:
```
sudo -b gedit ~/.bashrc
```

There are a couple reasons why it might not work for you. As a workaround issue:
```
gedit ~/.bashrc &
```

Another way is to use Nautilus, and go into your home directory, and then hit Ctrl-H (to view hidden files). Then just open it like normal. If it *isn't there*, you have bigger problems. lol

---

### Post by Ramses de Norre on 2007-01-30
Why do you edit files in your home directory with sudo? That's the best way to mess up permissions... (without intending to)

---

### Post by littleman54321 on 2007-01-30
guess i should just be more patient :p

The sudo -b ~/.bashrc was working for me, until just a few minutes ago..

```

matt@matt-laptop:~$ sudo -b gedit ~/.bashrc
bash: sudo: No such file or directory
matt@matt-laptop:~$ sudo -b gedit ~/.bashrc
bash: sudo: No such file or directory
matt@matt-laptop:~$ gedit ~/.bashrc &
[1] 5568
matt@matt-laptop:~$ bash: gedit: No such file or directory
matt@matt-laptop:~$ gedit ~/.bashrc&
[2] 5571
[1]   Exit 127                gedit ~/.bashrc

```

That's what it gives me now. Before, the file popped up. Now, nada.

---

### Post by phossal on 2007-01-30
Just use nautilus. Go into your home directory, and press Ctrl-H to view the hidden files.

---

### Post by Ramses de Norre on 2007-01-30
> **littleman54321 said:**
> guess i should just be more patient :p

The sudo -b ~/.bashrc was working for me, until just a few minutes ago..

```

matt@matt-laptop:~$ sudo -b gedit ~/.bashrc
bash: sudo: No such file or directory
matt@matt-laptop:~$ sudo -b gedit ~/.bashrc
bash: sudo: No such file or directory
matt@matt-laptop:~$ gedit ~/.bashrc &
[1] 5568
matt@matt-laptop:~$ bash: gedit: No such file or directory
matt@matt-laptop:~$ gedit ~/.bashrc&
[2] 5571
[1]   Exit 127                gedit ~/.bashrc

```

That's what it gives me now. Before, the file popped up. Now, nada.

What have you entered in your ~/.bashrc?!? That file can cause serious damage to your availability to use bash, as you can see. Post the changes here.

---

### Post by littleman54321 on 2007-01-30
This is what it says atm:

What I added is at the very bottom.

```

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
xterm-color)
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
*)
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    ;;
esac

# Comment in the above and uncomment this below for a color prompt
#PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    ;;
*)
    ;;
esac

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

#BEG Copy and Paste
#Copy and Paste at the bottom of your .bashrc file
# ~~~~~~~~~~~~~~~~~ JAVA (JDK,JRE) ~~~~~~~~~~~~~~~~~~~~~ 
export JAVA_HOME='/home/matt/Desktop/Java6/bin'
export PATH=$PATH:$JAVA_HOME
# 
# The eclipse alias below assumes that you have extracted the eclipse folder
# to your desktop. It can be anywhere. Edit path as necessary
#
alias eclipse='java -jar /etc/eclipse/startup.jar'
#END Copy and Paste

```

---

### Post by phossal on 2007-01-30
```
export JAVA_HOME='/home/matt/Desktop/Java6'
PATH=$PATH:$JAVA_HOME:$JAVA_HOME/bin:$JAVA_HOME/jre/bin
```

With those changes, and the file saved and closed:
```
source ~/.bashrc
```


lol The problem is that the value of $PATH is not what it should be. But it will correct itself next time you reboot. ::shrug::

---

### Post by littleman54321 on 2007-01-30
Alright, thanks :)

Now, just so I'm not playing "monkey follow the ball", what exactly is being said in the path line? Trying to learn this stuff so I can actually have an idea of what's going on :guitar:  ...just because.

---

### Post by phossal on 2007-01-30
PATH is a system variable that includes the paths to locations which the system will look for executable commands. For example, when you type java -version, it runs through the list of locations stored in PATH to see if "java" exists in there. If it finds it, it runs java with the arguments you've specified. If it doesn't find it, it tells you no command found. 

If you type:
```
echo $PATH
```
It will show you the locations.

Try it.

In fact, if you type $JAVA_HOME, it will show you the value of it:  /home/matt/Desktop/Java6. 

Oreilly Publishers publishes a good (short, concise) book on bash. It's worth reading if you're serious about Linux.

---

### Post by littleman54321 on 2007-01-30
sweet. Thanks for the info :)

Right now I'm trying out linux, seeing how much I can learn and what not. So far, it's been a bit of a pain, but when I finally get it working, it's like "WOO!"

Next on the list: Get wireless working
Dual Monitors
???
Profit

;) South Park fans will get it.

---

