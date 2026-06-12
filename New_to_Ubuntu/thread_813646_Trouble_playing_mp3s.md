---
title: "Trouble playing mp3s"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by jacatone on 2008-05-31
Can't seem to get Ubuntu 7.10 to play my mp3s. I installed every codec I could find. Finally tried a command line player and got the following results:

jacatone@eMax:~/Desktop$ mpg321 apollo to rescue.mp3
Link points to "/tmp/ksocket-jacatone"
can't create mcop directory

Anyone know what this means? Thanks.

---

### Post by SunnyRabbiera on 2008-05-31
hmm, you tried the restricted extras packages?
medibuntu?
are you using the 64bit kernel?

---

### Post by quelx on 2008-05-31
Guessing sound in general works...

your command line needs escaped spaces

```
mpg321 apollo\ to\ rescue.mp3
```

try installing **mplayer** (it will pull in all kinds of codecs)

then ```
mplayer apollo\ to\ rescue.mp3
```

also if you just type *apoll* and then hit the **TAB** key, bash (the terminal app) will complete the filename with the escaped spaces.

---

### Post by jacatone on 2008-05-31
Still get the same error message. The terminal installed "mplayer-nogui" whatever that is. Said it removed mplayer to install this. Still couldn't get it to launch, though. Didn't have this problem with Kubuntu. Everything played right from the get go.

---

### Post by cariboo on 2008-05-31
Linux doesn't like spaces in file names, it thinks that
"apollo to rescue.mp3" are three separate files. To fix the problem use the following script in your mp3 directory:

```
for i in *.mp3; do mv "$i" `echo $i | tr ' ' '_'`; done 
```

What I usually doe is create a script and copy it to /usr/local/bin so that it can be accessed in any directory.

Heres the script:

```
#! /bin/sh
# file name no_space
for i in *.mp3; do mv "$i" `echo $i | tr ' ' '_'`; done 
```

you can do this in gedit, save it as no_space

The next step is to make it executable, in a terminal type:

```
chmod +x no_space
```

Next move it to /usr/local/bin

```
sudo mv no_space /usr/local/bin
```

now you're ready to use the script, just open a terminal and cd into your music directory then type:

```
no_space *mp3
```

It will automagically remove the space in all your mp3 file names.

Good luck

Jim

---

