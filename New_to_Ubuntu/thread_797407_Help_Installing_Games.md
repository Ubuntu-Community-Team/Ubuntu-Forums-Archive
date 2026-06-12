---
title: "Help Installing Games"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by Twiggmbj on 2008-05-17
Hi Everyone !
I have installed Ubuntu 8.04 onto a second pc for my children to use.
As yet it has no internet connection.
I have tried to install some games for them to play until I get another router etc to connect them to the net.
the games i have tried to get to work are, scramble-0.9.5.tar and proscrabble_linux I have extracted the files onto the pc etc, but I cannot get them to run!:redface:
I am a complete newcomer to Ubunto and have only used ms windows before!! ](*,)
So this is probably a very easy and simple thing to do, but I dont know how to as yet, but I do learn fast!!
So any advice would be most appreciated
NOTE the pc has no other software or updates, just what come with the cd.
Thanks
Peeps!

---

### Post by macaholic on 2008-05-17
Well the way you would install it would be soemthing like this: ```
cd /path/to/directory/
./configure
make
sudo make install
```
However, I just tried installing it, and it has other dependencies that you probably are going to need to install before it gets working.

---

### Post by kestrel1 on 2008-05-17
If you want a variety of games you could have a look at this:
[http://packages.ubuntu.com/hardy/games](http://packages.ubuntu.com/hardy/games)
All you need to do to install these is to type:
```
sudo apt-get install 'name of game'
```
in a terminal, where name of game is the same as that found in the list.
If not look at the instructions for installing the games that you download.

---

### Post by macaholic on 2008-05-17
> **kestrel1 said:**
> If you want a variety of games you could have a look at this:
[http://packages.ubuntu.com/hardy/games](http://packages.ubuntu.com/hardy/games)
All you need to do to install these is to type:
```
sudo apt-get install 'name of game'
```
in a terminal, where name of game is the same as that found in the list.
If not look at the instructions for installing the games that you download.
Yes, but the two games he is trying to install aren't in the repositories.

---

### Post by philinux on 2008-05-17
Open synaptic package manager and search for games. Easy install.

---

### Post by hovzio on 2008-05-17
Without a working internet connection you cant use apt get. I like to use deb packages.Use your xp (if it is connected) pc and go to [www.getdeb.net](www.getdeb.net) and check it out. Some cool games there. Deb packages are easy to install, just double click.

---

### Post by macaholic on 2008-05-17
> **hovzio said:**
> Without a working internet connection you cant use apt get. I like to use deb packages.Use your xp (if it is connected) pc and go to [www.getdeb.net](www.getdeb.net) and check it out. Some cool games there. Deb packages are easy to install, just double click.
It's great that you are all telling him where he can find more games, but he is having problems installing two specific games, two of which that needed to be installed from the source.

---

### Post by hovzio on 2008-05-17
> **macaholic said:**
> It's great that you are all telling him where he can find more games, but he is having problems installing two specific games, two of which that needed to be installed from the source.

Very kind of you to point out. To me it sounded like he just wanted to get some games for his kids and since synaptic and Co are not an option I thought this might be helpfull. (Easier than installing from source) If I was mistaken I apologize for any unnecessary posts. :)

---

### Post by Twiggmbj on 2008-05-17
Ahh! so Deb files will open on double click!
I have treid some of the "Deb" games but now I get "Dependancy not satisfied pyton pygames??
I take it that It requires another application to run?
Sorry for bieng such a thicko!
:confused:

---

### Post by Twiggmbj on 2008-05-17
*Python*

---

### Post by macaholic on 2008-05-17
[SIZE="1"]> **hovzio said:**
> Very kind of you to point out. To me it sounded like he just wanted to get some games for his kids and since synaptic and Co are not an option I thought this might be helpfull. (Easier than installing from source) If I was mistaken I apologize for any unnecessary posts. :)
My post wasn't directed at you necessarily, but it seemed as if the two other people above you didn't even bother reading his original post, just read the title. And yes, mentioning getdeb.net was a good thing to do, so no hard feelings?
[/SIZE]

---

### Post by macaholic on 2008-05-17
> **Twiggmbj said:**
> Ahh! so Deb files will open on double click!
I have treid some of the "Deb" games but now I get "Dependancy not satisfied pyton pygames??
I take it that It requires another application to run?
Sorry for bieng such a thicko!
:confused:
Well for this you are going to want internet, unless you want to search the [ubuntu package archive]("http://packages.ubuntu.com/hardy/python-pygame"), find the python-pygame package, its dependencies and then move them over to the desired comp and install them that way. That begin said, with internet it should install the package for you.

---

### Post by hovzio on 2008-05-17
Sorry if it didn't work for you, I have not had any problems with debs but obviously the dependencies are not complete. Have you tried any other debs? It is kinda difficult to build dependencies yourself, so called dependency hell.. and this is what you have to do when you install from source. A package manager takes care of all of this for you but an internet connection is essential. Sorry have no other advise. :(

---

### Post by macaholic on 2008-05-17
> **hovzio said:**
> It is kinda difficult to build dependencies yourself, so called dependency hell.. and this is what you have to do when you install from source. A package manager takes care of all of this for you but an internet connection is essential.
He isn't installing something from the source when he gets the dependency error, and dependencies aren't THAT hard to resolve, jsut need a little searching know-how, and it is relatively easy.

---

### Post by Twiggmbj on 2008-05-17
> **macaholic said:**
> Well for this you are going to want internet, unless you want to search the [ubuntu package archive]("http://packages.ubuntu.com/hardy/python-pygame"), find the python-pygame package, its dependencies and then move them over to the desired comp and install them that way. That begin said, with internet it should install the package for you.

errm ok
found the python package, and a huge list of it's dependencies!!
I think its probably best to wait until the pc is connected to the net!
lol

---

### Post by hovzio on 2008-05-17
> **macaholic said:**
> [SIZE="1"]
My post wasn't directed at you necessarily, but it seemed as if the two other people above you didn't even bother reading his original post, just read the title. And yes, mentioning getdeb.net was a good thing to do, so no hard feelings?
[/SIZE]
Sure not ;)

---

### Post by macaholic on 2008-05-17
> **Twiggmbj said:**
> errm ok
found the python package, and a huge list of it's dependencies!!
I think its probably best to wait until the pc is connected to the net!
lol
Yes, that was my implied point, hence the description of the long drawn-out process description. I'll be sure to be more literal next time :).

---

### Post by unutbu on 2008-05-17
I think what you need is the python-pygame package.

[http://packages.ubuntu.com/hardy/i386/python-pygame/download](http://packages.ubuntu.com/hardy/i386/python-pygame/download)

Not only for finding games, but also for your overall Ubuntu experience, check out the search facility provided at [http://packages.ubuntu.com](http://packages.ubuntu.com). It can help you find out about tons of software available to you.

Edit: Oops, too slow...

---

### Post by hovzio on 2008-05-17
> **macaholic said:**
> [SIZE="1"]
My post wasn't directed at you necessarily, but it seemed as if the two other people above you didn't even bother reading his original post, just read the title. And yes, mentioning getdeb.net was a good thing to do, so no hard feelings?
[/SIZE]

> **macaholic said:**
> He isn't installing something from the source when he gets the dependency error, and dependencies aren't THAT hard to resolve, jsut need a little searching know-how, and it is relatively easy.

I know, I wasnt talking about the "Deb" package but installing from source in general...(back to the begining of the thread) oh and I have had some issues with dependencies. I would say; "Depends on what you wanna install."  All I wanted to do was give some advice, I'm not really lookin to argue..

---

### Post by Twiggmbj on 2008-05-17
> **macaholic said:**
> Yes, that was my implied point, hence the description of the long drawn-out process description. I'll be sure to be more literal next time :).

:lolflag: ok so when it is connected to the net (provided I can get it too) if i download the package will it get all the dependencies and install them?

---

### Post by macaholic on 2008-05-17
> **hovzio said:**
> I know, I wasnt talking about the "Deb" package but installing from source in general...oh and I have had some issues with dependencies. I would say; "Depends on what you wanna install."  All I wanted to do was give some advice, I'm not really lookin to argue..
I wasn't looking for an argument either, but I just thought that he shouldn't be totally discouraged from trying to resolve dependency issues.

---

### Post by macaholic on 2008-05-17
> **Twiggmbj said:**
> :lolflag: ok so when it is connected to the net (provided I can get it too) if i download the package will it get all the dependencies and install them?
If the dependencies are satisfiable within the ubuntu repositories, then yes, it should auto-resolve them. If it doesn't post what is unsatisfiable and I will help you satisfy it.

---

### Post by philinux on 2008-05-17
> **Twiggmbj said:**
> errm ok
found the python package, and a huge list of it's dependencies!!
I think its probably best to wait until the pc is connected to the net!
lol

Definitely a good idea. :)

---

### Post by hovzio on 2008-05-17
If all you wanna do is install some games, then just use add/remove in the applications menu and look under "games". This is probaly the simplest way and the dependencies are taken care of. Then there is also synaptik.(it has more software available) ;)

---

### Post by Twiggmbj on 2008-05-21
Hi Peeps,
Have got the pc online and all is well !, thanks to everyone who tried to help.
And I managed to get it online all by myself LOL.

---

