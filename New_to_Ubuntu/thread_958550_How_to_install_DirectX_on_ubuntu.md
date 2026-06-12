---
title: "How to install DirectX on ubuntu??"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by SandyM on 2008-10-25
I was recently surfing the net and suddenly came across a You Tube video showing installation of DirectX on Linux,but didn't tell how to do it.
Can anybody tell me how to do it and if it will be able to run DirectX 9.0c supported games on my Ubuntu.
I tried to install it but each time got an error message. Please tell me how to do it.
THANK YOU

---

### Post by dracayr on 2008-10-25
It is possible to execute windows executables (.exe's) with wine. So, install wine (sudo apt-get install wine), and google for "nameOfTheGame ubuntu" (without the quotes). with a bit of luck, you will find an instruction to install the game...

dracayr

---

### Post by cj2003 on 2008-10-25
I've only found this old how-to that mentions DirectX

[Ubuntu 7.10 + WINE vs. Windows XP]("http://ubuntu-news.net/modules/news/article.php?storyid=3426") - perhams it works on Ubuntu 8.xx?

Update: The link only compares the speed of XP vs. XP on ubuntu, and not directly how to install DirectX on Ubuntu

---

### Post by bhadotia on 2008-10-25
Open GL is DirectX's open source alternative.

---

### Post by Cebonet on 2008-10-25
I don't think you can install DirectX on linux, but you can emulate it using Wine. But emulation decreases the performance.

---

### Post by starcannon on 2008-10-25
To run Direct X applications in linux you have a few choices.

You can use [COLOR=Red]Wine[/COLOR] available from synaptic package manager {System}>{Administration}>{Synaptic Package Manager}>Search "wine">click the tick box to the left of the "wine" package that shows up after the search, choose install, click apply, click apply again.

More about wine available here:[http://www.winehq.org/](http://www.winehq.org/)

You can use [COLOR=Red]Cedega[/COLOR] it requires a subscription. I use it and play World of Warcraft with it (note you can do the same thing with wine).

It is available here: [http://www.cedega.com/](http://www.cedega.com/)

And finally you can use [COLOR=Red]Crossover Games[/COLOR], I have not tried it, but when my cedega subscription runs out, this will be my next software purchase. 

It is available here: [http://www.codeweavers.com/products/cxgames/](http://www.codeweavers.com/products/cxgames/)

GL and have fun.

---

