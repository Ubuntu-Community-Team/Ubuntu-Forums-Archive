---
title: "Make Windows Programs in Linux"
date: 2007-12-06
forum: Programming Talk
---

### Post by oneadvent on 2007-12-06
Can I write Windows VB programs in Linux, to be run under Windows?

I know that it is odd, but I need it to make money...and I hate to use windows on my pc.

---

### Post by LaRoza on 2007-12-06
You can write them, but you can't run them.

You can use a language like Python to make the programs, and it would work in Windows and Linux.

---

### Post by oneadvent on 2007-12-06
It has to be VB, because it needs to be sent back to a real programmer, and he does everything in VB.

What program could I use for it?

---

### Post by LaRoza on 2007-12-06
To write them, use any editor, but you can actually compile or run them.

---

### Post by oneadvent on 2007-12-06
Ok, um...not what I was thinking....

I guess I will have to boot up into the old windoze to do this job then. very inconvenient. You would think, being user made, that there would be a high demand for creating and testing vb or vb.net programs in a native linux environment. Skip the exe creation. 

Wouldn't that be convenient?

Geeze, put me in charge, eh?

(thats a joke.)

---

### Post by ThinkBuntu on 2007-12-06
Java's your best bet for cross-platform. And there are a ton of jobs for it, if that matters...

---

### Post by slavik on 2007-12-06
> **oneadvent said:**
> ... a real programmer ... does everything in VB.

the context is still there and you, my friend, have stated an oxymoron. (it is not a paradox because it is not true.)

NOTE: I wonder how LaRoza didn't point this one out. :(

---

### Post by LaRoza on 2007-12-07
> **slavik said:**
> the context is still there and you, my friend, have stated an oxymoron. (it is not a paradox because it is not true.)

NOTE: I wonder how LaRoza didn't point this one out. :(

I wanted to, but didn't want to start a flame war.

---

### Post by erginemr on 2007-12-07
> **oneadvent said:**
> It has to be VB, because it needs to be sent back to a real programmer, and he does everything in VB.

What program could I use for it?

Hello,

To your original question, you can develop Windows programs (that are not specifically written for direct hardware manipulation) from under Linux via a virtual pc software.  This way, you can run a virtual Windows XP system from under Linux, on to which you can install VB6 or VB.net and develop your programs there. There are a few alternatives; Virtual Box, VMWare, QEmu, and a few others. Yet, I recommend using Virtual Box ([http://www.virtualbox.org/](http://www.virtualbox.org/)) for it is free, fast, and gets the job done.

On a side note, if you (or your friend) are also interested in Linux programming, you can check out Gambas as a VB-alike alternative to develop native graphical applications under Linux ([http://gambas.sourceforge.net/](http://gambas.sourceforge.net/)). But if I were you, I would invest my time to learning Python, which is an easy-to-learn, platform-independent, powerful and flexible language to develop all kinds of applications, and which I believe, has a bright future.

---

### Post by DavidBell on 2007-12-07
In addition to erginemr, AFAIK you can install and run VB5 & VB6 on linux via ***wine*** though some functions/components may not work.

I think ***mono*** has some support for VB.NET now.

DB

---

### Post by oneadvent on 2007-12-07
> **slavik said:**
> the context is still there and you, my friend, have stated an oxymoron. (it is not a paradox because it is not true.)

NOTE: I wonder how LaRoza didn't point this one out. :(

Ya, well I mean that he is a real programmer, AND he uses VB. I recognize other languages and I know that each has its merit. In this case it is a free lance type job I want, and I don't want to go into windows for it. 

He is not interested in anything cross platform and neither is his clients. I am, however. 

And in order to use VM ware I have to actually own a copy of XP that hasn't been used on any PC yet. And I don't.

---

### Post by oneadvent on 2007-12-07
> **DavidBell said:**
> In addition to erginemr, AFAIK you can install and run VB5 & VB6 on linux via ***wine*** though some functions/components may not work.

I think ***mono*** has some support for VB.NET now.

DB

I was thinking about that. Would it run it well enough to build simple database type programs?

Like a library?

---

### Post by Vadi on 2007-12-07
You can use Virtualbox. You do need an XP install disk, but you don't have to register it - you can just take a snapshot of the machine after the install, and "reset" it every 30 days (I do have a valid license key for my laptop, it's on a sticker at the bottom... but I'm too lazy to call them for activation.)

---

### Post by Joeb454 on 2007-12-07
AFAIK, mono does support VB.net now, if you get mono develop then I think that has stuff for it...obviously you need mono installed first lol.

for mono develop:
```
sudo apt-get install mono-develop
```

---

### Post by oneadvent on 2007-12-07
> **Vadi said:**
> You can use Virtualbox. You do need an XP install disk, but you don't have to register it - you can just take a snapshot of the machine after the install, and "reset" it every 30 days (I do have a valid license key for my laptop, it's on a sticker at the bottom... but I'm too lazy to call them for activation.)

I have no idea how to take a snap shot of that install. Is it something included with VMware? I haven't had to use it yet.

I tried Mono but it does not have a "form" for me to develop off of. I  wouldn't even know where to start without it being object oriented.

(Speaking of which, is Ruby OO? I wanted to learn that in my spare time.)

---

### Post by Vadi on 2007-12-07
I said Virtualbox, not VMware - those are two completely different programs. I don't know if you can do it in vmware, I never used it - because virtualbox has an open-source edition and you can install it right from the repositories.

---

### Post by oneadvent on 2007-12-07
> **Vadi said:**
> I said Virtualbox, not VMware - those are two completely different programs. I don't know if you can do it in vmware, I never used it - because virtualbox has an open-source edition and you can install it right from the repositories.

Sorry, again haven't done it. 

so does virtual box allow for an image? Past that is it possible to save my program on my linux...partition(?)?

---

### Post by Vadi on 2007-12-07
Oh yeah, it saves it on your linux patrition. Virtualbox doesn't even patrition your drive at all, it uses the linux patrition.

You can also set up "shared folders", so that a folder is seen both by linux and virtualbox windows. That's what I've done - made a shared folder for my program, I code the program with linux tools & compile it for testing, but when I need to compile the windows version, I just load virtualbox, compile, & quit.

---

### Post by oneadvent on 2007-12-07
alright. I will set it up over the weekend. (I downloaded it)

I will just re do it every 30 days or whatever....wonder if vb.net would run in 98...

---

### Post by oneadvent on 2007-12-07
I get this:
```
 
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}


```

Oh, and I will start or continue a thread in the correct forum, as soon as I figure out what forum that is.

---

### Post by oneadvent on 2007-12-08
fixed my problems, everything is up and running and this should work perfectly.

Thanks.

---

### Post by oneadvent on 2007-12-08
Okay, I have to say it. This is cool.

---

### Post by Vadi on 2007-12-08
Yep. Feel free to safely mention to that programmer that this was coded on linux.

---

### Post by oneadvent on 2007-12-08
well it worked perfectly, so I will now be able to develope in both enviorments.

Now to network the two....

---

### Post by Vadi on 2007-12-08
Network?

---

### Post by oneadvent on 2007-12-08
Um...share a folder between the two.

I am actually using VB Express 2008 btw, its free.

---

### Post by Vadi on 2007-12-08
Ah. Read the docs, they say how to.

Never tried VB, don't have any use for it either. I got NetBreans, Eclipse, Code::Blocks, Anjuta, KDevelop, and Qt Assistant installed... now I just need to pick one.

(actually I'm still using notepad++).

---

### Post by kknd on 2007-12-08
VB still alive?? 

Please, if you like to use simple languages (I mean quick development, high level programming), try to learn Lua / Python / others that does well on both Windows and Linux.

If it's a legacy application, you can try on Mono.

---

### Post by oneadvent on 2007-12-08
> **oneadvent said:**
> Ya, well I mean that he is a real programmer, AND he uses VB. I recognize other languages and I know that each has its merit. In this case it is a free lance type job I want, and I don't want to go into windows for it. 

He is not interested in anything cross platform and neither is his clients. I am, however. 

And in order to use VM ware I have to actually own a copy of XP that hasn't been used on any PC yet. And I don't.

He uses it. I am 100 % on board with Python but if he wants me to create parts of the program, I will have to actually be on the same page as him, and that means I have to at least be in the right book.

Josh

---

### Post by fwilliams on 2007-12-08
Real programmers don't use VB.  VB is more of a proto typing language.

---

### Post by oneadvent on 2007-12-08
> **fwilliams said:**
> Real programmers don't use VB.  VB is more of a proto typing language.

Thank you for your witty remark, however, I disagree. He is a "real" programmer as he has a masters degree, and makes 6 figures a year. And, suprise! He uses VB6.

Think about it, if a program is written in that "simple" programming language and it does everything that needs done, why change it? Why learn something else? He has no reason.

---

### Post by Vadi on 2007-12-08
In short, he drinks the microsoft cool-aid, working for microsoft on making windows-only software, and is affected by vb6 vunerabilities (which, with the language being proprietary, he can do nothing to fix).

At least you're going on a better path!

---

### Post by oneadvent on 2007-12-08
I agree, but to say that VB6 is for prototyping only is just MS hatred to the point of ignorance. It is a very popular language for windoze. when VB.NET is included you see the vast majority being VB.

Anyway off the flame war (holy war?). I was wondering if there was a good object oriented language for Python? I thought I heard Ruby was, but I couldn't find a "form."

I have really only written anything on the BASIC level.

Josh

---

### Post by LaRoza on 2007-12-08
> **oneadvent said:**
> 
Anyway off the flame war (holy war?). I was wondering if there was a good object oriented language for Python? I thought I heard Ruby was, but I couldn't find a "form."


Python is object oriented. Ruby is object oriented also.

---

### Post by oneadvent on 2007-12-08
So does it have a form that you build off of, kind like the difference between Qbasic and Visual Basic

---

### Post by LaRoza on 2007-12-09
> **oneadvent said:**
> So does it have a form that you build off of, kind like the difference between Qbasic and Visual Basic

I don't know. I never used either of those languages, so I don't understand what you mean.

---

### Post by CptPicard on 2007-12-09
> **oneadvent said:**
> So does it have a form that you build off of, kind like the difference between Qbasic and Visual Basic

No, there are no full "create a GUI form and add code"-style development environments for Python or Ruby that I know of, although they would be possible... and QT Designer and Glade might come close to what you need; you just need to be willing to write more of the code by hand.

Those things, mind you, have nothing to do with object-orientedness, which Ruby is more rigorously (pretty much religiously so) than Python...

---

### Post by Vadi on 2007-12-09
Never looked at Ruby code, by Python code looks ugly :(

(sticking to my C/C++ as long as I can!)

---

### Post by oneadvent on 2007-12-09
> **CptPicard said:**
> No, there are no full "create a GUI form and add code"-style development environments for Python or Ruby that I know of, although they would be possible... and QT Designer and Glade might come close to what you need; you just need to be willing to write more of the code by hand.

Those things, mind you, have nothing to do with object-orientedness, which Ruby is more rigorously (pretty much religiously so) than Python...

I guess I am confused on the difference. Realistically I will need to just get down to it and learn Ruby. (Its a goal) To fully understand what you are trying to tell me. I think that VB is super easy.

And I think C/C++ is  a very good idea to stick with. It is not going to go anywhere. I was actually leaning toward that instead of Ruby because I know a lot of Windoze programs are written off of it. (realisticly windoze isn't going anywhere anytime fast either.)

Oh and if you noticed how bad my spelling is, that is because I am in epephany

---

### Post by CptPicard on 2007-12-09
> **oneadvent said:**
> I guess I am confused on the difference. Realistically I will need to just get down to it and learn Ruby. (Its a goal) To fully understand what you are trying to tell me.> 

Object-orientedness is, generally, a style of designing a programming language and programs written in that language where code and data are encapsulated into entities called objects, which can have an associated type system with inheritance.

I'd recommend you learn Python instead of Ruby. I do have a soft spot for some of Ruby's features, but the reasons for that do not really extend to beginners.

[quote]
 I think that VB is super easy.


Python is easier, and *way* better structured. Honestly, forget VB. There is the bonus though that both can be compiled into the .NET CLI, no? (I don't know much about the MS platform though...)

[quote]And I think C/C++ is  a very good idea to stick with. It is not going to go anywhere. I was actually leaning toward that instead of Ruby because I know a lot of Windoze programs are written off of it.

The vast majority of all native-compiled stuff is written in C/C++, and not just on Windows, but everywhere. C is more of a lower-level systems programming language, C++ an application programming language, as the OO features are considered helpful in the design of large application architectures.

But as long as you can use a higher-level language, you really should.

---

