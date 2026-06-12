---
title: "get ndisgtk without internet connection"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by jondiced on 2008-08-29
Hey folks, so first I should say I'm a total newbie but am very enthusiastic about getting started with Ubuntu. The computer on which I have installed Ubuntu does not have an internet connection (yes, this includes wired connections). I want to get my wireless card working with the Windows driver by using ndisgtk. So the question is: 

How do I get the whole ndisgtk package onto my computer? 

I have another computer running Windows. I burned ndisgtk to a CD from [http://packages.ubuntu.com/hardy/ndisgtk](http://packages.ubuntu.com/hardy/ndisgtk), and tried to run it, but got the following error:
[INDENT]Dependency is not satisfiable: ndiswrapper-utils-1.9[/INDENT]

Thanks for your help!

---

### Post by crispy_420 on 2008-08-30
May take many downloads. For example: ndiswrapper then has 4 dependencies and so on.

---

### Post by jondiced on 2008-08-30
Aw man, I was secretly hoping that that wasn't the answer, but deep inside I think I knew it was.


Really?

---

### Post by SunnyRabbiera on 2008-08-30
well if you have another computer with internet connection then that is good.
If you really need easy access to the drivers you need try linux mint, it has ndiswrapper pre installed as well as its gui:
[http://www.linuxmint.com/download.php](http://www.linuxmint.com/download.php)

---

### Post by jondiced on 2008-08-30
So I have to get all the dependencies. What about the suggestions and recommendations?

---

### Post by jondiced on 2008-09-03
just to wrap things up, i made a valiant effort to download all the dependencies and got fed up with it. i moved the ubuntu computer to a place where i could plug in a wired connection. thanks for all your help though!

---

### Post by moster on 2008-12-27
I have same problem too. I solve it by installing Ubuntu Ultimate who has bunch of stuff already installed among then ndisgtk.

Can someone with more knowledge answer why standard Ubuntu do not have this essential tool preinstalled?

---

### Post by abyssius on 2008-12-27
Although ndiswrapper/ndisgtk isn't installed by default, if you browse the live CD, you'll see a directory called [pool]. If you browse [pool] you'll see a sub-directory called [main]. If you browse [main] you'll find more sub-directories sorted alphabetically. If you select directory [n]. You'll find the [ndiswrapper] and [ndisgtk] directories. Install the ndiswrapper-common package first, the ndiswrapper-utils package next, then finally install the ndisgtk package. You'll be all set without having to access the internet to get them.

---

### Post by moster on 2008-12-28
Thanks, I really needed this. :)

---

