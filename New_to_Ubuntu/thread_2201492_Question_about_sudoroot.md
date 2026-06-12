---
title: "Question about sudo/root?"
date: 2014-01-24
forum: New to Ubuntu
---

### Post by Christian_Bonomo on 2014-01-24
Hello, I posted a thread about me installing Ubuntu a couple of days ago. I have some experience with this operating system, but I was curious; Is there a way to make myself permanently root in the terminal?

I know you can do, "sudo su" when you open the terminal, but is there a way to set it so that I'm root as soon as I open the terminal, always?

Thank you for any help/answers.

---

### Post by Bashing-om on 2014-01-24
Christian_Bonomo; Hi !

You can, but don't ! That subject is not discussed in this forum.
Consider, there are very good reasons why that ability is not enabled.
Least of all is user misuse and mistakes that will wreck your system -
Leaving your system wide open to security violations ! -

sudo is the means and the way to go !

[INDENT][INDENT][INDENT]just my little bit
[/INDENT][/INDENT][/INDENT]

---

### Post by deadflowr on 2014-01-24
> **Bashing-om said:**
> Christian_Bonomo; Hi !

You can, but don't ! That subject is not discussed in this forum.
Consider, there are very good reasons why that ability is not enabled.
Least of all is user misuse and mistakes that will wreck your system -
Leaving your system wide open to security violations ! -

sudo is the means and the way to go !
[INDENT][INDENT][INDENT]just my little bit
[/INDENT]
[/INDENT]
[/INDENT]


+1

I realized some time ago that after the initial tweakings I do to any system, I rarely have any need to run as root for more than one or two commands.
If I do, I simply will run
```
sudo -i
```
do what I need and then type exit to close it.

---

### Post by QIII on 2014-01-24
Hi!

Please have a read through [this]("https://help.ubuntu.com/community/RootSudo"), which generally explains the reasoning behind this.

(We'd prefer that users be directed to this when such questions arise so that the answers are the Forums are consistent with regard to this subject.  ;) )

Personally, I don't use sudo -i.  I want to type sudo each time to remind myself to stay on my toes.  It would be too easy to make a mess by being careless.

Cheers!

---

### Post by Christian_Bonomo on 2014-01-25
Thank you, I will take this into consideration now, knowing experienced users still type in 'sudo' everytime. If you guys are worried about messing up, then I could really mess up if a newbie like myself were to stay in root. Thank you again for the answers!

---

