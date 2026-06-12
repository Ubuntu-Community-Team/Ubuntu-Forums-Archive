---
title: "Help installing a package"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by epic1990 on 2008-10-08
I have downloaded the .tar file, and I am unsure about how to actually go about installing what is inside. Does it need to stay in the zipped file, or is there a file inside that needs to be used?

---

### Post by pytheas22 on 2008-10-08
Generally you should never have to install anything from a .tar file in Ubuntu--you can usually find everything you need pre-compiled and installable in one click from the repositories.  Please let us know what you're trying to install, and we can probably tell you how to install it in a much easier way.

Otherwise, if you provide a link to the .tar.gz file that you have, I'm happy to take a look and give you instructions for installing it, but it's probably not necessary to do it that way.

---

### Post by kk0sse54 on 2008-10-08
Can you please provide a link otherwise the generic method usually works
./configure 
make 
make install

Here's a link on a compiling tutorial [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by epic1990 on 2008-10-09
OH yes, I am trying to install saurbretan, it's a game.

---

### Post by aeiah on 2008-10-09
just unpack it (double click, drag the folder out and onto the desktop)

in it you should see a readme or install file or something. that will tell you what to do, most of the time. normally you do what was suggested though (ie, ./configure, make, make install). you perform these in the terminal after navigating to the folder you've just unpacked. the compiling tutorial will help you with all of this

---

### Post by hyper_ch on 2008-10-09
if you need to compile it then you also have to geat (at minimum):

```

sudo apt-get build-essential

```

And then untar the package and it should have a readme file that will say what else you need and how to compile...

---

### Post by oldos2er on 2008-10-09
> **epic1990 said:**
> OH yes, I am trying to install saurbretan, it's a game.

 Why not install it from the repositories?

---

### Post by pytheas22 on 2008-10-09
> OH yes, I am trying to install saurbretan, it's a game.

It's in the repositories, so first go to System>Administration>Software sources and under the "Ubuntu Software" tab, make sure that all of the boxes are checked to enable the use of all the standard software repositories.  Close the window; you'll be asked if you want to reload the sources list; say yes.  When that finishes, simply open a terminal and type:
```

sudo apt-get install sauerbraten
```

and it will automatically download and install the game for you.  No need to install build-essential or compile from the source code that you have in the .tar.gz file.

NB: you could also install this game through a graphical interface, if you prefer, by going to Applications>Add/Remove Programs or System>Administration>Synaptic Package Manager and searching for 'sauerbraten'.

---

