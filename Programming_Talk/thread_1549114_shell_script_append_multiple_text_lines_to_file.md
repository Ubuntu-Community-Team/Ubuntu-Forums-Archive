---
title: "shell script append multiple text lines to file?"
date: 2010-08-09
forum: Programming Talk
---

### Post by madinc on 2010-08-09
hello to all i need help with a shell script and my knowledge is almost 0 if someone would be willing  to help  that would be so good.

how can i append multiple text lines to a file from within the script?

---

### Post by Bachstelze on 2010-08-09
```
echo "foo
bar
baz" >> file.txt
```

---

### Post by madinc on 2010-08-09
i will try right now thanks Bachstelze

---

### Post by madinc on 2010-08-09
it doesn't do what i need and gives error.
i need to append something like this:

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoredups:ignorespace

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

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
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

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
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

---

### Post by Bachstelze on 2010-08-09
You need to escape the quotes in the text. Why would you ever want to do that, though? If that's what you want in your .bashrc, just copy it over.

---

### Post by madinc on 2010-08-09
i want to make a scrip that will run once on a fresh install i will show you so that you know what i mean and the .bashrc i posted it's original i want to do it with a modified one.

#!/bin/bash
#By:Madinc
#Date:09/08/2010
#
#Name:mad-essential
#Version:1.2
#License:GNU General Public License.
#Use:Create A Bin Directory Modify The .bashrc File Add Extra 3rd Party Binary Repos And Install Lots Of Apps To Ubuntu 10.04 LTS.
#Info:This Script Was Made To Fit My Needs Feel Free To Modify It To Fit Yours.

echo "Starting Modification & Installation.
Do You Wish To Continue? (y/n)"
read ans

case $ans in
Y|y) ;;
[Yy][Ee][Ss]) ;;
N|n) exit ;;
[Nn][Oo]) exit ;;
*) echo "Invalid command"
esac

#create a bin directory.
echo "Creating A Bin Directory"
if [ "$HOME/bin" ]; then
  echo "You Already Have A Bin Directory"
else
  mkdir $HOME/bin
fi

#save your original .bashrc file.
echo "Backing Up The .bashrc File"
if [ "$HOME/.bashrc" ]; then
  cp $HOME/.bashrc $HOME/.bashrc.backup
else
  touch $HOME/.bashrc
fi

#to do here i don't know#modify the .bashrc file.
echo "Modifying The .bashrc File"

#install python-software-properties.
echo "Installing python-software-properties"
sudo apt-get install python-software-properties

#save your original sources.list file.
echo "Backing Up The sources.list"
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup

#add extra repositories.
echo "Adding Repositories"
#uncomment all repositories listed in the sources.list file. 
sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list

#add Ailurus repo
# Ailurus - [http://code.google.com/p/ailurus/](http://code.google.com/p/ailurus/)
echo "Adding Ailurus Repo"
sudo add-apt-repository ppa:ailurus

#add AWN (Avant Window Navigator) repo
#AWN (Avant Window Navigator) Testing Packages - [http://awn-project.org/](http://awn-project.org/)
echo "Adding AWN (Avant Window Navigator) Repo"
sudo add-apt-repository ppa:awn-testing/ppa

---

### Post by DaithiF on 2010-08-09
Hi,
so I assume you have this content in a file somewhere, and you want to append it to another file?

```
cat file-with-the-content-to-append >> another-file

```


Edit: err, hang on, sounds like you want to replace a file's contents, not append to it?
cp /path/to/your/modified.bashrc  /home/someuser/.bashrc

---

### Post by madinc on 2010-08-09
i Daithif thanks for the help i'm trying to do something like this but without the errors in the terminal.

#!/bin/bash

cat <<EOF >>/home/madinc/Desktop/newfile

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoredups:ignorespace

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

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
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

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

EOF

---

### Post by conundrumx on 2010-08-09
Please describe exactly what you want to accomplish.  What are you starting with, what do you have, and what is your end goal?

---

### Post by madinc on 2010-08-09
i will backup then delete the .bashrc make a new empty one and append a modified one from within the script

---

### Post by madinc on 2010-08-09
i'm very new to computers and to linux i'm sorry if i cannot explain better

---

### Post by DaithiF on 2010-08-09
Hi,
you shoudn't do it this way, you would have to escape lots of stuff within the content to prevent it being expanded by bash as you cat it (everything of the form $(blah blah) will get executed and replaced with the results of its execution as it flies past)

so instead put this content into a file somewhere, then either cat or cp the file as described above.

---

### Post by DaithiF on 2010-08-09
Hi, so how about something like:
```
mv /home/newuser/.bashrc{,.orig}              # rename existing .bashrc to .bashrc.orig
cp /path/to/your/.bashrc /home/newuser/     # copy your template .bashrc to newusers home
```

---

### Post by madinc on 2010-08-09
> **DaithiF said:**
> Hi,
you shoudn't do it this way, you would have to escape lots of stuff within the content to prevent it being expanded by bash as you cat it (everything of the form $(blah blah) will get executed and replaced with the results of its execution as it flies past)

so instead put this content into a file somewhere, then either cat or cp the file as described above.


the meaning was to do everything with the script only and not the script with other files

---

### Post by conundrumx on 2010-08-09
> **DaithiF said:**
> Hi, so how about something like:
```
mv /home/newuser/.bashrc{,.orig}              # rename existing .bashrc to .bashrc.orig
cp /path/to/your/.bashrc /home/newuser/     # copy your template .bashrc to newusers home
```

This is the solution you're looking for.

---

### Post by madinc on 2010-08-09
no but thanks anyways guys.

---

### Post by DaithiF on 2010-08-09
actually, you *can* do it -- you need to quote the opening EOF, like:

```
cat <<"EOF" > somefile.out
 blah
 blah
EOF

```

amazing what you can (continue to) learn from **man bash**  :)

---

### Post by madinc on 2010-08-09
> **DaithiF said:**
> actually, you *can* do it -- you need to quote the opening EOF, like:

```
cat <<"EOF" > somefile.out
 blah
 blah
EOF

```amazing what you can (continue to) learn from **man bash**  :)


can i put like this  or must i put cat <<"EOF" > $HOME/.bashrc.out

see below

#!/bin/bash
#By:Madinc
#Date:09/08/2010
#
#Name:mad-essential
#Version:1.2
#License:GNU General Public License.
#Use:Create A Bin Directory Modify The .bashrc File Add Extra 3rd Party Binary Repos And Install Lots Of Apps To Ubuntu 10.04 LTS.
#Info:This Script Was Made To Fit My Needs Feel Free To Modify It To Fit Yours.

echo "Starting Modification & Installation.
Do You Wish To Continue? (y/n)"
read ans

case $ans in
Y|y) ;;
[Yy][Ee][Ss]) ;;
N|n) exit ;;
[Nn][Oo]) exit ;;
*) echo "Invalid command"
esac

#create a bin directory.
echo "Creating A Bin Directory"
if [ "$HOME/bin" ]; then
  echo "You Already Have A Bin Directory"
else
  mkdir $HOME/bin
fi

#save your original .bashrc file.
echo "Backing Up The .bashrc File"
if [ "$HOME/.bashrc" ]; then
  cp $HOME/.bashrc $HOME/.bashrc.backup
else
  touch $HOME/.bashrc
fi

#delete the original .bashrc file.
rm $HOME/.bashrc

#make new .bashrc file.
touch $HOME/.bashrc

#i need to append all this below into the new .bashrc above the closest i #get is like this and gives error in the terminal but it does append #everything.see below.

cat <<EOF >>$HOME/.bashrc

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
#case "$TERM" in
#xterm-color)
#    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
#    ;;
#*)
#    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
#    ;;
#esac

# Created by James Manning <jmm@raleigh.ibm.com>
# Changed by Spidey 08/06
function combo {
PS1="\[\033[01;34;01m\]\333\262\261\260\[\033[01;37;44m\]\u@\h\[\033[00;34;40m\]\260\261\262\333\[\033[00;34;40m\]\333\262\261\260\[\033[01;37;40m\]\d \$(date +%I:%M:%S%P)\n\[\033[01;33;40m\]$PWD>\[\033[00m\] "
PS2="\[\033[01;34;01m\]\333\262\261\260\[\033[00;34;40m\]\260\261\262\333\[\033[00;34;40m\]\333\262\261\260\[\033[01;01;34m\]>\[\033[00m\] 
"
}

# Comment in the above and uncomment this below for a color prompt
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

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
alias ll='ls -l'
alias la='ls -A'
alias l='ls -CF'

#Information
alias weather='/usr/bin/weather -f --id=KSLC -c "Salt Lake City" -s UT'
alias gcalcli='gcalcli --cals all'

#For getting around
alias videos='cd /home/multimedia/Media/Videos/Video/ && ls'
alias pics='cd /home/multimedia/Media/Pictures/ && ls'
alias music='cd /home/multimedia/Media/Music/ && ls'
alias podcasts='cd /home/multimedia/Media/podcasts/ && ls'
alias current='cd ~/current/ && ls'
alias dropbox='cd ~/Dropbox/ && ls'
alias documents='cd ~/Documents/ && ls'
alias notes='cd ~/Notes/ && ls'
alias backup='cd /media/backup/backups && ls'

#------Extraction of compressed files--------------
# from ARCH Wiki

extract () {
  if [ -f $1 ] ; then
      case $1 in
          *.tar.bz2)   tar xvjf $1    ;;
          *.tar.gz)    tar xvzf $1    ;;
          *.bz2)       bunzip2 $1     ;;
          *.rar)       rar x $1       ;;
          *.gz)        gunzip $1      ;;
          *.tar)       tar xvf $1     ;;
          *.tbz2)      tar xvjf $1    ;;
          *.tgz)       tar xvzf $1    ;;
          *.zip)       unzip $1       ;;
          *.Z)         uncompress $1  ;;
          *.7z)        7z x $1        ;;
          *)           echo "don't know how to extract '$1'..." ;;
      esac
  else
      echo "'$1' is not a valid file!"
  fi
}

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

function my_ip() # get IP adresses
{
        MY_IP=$(/sbin/ifconfig eth0 | awk "/inet/ { print $2 } " | sed -e s/addr://)
        MY_ISP=$(/sbin/ifconfig eth0 | awk "/P-t-P/ { print $3 } " | sed -e s/P-t-P://)
}

function ii() # get current host related info
{
    echo -e "\nYou are logged on ${RED}$HOST"
    echo -e "\nAdditionnal information:$NC " ; uname -a
    echo -e "\n${RED}Users logged on:$NC " ; w -h
    echo -e "\n${RED}Current date :$NC " ; date
    echo -e "\n${RED}Machine stats :$NC " ; uptime
    echo -e "\n${RED}Memory stats :$NC " ; free
    my_ip 2>&. ;
    echo -e "\n${RED}Local IP Address :$NC" ; echo ${MY_IP:."Not connected"}
    echo -e "\n${RED}ISP Address :$NC" ; echo ${MY_ISP:."Not connected"}
    echo
}



PATH="$HOME/bin:$PATH"

/usr/bin/verse

EOF

#install python-software-properties.
echo "Installing python-software-properties"
sudo apt-get install python-software-properties

#save your original sources.list file.
echo "Backing Up The sources.list"
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup

#add extra repositories.
echo "Adding Repositories"
#uncomment all repositories listed in the sources.list file. 
sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list

#add Ailurus repo
# Ailurus - [http://code.google.com/p/ailurus/](http://code.google.com/p/ailurus/)
echo "Adding Ailurus Repo"
sudo add-apt-repository ppa:ailurus

#add AWN (Avant Window Navigator) repo
#AWN (Avant Window Navigator) Testing Packages - [http://awn-project.org/](http://awn-project.org/)
echo "Adding AWN (Avant Window Navigator) Repo"
sudo add-apt-repository ppa:awn-testing/ppa

---

### Post by madinc on 2010-08-09
> **DaithiF said:**
> actually, you *can* do it -- you need to quote the opening EOF, like:

```
cat <<"EOF" > somefile.out
 blah
 blah
EOF

```amazing what you can (continue to) learn from **man bash**  :)


and thanks this much closer to what i want

---

### Post by DaithiF on 2010-08-09
just change this line:
```
cat <<EOF >>$HOME/.bashrc
```
to:
```
cat <<"EOF" >>$HOME/.bashrc

```

---

### Post by madinc on 2010-08-09
> **DaithiF said:**
> just change this line:
```
cat <<EOF >>$HOME/.bashrc
```to:
```
cat <<"EOF" >>$HOME/.bashrc

```





thank you so much you rule thanks :D

---

### Post by madinc on 2010-08-09
it runs perfectly thanks a lot DaithiF you are tha best ;)

---

### Post by DaithiF on 2010-08-09
great, you're welcome.

just something else I noticed in your script.  you do something like this a couple of times:
```
if [ "$HOME/bin" ]; then 
...

if [ "$HOME/.bashrc" ]; then
...


```
these won't work the way you want.

to illustrate, try this:
[ "$HOME/nosuchfileexists" ] && echo "True" || echo "False"

see what i mean?

instead try:
[ **-e** "$HOME/nosuchfileexists" ] && echo "True" || echo "False"

-e means 'exists', (or you can be more specific and use use **-d** for directory exists or **-f** for file exists, etc).

without an operator like this you aren't testing for the existence of a file, instead you are testing whether your string is empty or not.

---

### Post by madinc on 2010-08-09
> **DaithiF said:**
> great, you're welcome.

just something else I noticed in your script.  you do something like this a couple of times:
```
if [ "$HOME/bin" ]; then 
...

if [ "$HOME/.bashrc" ]; then
...


```these won't work the way you want.

to illustrate, try this:
[ "$HOME/nosuchfileexists" ] && echo "True" || echo "False"

see what i mean?

instead try:
[ **-e** "$HOME/nosuchfileexists" ] && echo "True" || echo "False"

-e means 'exists', (or you can be more specific and use use **-d** for directory exists or **-f** for file exists, etc).

without an operator like this you aren't testing for the existence of a file, instead you are testing whether your string is empty or not.


should i put like this if not please give me a better example like i posted my knowledge is almost 0 this script is all google search.

#create a bin directory.
echo "Creating A Bin Directory"
if [ "$HOME/bin" ] && echo "True" || echo "False" then
  echo "You Already Have A Bin Directory"
else
  mkdir $HOME/bin
fi

:???:

---

### Post by DaithiF on 2010-08-09
like this:

```
if [ -d "$HOME/bin" ]; then
    echo "You Already Have A Bin Directory"
else
    mkdir $HOME/bin
fi

```
and 

```
if [ -e "$HOME/.bashrc" ]; then
    cp $HOME/.bashrc $HOME/.bashrc.backup
else
    touch $HOME/.bashrc
fi

```

---

### Post by madinc on 2010-08-09
> **DaithiF said:**
> like this:

```
if [ -d "$HOME/bin" ]; then
    echo "You Already Have A Bin Directory"
else
    mkdir $HOME/bin
fi

```and 

```
if [ -e "$HOME/.bashrc" ]; then
    cp $HOME/.bashrc $HOME/.bashrc.backup
else
    touch $HOME/.bashrc
fi

```


once again thank you very very much i have learned a lot thanks to you, if there were more people like you life would be so much easier :D

---

