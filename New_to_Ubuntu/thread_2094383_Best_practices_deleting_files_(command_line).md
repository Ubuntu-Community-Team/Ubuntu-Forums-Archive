---
title: "Best practices: deleting files (command line)"
date: 2012-12-13
forum: New to Ubuntu
---

### Post by Lalaith on 2012-12-13
[FONT=Arial, sans-serif][SIZE=2]Hi all, 
  
 at work I am working connected to a linux server (I guess it's a  server). I launch a Konsole and from there I can access my files,  execute programs, launch applications, etc. Everytime I want to remove a  file and I type
 [/SIZE][/FONT]```
rm my_useless_file
```[FONT=Arial, sans-serif][SIZE=2] I get a message:
 [/SIZE][/FONT][HTML]"are you sure you want to delete the regular file my_useless_file"?[/HTML][FONT=Arial, sans-serif][SIZE=2] As if I was actually typing 
 [/SIZE][/FONT]```
rm &#8211;i my_useless_file.
```[FONT=Arial, sans-serif][SIZE=2] 
How could I apply also such a change at my home computer? I would like to  implement something similar[SIZE=2], so that when I forgot the -i option is still asking me :)
[/SIZE]
 
 And [SIZE=2]also,[/SIZE] when you want to [SIZE=2]remove[/SIZE] a file, what do you  do? Do you have some sort of &#8220;protection&#8221; to avoid you from doing stupid  things if you were not careful enough?
 
 many thanks!
[/SIZE][/FONT]

---

### Post by lykwydchykyn on 2012-12-13
Simplest way would be to add an alias to either your .bashrc or /etc/bash.bashrc.

Like so:
```

alias rm="rm -i"

```

This is generally the preferred way to provide default options for any command.

Note that if you put this in .bashrc, it won't (AFAIK) use this command when you sudo (since you're root at that point), but you may want to test that.

---

### Post by Cheesemill on 2012-12-13
You can set up an alias for the rm command.

Open your ~/.bashrc file for editing and add the following line to the end of the file:
```
alias rm='rm -i'
```
Then re-source your .bashrc
```
. ~/.bashrc
```

Aliases are simply custom commands, now every time you type 'rm' in a terminal the actual command that is being executed is 'rm -i'.

---

### Post by CharlesA on 2012-12-13
I put my custom aliases in ~/.bash_aliases

```
charles@Thor:~$ cat .bash_aliases
alias cputemp="echo CPU temp is "$(sensors | grep Core | cut -f2 -d'+' | cut -f1 -d' ' | awk '{print substr($1,0,3)}' | awk '{ sum+=$1 } END {print sum/NR}')°C""

```

---

### Post by Cheesemill on 2012-12-13
Me too, but I'm not sure if it's worth it for just the one. Also my /root/.bash_aliases is a symlink to /home/rob/.bash_aliases so they stay in sync over both accounts.
```
rob@arch:~$ cat .bash_aliases 
alias sudo='sudo '
alias pacman='pacman-color'
alias update-grub='sudo grub-mkconfig -o /boot/grub/grub.cfg'
alias vi='vim'
alias ipl='get_iplayer --nocopyright'
alias gipl='get_iplayer --nocopyright --output=/home/rob/Videos --tvmode=flashhd,flashvhigh,flashhigh,flashstd,flashnormal --get'
alias hist='history | grep'
alias paci='sudo pacman -S'
alias pacu='sudo pacman -Syyu'
alias pacr='sudo pacman -R'
alias pacs='pacman -Ss'
alias sv='sudo vim'
alias df='df -h -t ext4'
alias du='du -h --max-depth=1 | sort -hr'
alias ls='ls -lh --color=auto'
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias msf='sudo /opt/metasploit/msfconsole'
alias pg='ps -Af | grep $1'
```

---

### Post by CharlesA on 2012-12-13
Nice!

I would tend to agree with you there. It would probably be easier to keep track of just one alias if you throw it into .bash_rc.

BTW, nice one with the dots. ;)

---

### Post by Cheesemill on 2012-12-13
> **CharlesA said:**
> BTW, nice one with the dots. ;)
It's just what a good alias should be, simple, effective and easy to remember.
I think the sudo and hist ones are the most useful though.

---

### Post by CharlesA on 2012-12-13
> **Cheesemill said:**
> It's just what a good alias should be, simple, effective and easy to remember.
I think the sudo and hist ones are the most useful though.
sudo vim is handy. ;)

I didn't see the history one, but that one is pretty cool.

---

