---
title: "newbie having trouble with ./configure"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by Firewolf06 on 2008-07-02
i have been trying to install tarballs and i get as far a the ./configure part get this error 

:twisted::twisted::twisted::twisted::twisted:ty@FireWolf:~/slideview$ ./configure
bash: ./configure: No such file or directory
be
it was working before i used it with ndiswrapper can anyone explain to what i'm doing wrong?

---

### Post by Jeff250 on 2008-07-02
Bash is telling you that there is no configure script in your current directory.  What are you trying to compile?  Could you post a link to the tarball?  Not everything uses the gnu build system to compile, so there may be different instructions that you need to follow in order to compile and install this.

---

### Post by tjwoosta on 2008-07-02
read and follow the directions provided in the readme file that came with the source (it will tell you what you need to do) 

probably just skip the ./configure part and move on to the ./make part

---

### Post by Jeff250 on 2008-07-02
[quote=tjwoosta]probably just skip the ./configure part and move on to the ./make part[/quote]

Note that to run make, you tell bash **make**, not **./make**, since make is in /usr/bin, not the local directory.  :wink:

---

### Post by ChameleonDave on 2008-07-02
> **Firewolf06 said:**
> i have been trying to install tarballs and i get as far a the ./configure part get this error 

:twisted::twisted::twisted::twisted::twisted:ty@FireWolf:~/slideview$ ./configure
bash: ./configure: No such file or directory
be
it was working before i used it with ndiswrapper can anyone explain to what i'm doing wrong?

Well, if it's telling you there is no such file, the chances are that there is no such file.  Type "ls" to list the files in the current directory.  Read any README files in there.

---

### Post by tjwoosta on 2008-07-02
> Note that to run make, you tell bash make, not ./make, since make is in /usr/bin, not the local directory. 

lol.. oops

---

### Post by msidhard on 2008-07-02
HEY USE THis cd the directory then type sudo apt-get install build-essential and then ./configure

---

### Post by tjwoosta on 2008-07-02
> HEY USE THis cd the directory then type sudo apt-get install build-essential

ha nice catch i didnt even think to mention build-essential, but yes it is required to compile

---

### Post by aquavitae on 2008-07-02
> **tjwoosta said:**
> ha nice catch i didnt even think to mention build-essential, but yes it is required to compileBut not to configure. If ./configure doesn't work then it probably uses a different method of building.  I'll repeat Jeff's suggestion: post a link to the tarball you're trying to compile so we can see how it works.

---

### Post by rxtx on 2008-07-02
As above. Check the dir you extracted to for a configure script. If one doesn't exist, exaimine the README for info on install.

Possbily doesn't require ./configure, just;

```
make
sudo make install
```

It'd help a great deal if you told us the tarball you're trying to install :)

---

### Post by Firewolf06 on 2008-07-02
here is the link to down load the tar [http://sourceforge.net/projects/slideviewer/](http://sourceforge.net/projects/slideviewer/)

---

### Post by Xerp on 2008-07-02
Yup, it only has three files (the program, the source and a makefile) - no configure script. Just run make if you want to recompile it.

Simply run the program if not.

[http://slideviewer.sourceforge.net/](http://slideviewer.sourceforge.net/)

---

### Post by Firewolf06 on 2008-07-03
Thank you for all who helped i got it running

---

### Post by jsmnuk on 2010-02-05
> **Firewolf06 said:**
> i have been trying to install tarballs and i get as far a the ./configure part get this error 

:twisted::twisted::twisted::twisted::twisted:ty@FireWolf:~/slideview$ ./configure
bash: ./configure: No such file or directory
be
it was working before i used it with ndiswrapper can anyone explain to what i'm doing wrong?

I'm a newbie too, and one thing I discovered was: if you extract the tarball in Archive manager (or the Desktop if you want to copy the file there) rather than the command line, then find the "configure" file (not the folder, although the file may be in the "configure" folder), and double-click the file, in the end you will see a config.log in the files. **If you open that, the actual "invocation" (configure command) will appear at the top of the file script**. Not that you'd need it --- you personally already got it going, and the tarball is already configured --- but  the log file is worth saving just for the proper command should you want to re-install the program from the terminal.:popcorn:

---

