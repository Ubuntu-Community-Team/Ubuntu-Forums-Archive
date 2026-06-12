---
title: "Configuring MPD (music player daemon) ubuntu 12.04"
date: 2013-01-21
forum: New to Ubuntu
---

### Post by buzzkillington on 2013-01-21
Hello i'm trying to configure MPD following this guide 

[http://crunchbanglinux.org/wiki/howto/mpd](http://crunchbanglinux.org/wiki/howto/mpd)

i run into problems at this step 

 Copy the configuration file to our home folder:  
   gunzip -c /usr/share/doc/mpd/examples/mpd.conf.gz > ~/.mpd/mpd.conf


i get an error 


[EMAIL="dylan@dylan-K53SD:/home/.mpd"]dylan@dylan-K53SD:/home/.mpd[/EMAIL]$ sudo gunzip -c /usr/share/doc/mpd/examples/mpd.conf.gz > ~/.mpd/mpd.conf

bash: /home/dylan/.mpd/mpd.conf: Permission denied


Any ideas?
i'm running ubuntu 12.04, and i was using sudo so i should be root


i'm new to ubuntu and not 100% confident about terminal commands, i'm unsure if i'm following the instructions correctly.  



Also if any one can clarify when i use this command

mkdir -p ~/.mpd/playlists


and i then look in my home directory with ls i don't see the .mpd directory but when i try to move into it with cd it is there.  Can someone explain why this is?

---

### Post by Bashing-om on 2013-01-22
buzzkillington; Hi !

One should not need admin authority to copy a file to one's home directory. The dependent thing may be the file permissions on the file to be copied.

As to why the ls command does not list the .mpd file // the "."(dot) at the beginning of the file name designates the file as "hidden" -out of sight out of mind- //(everything in linux is a "file")
to see these "hidden" files pass the option a (all)with the ls command, better yet with the option l (long format) also ...as in:
```
ls -la /home/dylan/.mpd/playlist
```long for:
```
 ~/.mpd/playlists
```Nautilus file manager to "Show hidden files" ctl-h; ctl-h again to hide them.
[INDENT][INDENT]just ry'n to help
[/INDENT][/INDENT]

---

