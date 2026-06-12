---
title: "Terminal Login?"
date: 2012-09-12
forum: New to Ubuntu
---

### Post by geronl on 2012-09-12
Somehow something failed to work properly, possibly the CD burner thing it came with, I had to download another. That's not the question.

When it failed the screen went black and it asked me for a login and password, I don't know anything about a login to my own computer. I do know my password of course.

How do I find/change this?

---

### Post by Bashing-om on 2012-09-12
geronl; Hi ! welcome to the forum.

  Is this a fresh install that did not go right ?

In answer to your question: You are at a terminal and requires you to log into your system.
The prompt is for your user name you made when you installed your system, followed by your pass word you also created when you installed. Be aware when you enter your pass word there will be no echo to the screen (security reasons).

Post back for any additional assistance.

[INDENT]kind regards <==BDQ
[/INDENT]

---

### Post by robtygart on 2012-09-12
Did you restart? if not press ctrl+Alt+F7

You would login with the same name you do when you sigin to your computer..

Try it! But remember it will log you in as root. Any changes you make will happen with out "sudo"

---

### Post by geronl on 2012-09-12
> **Bashing-om said:**
> geronl; Hi ! welcome to the forum.

  Is this a fresh install that did not go right ?

In answer to your question: You are at a terminal and requires you to log into your system.
The prompt is for your user name you made when you installed your system, followed by your pass word you also created when you installed. Be aware when you enter your pass word there will be no echo to the screen (security reasons).

Post back for any additional assistance.
[INDENT]kind regards <==BDQ
[/INDENT]

The CD burner utility that came with Ubuntu 12.04 wasn't working properly and somehow I ended up on a blank screen asking me for a login and password.

Obviously I know my password but the login throws me off. I've never had to type a login to turn the computer on.

---

### Post by geronl on 2012-09-12
> **robtygart said:**
> Did you restart? if not press ctrl+Alt+F7

You would login with the same name you do when you sigin to your computer..

Try it! But remember it will log you in as root. Any changes you make will happen with out "sudo"

I downloaded another program that did the job properly, I hopefully won't have to face that again. The thing is, what the heck is a login name? The password is obvious to me but I have never had to login to my computer.

The CD burner 12.04 comes with wouldn't make a music disc, it would make a CD data disk with music on it but car stereos wouldn't play it. The new program called K3E or something like that works great thought. Has anyone else had this problem? 


OK... maybe what I am saying is that Ubuntu 12.04 should have installed with that program instead of the bad one. :)

How can I change my login so I'll know what it is? lol.

---

### Post by Kopkins on 2012-09-13
Your login is your username. Open a terminal and it should be username@computername$. Or from the command line/terminal ```
who -m
``` Will give who is logged in (you).

Kopkins

---

### Post by geronl on 2012-09-13
> **Kopkins said:**
> Your login is your username. Open a terminal and it should be username@computername$. Or from the command line/terminal ```
who -m
``` Will give who is logged in (you).

Kopkins

Thanks.

And knowing is half the battle.

---

