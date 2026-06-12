---
title: "alias syntax"
date: 2012-06-07
forum: New to Ubuntu
---

### Post by cmcanulty on 2012-06-07
I have an alias in my bash.rc file as follows
```

alias ud='sudo apt-get update && sudo apt-get upgrade -y && sudo apt-get dist-upgrade -y && sudo apt-get clean -y'
```

my question is can I add something that will let the alias to run without asking for a password?

---

### Post by vasa1 on 2012-06-07
My apt-get is a bit simpler but ```
alias fast='echo "password" | sudo -S apt-get update && sudo -S apt-get upgrade'

```works for me. It's my own PC and I'm the only user.

Also, mine is in .bash_aliases.

---

### Post by cmcanulty on 2012-06-08
OK great it worked after I figured out to change password to the actual password, duh, thanks One question why is the password first rather than after the commands?

---

### Post by vasa1 on 2012-06-08
> **cmcanulty said:**
> OK great it worked after I figured out to change password to the actual password, duh, thanks One question why is the password first rather than after the commands?
I did a copy pasta from somewhere. I'd like to know the answer as well :)

[http://stackoverflow.com/questions/233217/pass-password-to-su-sudo-ssh](http://stackoverflow.com/questions/233217/pass-password-to-su-sudo-ssh) has something ...

---

### Post by cortman on 2012-06-08
Because you're piping (|) the password text to sudo. The -S flag tells it to read from standard input rather than user input.

---

### Post by cmcanulty on 2012-06-08
new issue now:
after doing the new alias my terminal opens every time like this. I tried reset and clear but it keeps opening like that now.

```
bash: alias: need: not found
bash: alias: to: not found
bash: alias: enable: not found
cmcanulty@Darcy25:~$ 

``` 


Here is my bash.rc file

```
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
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF' 

alias ud='echo "m" | sudo -S apt-get update && sudo -S apt-get upgrade''



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
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi
export MOZ_DISABLE_PANGO=1 
export PATH=$PATH:/var/lib/gems/1.8/bin
export EDITOR="gedit"
cd ~
```

---

### Post by vasa1 on 2012-06-08
> **cortman said:**
> Because you're piping (|) the password text to sudo. The -S flag tells it to read from standard input rather than user input.

I think OP is wondering about the order. If we do things "normally", we do sudo apt-get **first** and **then** get prompted for the password. In the code, the password comes **first** and sudo apt-get comes **second**.

---

### Post by vasa1 on 2012-06-08
> **cmcanulty said:**
> new issue now:
after doing the new alias my terminal opens every time like this. I tried reset and clear but it keeps opening like that now.
...
Why do you not have a **separate** .bash_aliases file? (Not that I know what the present problem is or that I'm implying that .bashrc shouldn't be used for storing aliases.)

---

### Post by cortman on 2012-06-08
That isn't your entire .bashrc- what's causing the error doesn't appear to be in the section you pasted. Please paste the entire file.
One error is right here-

```
alias ud='echo "" | sudo -S apt-get update && sudo -S apt-get upgrade''
```

There's an extra single quote at the end. Delete it- I don't think it's causing the errors mentioned but it will cause others.
Also, you gave your sudo password in that paste- usually not a good idea. I deleted it out of the part I quoted, and you may want to edit your post.

---

### Post by vasa1 on 2012-06-08
Also, this seems odd:
alias ud='echo "m" | sudo -S apt-get update && sudo -S apt-get upgrade**''**

You end that line with **double quotes**. Maybe that's one problem. I didn't look at the full thing.

I still feel it's better to keep a separate file for aliases!

---

### Post by cmcanulty on 2012-06-08
Here is my whole bash.rc file, I thought I copied the whole file before but maybe not.I fixed the double quote at end of command.I don't have a .bash_aliases file.

```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# don't overwrite GNU Midnight Commander's setting of `ignorespace'.
HISTCONTROL=$HISTCONTROL${HISTCONTROL+,}ignoredups
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
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
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF' 

alias ud='echo "m" | sudo -S apt-get update && sudo -S apt-get upgrade'



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
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi
export MOZ_DISABLE_PANGO=1 
export PATH=$PATH:/var/lib/gems/1.8/bin
export EDITOR="gedit"
cd ~
```

---

### Post by cortman on 2012-06-09
Did fixing the extra single quote fix the error?

---

### Post by cmcanulty on 2012-06-10
i was dog sitting but this am -yes it worked, thanks!

---

### Post by cmcanulty on 2012-06-15
I altered the alias a bit and now get this error, but I don't know which -S it refers to as there is more than one. Can someone look at this and tell me what is wrong

```
alias ud='echo "my password here" | sudo -S apt-get update -y && sudo -S apt-get upgrade -y && sudo -S apt-get dist-upgrade -y && -S sudo apt-get clean -y'
```

  and here is the error

```
-S: command not found
```

---

### Post by vasa1 on 2012-06-15
> **cmcanulty said:**
> ...
alias ud='echo "my password here" | 
sudo -S apt-get update -y && 
sudo -S apt-get upgrade -y && 
sudo -S apt-get dist-upgrade -y && 
**_-S sudo_** apt-get clean -y'


The last one

---

### Post by vasa1 on 2012-06-15
I don't know how often you're planning to run that but why include **dist-upgrade**?

I've never understood its function even though people have been kind enough to explain :(

And I don't like **-y**. I'd rather watch things and provide the input when prompted.

---

### Post by NoTryDO on 2012-06-15
> **vasa1 said:**
> I don't know how often you're planning to run that but why include **dist-upgrade**?

I've never understood its function even though people have been kind enough to explain :(

And I don't like **-y**. I'd rather watch things and provide the input when prompted.

Maybe this helps [**apt-get question: dist-upgrade vs upgrade**]("https://www.linuxquestions.org/questions/fedora-35/apt-get-question-dist-upgrade-vs-upgrade-219920/")
like you I do not like "-y"

---

### Post by cmcanulty on 2012-06-15
Ok I think I will go safe and use it like this. I want to automate as much as possible as I run 10 Ubuntu machines at our library. Does it look OK now?

```
alias ud='echo "my password here" | sudo -S apt-get update -y && sudo -S apt-get upgrade -y && sudo apt-get clean -y'
```

---

### Post by vasa1 on 2012-06-15
> **cmcanulty said:**
> Ok I think I will go safe and use it like this. I want to automate as much as possible as I run 10 Ubuntu machines at our library. Does it look OK now?

alias ud='echo "my password here" | 
sudo -S apt-get update -y && 
sudo -S apt-get upgrade -y && 
sudo apt-get clean -y'

This time you left out the last **-S**. Is that intentional?

---

### Post by dodo3773 on 2012-06-16
Just so you know sudo eventually times out. I am pretty sure you need to pipe your sudo password to each sudo -S command. Like this:
```

echo password | sudo -S command1 && echo password | sudo -S command2 

```

I may be wrong but it does not seem to me that the password is going to be echoed to the second command the way you have it now.

---

### Post by vasa1 on 2012-06-16
> **dodo3773 said:**
> Just so you know sudo eventually times out. I am pretty sure you need to pipe your sudo password to each sudo -S command. Like this:
```

echo password | sudo -S command1 && echo password | sudo -S command2 

```

I may be wrong but it does not seem to me that the password is going to be echoed to the second command the way you have it now.

I've been using the following code for several months:```
alias fast='echo "password" | sudo -S ./bin/apt-fast update && sudo -S ./bin/apt-fast upgrade'

```with no time-out issues.

---

### Post by dodo3773 on 2012-06-16
> **vasa1 said:**
> I've been using the following code for several months:```
alias fast='echo "password" | sudo -S ./bin/apt-fast update && sudo -S ./bin/apt-fast upgrade'

```with no time-out issues.

I understand. What I am saying though is what if the first command took up to 35 minutes to complete? I am sure it hasn't yet as syncing your system would not normally take that long. But if it did would the string still be the correct one? That is what I am getting at. What if one part of the OPs alias does for some reason? What I am saying is that just because it has caused you no issues does not mean that it is the right way to do it. 

I personally do not use a time out for sudo at all. So my password going through once would be enough for me to run sudo commands all day long until I closed that shell or ran "sudo -k". So I too would not have any issues either. But that is not my point at all.

---

### Post by vasa1 on 2012-06-16
> **dodo3773 said:**
> I understand. What I am saying though is what if the first command took up to 35 minutes to complete? I am sure it hasn't yet as syncing your system would not normally take that long. But if it did would the string still be the correct one? That is what I am getting at. What if one part of the OPs alias does for some reason? What I am saying is that just because it has caused you no issues does not mean that it is the right way to do it. ...
You could be right, but, as you say, it hasn't yet happened (which doesn't make my way right either). What about this possibility: that the sudo doesn't not expire or the countdown doesn't start until the first task is complete?
But it would be nice to find something that removes doubt. [s]I'll take a look at [http://aplawrence.com/Basics/sudo.html](http://aplawrence.com/Basics/sudo.html).[/s]

---

### Post by dodo3773 on 2012-06-16
> **vasa1 said:**
>  What about this possibility: that the sudo doesn't not expire or the countdown doesn't start until the first task is complete?


It depends on the setup in your sudoers file. If you want sudo to not expire you would have to launch visudo and add a line like this (my sudoers):
```

Defaults:dodo3773 timestamp_timeout=-1

```

With your user name instead of mine of course. Be sure to test this by opening another shell before closing your sudoers file just in case. Any syntax error can really mess you up here. As to your other question yes the time out starts as soon as you hit enter after entering your password for sudo. I only know this from long long compile times in the past hahaha.

---

### Post by vasa1 on 2012-06-16
> **dodo3773 said:**
> It depends on the setup in your sudoers file. If you want sudo to not expire you would have to launch visudo and add a line like this (my sudoers):
```

Defaults:dodo3773 timestamp_timeout=-1

```
...
Thanks, I'll keep that in mind but I'm not too keen on having sudo _not_ expire. So far, I haven't done anything to sudoers.

---

### Post by dodo3773 on 2012-06-16
> **vasa1 said:**
> Thanks, I'll keep that in mind but I'm not too keen on having sudo _not_ expire. So far, I haven't done anything to sudoers.

Ah okay. Well either way by default (this is of course assuming that the original OP does use a default sudoers file) there is a time out. What I am trying to tell you is that this:
```

alias fast='echo "password" | sudo -S ./bin/apt-fast update && sudo -S ./bin/apt-fast upgrade'

```

and this:
```

alias fast='echo "password" | sudo -S ./bin/apt-fast update && sudo ./bin/apt-fast upgrade'

```

is the same thing. Or so I think. I am having a hard time understanding how the first echoed password could still be stored in stdin for the second command. That is all I was really trying to say. I guess I got a little off topic.

---

### Post by vasa1 on 2012-06-16
> **dodo3773 said:**
> Ah okay. Well either way by default (this is of course assuming that the original OP does use a default sudoers file) there is a time out. What I am trying to tell you is that this:
```

alias fast='echo "password" | sudo -S ./bin/apt-fast update && sudo -S ./bin/apt-fast upgrade'

```

and this:
```

alias fast='echo "password" | sudo -S ./bin/apt-fast update && sudo ./bin/apt-fast upgrade'

```

is the same thing. Or so I think. I am having a hard time understanding how the first echoed password could still be stored in stdin for the second command. That is all I was really trying to say. I guess I got a little off topic.

I'm not sure we're off-topic. I certainly hope not!

Come to think of it, if the apt-get update is done real fast, takes me about 3 min with a rotten connection, won't the password still be alive for apt-get upgrade?

Anyway, I'm feeling dizzy and need my lunch ;)

---

### Post by dodo3773 on 2012-06-16
> **vasa1 said:**
> 
Come to think of it, if the apt-get update is done real fast, takes me about 3 min with a rotten connection, won't the password still be alive for apt-get upgrade?


Well yes and no. In a sense you are right. For example if you were to type a command such as "sudo echo something" in your shell it would ask you for your password. Now if you were to type it again right away it would not need your password because the timeout for sudo has not expired yet. So in a way yes your password is still stored.

But where it is not stored is in stdin (the original echo "password"). Especially not since you are breaking the 2 commands apart with "&&". If you took the second -S out of your alias it should do the exact same thing because it is serving no purpose. Maybe it would make more sense to stick both commands together without the "&&" by issuing "sudo bash -c" (assuming you use bash for me it would be the same but with zsh). Something like:
```

echo "password" | sudo -S bash -c "command1; command2"

```

Have a great lunch.

---

### Post by cmcanulty on 2012-06-16
to Post #19 I took out the last -S as post #15 said I should. Now I am confused and don't understand how to know when to use the -S

---

### Post by vasa1 on 2012-06-16
> **cmcanulty said:**
> to Post #19 I took out the last -S as post #15 said I should. Now I am confused and don't understand how to know when to use the -S
Well, the points dodo3773 is making, if I understand correctly, are:
[LIST]
[*]If multiple commands requiring sudo are chained with && , there's a possibility of timing out if one or more of the earlier commands takes a long time. The default "life" of sudo is [15 min]("https://help.ubuntu.com/community/RootSudoTimeout") (thanks, Elfy).
[*]Assuming that one is sure that _all_ the commands will be completed within 15 min, with the clock starting when you hit enter after the alias, only one **-S**, the _first_ one, is needed; subsequent ones are redundant because [FONT="Courier New"]echo "password"[/FONT] is _not_ stored.
[/LIST]

I hope I got that correct!

Both dodo3773 and the answerer [here]("http://askubuntu.com/questions/151601/can-i-automate-updating-upgrading-with-sudo-in-this-way"), suggest another way to run multiple commands that need **sudo**: this way requires entering the password once (rather than storing the password in your .bashrc or wherever which could constitute a potential risk).

---

### Post by dodo3773 on 2012-06-16
> **cmcanulty said:**
> to Post #19 I took out the last -S as post #15 said I should. Now I am confused and don't understand how to know when to use the -S

Here is the simple answer: Standard input or stdin is the beginning of the pipe or the "echo password". This is taken by the -S switch for sudo. If you wanted to echo your password to sudo for multiple commands you need to do something like this (as indicated by the link vasa1 just sent you):
```

echo password | sudo -S command1 && echo password | sudo -S command2

```
The security risk involved is that anyone who can view your .bashrc (.bash_profile whatever) can see your password as it is in plaintext. Personally I am the only one with direct access to my machine and this does not bother me at all. But that is certainly something you have to keep in mind.


If you are still confused do this: Open a terminal. Type "echo something". Notice how the word something is displayed in your terminal? Well instead of that word getting echoed in your terminal it is being piped (the "|" symbol) into the next command. This is relevant to a lot more then just the sudo command. It is something important to learn if you decide to start doing a lot of scripting.


Not sure if I can explain it any better then that. If you are still confused feel free to ask any question you may have.

---

