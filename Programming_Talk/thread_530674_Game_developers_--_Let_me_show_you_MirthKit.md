---
title: "Game developers -- Let me show you MirthKit"
date: 2007-08-20
forum: Programming Talk
---

### Post by curvedinfinity on 2007-08-20
For those with short attention spans, here is a pretty picture:
[IMG]http://www.mirthkit.com/arcade/FinityFlight/screenshot.png[/IMG]

Hey Everyone,
I'm an independent game developer, and a fan of OSS. For the last number of months I've been working on a project called MirthKit. In a couple words, its an executable that runs script and assets downloaded from the internet. 

-- In more than a few words, its a whole lot more than that. Its a game player, an arcade if you will (or at least will be soon...), that simplifies developing and publishing casual games. Its has a little bit of Flash and a little bit of XBOX Live Arcade in its inspiration, but I think it is better than either.

As I've done in the past with my games, I'd like the Ubuntu developer community to give it a whirl before moving onwards. Its still an early version, and has plenty of rough corners, but the foundations are in, and it works pretty rock-solidly. It includes a sort-of-game based on one of my previous games called Finity Flight, which was made in C++. Its mainly just there for you to see how the thing works though.

If you want to check it out, follow the link below.

Link:
[http://www.mirthkit.com]("http://www.mirthkit.com")

If you have any problems or questions, send me a mail or leave a message here.

Chase "curvedinfinity" Adams

Update:
A new version is out with a cool new persistent storage subsystem.

---

### Post by Tomosaur on 2007-08-20
Looks good, I really liked your shooter games :P

I'll check it out right......now!

---

### Post by loell on 2007-08-20
hello chase :) its been a while ;)

nice to see you again, i thought you've stop infinity flight , but then you never stop surpirsing the community with your latest kit. 

my hats off to you :KS

---

### Post by curvedinfinity on 2007-08-20
Hey fans (I guess?!) :) 

Thanks for the support. Please try making a little game with it and tell me what you think. :)

---

### Post by samjh on 2007-08-20
Very interesting.

Is a game developed using the Ubuntu kit fully compatible for use with the Windows kit?

---

### Post by MetalMusicAddict on 2007-08-20
I would suggest posting to dome of the -devel mailing lists as well. That will get you more developer attention.

---

### Post by snoop on 2007-08-20
Looks pretty cool! Great job.

---

### Post by Mickeysofine1972 on 2007-08-21
Hey Chase

Nice to see your plans working, I remember you demoing this to me last year and I though its way cool then!

WTG dude!

Mike

---

### Post by curvedinfinity on 2007-08-21
> **samjh said:**
> Very interesting.

Is a game developed using the Ubuntu kit fully compatible for use with the Windows kit?

Correct, you write one game, and you don't even have to distribute two copies of it.

Thanks for the support guys :)

Do try making something really easy, like Pong! :)

---

### Post by curvedinfinity on 2007-08-22
A little update --

I'm currently planning the graphical design of its (complete) website and arcade application. If you have any feature suggestions for either, please tell me about them.

---

### Post by Tomosaur on 2007-08-22
Quick question about the scripting engine - does it re-route / block stdout? I only toyed with it for a few minutes the other day, but when I'm coding I like to be able to print debugging info into the terminal. I couldn't get MirthKit to do the same. Do we need to launch MirthKit with some argument, or is it just not possible?

Either way - it looks very promising, but I'll need to spend a bit more time with it :D

---

### Post by curvedinfinity on 2007-08-23
Hey,
If you want to print something out, just use the text(...) function and then an update(...). I usually post all of the information I wish to monitor to the upper-left corner (which is 0,0 by the way) using that method.

Just so everyone knows, a new version is up on the website now.

---

### Post by SOULRiDER on 2007-08-23
Sounds/looks good, ill check it out since i wanted to get into game programming :) Also, FF looks like a very very cool shooter, ill chekc it out, i love these kinds of games!

---

### Post by shynko on 2007-08-23
looks cool but didn't work for :(
I click the executable and a black screen would pop up then dissapear good luck though

---

### Post by curvedinfinity on 2007-08-23
You probably don't have the dependencies listed in dependencies.txt :)

---

