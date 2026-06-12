---
title: "Torc - the MythTV Fork - Where to install?"
date: 2013-04-28
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2013-04-28
From GitHub, I found a MythTV fork called ["Torc"]("https://github.com/Torc"). It comes in .zip format. I have tried to understand where to and how to install this package, but there is nothing on the 'net or at github about that. Including the various Docs & Readme-s at the github page about Torc.

SO, if someone can suggest a directory for this, it would oblige me.

---

### Post by schragge on 2013-04-28
Well, since it's a MythTV fork, so I guess [the MythTV installation procedure]("http://www.mythtv.org/wiki/Ubuntu_Raring_Ringtail_Installation") applies here as well. Try
```

sudo apt-get install git build-essential qt4-dev-tools yasm uuid-dev lib{freetype6,mp3lame,xinerama}-dev
git clone git://github.com/Torc/torc.git
cd torc
git pull
./configure
make
sudo make install

```

---

### Post by Mark_in_Hollywood on 2013-04-28
As I am so 'puter ILLITERATE I'm posting these results. I have no clue as to whether I have done something wrong, whether my installed apps and associated dependencies have prevented or harmed the 'torc' install or whether the github has a failure or the internet is bad. 

None the less, if the instructions in the above post are to create a directory:

/torc

they have failed to do so.

mark@Lexington-19:~$ git clone git://github.com/Torc/torc.git
Cloning into 'torc'...
remote: Counting objects: 8002, done.
remote: Compressing objects: 100% (3530/3530), done.
remote: Total 8002 (delta 4742), reused 7594 (delta 4334)
Receiving objects: 100% (8002/8002), 12.32 MiB | 626 KiB/s, done.
Resolving deltas: 100% (4742/4742), done.
mark@Lexington-19:~$ cd /torc
bash: cd: /torc: No such file or directory

---

### Post by schragge on 2013-04-28
```
cd [color=red]/[/color]torc
``` should be ```
cd torc
```

---

### Post by Mark_in_Hollywood on 2013-04-28
That got it much closer. After the terminal printed out 5 minutes of compile and associated stuff, it balked at -- from somewhere in the "make" command

make[2]: Leaving directory `/home/mark/torc/libs/libtorc-media'
cd libtorc-baseui/ && /usr/bin/qmake /home/mark/torc/libs/libtorc-baseui/libtorc-baseui.pro QMAKE=qmake -o Makefile
Project ERROR: No valid display class. Aborting
make[1]: *** [libtorc-baseui//Makefile] Error 2
make[1]: Leaving directory `/home/mark/torc/libs'
make: *** [libs] Error 2

---

### Post by Mark_in_Hollywood on 2013-04-30
The "make" failed. Where are the countless files now installed on my harddrive and how do I remove them? I tried sudo aptitude remove torc, but aptitude said it was not installed.

---

