---
title: "HOWTO: make life easier in terminal using bash aliasing"
date: 2005-06-26
forum: Outdated Tutorials &amp; Tips
---

### Post by moment on 2005-06-26
I prefer command line to anything else whenever it's possible. So I usually work in terminal. There is a capability in bash which enables you to define aliases for commands in order to make them easier to run or just as a matter of convenience. For instance you might want to have untgz as an alias for "tar xvfz" and simply type untgz foo.tar.gz to uncompress it. Or you might need to make the "rm" command safer by aliasing it to "rm -i" to ask you if it should be really removed in order to save you from horrible mistakes.

First of all open a terminal and type
```
gedit .bashrc
```

near the end of the file uncomment and change these lines:
```
# Define your own aliases here ...
#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

```
to:
```
# Define your own aliases here ...
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

```
save and close the file. Now you can define your own aliases in a file named ".bash_aliases" (note the dot before the name please) in your home directory. Mine as a sample looks like this:
```
# For safety
alias cp='cp -i'
alias ln='ln -s'
alias mv='mv -i'
alias rm='rm -i'

# convenience redefinitions
alias ..='cd ..'
alias ...='cd ...'
alias cd..='cd ..'
alias cd-='cd -'
alias ls='ls -lh --color=auto'
alias dir='ls -lh --color=auto'
alias df="df -h"
alias h=history

alias untgz="tar -xvfz"
alias untbz2="tar -xvfj"
alias netstati="netstat --verbose --tcp --udp --programs --extend"

# inventions!
alias aptsource='sudo gedit /etc/apt/sources.list'
alias penning='ssh  -L 5902:localhost:5902 myusername@myhost'
alias wireless='sudo iwconfig eth1 essid belkin54g; sudo dhclient eth1'
```
I hope that some people would join me and contribute by adding their own aliases :D

---

### Post by Jesus Franco on 2005-06-26
F*cking AWESOME!
I didnt even know that was possible.  \\:D/  But then agian everything is possible with linux.
That is very VERY neat.  Thanks for that cool and neat tut.

Ones I added so far. Will add more when I get the chance  :grin: 
```

alias aptU='sudo apt-get update'
alias aptUI='sudo apt-get upgrade'
alias aptI='sudo apt-get install'
alias browse=nautilus
alias sbrowse='sudo nautilus'
```

I hope breezy includes these.

---

### Post by cdk on 2005-06-26
this is wicked m8!  i new aboit aliasing but i didnt realize i could do this much with it.  Simple awesome.  this is going to save me so much time.

cheers,

---

### Post by dbeckham32 on 2005-07-24
Thanks very much for the bash aliases tips! It may be basic for advanced users, but newbies appreciate the tips.

---

### Post by benplaut on 2005-07-24
(my syntax might be wrong)

for everything that requires sudo, 

alias synaptic='gksudo synaptic'
alias iwconfig='sudo iwconfig'

etc, etc, etc...

---

### Post by cutOff on 2005-07-25
more...
```
# some more aliases
alias vim='sudo vim'
alias nano='sudo nano'
alias up='sudo aptitude update'
alias search='sudo aptitude search'
alias show='sudo aptitude show'
alias ins='sudo aptitude install'
alias rem='sudo aptitude purge'
alias clean='sudo aptitude clean'
alias break='dpkg -l | grep -v ^ii'
alias purge='sudo dpkg --purge'
alias huerfan='sudo deborphan | sudo xargs apt-get remove -y'  (require deborphan installed)
alias rules='sudo iptables -L -n'
alias cd..='cd ..'
alias repos='sudo nano /etc/apt/sources.list'
```

---

### Post by benplaut on 2005-07-25
[QUOTE=cutOff]more...
```
# some more aliases
alias nano='sudo nano'
alias up='sudo aptitude update'
alias search='sudo aptitude search'
alias show='sudo aptitude show'
alias ins='sudo aptitude install'
alias rem='sudo aptitude purge'
alias clean='sudo aptitude clean'
alias break='dpkg -l | grep -v ^ii'
alias purge='sudo dpkg --purge'
alias huerfan='sudo deborphan | sudo xargs apt-get remove -y'  (require deborphan installed)
alias rules='sudo iptables -L -n'
alias cd..='cd ..'
alias repos='sudo nano /etc/apt/sources.list'
```[/QUOTE]

replace nano with your favorite editor, of course  :wink:

---

### Post by Kyral on 2005-07-26
Here is mine!

 ```
kyral@ArcadianUbuntu:~$ cat .bash_aliases
alias cp='cp -i'
alias ln='ln -s'
alias mv='mv -i'
alias rm='rm -i'
alias ..='cd ..'
alias ...='cd ...'
alias cd..='cd ..'
alias cd-='cd -'
alias dir='ls -lh --color=auto'
alias df="df -h"
alias h=history
alias untgz="tar -xvfz"
alias untbz2="tar -xvfj"
alias aptsource='sudo gedit /etc/apt/sources.list'
alias aptU='sudo apt-get update'
alias aptUI='sudo apt-get dist-upgrade'
alias aptI='sudo apt-get install'
alias aptR='sudo apt-get remove'
alias aptS='apt-cache search'
alias aptSh='apt-cache show'
alias sourcebuild='sudo apt-get -b source'
alias depbuild='sudo apt-get build-dep'
alias debI='sudo dpkg -i'

```

---

### Post by roots on 2005-08-22
i love the quick suse style

> alias l='ls -l'


cheers,
.roots

---

### Post by roots on 2005-08-22
sorry...double post by mistake ;-)

---

### Post by crxgames on 2005-08-30
```

alias updick='/usr/bin/uptime | perl -ne "/(\d+) d/;print 8,q(=)x\$1,\"D\n\""'
alias make='colormake'
alias gcc='colorgcc'

```

---

### Post by nickless on 2005-08-30
I have no .bashrc in my home dir... but one in /root. I would have just copied it to my home, but there is no:
```
# Define your own aliases here ...
#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi
```
Also there are simply to many things in it I don't understand. Is it possible to use the one in /root ?

---

### Post by Lux Perpetua on 2005-08-30
You are using bash, right? If you do 'ps' in your terminal, it should list bash. If so, the absence of .bashrc shouldn't stop you from creating one. You can make yours a symbolic link to root's, or create a fresh .bashrc in your home directory containing your aliases. .bashrc doesn't have any special format; it is a regular old shell script that you want bash to source at startup.

---

### Post by vkkim on 2005-08-31
I like to use Princeton's WordNet as my dictionary/thesaurus of choice, and I am wondering if I can incorporate this into bash aliasing.

The standard syntax for definitions is: wn <word> -over, noun synonyms are: wn <word> -synsn, verb synonyms are: wn <word> -synsv, etc.

Could I use something that would let me alias def <word>=wn <word> -over?

---

### Post by liljencrantz on 2005-08-31
I use fish, not bash, but I thought I'd post some of my scripts here if someone likes them and wants to reimplement them in bash.

This is what they do: **unpack** unpacks all the archives given as arguments. i.e. you can write **unpack foo.tar bar.zip baz.tar.bz2** to unpack the specified archives. I use this so I don't have to remember what switches different decompressors use.

The **mkdir** and **mount** functions are wrappers around their regular counterparts. They work by calling their orginal command and it it is succesfull, the current working directory is switched.

```

# Generic archive unpacker. Extracts archives of arbitrary type
function unpack -d "Unpack arbitrary archive files"
    for i in $argv
        switch $i

            case '**.tar'
                tar -xf $i

            case '**.tar.gz' '**.tgz'
                tar -zxf $i

            case '**.tar.bz' '**.tar.bz2' '**.tbz' '**.tbz2'
                 tar -jxf $i

            case '**.rar'
                 unrar e $i

            case '**.zip'
                 unzip $i

            case '**'
                echo File $i is of unknown type

        end
    end
end

function mkdir -d "Create a directory and set CWD"
    mkdir $argv
    if test $status = 0
        switch $argv[(count $argv)]
            case '-*'

            case '*'
                cd $argv[(count $argv)]
                return
        end
    end
end

function mount -d "Mount a filesystem and set CWD"
    command mount $argv

    if test $status = 0
        switch $argv[(count $argv)]
            case '-*'

            case '**'
                cd $argv[(count $argv)]
                return
        end
    end
end


```

---

### Post by vkkim on 2005-08-31
[QUOTE=liljencrantz]I use fish, not bash, but I thought I'd post some of my scripts here if someone likes them and wants to reimplement them in bash.
[/QUOTE]

I don't know too much about shells, but what's the difference between the two and why are you using fish over bash?

---

### Post by liljencrantz on 2005-09-01
[QUOTE=vkkim]I don't know too much about shells, but what's the difference between the two and why are you using fish over bash?[/QUOTE]

I am the original author if fish, so I am far from objective, but I think it is a better shell. For a description of why, read [this page]("http://lwn.net/Articles/136232/").

---

### Post by DirtDawg on 2006-03-18
I can't seem to get this trick to work. I changed my .bashrc file and created a .bash_aliases file in my /home/dirtdawg directory, but I get nothing. For example, I tried:
alias test='echo this is a test'
in my .bash_aliases file, but I get no response. The terminal only acts like I pressed return. Other aliases simply reply "command not found"
I'm using Hoary PPC. 
What am I doing wrong?

---

### Post by virgule on 2006-03-18
I have some of these!
```

alias yum='sudo apt-get update; sudo apt-get install'
alias yup='sudo apt-get update; sudo apt-get upgrade'
alias yuk='sudo apt-get remove --purge'
alias findpkg='apt-cache search'
alias pkginfo='apt-cache show'
alias df='df -h'
alias rgrep='grep -v'
alias burn='cdrecord -speed=4 -v -pad -eject dev=/dev/sr0'

```

---

### Post by virgule on 2006-03-18
[QUOTE=DirtDawg]I can't seem to get this trick to work. I changed my .bashrc file and created a .bash_aliases file in my /home/dirtdawg directory, but I get nothing. For example, I tried:
alias test='echo this is a test'
in my .bash_aliases file, but I get no response. The terminal only acts like I pressed return. Other aliases simply reply "command not found"
I'm using Hoary PPC. 
What am I doing wrong?[/QUOTE]
You probly just need to "reload" the .bashrc and/or .bash_aliases file. Easy stuffs:

```

source ~/.bashrc
--and/or--
source ~/.bash_aliases

```

---

### Post by DirtDawg on 2006-03-18
[QUOTE=virgule]You probly just need to "reload" the .bashrc and/or .bash_aliases file. Easy stuffs:

```

source ~/.bashrc
--and/or--
source ~/.bash_aliases

```[/QUOTE]

Right on, that did it. Thank you.

---

### Post by sbkcu on 2006-05-15
Is it true that an alias cannot have any white space?
For example, is it true that I could not do
alias sudo apt-get upgrade='sudo apt-get -u upgrade'
??
Any other rules about alias syntax?
Thanks,
Steve

---

### Post by johan.t on 2006-09-26
Ok, maybe this is an old thread. But still, here is my .bash_aliases:

```
alias +alias='echo alias $1 >> ~/.bash_aliases'
alias aliases='cat -n ~/.bash_aliases'
alias bash-reload='. ~/.bashrc'
alias bash-aliases='nano ~/.bash_aliases'

alias apti='sudo aptitude install'
alias aptr='sudo aptitude remove'
alias apts='aptitude search'
alias update='sudo aptitude update'
alias upgrade='sudo aptitude upgrade'
alias dist-upgrade='sudo aptitude dist-upgrade'

alias sources='gksudo gedit /etc/apt/sources.list &'


alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias mp3='cd ~/musik'

alias fcc='/opt/firstclass/fcc &'
alias bt='btdownloadgui &'
alias irc='Eterm --trans -x --shade=0 --scrollbar=0 --buttonbar=0 --geometry=75x30+850+750 -e irssi -c chat.freenode.net --nick=PUT YOUR NICK HERE'

alias forum='firefox http://ubuntu-se.org/forum &'
alias mail='firefox http://gmail.com &'
alias google='firefox http://google.se &'

alias music='xmms ~/musik/ &'
alias rhcp='xmms ~/musik/red_hot_chili_peppers/ &'
alias soad='xmms ~/musik/system_of_a_down/ &'
alias madonna='xmms ~/musik/madonna/ &'
alias arctic='xmms ~/musik/arctic_monkeys/ &'
alias muse='xmms ~/musik/muse/ &'
alias tot='xmms ~/musik/theatre_of_tradgedy/ &'
alias queen='xmms ~/musik/Queen/ &'

alias xx='exit'
alias cc='clear'
alias ccd='cd ~/ && clear'

alias start-all='conky & gajim & xchat & mail rhcp'


```

---

### Post by andiii on 2006-09-26
I got some good ideas from this thread, so I want to post my stuff now:

```

#
# set PATH so it includes user's private bin if it exists
#if [ -d ~/bin ] ; then
#    PATH=~/bin:"${PATH}"
#fi
alias addpath='. ~/bin/etc/addpathbash'

alias rm='rm -i'
alias ll='ls -oah'
alias ln='ln -s'
alias d='ls -hCF'
alias da='ls -a'
alias sd='ls -CFRh'
alias p='pwd'
alias l='ls -lh'
alias la='ls -lah'
#alias lg='ls -l'
alias ..='cd ..; ls'
alias g='grep'
alias h='head'
alias t='tail'
alias m='most'
alias man='man -P most'
alias c='cat'
alias hi='history'
alias hg='history | grep'
alias df='df -khT'
alias du='du -hc --max-depth=1'
alias pdf='evince'
alias pdf2='pdf_preview'
alias todo='vi ~/todo'
alias shop='vi ~/shop'
alias info='/usr/bin/info'
alias apti='sudo aptitude install'
alias apts='aptitude search'

alias iwscan='iwlist eth1 scan'
alias gimpw='Xnest :1 -ac -name GIMP -geometry 1024x750 & metacity --display :1 & gimp --display :1'
alias wifi-radar='sudo wifi-radar'
alias 606='sudo mount -o loop -t iso9660 /media/sda4/linsys/ubuntu-6.06.1-alternate-i386.iso /cdrom'

#----------------
#  Pfade
alias win='cd /media/win/; pwd'
alias cd2='cd /media/sda2/; pwd; ls'
alias cd4='cd /media/sda4/; pwd; ls'
alias usb='cd /media/ANDIII_USB; pwd; ls'

#-----------------
#   geophysical
#-----------------
export MATLAB='/seismo/matlab'
alias ml='matlab &'
alias jabref='java -jar ~/bin/JabRef-2.1.jar'

#-----------------
#  functions 
#-----------------
if [ -f ~/.prompt.cfg ] ; then
source ~/.prompt.cfg
fi

function gman() {   /usr/bin/man $* | col -b | /usr/bin/gvim -R -c 'set ft=man nomod nolist' -; }

display-dhammapada
echo
fortune | cowsay -n
echo
spruch -x | cowthink -n
echo
uname -a

```

What i really like is the hg alias, I use it quite often. Also I find it useful to assign short aliases to very frequently used commands like cat, grep, more (less, most), tail.

However I have seen some tar aliases here. My tar version (1.15.1) automatically uncompresses zipped stuff. I just type "tar xvf file" and thats it.

---

### Post by fvu on 2006-11-05
You can take the .. ... .... etc aliases one step further by including the script below (cdots.sh) in your .bashrc.  This allows you to take U-turns with cd: the functions .. ... .... etc. can be given an additional argument: the directory to go forth from there.  With TAB-completion.

.. [dir] = cd ../[dir]
... [dir] = cd ../../[dir]
.... [dir] = cd ../../../[dir]
..... [dir] = cd ../../../../[dir]
...... [dir] = cd ../../../../../[dir]
....... [dir] = cd ../../../../../../[dir]
........ [dir] = cd ../../../../../../../[dir]

See also:
[http://www.fvue.nl/cdots](http://www.fvue.nl/cdots)

The script:
```

#!/bin/bash
# --- cdots.sh -------------------------------------------------------
# Change directory back - 1-7 times - and forth with TAB-completion.
# Copyright (C) 2007  Freddy Vulto
# Version: 1.0.10
# Usage: ..[.[.[.[.[.[.]]]]]] [dir]
#
# Arguments: [dir]   Directory to go forth - down the directory tree
#
# Example:   $/usr/share> .. local/share/   # .. lo[TAB]/sh[TAB])
#            $/usr/local/share>  
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2, or (at your option)
# any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software 
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, 
# MA  02110-1301, USA
#
# The latest version of this software can be obtained here:
# http://www.fvue.nl/cdots/


CDOTS_DEPTH=7


#--- _cdots() --------------------------------------------------------
# TAB completion for the .. ... .... etc commands
# @see cdots()
function _cdots() {
        # ':1' = Ignore dot at pos 0, $'\012' = newline (\n)
    local dots=${COMP_WORDS[COMP_CWORD-1]:1} IFS=$'\012' i j k=0
        #      +-----------2---------+ : Remove trailing /*s from PWD
        #      |     +-------1------+| : Replace every . with /*
    local dir="${PWD%${dots//\./\/\*}}/"
    for j in $(compgen -d -- "$dir${COMP_WORDS[COMP_CWORD]}"); do
            #  If j not dir in current dir, append extra slash '/'
            #  NOTE: With bash > v2, if j is also dir in current dir, 
            #+       'complete -o filenames' automatically appends 
            #+       slash '/'
        (( $BASH_VERSINFO == 2 )) || [ ! -d ${j#$dir} ] && j="$j/"
        COMPREPLY[k++]="${j#$dir}"
    done
} # _cdots()


#--- cdots() ---------------------------------------------------------
# Change directory to specified directories back, and forth
# @param $1 string   Directory back
# @param $2 string   Directory forth
# @see _cdots() for TAB-completion
function cdots() {
    eval cd "$1$2"
} # cdots()


    # Define aliases .. ... .... etc
    # NOTE: Functions are not defined directly as .. ... .... etc, 
    #       because these are not valid identifiers under `POSIX'
cdotsAlias=.; cdotsAliases=; cdotsDir=
for ((i = 1; i <= $CDOTS_DEPTH; i++)); do
    cdotsAlias=$cdotsAlias.; cdotsDir=$cdotsDir../
    alias $cdotsAlias="cdots $cdotsDir"
    cdotsAliases="$cdotsAliases $cdotsAlias"
done
    # Set completion of aliases .. ... .... etc to _cdots()
    # -o filenames: Escapes whitespace
complete -o filenames -o nospace -F _cdots $cdotsAliases
unset -v CDOTS_DEPTH cdotsAlias cdotsAliases cdotsDir i

```

Freddy Vulto
[http://www.fvue.nl](http://www.fvue.nl)

---

### Post by aliyanage on 2006-11-07
alias l='ls -la'
to get the hidden .filename as well :-)

---

### Post by edthefox on 2006-11-07
> **cutOff said:**
> more...
```
# some more aliases
alias vim='sudo vim'
alias nano='sudo nano'
alias up='sudo aptitude update'
alias search='sudo aptitude search'
alias show='sudo aptitude show'
alias ins='sudo aptitude install'
alias rem='sudo aptitude purge'
alias clean='sudo aptitude clean'
alias break='dpkg -l | grep -v ^ii'
alias purge='sudo dpkg --purge'
alias huerfan='sudo deborphan | sudo xargs apt-get remove -y'  (require deborphan installed)
alias rules='sudo iptables -L -n'
alias cd..='cd ..'
alias repos='sudo nano /etc/apt/sources.list'
```

be careful when aliasing commands involving sudo.

example:
you alias 'vim' to 'sudo vim'
any new file you create with vim will belong
to root. This could annoy some users =)

---

### Post by Brando569 on 2006-11-29
this trick always used to work for me and all the sudden it doesnt want to. i edited my .bashrc correctly and created my alias list and named it .bash_aliases and then i reloaded it and it didnt want to work so i renamed the file itself and changed the name in .bashrc and it still doesnt work. what gives?? btw i am using bash

---

### Post by cajunlibra on 2007-01-03
Here is mine but it doesn't work.
I'm also posting my .bashrc file also.   They have been untouched for months and the only alias that is saved is:

alias ls='ls --color=auto'

Thanks

.bashrc:
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

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    alias dir='ls --color=auto --format=vertical'
    alias vdir='ls --color=auto --format=long'

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


.bash_aliases:
alias bluetoothsearch='sudo hidd --search'
alias connectmouse='sudo hidd --connect 00:07:61:3b:0c:3e'
alias gsuoffcampus='vpnclient connect OffCampusVPN'
alias gsuoncampus='vpnclient connect OnCampusVPN'
alias gsuwireless='vpnclient connect WirelessVPN'
alias startvpn='cd /etc/init.d ; ./vpnclient_init start ;./vpnclient connect WirelessVPN'
alias aliasfile='kate /home/cajun/.bash_aliases'
alias mountrossdrive='mount /dev/sdb1 /media/sdb1'

---

### Post by Athanasius on 2007-01-12
I see some entries by people here have a single quote instead of a double quote.  I made all mine double quoted and they work fine.  Is there a difference?

```
alias upd="sudo aptitude update"
```
instead of
```
alias upd='sudo aptitude update'
```

---

### Post by jincast90 on 2007-01-12
Cool.. This seems really useful..

---

### Post by chavo on 2007-01-12
I have most of these aliases already including the multi-unarchiving script. Nere's one I use quite often that I haven't seen here ```

alias cdo='cd $OLDPWD'
```
This will cd back to the directory you just cd'd from.

These 2 functions use ps to either kill a process or just check if it's running.
```
pskill () {
    if [ ! -z $1 ] ; then
        local pid
        pid=$(ps ax | grep $1 | grep -v grep | awk '{ print $1 }')
        if [ x$pid != x ] ; then
            echo -n ">> Killing $1 (process $pid)... "
            kill -9 $pid
            echo "slaughtered"
        else
            echo "!! Process not found"
        fi
    else
        echo "!! Need process name"
    fi
}
psa() {
    if [ ! -z $1 ] ; then
        echo "Grepping for processes matching $1..."
        ps ax | grep $1 | grep -v grep
    else
        echo "!! Need name to grep for"
    fi
}

```

And finally this function will give you ownership to all the files and directories in the current directory.
```

grab() {
    sudo chown -R ${USER} ${1:-.}
}

```

---

### Post by Amaroq on 2007-03-23
There hasn't been much that has bugged me yet regarding long commands, but I do hate having to press the up arrow key endlessly until I find some big command that I can't remember. Aliasing has really helped me out with this:

I like to sometimes mess with files on my windows computer via the terminal. There's two shared folders I like to use, so I made an alias to mount each of them.

```
alias mountshared='mount -t smbfs -o username=amaroq,password=************* //192.168.1.101/SharedDocs /mnt/SharedDocs/'
alias mounthtdocs='mount -t smbfs -o username=amaroq,password=************* //192.168.1.101/htdocs /mnt/htdocs/'
```

Where those asterisks are my password, of course. Note that these aliases are for mounting a network folder from a windows computer. You'll probably have to change it if you're mounting from another linux one.

EDIT: Hmm... I'm having a bit of trouble here...
I can't use them. When I do it without sudo (which will fail, of course), it tells me that I must be root to mount. However, when I use sudo first, the command cannot be found.

I tried adding an identical file to my /root, but it did no good.

```
amaroq@Amaroq1:~$ mountshared
mount: only root can do that
amaroq@Amaroq1:~$ sudo mountshared
sudo: mountshared: command not found
amaroq@Amaroq1:~$
```

EDIT: I decided to go a different route, adding the shared folders to my fstab and using a function rather than two aliases.

I added the following to .bashrc:
```
if [ -f ~/.bash_functions ]; then
    . ~/.bash_functions
fi
```

And in the .bash_functions file:
```
function winmount {
    mount -t smbfs -o username=amaroq,password=************* //192.168.1.101/$1; }
```

I haven't gotten to test this yet, because my mom's boyfriend was using my windows computer and he shut it off when he was done with it. But, I added an option, user, to the fstab to allow users to mount it without having to be root. Therefore, I should be able to use winmount SharedDocs, as arguments passed into a function go into numbered variables, $1, $2, etc.

---

### Post by amadeov on 2007-04-05
Thanks a lot, guys!  This is really useful to define these aliases, especially for things that I  run from the command line, e.g. JabRef or Folding@Home.

From mine:
```

# folding aliases
alias fah='sudo /etc/init.d/foldingathome start'
alias fahstop='sudo /etc/init.d/foldingathome stop'
alias fahrestart='sudo /etc/init.d/foldingathome restart'
alias unit='cat /opt/foldingathome/1/unitinfo.txt'

```

---

### Post by Zdravko on 2007-04-06
> **moment said:**
> 
```
# For safety
alias cp='cp -i'
alias ln='ln -s'
alias mv='mv -i'
alias rm='rm -i'

# convenience redefinitions
alias ..='cd ..'
alias ...='cd ...'
alias cd..='cd ..'
alias cd-='cd -'
alias ls='ls -lh --color=auto'
alias dir='ls -lh --color=auto'
alias df="df -h"
alias h=history

alias untgz="tar -xvfz"
alias untbz2="tar -xvfj"
alias netstati="netstat --verbose --tcp --udp --programs --extend"


```
Can you explain each alias line by line? I am confused to try it....

---

### Post by amadeov on 2007-04-09
All of my aliases as of 4/9/2007 with new aliases for peerguardian.

```
# alias aliases
alias aliases='cat -n ~/.bash_aliases'
alias bash_reload='. ~/.bashrc'
alias bash_aliases='sudo nano ~/.bash_aliases'
alias gbash_aliases='gksudo gedit ~/.bash_aliases'

# safety aliases
alias cp='cp -i'
alias ln='ln -s'
alias mv='mv -i'
alias rm='rm -i'

# convenience redefinitions
alias ..='cd ..'
alias ...='cd ...'
alias cd..='cd ..'
alias cd-='cd -'
alias ls='ls -lh --color=auto'
alias dir='ls -lh --color=auto'
alias df="df -h"
alias md='mkdir'
alias h=history
alias hg='history | grep'
alias cc='clear'
alias ccd='cd ~/ && clear'

# folding aliases
alias fah='sudo /etc/init.d/foldingathome start'
alias fahstop='sudo /etc/init.d/foldingathome stop'
alias fahrestart='sudo /etc/init.d/foldingathome restart'
alias unit='cat /opt/foldingathome/1/unitinfo.txt'

# peerguardian aliases
alias pg='sudo peerguardian.sh start'
alias pgstop='sudo peerguardian.sh stop'
alias pgrestart='sudo peerguardian.sh restart'

# apt aliases
alias aptu='sudo aptitude update'
alias aptup='sudo aptitude upgrade'
alias apti='sudo aptitude install'
alias aptr='sudo aptitude purge'

# other aliases
alias sources='gksudo gedit /etc/apt/sources.list'
alias x11='gksudo gedit /etc/X11/xorg.conf'
alias jabref='java -jar ~/JabRef-2.2.jar'

```

---

### Post by jhenager on 2007-04-09
I don't use a lot of them, but I do use this one because I like to get out of terminal quickly.

alias x='exit'

and in Windoze, I have a lot of batch files similar to this

@echo off
exit

I call it x.bat.
also have a ls.bat that lets me do directories.

@echo off
ls.bat
dir %1 %2

You can do the same for cls, clear, and so on. Makes it easier when you go back and forth between operating systems.

---

### Post by jba6511 on 2007-09-15
I know this is an old thread but maybe I can get some help. Everything is working fine except for one command. I tried to make an alias to reload .bash_aliases. However bash gives me a command not found. Everything else works and I am sure I have the correct command listed. Any ideas? Here is a copy of my .bash_aliases 

[PHP]# For safety
alias cp='cp -i'
alias ln='ln -s'
alias mv='mv -i'
alias rm='rm -i'

#Synaptic related
alias repos='sudo gedit /etc/apt/sources.list'

#MythTV 
alias restart_myth='sudo /etc/init.d/mythtv-backend restart'

#Xorg file
alias X11='sudo gedit /etc/X11/xorg.conf'

#.bash
alias .bash_aliases='sudo gedit .bash_aliases'
alias reload_bash='source ~/.bashrc'
alias reload_alias='source ~/.bash_aliases'[/PHP]

---

### Post by zephyrus17 on 2007-12-23
How do you chain the aliases?

Basically I want a simple word to change the brightness of my 1501.

I need to log in as root first,
[COLOR="Red"]sudo -i [/COLOR]

then change the brightness,
[COLOR="Red"]echo -n 25 > /proc/acpi/video/VGA/LCD/brightness[/COLOR]

How can I chain these up? Also, can I make it so that in this case, the password is automatically entered for me when I enter root?

---

### Post by picpak on 2007-12-23
Here's my aliases:

```
alias kill='pkill'
alias apt='sudo apt-get install'
alias remove='sudo apt-get remove'
alias search='apt-cache search'
alias edit='gedit'
alias suedit='gksudo gedit'
alias i='sudo dpkg -i'
alias update='sudo apt-get update'
alias dist-upgrade='sudo apt-get dist-upgrade'
alias upgrade='sudo apt-get upgrade'
alias clean='sudo apt-get clean'
alias build-dep='sudo apt-get build-dep'
alias autoremove='sudo apt-get autoremove'
alias df='df -Hl'
alias home='cd ~'
alias mktar='tar -cvf'
alias mkbz2='tar -cvjf'
alias mkgz='tar -cvzf'
alias untar='tar -xvf'
alias unbz2='tar -xvjf'
alias ungz='tar -xvzf'
alias xorg.conf='gksudo gedit /etc/X11/xorg.conf'
alias sources.list='gksudo gedit /etc/apt/sources.list'
uucc() {
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get clean
clear
}
```

gnome-terminal should make a GUI for setting aliases. It's one of bash's best kept secrets.

---

### Post by ironstorm on 2007-12-30
> **vkkim said:**
> I like to use Princeton's WordNet as my dictionary/thesaurus of choice, and I am wondering if I can incorporate this into bash aliasing.

The standard syntax for definitions is: wn <word> -over, noun synonyms are: wn <word> -synsn, verb synonyms are: wn <word> -synsv, etc.

Could I use something that would let me alias def <word>=wn <word> -over?

Not directly, the parameter must always be the last thing in an alias...  You could however create a function in bash and alias that... 

[PHP]function mydef(){
  wn $1 -over
}
alias def='mydef'[/PHP]

---

### Post by nils234 on 2007-12-30
Heya, I cant seem to get mine working, here's my .bash_aliances file:

[PHP]
# Burning Shortcuts
alias burniso='growisofs -Z /dev/dvd='
[/PHP]

now, after the dev/dvd= I have to type the path to the iso.

When I do for example:

[PHP]
burniso ~/downloads/Film/DVD/I\ Am\ Legend/tgp-legend.img 
[/PHP]

it gives me

[PHP]
:-( unable to open64("",O_RDONLY): No such file or directory
[/PHP]
is there anyting wrong with my syntax? The file path is correct.

This does work ( when entered in terminal ):

[PHP]
growisofs -Z /dev/dvd=~/downloads/Film/DVD/I\ Am\ Legend/tgp-legend.img
[/PHP]

---

### Post by DirtDawg on 2007-12-30
You need to put quotes around any filename with spaces or unusual characters in them. For example:
```
~/downloads/FILM/DVD/Movie I did not Steal.img
```
must become:
```
~/downloads/FILM/DVD/'Movie I did not Steal.img'
```

---

### Post by nils234 on 2007-12-30
I used stripslashes so I am legend.img becomes I\ am\ legend

btw in response to the " did not steal " diss, I download low quality cams and skip through them when a movie is in the cinema. If I like what I see, I go pay for it and see it in the cinema.

---

### Post by DirtDawg on 2007-12-30
> **nils234 said:**
> 
btw in response to the " did not steal " diss, I download low quality cams and skip through them when a movie is in the cinema. If I like what I see, I go pay for it and see it in the cinema.

No diss. I just thought it was funny.

---

### Post by nils234 on 2007-12-31
ok :P no offense taken lol

---

