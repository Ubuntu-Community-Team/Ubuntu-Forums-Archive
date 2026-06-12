---
title: "What's in your .bash_aliases file?"
date: 2010-01-07
forum: Programming Talk
---

### Post by fancypiper on 2010-01-07
I am looking for some more neat tricks you can use with a .bash_aliases file.

Here is my user .bash_aliases file. Post yours. :popcorn:

## tinwhistle box ~/.bash_aliases file for user
# User specific aliases and functions

# Streaming Radio Stations
alias kdox='mplayer [http://wms2.mainstreamnetwork.com/kdox-am](http://wms2.mainstreamnetwork.com/kdox-am) &'
alias wabc='mplayer [http://69.28.128.148:80/stream/citadelcc_WABC-AM](http://69.28.128.148:80/stream/citadelcc_WABC-AM) &'

# Clear the terminal
alias cls='clear'

# Start X server
alias x='startx'

# Change bash prompt. See the article
# [http://www-106.ibm.com/developerworks/linux/library/l-tip-prompt/](http://www-106.ibm.com/developerworks/linux/library/l-tip-prompt/)
export PS1='\d \@ \[\e[32;1m\]\u\[\e[34;1m\]@\[\e[36;1m\]\H \[\e[34;1m\]\w\[\e[32;1m\] $ \[\e[0m\]'

# Monitor logs
# alias syslog='sudo tail -100f /var/log/syslog'
# alias messages='sudo tail -100f /var/log/messages'

# Keep 1000 lines in .bash_history (default is 500)
export HISTSIZE=1000
export HISTFILESIZE=1000

#Stop bash from caching duplicate lines.
HISTCONTROL=ignoredups

# Disk free in human terms
alias df='df -h'

# List paths
alias path='echo -e ${PATH//:/\\n}'

# Upgrade/update system
# alias upgrade='sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get autoremove'

# Encode wav files to flac and delete the wav file
alias zipwavd='flac -V --best --delete-input-file *.wav'

# Encode wav files to flac and keep the wav file
alias zipwav='flac -V --best *.wav'

# Decode flac files to wav format
alias uzipwav='flac -d -V *.flac'

# Encode wav to ogg
# alias oggem=oggenc -n *.wav -o *.ogg

# Allow local users to use my X session
# xhost +local:

# I can't remember the new gnome command!
alias gtop='/usr/bin/gnome-system-monitor'

# Alter the ls command
alias ll='ls --color --time-style="+%b %d %Y %H:%M"'
alias ls='ls -ac'
alias lls='ls -lac'
alias la="ls --color -lAGbh --time-style='+%b %d %Y %H:%M'"

# Set background in Fluxbox
# alias bg='fbsetbg -a /home/phil/Pictures/kells/kelljesusarrest.gif'
# alias bg='fbsetbg -a /home/phil/Pictures/kells/KellsFol114rArrestOfChrist.jpg'
# alias bg='fbsetbg -a /home/phil/Pictures/kells/KellsFol007vMadonnaChild.jpg'
# alias bg='fbsetbg -a /home/phil/Pictures/kells/4evangelists.jpg'

# Become system administrator
alias god='sudo -i'
alias root='sudo -i'

# Because less is more and more is less
alias more='less'

# xterm
# alias xterm='xterm -bg black -fg green'

# Launch links or w3m with my linux links page
alias web='links2 -g /home/phil/bookmarks.html'
alias wweb='w3mmee /home/phil/bookmarks.html'

# For nano editor
alias nano='nano -w'

# Start gkrellm after stopping it in x
alias gkrellm='gkrellm -w &'

# Kill mplayer
alias kmp='killall -9 mplayer & killall -9 gnome-mplayer'

---

### Post by akvino on 2010-01-07
lt='ls -alt|more'   ->newest files
xx='exit'

---

### Post by SuperSonic4 on 2010-01-07
```
#Installation
alias y='yaourt'
alias up='y -Syu --aur'
#
#Network
alias ping1='ping -c 4 www.google.com'
alias ping2='ping -c 4 192.168.0.1'
alias wget='wget -c'
alias mac='ifconfig | grep HWaddr'
#
#Multimedia
alias avidemux='/usr/bin/avidemux2_qt4 --video-codec xvid'
alias handbrake1='handbrake -i /dev/sr1 -t 6 -e x264 -b 1024 -E ac3 -s 1 -o output.avi'
alias flash='get_flash_videos'
#
#KDE Desktop
alias plasmoid='kbuildsycoca4 --noincremental && clear'
#alias shutdown='sudo shutdown -hP now'
alias ls='ls --color=always'
alias unmount='umount'
alias crossover='/home/lee/cxoffice/bin/cxinstallwizard /usr/bin/crossover'
#
#Other
alias 'make_me_a_sandwich'='echo "What? Make it yourself"'
alias 'sudo_make_me_a_sandwich'='echo "ok"'
#
#System
export GREP_COLOR="1;33"
alias grep='grep --color=auto'
#alias command=''history|awk '{print $2}'|awk 'BEGIN {FS="|"} {print $1}'|sort|uniq -c|sort -r''
alias hddtemp='sudo hddtemp /dev/sda /dev/sdb /dev/sdc'
#
# Amarok SVN
#export PATH=$HOME/kde/bin:$PATH
export PATH=/usr/local/bin:$PATH

```

---

### Post by apmcd47 on 2010-01-07
Among other things, [this vipath function]("http://ubuntuforums.org/showthread.php?p=8441063#post8441063"). I don't use it much now, but it can be useful.

Andrew

---

### Post by johnl on 2010-01-07
The two most useful for me:

```

# perform 'ls' after 'cd' if successful.
cdls() {
  builtin cd "$*"
  RESULT=$?
  if [ "$RESULT" -eq 0 ]; then
    ls
  fi
}

alias cd='cdls'

# search for a string recursively in any C source files 
alias src-grep='find . -name "*.[ch]" | xargs grep '


```

---

### Post by diesch on 2010-01-07
```
alias apt-install='sudo apt-get install'
alias apt-search='apt-cache search'
alias apt-show='apt-cache show'
alias apt-purge='sudo apt-get --purge  remove'
alias apt-remove='sudo apt-get remove'
alias apt-up="sudo apt-get update && sudo apt-get upgrade"
alias apt-policy="LANG=C apt-cache policy"

```

---

### Post by Barriehie on 2010-01-07
```

alias emacs='emacs22-gtk'
alias emacsfs='emacs22-gtk -fs'
alias gohome='cd ~; clear'
alias h='head'
alias ls='ls --color=auto'
alias reload='source $HOME/.bashrc'
alias showalias='cat $HOME/.bash_alias'
alias shr='shred -u '
alias t='tail'
alias temps='acpi -t'

```

---

### Post by junapp on 2010-01-07
alias h='history | grep '

---

### Post by Simian Man on 2010-01-07
alias emacs='echo "emacs sucks :P" && sleep 2 && vim'


Just in case I forget.

---

### Post by dwhitney67 on 2010-01-07
<oops... I misunderstood the thread; I thought it was about something meaningful.>

---

### Post by Rany Albeg on 2010-01-08
alias et='rm -rvf ~/.local/share/Trash'
alias rmb='rm *~ 2>/dev/null'

alias ll='ls -l'
alias la='ls -a'
alias lla='ls -la'
alias lsd='ls -d */'
alias lsb='ls|bidiv'
alias shutd='sudo shutdown -P now'
alias shutr='sudo shutdown -r now'

---

### Post by ssam on 2010-01-08
```

#find file
alias f='find . |grep '
#search history
alias h='history|grep '
#search processes
alias p='ps aux |grep '
#open any file or folder with default app
alias o='xdg-open '
#python calculator
alias pc='python -i -Qnew -c "from math import *"'
#python calculator (plus numpy and matplotlib)
alias pcn='python -i -Qnew -c "from math import *;from pylab import *"'

```

---

### Post by VCoolio on 2010-01-08
I've switched to zsh this week, has far better aliases (you can use variables in them too, and they get autocompletion for their aliased object). But here is some stuff I use:

```
alias abs-guide='w3m /usr/share/doc/abs-guide/html/index.html'
alias nano='nano -w -$'
alias nanoeconf='sudo nano /etc/easy_e17.conf'
alias nanoesh='sudo nano /usr/bin/easy_e17.sh'
alias nanosources='sudo nano /etc/apt/sources.list'
alias nanofstab='sudo nano /etc/fstab'
alias nanogrub='sudo nano /etc/default/grub && echo Now run sudo update-grub'
alias nanompd='sudo nano /etc/mpd.conf'
alias nanoxorg='sudo nano /etc/X11/xorg.conf'

alias ags='apt-get source'
alias hold='sudo hold'
alias saar='sudo add-apt-repository'
alias sagb='sudo apt-get build-dep'
alias sagi='sudo apt-get install'
alias sagr='sudo apt-get remove'
alias sagu='sudo apt-get update'
alias aptkey='sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys'
alias aptkey2='sudo apt-key adv --keyserver pool.sks-keyservers.net --recv-keys'
alias updates='aptitude search "~U"'
alias acm='apt-cache madison'
alias acp='apt-cache policy'
alias acs='apt-cache search'
alias aarc='auto-apt run ./configure'
alias dpkgrep='dpkg -l | grep -i'
alias dqp='dpkg-query -p'
alias dql='dpkg-query -L'
alias dqw='dpkg-query -W'
alias dqs='dpkg-query -S'
alias listfiles='dpkg-query -L'
alias findsource='dpkg-query -S'

alias xp='xprop | grep "WM_WINDOW_ROLE\|WM_CLASS" && echo "WM_CLASS(STRING) = \"NAME\", \"CLASS\""'
alias xterm='xterm -fa monaco -fs 12 -bg black -fg orange1 -g 95x25 -sb -rightbar'

alias ls='ls --group-directories-first --color'
alias lsgrep='ls -al --group-directories-first | grep -i'
alias psgrep='ps -ef | grep -i'
alias root='sudo -i'
alias ll='ls -al'
alias lssize='find -type f -printf '\''%s %p\n'\'' | sort -nr | head -n 40 | gawk "{ print \$1/1000000 \" \" \$2 \" \" \$3 \" \" \$4 \" \" \$5 \" \" \$6 \" \" \$7 \" \" \$8 \" \" \$9 }"'
alias c+x='chmod +x'

man2pdf() {
    if [[ -z $1 ]]; then
    	echo "USAGE: man2pdf [manpage]"
    else
    	if [[ `find /usr/share/man -name $1\* | wc -l` -gt 0 ]]; then
		out=/tmp/$1.pdf
		if [[ ! -e $out ]]; then
			man -t $1 | ps2pdf - > $out
		fi
		if [[ -e $out ]]; then
			/usr/bin/evince $out
		fi
	else
		echo "ERROR: manpage \"$1\" not found."
	fi
    fi
}


```

---

### Post by JSeymour on 2010-01-08
Most of these are functions, rather than aliases.  The first four of these shell directory ops were first "borrowed" from a csh profile from Back In The Day when all there was was Bourne shell and C shell.  When Korn shell came out, they were "ported" and expanded-on.  I've been improving and expanding them ever since.

I'm a 'nix dinosaur.  Been using some form or another of 'nix since before there was X :).  So I still spend a **lot** of my time in the shell.  Almost like one colleague of mine:
> 
Me: So why do you use X, anyway, if you spend all your time in sh?
Him: How else to organize my xterms? :)
So, for those of you who spend a lot of time in ksh or bash, you might find these handy:
```

# directory operations: pushd, popd, flipd, and swapd as per csh
# Change to new dir, pushing current onto stack
function pushd {
  export DS="$PWD:$DS"
  if [ -n "$1" ]; then cd "$1"; else cd; fi || export DS="${DS#*:}"
}
# pop top dir off stack and cd to it
function popd {
  if [ "$DS" ]
  then
    cd "${DS%%:*}"
    export DS="${DS#*:}"
  else
    echo "$0: empty directory stack" >&2
  fi
}
# flip back-and-forth between current dir and top of stack (like "cd -")
function flipd {
  if [ "$DS" ]
  then
    cd "${DS%%:*}"
    export DS="$OLDPWD:${DS#*:}"
  else
    echo "$0: empty directory stack" >&2
  fi
}
# swap top two dir stack entries
function swapd {
  typeset DSr="${DS#*:}"
  if [ "$DSr" ]
  then
    export DS="${DSr%%:*}:${DS%%:*}:${DSr#*:}"
  else
    echo "$0: less than two on directory stack" >&2
  fi
}
# rotate thru directory stack (from bottom to top)
function rotd {
  if [ "$DS" ]
  then
    typeset DSr="${DS%:*:}"
    [ "${DSr}" = "${DS}" ] || export DS="${DS##${DSr}:}$DSr:"
    flipd
  else
    echo "$0: directory stack is empty" >&2
  fi
}
# Print directory stack
function printd {
  ( IFS=:; for each in $DS; do echo $each; done; )
}
# Edit directory stack
function editd {
  export EDITDNO=$((${EDITDNO:=0} + 1))
  typeset FiLe=/tmp/`basename -- $0`$$.${EDITDNO}
  printd >${FiLe}
  ${EDITOR} ${FiLe}
  DS=`while read ea; do echo -n "$ea:"; done <${FiLe}`
  rm -f ${FiLe}
}
alias lastd="cd $(cat ~/.lastdir)"         # chng to last dir at 'bye'
# Save current dir for lastd on exit if not $HOME
alias saved='[ ${PWD} != ${HOME} ] && pwd >~/.lastdir; [ -n "${DS}" ] && echo "${DS}" >~/.dirstak'

```Standard Disclaimer: No warranty for any particular use, express or implied.  Use at your own risk!

(Edit): I realize that pushd() and popd() are bash builtins, but I over-ride them with my functions so they're all using the same directory stack.

Oh yeah, you'll also want this:
```

# get dir stack back on login
[ -s ${HOME}/.dirstak ] && export DS=`cat ${HOME}/.dirstak`

```

---

### Post by falconindy on 2010-01-08
```
alias !='sudo'
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias cdg='cd $(git rev-parse --git-dir)/..'
alias grep='grep --color'
alias hman='man -Hchromium-browser'
alias j='jobs'
alias ls='ls --color=auto'
alias ll='ls -lA --group-directories-first'
alias lsd='ls -l | grep ^[dl] --color=none'
alias md5='md5sum'
alias mkchpkg='sudo makechrootpkg -c -r /mnt/Entropy/cleanroot'
alias pp='powerpill'
alias spp='sudo powerpill'
alias sls='slurpy -c -s'
alias sld='slurpy -c -d'
alias sli='slurpy -c -i'
alias udevinfo='udevadm info -q all -n'
alias webshare='python /usr/lib/python2.6/SimpleHTTPServer.py 8001'
alias wgetxc='wget `xclip -o`'

deps() {
    [[ `file $1 | grep "shared lib"` ]] || { echo "Not a dynamically linked file"; return 1; }
    readelf -d $1 | sed -n '/NEEDED/s/.* library: \[\(.*\)\]/\1/p'

}

qp() {
    pacman-color -Qi $1 2> /dev/null
    if [[ $? -gt 0 ]]; then
        echo "$1 not found, searching..."
        pacman-color -Qs $1
        [[ $? -gt 0 ]] && echo "No local results for $1"
    fi
}

dsz() {
    [[ -z $1 ]] && target=$(pwd) || target=$1
    [[ ! -d "$target" ]] && { echo "'$target' is not a directory"; return 1; }
    du -sh $(du -s $(find $(readlink -f $target) -maxdepth 1 -type d) | sort -n | awk '{print $2}')
}

calc() {
    echo "scale=3; $*" | bc
}

unwork() {
    if [[ -z $1 ]]; then
        echo "USAGE: unwork [dirname]"
    else
        if [[ -d $1 ]]; then
            count=0
            for f in `find $1 -name .svn`; do 
                rm -r $f
                count=$((count + 1))
            done
            echo "SUCCESS. Directory is no longer a working copy ($count .svns removed)."
            unset count
        else
            echo "ERROR: $1 is not a directory"
        fi
    fi
}

man2pdf() {
    if [[ -z $1 ]]; then
        echo "USAGE: man2pdf [manpage]"
    else
        if [[ `find /usr/share/man -name $1\* | wc -l` -gt 0 ]]; then
        out=/tmp/$1.pdf
        if [[ ! -e $out ]]; then
            man -t $1 | ps2pdf - > $out
        fi
        if [[ -e $out ]]; then
            /usr/bin/evince $out
        fi
    else
        echo "ERROR: manpage \"$1\" not found."
    fi
    fi
}

ex () {
  if [ -f $1 ] ; then
      case $1 in
          *.tar.bz2)   tar xvjf $1    ;;
          *.tar.gz)    tar xvzf $1    ;;
          *.bz2)       bunzip2 $1     ;;
          *.rar)       unrar x $1     ;;
          *.gz)        gunzip $1      ;;
          *.tar)       tar xvf $1     ;;
          *.tbz2)      tar xvjf $1    ;;
          *.tgz)       tar xvzf $1    ;;
          *.zip)       unzip $1       ;;
          *.Z)         uncompress $1  ;;
          *.7z)        7z x $1        ;;
          *.exe)       cabextract $1  ;;
          *)           echo "'$1': unrecognized file compression" ;;
      esac
  else
      echo "'$1' is not a valid file"
  fi
}

ljoin() {
    local OLDIFS=$IFS
    IFS=${1:?"Missing separator"}; shift
    echo "$*"
    IFS=$OLDIFS
}

scr () {
    screen -ls | grep -q Main && screen -xr Main || screen -S Main
}

t () {
    if [[ `tmux -L Main ls | grep windows` ]]; then
        tmux -L Main a
    else
        tmux -L Main
    fi
}

miso () {
    [[ ! -f "$1" ]] && { echo "Provide a valid iso file"; return 1; }
    mountpoint="/media/${1//.iso}"
    sudo mkdir -p "$mountpoint"
    sudo mount -o loop "$1" "$mountpoint"

}

umiso () {
    mountpoint="/media/${1//.iso}"
    [[ ! -d "$mountpoint" ]] && { echo "Not a valid mount point"; return 1; }
    sudo umount "$mountpoint"
    sudo rm -ir "$mountpoint"

}
```

---

