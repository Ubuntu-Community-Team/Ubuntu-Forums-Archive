---
title: "Power of Python"
date: 2009-10-26
forum: Programming Talk
---

### Post by 7raTEYdCql on 2009-10-26
I didn't know where to post this thread, so it ended up here.

I have been fiddling around with Python for sometime now, and have realized the potential of the language. But, i haven't been able to use this potential.

Anyone having productive ideas, that can be implemented by programming in Python. Or any recommendation for sites, where people who require python programmers??

I am simply bored just learning the language, and want to do something more with it.
Any thoughts??

---

### Post by Tony Flury on 2009-10-26
Do you not have any jobs that you want to automate ?

Often that might be the way to go - or even use your python knowledge to recreate a (simple) application that you have already seen - for instance my first python application is one that provides a GUI to upload pictures to flickr, including being able to automatically add Tags, Sets etc.

Your could write maybe a Screenlet - or something ?

There maybe a lot of projects out there that use python, but to be honest unless you go from being a beginner to being profficient with the lanaguage and some of the external libraries GTK, cairo, PyGame, SDL, I fear you will be out of your depth very quickly.

---

### Post by Nevon on 2009-10-26
There are always projects available that wouldn't mind an extra pair of eyes fixing bugs. 

A project I'm involved in, [Caffeine](https://bugs.launchpad.net/caffeine/+bug/460124) currently has a memory leak that we can't seem to find. If you feel up to it, feel free to try to find it. If you're just starting out, that might be out of your depth - but no one's going to stop you from trying.

If you're looking to start your own little project, just look at your daily routine and see if there's anything you wish you could simplify or automate. One idea would be to build a parser that reads through the system logs, collects things like application crashes, updates, etc. and then displays that on a calendar. Could be neat.

---

### Post by 7raTEYdCql on 2009-10-26
Thank you for your responses. From what i gather, GUI building is an important part f a programmers toolkit. Guess i should get started off with that then.

I was looking for something simpler. But nonetheless, i do take part in algorithm challenges, like SPOJ, etc, to build my affinity for the language.

From what i understand, when you want to build applications, it is more about the knownedge(amount of information) you have with the language, rather than just Logic(which is tested in algorithm competitions).

Any recommendations, to a first applications, or important tools for your application?

---

### Post by benj1 on 2009-10-26
it depends on what kind of things you want to do, you dont need to do gui apps, most of mine tend to be terminal apps, but its what ever floats your boat.
> From what i understand, when you want to build applications, it is more about the knownedge(amount of information) you have with the language, rather than just Logic(which is tested in algorithm competitions)
not necessarily, both are useful to code efficiently, even if youre coding an algorithm you still need an appreciation of the language. 

i just tend to find projects by programming something that i either cant find, or cant find one that does exactly what i want.

---

### Post by bruce2000 on 2009-10-26
these "problems" are often posted in this forum, and they puzzle me a little. what is the point of learning to program, if you don't have some idea of the software you want to create? it's like learning say japanese when you have no intention of using it.

yes learning the language and writing "hello world" type programs is boring, because you're not creating anything significant.

jump in and write something, something non-trivial. yes you will meet obstacles - look for solutions on google. that's how you learn, and how you become a better coder.

:)

---

### Post by Barrucadu on 2009-10-26
> **bruce2000 said:**
> these "problems" are often posted in this forum, and they puzzle me a little. what is the point of learning to program, if you don't have some idea of the software you want to create? it's like learning say japanese when you have no intention of using it.

What's wrong with learning to program without deciding what you would like to create?

---

### Post by 7raTEYdCql on 2009-10-26
Well let me put it straight, i learned python due to its simplicity, its wide range of uses (you have pylab which can act as a substitute for Matlab as well!) etc.

The very fact that i have learned enough basics, i think, putting it to practice is important.

Hope something strikes me soon, and learning a language is only through experience, that is what i learn.

Thanks all, for your replies.

---

### Post by bruce2000 on 2009-10-26
> **Barrucadu said:**
> What's wrong with learning to program without deciding what you would like to create?

why bother to learn programming if you don't have some end-result in mind?

---

### Post by Pyro.699 on 2009-10-26
I started working on this language a few years ago; but only in the last few months have i really gotten into it.

Some of you may know the website [Neopets](http://www.neopets.com). My summer project was to create a program to preform automated tasks on the website. I know it is designed for children and such but it was a good way for me to have a starting point and an end goal. The current version of the script is aproximatly 10,000 lines long; has over 56 automated functions. From stocking a shop, playing their games (such as Hi-Lo, Poker, Blackjack... Minesweeper ;)), checking stock updates, sending notifying emails and so on. In the beginning it was pretty buggy and hard to manage; scheduling the times that the events would run. To solve that problem i created a minute calendar that contained every minute within the span of 24 hours and assigned a function to that minute.

Python is a very powerful language; it has its flaws, but with those flaws it allows you to try and find your own way around that problem. I highly sugguest this languge to all those who like programming, from begginer to extreemly advanced.

~Cody

---

### Post by slavik on 2009-10-26
> **bruce2000 said:**
> why bother to learn programming if you don't have some end-result in mind?
because society improves based on want, not need.

as for the OP: try to apply python in some of your everyday tasks (scripting something), write a hello world program with mod_python (read: web based), make it access a DB and insert/retrieve data from it.

---

### Post by unknownPoster on 2009-10-26
> **Pyro.699 said:**
> I started working on this language a few years ago; but only in the last few months have i really gotten into it.

Some of you may know the website [Neopets]("http://www.neopets.com"). My summer project was to create a program to preform automated tasks on the website. I know it is designed for children and such but it was a good way for me to have a starting point and an end goal. The current version of the script is aproximatly 10,000 lines long; has over 56 automated functions. From stocking a shop, playing their games (such as Hi-Lo, Poker, Blackjack... Minesweeper ;)), checking stock updates, sending notifying emails and so on. In the beginning it was pretty buggy and hard to manage; scheduling the times that the events would run. To solve that problem i created a minute calendar that contained every minute within the span of 24 hours and assigned a function to that minute.

Python is a very powerful language; it has its flaws, but with those flaws it allows you to try and find your own way around that problem. I highly sugguest this languge to all those who like programming, from begginer to extreemly advanced.

~Cody

Not to derail the discussion, but wouldn't that be considered a form of botting?

---

### Post by Pyro.699 on 2009-10-26
Yeah; it is... but i don't use it as a form of gain. Its more of a learning experience ^^;

---

