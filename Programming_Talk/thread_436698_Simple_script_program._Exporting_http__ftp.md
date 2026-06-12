---
title: "Simple script program. Exporting http / ftp"
date: 2007-05-08
forum: Programming Talk
---

### Post by Peter Sommer-Larsen on 2007-05-08
Hi.!

I would like to program a script that puts the following into my xterm:

--------------------------------------------------------------------------------------
export http_proxy="http://wwwproxy.physics.aau.dk:3128"
export ftp_proxy="http://wwwproxy.physics.aau.dk:3128"
--------------------------------------------------------------------------------------

every time I have to use the network in my xterm's I have to write this.. their must be a easyer
way. I tried to make a *.sh script:

--------------------------------------------------------------------------------------
!#/bin/sh
export http_proxy="http://wwwproxy.physics.aau.dk:3128"
export ftp_proxy="http://wwwproxy.physics.aau.dk:3128"
echo "Now your network is ready to go"
--------------------------------------------------------------------------------------

and then I made a chmod on it, but to be honest I dont know anything about programming
scripts in Linux. I also tried the "Call system" command in Fortran but that didnt work either.

Any suggestions ? 

Chill.
Sommer

---

### Post by jfinkels on 2007-05-08
> **Peter Sommer-Larsen said:**
> Hi.!

I would like to program a script that puts the following into my xterm:

--------------------------------------------------------------------------------------
export http_proxy="http://wwwproxy.physics.aau.dk:3128"
export ftp_proxy="http://wwwproxy.physics.aau.dk:3128"
--------------------------------------------------------------------------------------

every time I have to use the network in my xterm's I have to write this.. their must be a easyer
way. I tried to make a *.sh script:

--------------------------------------------------------------------------------------
!#/bin/sh
export http_proxy="http://wwwproxy.physics.aau.dk:3128"
export ftp_proxy="http://wwwproxy.physics.aau.dk:3128"
echo "Now your network is ready to go"
--------------------------------------------------------------------------------------

and then I made a chmod on it, but to be honest I dont know anything about programming
scripts in Linux. I also tried the "Call system" command in Fortran but that didnt work either.

Any suggestions ? 

Chill.
Sommer

If you want to add environment variables to be loaded everytime you log in, try adding lines to your  ~/.profile file:
```

HTTP_PROXY="http://wwwproxy.physics.aau.dk:3128"
export HTTP_PROXY
FTP_PROXY="http://wwwproxy.physics.aau.dk:3128"
export FTP_PROXY

```

---

### Post by Peter Sommer-Larsen on 2007-05-09
The problem is just, that I use my computer allot of different places, so it would
be nice to make some scripts..

---

### Post by cwaldbieser on 2007-05-09
> **Peter Sommer-Larsen said:**
> The problem is just, that I use my computer allot of different places, so it would
be nice to make some scripts..
Your script actually works-- just not how you intended.
```

$ ./yourscript.sh

```
When you run your script, it starts a subshell and exports the value of those variables so any child processes will inherit them.  Then the subshell exits and you are back in your interactive shell, which was totally unaffected.

```

$ source yourscript.sh

```
The source command will cause the current interactive shell to read yourscript.sh and execute it without spawning a subshell.  Now if you echo the variables, they should be the correct values.

You can also abbreviate the "source" command:
```

$ . yourscript.sh

```

---

### Post by ssam on 2007-05-09
the problem might be that you have
```

!#/bin/sh

```
instead of
```

#!/bin/sh

```

you can remember it as shebang (# is ha**sh** and ! is a bang). or remember that # starts a comment line, and this is a special comment to tell linux which interpreter to use.

you may also do better using bash rather and sh.

traditionally sh is a alias for bash on linux, but in ubuntu and debain sh means dash, which is a more minimal shell (this is to make boots faster if the full features of bash are not needed)

---

### Post by Peter Sommer-Larsen on 2007-05-10
Thanks alot.. now It works.
I just had to run it like this:

# . myscript.sh
I didnt know the thing wit the subshell's. Maybe I should have know.. :(
and oops, of cause it is "#!", I typed a bit too fast. 

I have a last question. How can I (if it is possible) make my script global, so I can
execute it from what ever folder I am in. Normally I just put the files into /bin, but
I dont know how to do this when its a script. And oh'.! Does some of you guys know
a good homepage with Linux script programming. I googled' it, but i didnt find something
good, only bad described basics.

---

### Post by jfinkels on 2007-05-10
> **Peter Sommer-Larsen said:**
> Thanks alot.. now It works.
I just had to run it like this:

# . myscript.sh
I didnt know the thing wit the subshell's. Maybe I should have know.. :(
and oops, of cause it is "#!", I typed a bit too fast. 

I have a last question. How can I (if it is possible) make my script global, so I can
execute it from what ever folder I am in. Normally I just put the files into /bin, but
I dont know how to do this when its a script. And oh'.! Does some of you guys know
a good homepage with Linux script programming. I googled' it, but i didnt find something
good, only bad described basics.

If your script is named "myscript", just put in /usr/bin (or /bin if you want), then type "myscript" from any directory and it will run "myscript".

You might want to rename your "myscript.sh" to something without the ".sh" ending just so that it's easier to type.

---

