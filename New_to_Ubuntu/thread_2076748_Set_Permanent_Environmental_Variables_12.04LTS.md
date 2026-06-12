---
title: "Set Permanent Environmental Variables 12.04LTS"
date: 2012-10-26
forum: New to Ubuntu
---

### Post by mysteriouskiwi on 2012-10-26
Hi,

Having a little trouble finding good documentation on adding in environmental variables permanently in Ubuntu 12.04LTS.

I've read the official documentation, search on these forums on others and viewed all relevant posts from other people on editing the: ~/.bashrs , ~/.profile , /etc/environment.

I've also tried adding a ~/.pum_environment with the supposed correct formating, which caused a crash of my user, fixing it by going into the text login (CTRL+ATL+F1) and loading the default PATH variables again (. /etc/environment) and deleting the file.

I'm trying to add these, as currently I am doing it manually in the Terminal at the beginning of each session.

```

export NETKIT_HOME=~/netkit
export PATH=$PATH:$NETKIT_HOME/bin
export MANPATH=:$NETKIT_HOME/man

```I'm currently using netkit and really would like to add these to my PATH to remove me doing to manually.

I'm assuming I need to add it to ~/.profile , which i have tried logged-in, out, to reload it and nothing happened (creating a backup first of course, in case it failed).

I would like really simple instructions to learn it first. Please if you respond, could include why things are placed there so I actually learn something instead of just doing it? Hehe :)

The original documentation is here: [http://wiki.netkit.org/netkit-labs/netkit_introduction/netkit-introduction.pdf ]("http://wiki.netkit.org/netkit-labs/netkit_introduction/netkit-introduction.pdf")(page 16, "Setting up Netkit").

Thanks :)

---

### Post by offgridguy on 2012-10-26
What are environmental variables anyway ??

---

### Post by madinc on 2012-10-26
look for ~/ .bashrc file and add what you want at the end.

---

### Post by madinc on 2012-10-26
> **madinc said:**
> look for ~/ .bashrc file and add what you want at the end.

for example to add my bin to the path  "/home/madinc/bin" i add this code at the end of the bashrc file like this:

```
export PATH
PATH="/home/madinc/bin:$PATH"

```

---

### Post by mysteriouskiwi on 2012-10-26
So, for example, would the '.bashrc' file look like this?:

```

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
   #my lines
   export NETKIT_HOME
   NETKIT_HOME="~/netkit:$NETKIT_HOME"
   export PATH
   PATH="$NETKIT_HOME/bin:$PATH"
   export MANPATH
   MANPATH="$NETKIT_HOME/man:$MANPATH"
fi

```

Would that work? Off to bed as it's 4:30am, but I'll check back on this later! :)

Thanks for the help, by the way! :D

---

### Post by mysteriouskiwi on 2012-10-26
> **offgridguy said:**
> What are environmental variables anyway ??

I believe something in which are defined system or session wide to provide processes with common links to areas of the operating system, by user or developer definition.

For example, to set the PATH for new Java installations for the JDK so that it can access its root files. Like an operating shell for processess, an aid to defined directories for the bash/shell/command area to check if the user hasn't predefined their own input, in which it checks before throwing an error or returning the correct desired result.

Say, you're programming in C and have a directory setup for that. You would assign a new PATH to that director[SIZE=2]y, to tell the OS to check that directory when you input say "test.c", instead of having to type "./test.c" do show the process what directory that file is in to run.[/SIZE] 

Eg: say your directory for working with said 'test.c' was "~/c_stuff/", ' PATH="$PATH":~/c_stuff ' would add the directory to the predefined directories in which the execute command would search in for the desired file name when you type in Bash "test.c". If the path is added correctly the program will run as it has found the path with the file named 'test.c' and run it. Instead of the person typing ./test.c to define the location and execute the file.

Although with Netkit, the PATH(s) have to be set as it needs to use the commands without defining the directory each time. It would be like having to type ' . /etc/environment ' every time you wanted to use Terminal, so you have access to; sudo, rm, cp, etc....

Sorry if that is slightly over complicated it or is just poorly explained. :)

---

### Post by madinc on 2012-10-27
> **mysteriouskiwi said:**
> Would that work? Off to bed as it's 4:30am, but I'll check back on this later! :)

Thanks for the help, by the way! :D
 
Well it works for me but most people seem to put it in ~/.bash_profile i really don't know the difference i just put it in the ~/.bashrc at the end of it after "fi"  and not like you have there i hope it works for you too if it does please let me know you can also check this link [http://www.troubleshooters.com/linux/prepostpath.htm](http://www.troubleshooters.com/linux/prepostpath.htm)
and this [http://www.linuxheadquarters.com/howto/basic/path.shtml](http://www.linuxheadquarters.com/howto/basic/path.shtml)
and my favourite [https://www.ccs.uky.edu/docs/cluster/env.html](https://www.ccs.uky.edu/docs/cluster/env.html)
sometimes it's a matter of trial & error please let  me know what worked for you.


```
# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi
export DEBFULLNAME="Madinc"
export DEBEMAIL="madinc29@gmail.com"
export PATH
PATH="/home/madinc/bin:$PATH"

```

---

### Post by madinc on 2012-10-27
```
# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi
export DEBFULLNAME="Madinc"
export DEBEMAIL="madinc29@gmail.com"
export PATH
PATH="/home/madinc/bin:$PATH"

```

To take efect type this in the terminal

```
~/.bash_profile
```

doing that you don't need to logout.

---

### Post by mcduck on 2012-10-27
put it ~/.bashrc if you want it to only affect terminal sessions, or in ~/.profile if you want the variables to be set any time you are logged in, including the graphical environment.

(~/.bashrc is sourced for each Bash session, while ~/.profile is sourced when you log in, for all shells and graphical environments)

---

### Post by Vaphell on 2012-10-27
default config adds ~/bin (if it exists) to $PATH automatically either way (~/.profile)

---

### Post by madinc on 2012-10-27
> **Vaphell said:**
> default config adds ~/bin (if it exists) to $PATH automatically either way (~/.profile)

Hey i didn't know that since which Ubuntu version because i have done this since 8.04?

---

### Post by jerome1232 on 2012-10-27
My understanding is system wide environment variables are actually "supposed" to go in /etc/environment in Ubuntu. User only enviroment variables should go in ~/.pam_environment

see this documentation [https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)

It's a long story but some variables get reset if they are in the places others have mentioned, I ran into this specifically with a variable related to getting minecraft to work on a 64 bit machine.

---

### Post by madinc on 2012-10-28
> **jerome1232 said:**
> My understanding is system wide environment variables are actually "supposed" to go in /etc/environment in Ubuntu. User only enviroment variables should go in ~/.pam_environment

He said to have tried that and didn't work.

---

### Post by jerome1232 on 2012-10-28
That's what I get for skimming, my bad.

---

### Post by asaleemsajid on 2012-10-28
1. Create a file custom.sh in the folder /etc/profiled.d with the required commands . 
 
   **[COLOR="Blue"] sudo vi /etc/profile.d/custom.sh[/COLOR]**

In place of vi you can use gedit / nedit or the like

In your case custom.sh will have the following lines:
export NETKIT_HOME=~/netkit
export PATH=$PATH:$NETKIT_HOME/bin
export MANPATH=:$NETKIT_HOME/man

2.Make the file executable
command :[COLOR="blue"]** chmod +x custom.sh**[/COLOR]

3.Now these variables are permanently available. To remove them either eit the file or remove the file itself.

4.I use this approach in RHEL and it works flawlessly

---

### Post by drmrgd on 2012-10-28
> **madinc said:**
> Hey i didn't know that since which Ubuntu version because i have done this since 8.04?

Not sure since when exactly, but it's outlined in your ~/.profile file by default:

```
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
```

As mcduck says, you're best off putting the extra paths in .profile if you want them system wide, while just putting them in .bashrc would suffice if you only need them in bash shells.

EDIT:  Also should point out that if you create ~/bin and want it to become part of your path, all you need to do is to logout and log back on, or simply reload your shell:

```
source ~/.bashrc
```

---

### Post by madinc on 2012-10-28
> **drmrgd said:**
> Not sure since when exactly, but it's outlined in your ~/.profile file by default:

EDIT:  Also should point out that if you create ~/bin and want it to become part of your path, all you need to do is to logout and log back on, or simply reload your shell:
  Thank's it's always good to know.

---

