---
title: "Aliases disappear and other problems"
date: 2012-11-19
forum: New to Ubuntu
---

### Post by Lutrine on 2012-11-19
Hi,
I have a number of problems with ubuntu server 12.10. Hopefully someone can help me out.
1. I made a number of aliases (alias start.minecraft='java...) they all worked well, but when I shut the computer down overnight and switched it back on later all the aliases failed to work. I got the message command not found, or words to the effect. Similarly when I set the aliases as root they were forgotten when I went back to normal user. Also when I went back to root they had gone from there.

2. Possibly the wrong forum, but I'll give it a go. I use no-ip.org to keep track of my ip. I've downloaded the software, but it doesn't update the ip-address. Ever. The software runs fine, but nothing happens.

I hope someone can help me out.

---

### Post by nothingspecial on 2012-11-19
Aliases defined in a shell only survive until it is terminated. You need to add them to ~/.bashrc or ~/.bash_aliases

---

### Post by nothingspecial on 2012-11-19
Further to the previous answer

You create a file in your home folder called .bash_aliases and put them in there.

For example, here is a small portion of one of my .bash_aliases file

```

#Cd ripping/playing
alias cd2flac='abcde -c ~/.abcde_flac.conf'
alias cd2ogg='abcde -c ~/.abcde_ogg.conf'
alias cd2mp3='abcde -c ~/.abcde_mp3.conf'
alias cdp='mplayer cdda://'
alias vinyl='ffmpeg -f alsa -i hw:0,0 -acodec pcm_s16le'

#updating
alias upd='sudo apt-get update'
alias upg='sudo apt-get upgrade'
alias dupg='sudo apt-get dist-upgrade'
alias inst="sudo apt-get install"

alias tran='transmission-cli -b -D -er -u 5 -w ./'
alias here="PS1='${debian_chroot:+($debian_chroot)}\W\ $ '"
alias twit='twidge lsrecent -su'
alias punk='mplayer -really-quiet http://65.60.32.242:8600 < /dev/null &'
alias ran='mplayer -quiet -shuffle -playlist <(find ~/Music -type f)'
alias sq='mplayer http://192.168.0.5:9000/stream.mp3'


```

Save it, then when you log back on they will all be available to you. You can use them straight away if you type ```
. ~/.bashrc
``` after you save the file and after you modify it a later point.

---

### Post by papibe on 2012-11-19
EDIT: oops.. slow reply.. as usual.


Hi Lutrine. Welcome to the forums ):P

In order to keep your aliases, save them in a file called ~/.bash_aliases

That is a file called .bash_aliases, locate on your home.

Let us know how it goes.
Regards.

---

