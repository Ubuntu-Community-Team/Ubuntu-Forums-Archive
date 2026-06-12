---
title: "downloading and installing libraries"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Girya on 2008-04-26
hey all, 

I'm trying to install Toribash for my son to play but am having trouble with the dependicies. I need to install these: 

On Ubuntu make sure the following apt-get packages are installed
- libsdl-mixer1.2
- libsdl
- libsdl-ttf
- freeglut3

when I apt-get install i get this 


 Couldn't find package libsdl-mixer1.2 libsdl
 libsdl-ttf
What do I do to download these libs? 

Thanks kevin

---

### Post by LaRoza on 2008-04-26
> **Girya said:**
> hey all, 

I'm trying to install Toribash for my son to play but am having trouble with the dependicies. I need to install these: 

On Ubuntu make sure the following apt-get packages are installed
- libsdl-mixer1.2
- libsdl
- libsdl-ttf
- freeglut3

when I apt-get install i get this 
What do I do to download these libs? 


Enable all repositories (to go Add/Remove and change it to "All available applications" and try again.
```

~$apt-cache search libsdl-mixer
libsdl-mixer1.2 - mixer library for Simple DirectMedia Layer 1.2
libsdl-mixer1.2-dev - development files for SDL1.2 mixer library

```

---

### Post by Girya on 2008-04-26
I did what you sugested and no luck. I checked /etc/apt/sources.list and all repositories are enabled.

I don't know what I'm missing

---

### Post by LaRoza on 2008-04-26
> **Girya said:**
> I did what you sugested and no luck. I checked /etc/apt/sources.list and all repositories are enabled.

I don't know what I'm missing

Try:
```

sudo apt-get update && sudo aptitude install libsdl-mixer1.2 libsdl-ttf2.0-0

```

(There are GUI ways of doing this, but I don't really remember how, sorry)

---

### Post by Girya on 2008-04-26
Thanks that did the trick! 

could you explain, I'm guessing that since I upgraded to 8.04 i needed to update my repositories?

also where do I put the file so my son doesn't have to use the command line to start the game.

---

### Post by LaRoza on 2008-04-26
> **Girya said:**
> Thanks that did the trick! 

could you explain, I'm guessing that since I upgraded to 8.04 i needed to update my repositories?

also where do I put the file so my son doesn't have to use the command line to start the game.

Sure. When you switched it to "All Available Applications" the sources.list was changed, but the package manager didn't know that.

```

sudo apt-get update

```
Downloads all the lists from the repositories so the package manager knows where everything is. 
```

&& 

```
Just runs the command after the previous one is finished.

You can create a launcher for it.

You might want to install this way: [https://redmoonstudios.org/~aszlig/toribash/debian/](https://redmoonstudios.org/~aszlig/toribash/debian/)

It probably adds a menu entry under games or something. (It may have done it already, check)

---

