---
title: "OpenGL w/ C++ tutorials?"
date: 2008-06-14
forum: Programming Talk
---

### Post by TheVirtualMember on 2008-06-14
Hey,

I want to begin learning how to use OpenGL (as I find myself spending more time away from my Windows Computer and more on my Ubuntu computer). I know C++ well (i.e., decent knowledge of classes, inheritance, polymorphism, pointers), and I would say I was proficient, or at least decent, with 2D DirectX.

So I'm not looking for a basic C++ tutorial. I tried finding tutorials for OpenGL Apps in C++ on Ubuntu,but all the ones I found where either in python, or for windows.

So, question: I know that to make a C++ app on windows (that isn't a console app), you would ```
#include <windows.h>
```, then use WinMain() as your main function, define a WinProc()function for message handling, and go on from there. So, is there like a ubuntu.h header file (doubt its called that), or something like that that you can use to make GUI apps in Ubuntu? Or would you simply use an API for that? If that's the case, should I learn how to make some basic windows in Ubuntu, or should I jump right in to using OpenGL?

Answer to above question and any other advice on the subject will be appreciated! :)

---

### Post by LaRoza on 2008-06-14
See my wiki under Programming Libraries for various toolkits.

You will have to chose a toolkit to use, install the development files and then link it when you compile.

Exactly what type of GUI do you want?

[http://laroza.pbwiki.com/LibraryLibrary](http://laroza.pbwiki.com/LibraryLibrary)

---

### Post by TheVirtualMember on 2008-06-14
I was planning on making games. Since it appears I will have to download a toolkit to make an app anyway, I might as well go straight to OpenGL, right?

If so, how exactly do I download OpenGL/GLT? I couldn't find it with apt-cache search (I'm guessing because its not an application) .

---

### Post by Can+~ on 2008-06-14
[http://ubuntuforums.org/showpost.php?p=4455523&postcount=17](http://ubuntuforums.org/showpost.php?p=4455523&postcount=17)

---

### Post by TheVirtualMember on 2008-06-14
Multas gratias!

---

### Post by Mickeysofine1972 on 2008-06-15
Also check out the Ubuntu Games Programmers Resource Wiki below

There is a guide to setting up for games development under ubuntu/linux in the 2d section that also will show how to setup for OpenGL too.

Mike

---

### Post by moma on 2008-06-15
Go for [http://www.futuredesktop.org/codeblocks_on_ubuntu_8.04.html](http://www.futuredesktop.org/codeblocks_on_ubuntu_8.04.html) 
and study **note 1)** and **note 5).**

---

### Post by xlinuks on 2008-06-15
> **TheVirtualMember said:**
> Multas gratias!
"Muchas gracias" if you mean it in Spanish :)

---

### Post by LaRoza on 2008-06-15
> **xlinuks said:**
> "Muchas gracias" if you mean it in Spanish :)

I think it is in Italian.

---

### Post by TheVirtualMember on 2008-06-15
> **xlinuks said:**
> "Muchas gracias" if you mean it in Spanish :)
Lol, i've been waiting for someone to sat that.

It's Latin, actually (or so I believe thats the proper way to say it in Latin).

---

### Post by LaRoza on 2008-06-15
> **TheVirtualMember said:**
> Lol, i've been waiting for someone to sat that.

It's Latin, actually (or so I believe thats the proper way to say it in Latin).

I recognized it as either Italian or Latin. 

(On further research it isn't Italian, but very close)

---

### Post by TheVirtualMember on 2008-06-16
Err... alright - I'm getting a bit confused with all the different things I'm finding. I've seen tutorials to make games with SDL, OpenGL, GLUT, and GLT, and they all seem to have some overlap in the functions they use.

Also, anyone know a good GLT tutorial? (I'm sticking with GLT @ LaRoza's wiki's suggestion) I'm having trouble finding one.

---

### Post by Mickeysofine1972 on 2008-06-16
Well SDL will help you setup a game environment, (screen resolution, OpenGL system and sounds etc, like DirectX if you like), GLUT will also provide a route for setup and usage of OpenGL but isnt really meant to be games specific.

There are a few was to initialize OpenGL really but it depends on your goal.

Mike

---

