---
title: "&quot;echo&quot; problem/Spotify"
date: 2013-02-07
forum: New to Ubuntu
---

### Post by Satchel88 on 2013-02-07
So I tried to install Spotify for Linux ([http://www.spotify.com/us/download/previews/](http://www.spotify.com/us/download/previews/)) using instructions from around the web and this thread:  [http://ubuntuforums.org/showthread.php?t=2057741&highlight=spotify+linux](http://ubuntuforums.org/showthread.php?t=2057741&highlight=spotify+linux)  


I noticed most everything worked but system got hung up on the "aptitude" command.  And then,
Attempting to install Spotify from the Terminal now gets:

```

E: Type 'echo' is not known on line 61 in source list /etc/apt/sources.list
E: The list of sources could not be read.
E: Unable to locate package spotify-client

```Also there are random error messages, now, since I edited in that "echo" thing.  I think I edited my etc/sources.list to include an echo and I don't know how to get it out.  I tried sudo gedit /etc/apt/sources.list but that brings up a blank text document.  I know this is all really basic stuff...but :confused:


Thanks
Ubuntu 12.04.01
Asus EE PC
Nathan

p.s.
Perhaps this was what did it?  I tried:

```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 94558F59
sudo sh -c 'echo "deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free" >> /etc/apt/sources.list'
sudo apt-get update
sudo apt-get install spotify-client
```

---

### Post by omeomi on 2013-02-08
First of all you should just follow the instructions that are on the Spotify website, those will work fine.

Can you post your /etc/apt/sources.list here? (e.g. the output of 'sudo nano /etc/apt/sources.list') Because it seems you just put something in there that shouldn't be.

---

### Post by schragge on 2013-02-08
It seems, you somehow managed to put 'echo' into */etc/apt/sources.list*. To see the problem, try
```
grep echo /etc/apt/sources.list
```

---

### Post by Satchel88 on 2013-02-08
Yea, I really messed up I think...keep getting weird error messages.

Tried what you said, got this:
```

me@mypc:~$ grep echo /etc/apt/sources.list
[COLOR=Red]echo[/COLOR] "deb http://repository.spotify.com stable non-free" | sudo tee -a /etc/apt/sources.list
[COLOR=Red]echo[/COLOR] "deb http://repository.spotify.com stable non-free" | sudo tee -a /etc/apt/sources.list

```

???

---

### Post by schragge on 2013-02-09
Try to edit */etc/apt/sources.list* manually
```

sudo sensible-editor /etc/apt/sources.list

```and change the two lines starting with *echo* to one line below
```
deb http://repository.spotify.com stable non-free
```

---

### Post by Satchel88 on 2013-02-09
Okay so one of the error messages when I check for updates says this:

> An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'cancel' is not known on line 68 in source list /etc/apt/sources.list'

I did edit out the two echo lines as you instructed, and nothing shows, now, when I tried your initial "grep echo" suggestion.

---

### Post by CharlesA on 2013-02-09
Delete those two lines from sources.list and replace it with this one:

```
deb http://repository.spotify.com stable non-free
```

Then run:

```
sudo apt-get update
sudo apt-get install spotify-client
```

---

### Post by Satchel88 on 2013-02-09
Worked like a charm, thanks!

---

