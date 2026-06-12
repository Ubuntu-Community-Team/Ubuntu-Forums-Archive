---
title: "New to Ubuntu - what to learn"
date: 2010-08-18
forum: Programming Talk
---

### Post by stryker719 on 2010-08-18
All,
Just downloaded Ubuntu, pretty excited to get things going with it.

As I've had to download wireless drivers, I have had to use the prompt numerous times.  I can copy and paste the code I've found from other forum support entries, but I have no idea what they mean.

As I move forward with Ubuntu, I'd like to be more familiar with the system.  What language is Ubuntu written in?  What should I learn so I can do basic "maintenance" where needed?  I know Ubuntu is supposed to remove (mostly) the need for end-user coding, but I'd still like to learn.

---

### Post by Bachstelze on 2010-08-18
Ubuntu is a collection of sofware, and not all software is written in the same language.  I guess it would be safe to assume that most software shipped with Ubuntu is written in C.  However, most of the Ubuntu-specific things (Software Center, Restricted Drivers Manager...) are written in Python.

---

### Post by aeronutt on 2010-08-18
A few resources:

[http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

There is also a helpful book, which can be found in pdf,
'A practical guide to Ubuntu Linux'

---

### Post by worksofcraft on 2010-08-18
what would you like to do with your computer?

If you want to learn programming skills (I'm jumping to conclusions here based on fact you post in this "Programming Talk" forum)...

well I recommend bash, C++ and Python. I can help with C++ questions and am learning these other two myself atm.

---

### Post by stryker719 on 2010-08-19
Thanks for all the feedback.

I should have been more clear in my post; what I'd like to do is learn the language of the kernel itself so I understand what bin and hash and all the other neato terms mean.  I don't plan on writing on programs; rather I'd just like to have a better understanding of what's going on beneath the hood of Ubuntu's core software.

Thanks again.

---

### Post by GenBattle on 2010-08-19
Understanding the kernel is about far more than just learning the language. But as far as i know the kernel is written in C. that said, you don't need to learn C to understand what a kernel does. Sure, it might help, but you can only learn so much by wading through millions of lines of code code. IMO, what you need is an overview of computer science and computer theory, followed by operating system and kernel specifics like multitasking, file systems, memory allocation and management, permissions, etc.

You can learn what things like hash and bin mean without learning specifically about the kernel. For instance, bin usually refers to compiled binary code which is executed or processed by the computer directly. It doesn't relate specifically to the kernel, but more to the general nature of computing.

---

### Post by qedprigmosynois on 2010-08-19
i suppose what you could do if you're into being efficient in linux; learn unix

---

### Post by nvteighen on 2010-08-19
> **stryker719 said:**
> Thanks for all the feedback.

I should have been more clear in my post; what I'd like to do is learn the language of the kernel itself so I understand what bin and hash and all the other neato terms mean.  I don't plan on writing on programs; rather I'd just like to have a better understanding of what's going on beneath the hood of Ubuntu's core software.

Thanks again.

Then you don't need to learn how the kernel is programmed. I suggest you to take this from a system administrator's point of view: learn the design, what component does what and some basic (or advanced) shell scripting. Wikipedia is a great resource for this kind of topics: look up at the articles for the Linux kernel, bash, init.d, etc. Maybe a good method to start would be, for example, to take a look at the bootup process (IIRC, press esc if you have the Ubuntu splash image installed) and try to grasp some names (MTA, exim4, fsck, etc.) you later look up on Wikipedia or somewhere else. Then, just follow hyperlinks and be curious :P

Programming may help you, of course, but not necessarily: it would only if you do OS-specific stuff, for example, you use some POSIX interface (another name for you to look up ;)) or write something that is designed to call the Linux kernel and therefore wouldn't work on Windows.

---

