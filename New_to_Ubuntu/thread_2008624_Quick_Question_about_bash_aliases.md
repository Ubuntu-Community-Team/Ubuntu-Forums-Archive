---
title: "Quick Question about bash aliases"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by ironskillet on 2012-06-23
Hey all, 

I have a lot of music files in a directory on an external HD. I tried to create an alias for the directory path to save myself some time. 

In my .bashrc file I added the following:

if [ -d /media/path_to_directory ]; then
     alias gmusic='/media/path_to_directory'
fi

My goal was to be able to use this alias to do the following (or something similar):

cd gmusic
----OR----
vlc gmusic/artist_name/song_name

but it doesn't seem to work. When I type 'gmusic' into the terminal it says: 

/media/path_to_directory is a directory 

but if I type something like 'cd gmusic', it says:

bash: cd: gmusic: no such file or directory

Is this something that I should be able to do? Or does bash not let you use aliases in this way? I would appreciate any help. 

Thanks a million in advance

---

### Post by bab1 on 2012-06-23
> **ironskillet said:**
> Hey all, 

I have a lot of music files in a directory on an external HD. I tried to create an alias for the directory path to save myself some time. 
A good idea. ^^^> 

In my .bashrc file I added the following:

if [ -d /media/path_to_directory ]; then
     alias gmusic='/media/path_to_directory'
fi
Not so good an idea. ^^^  For neatness sake it's better to put all aliases in a .bash_aliases file.  There is a stanza just for this already in .bashrc```
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

```
In the .bash_aliases file the syntax is ```

alias gmuisic='some_command"
```> 

cd gmusic
----OR----
vlc gmusic/artist_name/song_name

but it doesn't seem to work. When I type 'gmusic' into the terminal it says: 

/media/path_to_directory is a directory 

but if I type something like 'cd gmusic', it says:

bash: cd: gmusic: no such file or directory

Is this something that I should be able to do? Or does bash not let you use aliases in this way? I would appreciate any help. 

Thanks a million in advance
The problem in the end is you have not used a bash command in your alias.  Think of it as a verb (i.e. do this or go there).  if you wanted to do something like change to the /media/music then the alias would be like this in the .bash_aliases file```
alias gmusic='**[COLOR="Red"]cd[/COLOR]** /media/music'
```

The **[COLOR="Red"]cd[/COLOR]** in the above alias is the command and the destination is /media/music.  It says: change directory to /media/music and you have aliased that to gmusic.

Does that help?

---

### Post by HiImTye on 2012-06-23
you have a good intent but the wrong execution. where you put your aliases is generally only important if you 'upgrade' from one version to another (as you might have your .bashrc overwritten). my .bashrc is actually just a soft link to a file on another mount point. regardless..

an alias works like this, I'll show you one of mine so you can see:
```
alias tracksearch="mpc playlist -f '%position%. %artist%: %album% -  %title%' | grep -iE"
```
what this does is the following:
output mpc's current playlist (and then format it):
```
mpc playlist -f '%position%. %artist%: %album% -  %title%'
```
search the output for a string (ignoring the case and using extended regex):
```
grep -iE
```
note how the string is not provided. that is what we put *after* the alias. if I want to search for a song, say *Sage Francis - Sea Lion*, I would do something like this:
```
tye@T:~$ tracksearch 'sage francis.*sea lion'
6370. Sage Francis: A Healthy Distrust -  Sea Lion
```
and now I can do:
```
mpc play 6370
```
and it will play the song. the reason Im showing you all of this is because it shows you how an alias works. when I use the alias
```
tracksearch 'sage francis.*sea lion'
```
it expands the alias in place so that the command I'm issuing is this:
```
mpc playlist -f '%position%. %artist%: %album% -  %title%' | grep -iE 'sage francis.*sea lion'
```
notice how the extra arguments I provide go *at the end* of the alias, not before it, so I couldn't, for instance, put my input in the middle of the alias or before the alias. if you want to store information to call later on, you can use an environment variable, that is, the exact same only without the *alias* command. something like:
```
gmusic='/storage/Music'
```
and then you call it with a dollar sign and the name, like so:
```
cd $gmusic
```

---

### Post by ironskillet on 2012-07-25
Thanks guys! It all makes sense now.

I apologize for the late reply..... I used your advice a few weeks ago and got things working. In my excitement, I forgot to reply.

---

### Post by bab1 on 2012-07-25
> **ironskillet said:**
> Thanks guys! It all makes sense now.

I apologize for the late reply..... I used your advice a few weeks ago and got things working. In my excitement, I forgot to reply.

How about marking it solved now.  ;-)

---

