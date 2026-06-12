---
title: "I need help installing Byond"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by kulote on 2008-07-09
HI... i wanna install the byond client in ubuntu, in the download section they have a version for linux , the thing is that i dont know how to install it =( 

Please help me =D [www.byond.com](www.byond.com) =D

When i download a bunch of files appears and i dont know how to run Byond so plz im begging for explications of how to use it ....

---

### Post by tjwoosta on 2008-07-09
well..

i dont know anything about byond

but i do know that that installer says its for the linux 2.4+

our current kernal is 2.6.24  (so the installer might be to old to compile properly)


but anyway to compile, just read the readme file that comes with


by the looks of it just do this

```
cd /wherever/the/file/is
```

then

```
make
```

then

```
sudo make install
```

---

### Post by kulote on 2008-07-09
well the file is the desktop plz send the code for this @_@ im very silly with this things .... the readme file is Japanese for me... I DONT GET ANYTHING =(...

The file is in my desktop so plz send the code for this =D

---

### Post by kulote on 2008-07-09
OMG i have been reading the readme file and its not easy for me ..... im having trouble with this and its because im new using ubuntu and its very difficult for me..

So please explain me in CHILDREN language so i can understand what to do...

The ubuntu system is very nice but hard to use ...

Please help me again

---

### Post by cariboo on 2008-07-09
The readme is as about as simple as it is going to get. Open up a System-->Administration-->Terminal and just follow the instructions in the readme.txt

I would suggest creating a directory in your home directory and extracting the files into that directory, Otherwise you will have the application files all over your desktop.

Jim

---

### Post by tjwoosta on 2008-07-09
> well the file is the desktop plz send the code for this @_@ im very silly with this thing

so do this

first move the .zip into you home directory   (Places-Home)

then 

right click the .zip and choose extract here

then open a terminal and

```
cd ~/byond
```

then

```
make
```

then

```
sudo make install
```


> the readme file is Japanese for me... I DONT GET ANYTHING =(...

? why is it japaneese?

i just downloaded a copy and mine is english

> The ubuntu system is very nice but hard to use ..

its not really that hard to use, it just requires that you actually know what things are doing when you input commands

---

### Post by chris062689 on 2008-07-09
It's quite easy to install BYOND!
I was kind of supprised to see someone like you here :)

I believe all you do is 'cd' into the directory and type "make here"
then "make install"; not positive on that though.
But remember, it doesn't have any form of a GUI; only terminal based.

And WINE support is quite broken right now.  Your best bet would be to run it through a VM.
[http://members.byond.com/linuxguild](http://members.byond.com/linuxguild)

---

### Post by kulote on 2008-07-09
omg i dont know yet what to do!!! here is what my terminal says when i use the codes :

daniel@daniel-desktop:~$ cd ~/byond
bash: cd: /home/daniel/byond: No such file or directory
daniel@daniel-desktop:~$ cd ~/byond
daniel@daniel-desktop:~/byond$ make
make: *** No targets specified and no makefile found.  Stop.
daniel@daniel-desktop:~/byond$ sudo make install
[sudo] password for daniel: 
make: *** No rule to make target `install'.  Stop.
daniel@daniel-desktop:~/byond$ sudo make -i
make: *** No targets specified and no makefile found.  Stop.
daniel@daniel-desktop:~/byond$ sudo make install
make: *** No rule to make target `install'.  Stop.
daniel@daniel-desktop:~/byond$ make install
make: *** No rule to make target `install'.  Stop.

what im suppose to do? whats the mistake ?
 @_@

---

### Post by kulote on 2008-07-09
anyways when im in the byond web page FireFox says it doesnt recognize the file game ..... how i run the games ?

---

### Post by chris062689 on 2008-07-09
I already TOLD you, BYOND for LINUX does not have a GUI!
If you want to run BYOND; your going to have to use a Virtual Machine; look at VirtualBox and put XP on that.

---

