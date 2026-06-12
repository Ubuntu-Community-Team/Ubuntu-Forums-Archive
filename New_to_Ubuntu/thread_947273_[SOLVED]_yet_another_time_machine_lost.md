---
title: "[SOLVED] yet another time machine lost"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by telltommy on 2008-10-14
I downloaded the program using synaptic manager and now i can't find the program? it's not listed anywhere? is there something i should run in terminal to bring up the program. I typed yatm and response was
tom@tom-desktop:~$ yatm
No input file specified, aborting...
tom@tom-desktop:~$ 

thanks, tom

---

### Post by drowner on 2008-10-14
I've not used the program, but it sounds like it wants you to tell it what file to use, so probably something like

```
yatm examplefile.mp3
```

Have you tried typing

```
man yatm
```

That should give you some information on how to use it.

---

### Post by telltommy on 2008-10-14
YATM(1)                                                                YATM(1)

NAME
       yatm - Yet Another Time Machine

SYNOPSIS
       yatm [options] file

DESCRIPTION
       yatm  plays  Vorbis, Speex and MPEG audio files while allowing the user
       to choose a new tempo without changing the pitch.

       The tempo can be interactively  controlled  by  pressing  ’+’  or  ’-’,
       incrementing  and  decrementing the playback tempo by 1 percent respec&#8208;
       tively.  Use "q" to stop playback.

OPTIONS
       yatm accepts the following options:

       -b     Begin playing at time, given as an offset from the beginning  of
              the file (0:00:00).

       -e     Stop after duration seconds of audio have been decoded.
 Manual page yatm(1) line 1

YATM(1)                                                                YATM(1)

NAME
       yatm - Yet Another Time Machine

SYNOPSIS
       yatm [options] file

DESCRIPTION
       yatm  plays  Vorbis, Speex and MPEG audio files while allowing the user
       to choose a new tempo without changing the pitch.

       The tempo can be interactively  controlled  by  pressing  ’+’  or  ’-’,
       incrementing  and  decrementing the playback tempo by 1 percent respec&#8208;
       tively.  Use "q" to stop playback.

OPTIONS
       yatm accepts the following options:

       -b     Begin playing at time, given as an offset from the beginning  of
              the file (0:00:00).

       -e     Stop after duration seconds of audio have been decoded.
 Manual page yatm(1) line 1

YATM(1)                                                                YATM(1)

NAME
       yatm - Yet Another Time Machine

SYNOPSIS
       yatm [options] file

DESCRIPTION
       yatm  plays  Vorbis, Speex and MPEG audio files while allowing the user
       to choose a new tempo without changing the pitch.

       The tempo can be interactively  controlled  by  pressing  ’+’  or  ’-’,
       incrementing  and  decrementing the playback tempo by 1 percent respec&#8208;
       tively.  Use "q" to stop playback.

OPTIONS
       yatm accepts the following options:

       -b     Begin playing at time, given as an offset from the beginning  of
              the file (0:00:00).

       -e     Stop after duration seconds of audio have been decoded.
 Manual page yatm(1) line 1

that's it but i still cant find the program

---

### Post by nothingspecial on 2008-10-14
> **drowner said:**
> I've not used the program, but it sounds like it wants you to tell it what file to use, so probably something like

```
yatm examplefile.mp3
```

Have you tried typing

```
man yatm
```

That should give you some information on how to use it.

In that case this advice looks good.

---

### Post by drowner on 2008-10-14
The instructions for use are all there ;)

You need to open it going to the directory where the file is (using cd), then typing

```
yatm [filename]
```

Or, if you don't want to move to the directory where the file is, you could do:

```
yatm /path/to/filename/filename.mp3
```

An example, for the user called 'drowner', wanting to play a random file called random_file.mp3, which he kept in a folder called 'Music' would be:

```
yatm /home/drowner/Music/random_file.mp3
```

---

### Post by drowner on 2008-10-14
The program is there, it's all installed - there may be no Graphical interface though - is that what the problem is? It may just run from terminal.

I don't know anything about this program though, but you DO have it installed!

---

### Post by telltommy on 2008-10-15
thanks, i didn't realize it must be run in terminal.

---

