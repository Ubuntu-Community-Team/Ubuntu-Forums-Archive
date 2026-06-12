---
title: "Problems with pianobarfly - pianobar works"
date: 2010-12-15
forum: Packaging and Compiling Programs
---

### Post by BoredOutOfMyMind on 2010-12-15
I have tried installing deb, tar.gz and from synaptic. 

```
:~$ pianobarfly
Welcome to pianobarfly!
[?] Username: boredoomm
[?] Password: 
(i) Login... Error: Protocol incompatible. Please upgrade libpiano.
```

Where and how do I install libpiano to then run CLI from ~/Music/Pianobar/ ?

:)

---

### Post by File_ on 2010-12-15
Here I found something about installing pianobarfly: [http://linuxbasement.com/content/lb-episode-57-self-barfly-linux-basement](http://linuxbasement.com/content/lb-episode-57-self-barfly-linux-basement) ```
Reviews/Discussion Linux command line Pandora client that saves Pandora streams to mp3. Based off of pianobar. Automatically organizes files in the directory you run it from.
Pianobar: http://6xq.net/html/00/17.html Ubuntu install instructions:
    wget http://va2600.net/projects/fie/pianobarfly/
    tar -xzf pianobarfly.tgz
    cd pianobarfly
    sudo apt-get install cmake libmad0-dev libao-devin libpiano/src/piano.c, change PIANO_PROTOCOL_VERSION "26" to PIANO_PROTOCOL_VERSION "27" and recompile.cmake .
    sudo make
    sudo make install
```

---

### Post by BoredOutOfMyMind on 2010-12-16
> **File_ said:**
> Here I found something about installing pianobarfly: [http://linuxbasement.com/content/lb-episode-57-self-barfly-linux-basement](http://linuxbasement.com/content/lb-episode-57-self-barfly-linux-basement) 

Thanks for the link. Line #2 should read-
```
wget http://va2600.net/projects/fie/pianobarfly/pianobarfly.tgz
```

This did not work. 

I did remove with Admin Nautlius the entire pianofly files and reinstalled. 

It still complains it wants to update libpiano. 

cd ~/pianobarfly/libpiano
make .
sudo make
sudo make install 

No success...:popcorn:

---

### Post by silverfunk on 2011-02-16
Hey, a new version was uploaded.  It seems to be working for me.

---

### Post by dfacto on 2011-03-10
New version worked for me.  I was able to compile by:
```

wget [http://va2600.net/projects/fie/pianobarfly/pianobarfly-2011.01.24.tar.bz2](http://va2600.net/projects/fie/pianobarfly/pianobarfly-2011.01.24.tar.bz2)
tar xjvf pianobarfly-2011.01.24.tar.bz2
sudo aptitude install libao-dev libfaad-dev libmad0-dev libtagc0-dev
cd pianobarfly-2011.01.24
make

```

And to use MP3 and keep a longer history,
```

mkdir -p ~/.config/pianobar
cat<<EOF >~/.config/pianobar/config 
audio_format = mp3
history = 20
EOF

```

---

### Post by silverfunk on 2011-03-15
Actually pianobarfly is using a different config file from pianobar (~/.config/pianobarfly/config).

---

### Post by idumych on 2011-05-27
> **dfacto said:**
> New version worked for me.  I was able to compile by:
```

wget [http://va2600.net/projects/fie/pianobarfly/pianobarfly-2011.01.24.tar.bz2](http://va2600.net/projects/fie/pianobarfly/pianobarfly-2011.01.24.tar.bz2)
tar xjvf pianobarfly-2011.01.24.tar.bz2
sudo aptitude install libao-dev libfaad-dev libmad0-dev libtagc0-dev
cd pianobarfly-2011.01.24
make

```

And to use MP3 and keep a longer history,
```

mkdir -p ~/.config/pianobar
cat<<EOF >~/.config/pianobar/config 
audio_format = mp3
history = 20
EOF

```

Followed your steps exactly, but I get this every time

```
cc -std=c99 -O2 -DNDEBUG -I src/libpiano -I src/libwaitress \
			-I src/libezxml -I /usr/include -I /usr/include -DENABLE_FAAD \
			-I /usr/include -DENABLE_MAD -I /usr/include -DENABLE_TAG -c -o src/ui_readline.o src/ui_readline.c
cc -std=c99 -O2 -DNDEBUG -I src/libpiano -I src/libwaitress \
			-I src/libezxml -I /usr/include -I /usr/include -DENABLE_FAAD \
			-I /usr/include -DENABLE_MAD -I /usr/include -DENABLE_TAG -c -o src/fly.o src/fly.c
src/fly.c:38:26: fatal error: taglib/tag_c.h: No such file or directory
compilation terminated.
make: *** [src/fly.o] Error 1

```

---

### Post by dfacto on 2011-07-26
Since my post pandora made some changes and pianobar was updated.  Merge in the relevant files from pianobar into pianobarfly and recompile.  Sorry I cannot give you more details than this as it was a long time ago.  Trust me though--pianobarfly works and it is awesome.

---

