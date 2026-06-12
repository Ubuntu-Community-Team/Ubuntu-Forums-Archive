---
title: "Ubuntu &amp; Programming in Python/Java"
date: 2013-01-24
forum: Programming Talk
---

### Post by Iterum on 2013-01-24
I am currently taking a Computer Science class at my school, and we use Python as our programming language of choice. Honestly LOVING Python. For a time I was trying to get into programming, and I couldn't really grasp it much, but after getting into this class and discovering Python, I am hooked and am doing my own stuff at home. With that being said, I have decided to give a look at Linux Distros, because I have been told that Linux is optimized for programmers. Not sure of the validity of the statement, nor am I sure if it is just being taken out of context, but, I would really like to know: is Linux more conducive for programming than, say, Windows 7? Currently working with Python, and I likely will be for some time, though once I finish this year's Computer Science class, the plan is to tackle Java.

Any insight at all would be greatly appreciated -- keep in mind that I am going to be more or less a total "noob" with Linux, so, if you guys do believe Linux would be a programmer's choice, please let me know what Distro would be best.

My understanding is that Ubuntu is relatively simple to use, and comes with less pre-installed software, unlike Linux Mint. Is this software going to be difficult to install or would I be able to figure it out? Example being JDK and Python.

---

### Post by Bachstelze on 2013-01-24
Ubuntu has Python installed by defaults (actually, a lot of components of a default Ubuntu installation are programmed in Python, so Python is necessary for Ubuntu to run). In general, installing software in Ubuntu is very simple as long as it is in the Ubuntu repositories, and everything you need to program in Python is in there.

I haven't done much Java beyond the basics (and my opinion is that you shouldn't either, unless for some reason you really want to), but everything I needed for it was in the repositories, as well.

---

### Post by trent.josephsen on 2013-01-24
Most people would say yes, Linux is better suited to programming in a general sense than Windows. It's a point of no little contention, though (and obviously different when discussing c#ertain languages). I'd certainly recommend using Linux to anyone wanting to learn programming, but that's only one man's opinion.

As for which distro, it really doesn't make much difference. The process of using Python or Java or C or Perl or whatever is going to be essentially the same from one distro to the next. The only things that are really going to be different are the names of the packages you may have to install. You say "apt-get install openjdk-6-jdk", I say "pacman -S openjdk6". The choice of distro is going to boil down to what you like to use, not what the language you like demands.

---

### Post by Iterum on 2013-01-24
> **Bachstelze said:**
> Ubuntu has Python installed by defaults (actually, a lot of components of a default Ubuntu installation are programmed in Python, so Python is necessary for Ubuntu to run). In general, installing software in Ubuntu is very simple as long as it is in the Ubuntu repositories, and everything you need to program in Python is in there.

I haven't done much Java beyond the basics (and my opinion is that you shouldn't either, unless for some reason you really want to), but everything I needed for it was in the repositories, as well.

Very cool, did not know Python had involvement with the Ubuntu components, good to know. Makes Python all the more appealing to me now.

Yeah, I know what you are saying. So far, I have gotten into class hierarchy and inheritance, and of course the OOP model. Even this much information gathered from Java has actually helped me when doing certain things with Python. Great for baseline programming knowledge. I also hear learning C++ would be beneficial too, but it is also my understanding that Java is a deviation of C++, so would Java help me get the same basics as I would from C++, having been derived from C++ (I guess I am digressing a bit, though I am curious now)?

> **trent.josephsen said:**
> Most people would say yes, Linux is better suited to programming in a general sense than Windows. It's a point of no little contention, though (and obviously different when discussing c#ertain languages). I'd certainly recommend using Linux to anyone wanting to learn programming, but that's only one man's opinion.

As for which distro, it really doesn't make much difference. The process of using Python or Java or C or Perl or whatever is going to be essentially the same from one distro to the next. The only things that are really going to be different are the names of the packages you may have to install. You say "apt-get install openjdk-6-jdk", I say "pacman -S openjdk6". **The choice of distro is going to boil down to what you like to use, not what the language you like demands**.

I see. The plan is to just have Linux as a dual-boot, and do all my programming things on that end, then do my tagging, gaming, music, etc on my Windows 7 boot. Just mainly wanting to know if it's worth my time to do all the partitioning and whatnot, to create a better environment to program in. Whenever I hop on Windows I get a "let's game" vibe, and when I look at Linux and hop on Linux Distro forums, I get the "let's make some programs" vibe. Not sure if it's just the stereotype creeping into my thoughts or if that's actually the intended vibe. :p

You make a very good point with the bold passage. I will keep that in mind when I choose a distro, though as I look into Ubuntu, that may be my choice.

Thank you both for the feedback, it's much appreciated and actually has helped bring me just that much closer to making a decision.

---

### Post by xb12x on 2013-01-24
One thing to keep in mind: if your instructor uses Windows to teach this class, and grade your homework, you can run into differences from Linux. So keep Windows available just in case.

---

### Post by Iterum on 2013-01-24
> **xb12x said:**
> One thing to keep in mind: if your instructor uses Windows to teach this class, and grade your homework, you can run into differences from Linux. So keep Windows available just in case.

This is just at the high school level, as I am only in my Junior year of high school. With that being said, there's really no OS restriction other than our school only having Mac OSX machines. Even at that, though, he only checks our screens in class to see if our code is proper/conventional as well as looking at our outputs to see if they are the desired output.

But even still, the plan is to keep it on a dual-boot: one with Windows 7 for stuff that requires Windows 7 such as games and maybe even college things when I get to that point, and another with Linux for programming and maybe other things to such as basic browsing.

So yeah, definitely keeping Windows 7 on my machine just in case.

---

### Post by memilanuk on 2013-01-25
If you haven't already committed to partitioning the drive, you might consider another option: running Linux in a virtual machine such as VirtualBox.  As long as your physical machine has sufficient resources such that you can devote enough to Linux to keep the environment somewhat responsive... you can do 95% (or more) of what you need without having to juggle partitions or boot back and forth between one and the other.  For basic programming its almost certainly enough.

---

### Post by llanitedave on 2013-01-25
> **Iterum said:**
> I see. The plan is to just have Linux as a dual-boot, and do all my programming things on that end, then do my tagging, gaming, music, etc on my Windows 7 boot. 

No argument about gaming at this point, but in my own personal experience I find I get more flexibility and enjoyment from the Linux music applications than I do with the Windows Multimedia player.  If you've got some dedicated music app, it may be a different story.

---

