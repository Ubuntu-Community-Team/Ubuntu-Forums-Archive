---
title: "installing tar.gz"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by SpenceMakesSense on 2008-06-04
So Ive been wondering this for awhile and havent gotten much of a straight answer. When I download a program and It gives my a 
.tar.gz, how would I come about installing it?

---

### Post by Joeb454 on 2008-06-04
It depends what's in the extracted folder.

If there is a "configure" or "autoconf" file, then you have to compile it from source.

---

### Post by tamoneya on 2008-06-04
[http://www.psychocats.net/ubuntu/installingsoftware#lastresorts](http://www.psychocats.net/ubuntu/installingsoftware#lastresorts)

---

### Post by django0909 on 2008-06-04
Which would be something like

./configure
make 
make install?

Am I right?

---

### Post by iaculallad on 2008-06-04
Usually you are downloading a compressed file with more files inside of it. You need to uncompress (tar xvfz filename.tar.gz) it so you can compile the files. Usually you do ~/.install commands or make commands to install it.

---

### Post by Joeb454 on 2008-06-04
Yep that's usually what you'd do for compiling, personally I replace "**sudo make install**" with "**sudo checkinstall**"

Anyway **./configure** can take a while, especially if you have to find a load of dependencies :)

---

### Post by soldierdad on 2008-06-07
where and how do you do this?

---

### Post by rampageoberon on 2008-06-07
First you want to extract the files and then run the commands stated above.

```
tar -xzf <your filename>
```

---

### Post by soldierdad on 2008-06-07
what do you use to run the command?

---

### Post by soldierdad on 2008-06-07
okay, so i figured out how to extract and compile a tar.gz file.  i ran sudo make install <filename> and go this error 
" make: *** No rule to make target 'install'.  Stop."
what did i do wrong?

---

### Post by t0p on 2008-06-07
> **soldierdad said:**
> what do you use to run the command?

I'm not sure what you mean... you run the command by typing it into terminal.

This is all very difficult to explain when you don't have any actual details.  The commands depend on what you have downloaded.  We'd need to know what files came in the archive.

---

### Post by soldierdad on 2008-06-07
sorry, i am trying to run/install gyachicam, which i found in a another post on here to get my logitech quick cam to work on gyachi so i can acutually use it.  i have cheese and camorama installed, which they work fine, i just can't do a video chat on gyachi with it.  not yet anyway.

---

### Post by rampageoberon on 2008-06-07
After extracting the files in the directory do

```
./configure
make
sudo make install
```

Its not sudo make install <filename>

---

### Post by soldierdad on 2008-06-07
okay, i am feeling really dumb now.  i have tried those commands, as well as putting the file name and path before the ./configure, and i keep getting the message 
"bash: <command> : no such file or directory"
i have gone and looked at where the file is saved on my computer and the path is correct.  i really don't know what i am doing wrong.

---

### Post by MattBD on 2008-06-07
> **soldierdad said:**
> okay, i am feeling really dumb now.  i have tried those commands, as well as putting the file name and path before the ./configure, and i keep getting the message 
"bash: <command> : no such file or directory"
i have gone and looked at where the file is saved on my computer and the path is correct.  i really don't know what i am doing wrong.

The command ./configure runs the configure shell script. To run it, you have to be in the same directory as that script. Have a look through the directory you unpacked the tar package to and find a script called configure. You'll then need to get the path to that folder and use that at the command line to switch to that folder. For instance, if it was in /home/ubuntu/appname, you'd enter the following:
```
cd /home/ubuntu/appname
```
Once you're in the same directory as the configure script, you should be able to run it fine.

---

### Post by MattBD on 2008-06-07
Oh, and have you installed the tools you need? You definitely need to install the build-essential package, and I would recommend installing checkinstall as well. Both can be gotten via Synaptic. Checkinstall is handy as it turns the compiled software into a deb package, making it easy to remove
You'll also need to read the text files included in the folder you extracted the package to in order to find out what dependencies it has.

---

### Post by Xerp on 2008-06-07
gunzip will unzip a gzip file (.gz)
tar will untar a tar file (.tar)

you can run both together with tar:

tar -zxvf file.tar.gz

The contents can then be used as the author intended.

---

