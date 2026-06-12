---
title: "[SOLVED] How to get pygame working ??"
date: 2008-06-29
forum: Programming Talk
---

### Post by myromance123 on 2008-06-29
Hi, ok Im at my first steps with python game programming and I would like to know how to get pygame running on ubuntu.

   From the site I got the 1.8 version and it says to install from the setup.py script. I didnt know how to run it so I guessed that I needed to use the terminal and it ran. But at the end it gave me a whole lot of errors (seriously too much, but if you want to see it I will show it)

 So I checked the readme.txt to see if i missed anything and it said to
     > You should definitely begin by installing a binary package for your
     system. The binary packages usually come with or give the
     information needed for dependencies. Choose an appropriate
     installer for your system and version of python from the pygame
     downloads page. [http://www.pygame.org/download.shtml](http://www.pygame.org/download.shtml)

     Installing from source is fairly automated. The most work will
     involve compiling and installing all the pygame dependencies. Once
     that is done run the "setup.py" script which will attempt to
     auto-configure, build, and install pygame.

 I do not know how to install binary packages( I dont even know what they are, are they source codes?) or where to get them from. It also says to compile and install all the pygame dependencies first and I am at a lost on how to do so.

  Please, any help is much appreciated. Thanks for your time in advance~

---

### Post by raja on 2008-06-29
Installing the binary package here means searching for pygame on synaptic, or (better) simply installing it from the terminal so ..

```
sudo aptitude install python-pygame
```

---

### Post by Can+~ on 2008-06-29
General rule for a debian-based OS: check the repository first.

We should have a big sign with a tutorial when people first boots into ubuntu.

---

### Post by myromance123 on 2008-06-30
Ok thanks for the help, I used the terminal as said and it said it was already installed so I was wondering why I cant find it anywhere .
  I have looked through applications and system and cant find it. I have checked all hidden folders and I dont see it anywhere.

  The answer may be obvious but I dont know, what should I do to gain access to it ?

  (All help appreciated, and thnx for replying so fast ~ :D)

---

### Post by raja on 2008-06-30
open a terminal and start python
```
python
```

And at the python prompt, try this
```
import pygame
```

If you dont get any errors, you have pygame installed properly on your system.

---

### Post by myromance123 on 2008-06-30
Okey, I did so and indeed no errors so it must be installed correctly.
What I just did was loading it in python for use on the codes Im going to write is it?

  Pygame isnt a runnable program? I am looking at the pygame website now to understand a little more on what it is. Thanks for the help raja, means a lot ~

---

### Post by raja on 2008-06-30
You are right. Pygame is a python module that helps write games. Good idea to spend some more time with the tutorials on the pygame site.

---

### Post by Toadmund on 2008-12-04
> **raja said:**
> open a terminal and start python
```
python
```

And at the python prompt, try this
```
import pygame
```

If you dont get any errors, you have pygame installed properly on your system.

OK, I did this, after 'import pygame' it just gave me another prompt, is that right?

If that is normal, how do I open 'ocempgui'then?

---

### Post by strider1551 on 2008-12-04
> after 'import pygame' it just gave me another prompt, is that right?
Yes.  If pygame wasn't installed, you would have gotten a ImportError message.

> how do I open 'ocempgui'then?
Well, looking at their [documentation]("http://ocemp.sourceforge.net/manual/ocempgui-manual.html"), ocempgui is another library just like pygame.  Start reading through their section on [integrating ocempgui into projects]("http://ocemp.sourceforge.net/manual/usage.html"), and that should get you started.

---

