---
title: "Attention to all smarties..."
date: 2010-05-27
forum: Recurring Discussions
---

### Post by thelionphoenix on 2010-05-27
Hey everyone.

Just joined this forum, and recently installed ubuntu.

(I am totally new to Linux!!:))

I plan to purchase a macbook, and was thinking to install ubuntu on that too...

So can someone tell me a little about ubuntu, and how much different is it from other linux distributions,and if i currently use linux just as a pc but further plan to practice computer programming **(m a computer student)** , web scripting and stuff, should i consider other distros like red hat or fedora.

someone smart enuff??
Pls Help!!

---

### Post by lisati on 2010-05-27
Moved to "Absolute beginner talk"

---

### Post by coolman98 on 2010-05-27
Well,
ubuntu has alot of focus on python
and I find it very easy to use.
First of all it uses apt and .debs
I would really recommend sticking with ubuntu.
I have tried many other distro
and they just are'nt as good.

---

### Post by -humanaut- on 2010-05-27
Ubuntu is a Debian based distribution ([http://www.debian.com](http://www.debian.com)) but more user friendly however it shares alot of Debian's power (Command line applications,Tools,etc...) It's just much more on the bleeding edge then Debian Stable. You can program in Ubuntu just the same as any Linux distribution and repackage them in .deb files. There's a countless number of programming tools available from the repositories for C,C#,Mono(basically .net framework),Python,QT,etc... If you wanna hop around distro's like some of use still do I'd encourage it you can learn alot from different distributions I just stick with Ubuntu nowadays though I have CentOS installed on my Servers. Also if your interested in learning about Linux heres a site that you can literally learn everything at I've used in multiple times for various different studying materials (I'm a Computer Science student) [http://tldp.org](http://tldp.org) <---Best site on Linux hands down.

---

### Post by anewguy on 2010-05-27
Ubuntu has all you will need.  I've done a little cross-platform development by starting in Ubuntu with C/C++, libusb and GTK (for GUI development), then used the free GTK for Windows, MingW and MSys in Windows to compile and run  the same application in Windows.  Only a couple of #ifdef's are needed for Windows versus Linux specific things - everything else is the same.

Dave ;)

---

### Post by jrothwell97 on 2010-05-27
Welcome to Ubuntu!

Ubuntu's not too different to most other Linux distros, but beware that all of them have their own little quirks. Ubuntu, for example, disables the root user and so you have to use "sudo" to elevate to administrator privileges. (This is the same as what Mac OS X does if you wanted an analogue.)

Programming should be easy enough, as long as you stick to console programming. (If you're looking for something Visual Studio-like, dual-boot with Windows - this is not one of Ubuntu's strong points.)

Ubuntu's a good distribution if you're just getting started: diversifying into other distributions will definitely be easier once you're comfortable with it.

Good luck, and enjoy Ubuntu! :D

---

### Post by oleink on 2010-05-27
ubuntu is pretty similar to other gnome based distros.  But the seal for me on choosing it over the others was the large amount of proprietary drivers that could be installed (without using ndiswrapper) for wireless cards and the fact it has a software center:popcorn:

---

### Post by pzkfw on 2010-05-27
please don't buy a mac if you're thinking of only using ubuntu on it.  That would be a complete waste of money.

---

### Post by oleink on 2010-05-27
haha hardware + way overpriced = mac

---

### Post by steveneddy on 2010-05-27
large feline which may actually be a bird reborn from fire

welcome

---

### Post by geet89 on 2010-05-27
hey, great to know that you are using ubuntu...but since you are a computer programmer i suggest you get you hand dirty with open solaris... it has great tools for debugging etc..

---

### Post by Ozymandias_117 on 2010-05-27
> **oleink said:**
> ubuntu is pretty similar to other gnome based distros.  But the seal for me on choosing it over the others was the large amount of proprietary drivers that could be installed (without using ndiswrapper) for wireless cards and the fact it has a software center:popcorn:

Software Center is also in Debian. Ubuntu is pretty good for starting out, but I started learning a lot more after switching to Debian on my main box and Slackware on my spare box.

Linux will be great for you if you want to start programming, since you can download the source code of any program and look at it (a great way to learn about programming). I would say the majority in Linux are written in C/C++ or Python. (This is based on a gut feeling, not any facts :P)

If you want to check out the source code for a program, just use ```
apt-get source *packagename*
```

---

### Post by oleink on 2010-05-27
> **Ozymandias_117 said:**
> Software Center is also in Debian. Ubuntu is pretty good for starting out, but I started learning a lot more after switching to Debian on my main box and Slackware on my spare box.

Linux will be great for you if you want to start programming, since you can download the source code of any program and look at it (a great way to learn about programming). I would say the majority in Linux are written in C/C++ or Python. (This is based on a gut feeling, not any facts :P)

If you want to check out the source code for a program, just use ```
apt-get source *packagename*
```

I believe some bsd distros are written in java...???

---

### Post by QIII on 2010-05-27
> **jrothwell97 said:**
> Ubuntu's a good distribution if you're just getting started: diversifying into other distributions will definitely be easier once you're comfortable with it.


I hope you don't want to leave the OP with the impression that Ubuntu is only for novices.  Nor that some other distros are not good places to start.  Dreamlinux, for instance, is another Debian-based distro that is really easy to pick up, is light on requirements and still allows you under the hood.  Besides, it has that cool dock-looking dealy at the bottom of the screen if you are in to that.

RPM based distros are just as easy, it's just that the terms of the metaphor differ.  Instead of "sudo" and "apt-get", for instance, you use "su" and "yum".  Fedora's GNOME interface is nearly identical to Ubuntu's.

For that matter, GNOME on OpenSolaris looks the same.

For the casual user, it might be hard to distinguish since you will mostly be working from GNOME anyway.

When you want to get under the hood and crank up the horsepower in Ubuntu, you do it the same way you do in any distro.  I think the "MyDistro is better because it is more powerful" thing is hogwash.  I use a lot of them.  I can get the same things done with each of them.  You learn as much from unbolting the body panels on DistroX as you do on DistroY.

The difference is one of aesthetics, which is a fair measure of preference.  You have the right to, and ought to, use what works for you.  

But the "I'm technically smarter because I use DistroX and you use DistroY" is a bit condescending.  I've been doing this computer gig since the days of punch cards, acoustic couplers and room-sized mainframes.  I have long since lost the "Levi's versus Wrangler" mentality.

Jeans is jeans.

---

### Post by oleink on 2010-05-27
Yeah python is pretty solid, simple, and powerful.  The only thing not simple that I've found is the same in java and c++ and the dang "nonlocal" statements I couldn't find logical explanations of it anywhere

---

### Post by Jharder on 2010-05-27
Welcome to Ubuntu!

Ubuntu is gonna work well for what you are looking to do. It may take some time but keep working on it! 

Please Please Please! Do not buy a Mac and install Ubuntu on it. Most of what you pay for in the mac is the Operating System. Doing so would defeat the purpose of buying a Mac! 

Well have fun and enjoy the free virus-free software that wont give you a blue screen!

---

### Post by Ozymandias_117 on 2010-05-27
> **oleink said:**
> I believe some bsd distros are written in java...???

Maybe BSD, but the Linux kernel is in C most of the /bin and /sbin commands are C or C++ lots of the applications in the repositories are C, C++ or Python. I'm not trying to say that that is the ONLY thing that is used, just it looks like they are the most popular.

---

### Post by oleink on 2010-05-27
> **thelionphoenix said:**
> Hey everyone.

Just joined this forum, and recently installed ubuntu.

(I am totally new to Linux!!:))

I plan to purchase a macbook, and was thinking to install ubuntu on that too...

So can someone tell me a little about ubuntu, and how much different is it from other linux distributions,and if i currently use linux just as a pc but further plan to practice computer programming **(m a computer student)** , web scripting and stuff, should i consider other distros like red hat or fedora.

someone smart enuff??
Pls Help!!

Like the last post said.  Ubuntu (and many other distros may be great for your needs.  If you are very new to programming and want to use the best language for ubuntu (imho- after all I'm still a noob) check out "A Byte of Python" it is a free book that is updated as the language is.  Also for your other needs Ubuntu (being based in TCP/IP with some mods) is great for your web scripting needs.

---

### Post by thelionphoenix on 2010-05-28
Thanx everyone,

My choice of ubuntu was only due to it was the first linux distro i came across,

anywayz, if most of you r right then i m probably lucky:) 

By d way i dont mean to buy a mac only 4 linux, its only that i somehow for some reason hate windows, not sure why, but i do..

its odd u kno cuz since childhood i've been using microsoft prods,
may be thats the reason

And afterall a MAC is a mac, the most advanced operating system in the world, wouldn't u all agree..?? 

n thanx again.

---

### Post by -humanaut- on 2010-05-28
> **geet89 said:**
> hey, great to know that you are using ubuntu...but since you are a computer programmer i suggest you get you hand dirty with open solaris... it has great tools for debugging etc..

Hey did you see Oracle accidentally posted an 'Opensolaris 2010.05' a couple days ago man I hope that wasn't an error I really liked opensolaris but b134 was too unstable and thats really the only way now to go about getting security updates.

---

### Post by nikhilbhardwaj on 2010-05-28
> **pzkfw said:**
> please don't buy a mac if you're thinking of only using ubuntu on it.  That would be a complete waste of money.
 
i agree with this
unless you have a lot of money to burn.

---

### Post by nikhilbhardwaj on 2010-05-28
> **oleink said:**
> I believe some bsd distros are written in java...???

lol
you're joking arent you??

bsd has been around from times when java didn't exist

---

### Post by nikhilbhardwaj on 2010-05-28
> **thelionphoenix said:**
> 

And afterall a MAC is a mac, the most advanced operating system in the world, wouldn't u all agree..?? 


if that's the case 
why even bother with linux??

you'll be able to program and do all your stuff on os x too

---

### Post by thelionphoenix on 2010-05-28
Cause it's open source and i look forward to becum a member of an open source community in my university (VIT,Tamil nadu).

---

### Post by oleink on 2010-05-28
> **Ozymandias_117 said:**
> Maybe BSD, but the Linux kernel is in C most of the /bin and /sbin commands are C or C++ lots of the applications in the repositories are C, C++ or Python. I'm not trying to say that that is the ONLY thing that is used, just it looks like they are the most popular.

Agreed although I've found that out of those python is probably the fastest and smoothest just from experience and the fact that coding can be shorter because it is quite powerful.  I think Java is used for a few bsd's but you're absolutely correct: most of the time it is C or C++ or Python

---

### Post by oleink on 2010-05-28
> **thelionphoenix said:**
> Thanx everyone,

My choice of ubuntu was only due to it was the first linux distro i came across,

anywayz, if most of you r right then i m probably lucky:) 

By d way i dont mean to buy a mac only 4 linux, its only that i somehow for some reason hate windows, not sure why, but i do..

its odd u kno cuz since childhood i've been using microsoft prods,
may be thats the reason

And afterall a MAC is a mac, the most advanced operating system in the world, wouldn't u all agree..?? 

n thanx again.

I would have to disagree.  OSX is not the most advanced OS in the world.  It is based on bsd and has taken open source out of the picture and added proprietary.  I don't think any OS is the "most advanced."  Linux has all the capabilities OSX has but may not have quite as much software for some things (recording music, photography etc) but I'm a musician and a photographer and I get by with it just fine in fact I prefer rawstudio for photography over anything I've ever used (including all the major softwares out there) and pro quality music can still be produced with ubuntu.  The reason everyone thinks OSX is the "most advanced" is because it is based on linux which has some of (if not) the best graphics and sound capabilities in the world.  But the main thing I don't like about OSX is that it is proprietary.  I still like their software some but their prices are ridiculous.  I'm building a desktop and will likely use OSX on it too but that is because buying a cd of OSX is not very expensive whereas buying a Mac is like selling your soul to the devil because it costs way too much and it is proprietary.

---

### Post by oleink on 2010-05-28
> **nikhilbhardwaj said:**
> lol
you're joking arent you??

bsd has been around from times when java didn't exist

Hello you can change languages.  Doesn't Ubuntu incorporate more Python than Debian from which it came?  (I'm not certain of this which is why I'm asking and I did not post it as a declaritive sentence)

Different derivatives of the same OS?:

[http://shootout.alioth.debian.org/u64q/code-used-time-used-shapes.php]("http://shootout.alioth.debian.org/u64q/code-used-time-used-shapes.php")


And yeah I know it was around b4 Java it started in 77? at least sometime around there and Java wasn't officially released until 1995.

---

### Post by QIII on 2010-05-28
OK.  Back to a couple of original questions for the OP.

Red Hat is proprietary and it is not free.  Unless you want to pay for it, you won't be using it on your PC.  Fedora is Red Hat's test-bed.  Some say Red Hat is "based" on Fedora, but I don't think it's quite as simple as that.  There's some history to Red Hat (and part of that history is why I turned my back on Red Hat years ago.)  Fedora is free and open source.  In general, if you want to know what Red Hat is all about (except for some of the Enterprise components), you'll find it in Fedora.

As for other distros, you SHOULD try as many as you can.  You should choose the one that best fits what you want to do.  Use what works for you. 

As far as languages go, we could sit here for days and each fan could extol the virtues of his language of choice.

In general, we used to say that the simpler a language was to write, the slower it was to execute.  That is probably not so true nowadays.

Among the high-level languages, C++ executes very fast.  But execution time is becoming less and less of an issue as hardware technology advances, as I said.  It is also not type safe in some respects, particularly with pointers.  Its type-safety is limited, but definitely an improvement over C.  C++ is ubiquitous.

Python has a couple of advantages in that it is type safe and can be better used for aspect-oriented programming.  It is easier on the eyes for some.  

Here's what you should do:  Using whatever language is most readily available to you, learn to PROGRAM.  Understanding that is the key.  The language is secondary.  I have seen a lot of code that is technically correct, but does a terrible job of implementing a solution.

Until you learn how to identify problems, develop solutions and implement them in a manner that will give you the results you want, purely technical knowledge of any language is useless.

The language is only a tool.  You might have a great grasp of the technical details of a particular make and model of shovel; but unless you can turn dirt with it, you can't dig a ditch.  If you don't know how to slope the sides of the ditch under different circumstances and you don't know how to angle the ditch as it passes over terrain, nobody will hire you to dig ditches.

Nobody is hired to write code.  They are hired to create solutions.

Is it "easy" to learn another language?  Not necessarily.  But it is doable.

What cannot be absent is the ability to formulate a conceptual understanding of the task at hand, its solution and its satisfactory implementation.  If you understand how and where to dig your ditch, the make and model of shovel is of little concern.

---

### Post by lavinog on 2010-05-28
> **thelionphoenix said:**
> 
By d way i dont mean to buy a mac only 4 linux, its only that i somehow for some reason hate windows, not sure why, but i do..

its odd u kno cuz since childhood i've been using microsoft prods,
may be thats the reason

And afterall a MAC is a mac, the most advanced operating system in the world, wouldn't u all agree..?? 


You should try and refrain from making these sort of statements on the forums.  They tend to lead to flame wars and stray off topic.

Also, similar statements can hurt your chances finding employment with some companies.

---

### Post by oleink on 2010-05-28
> **QIII said:**
> OK.  Back to a couple of original questions for the OP.

Red Hat is proprietary and it is not free.  Unless you want to pay for it, you won't be using it on your PC.  Fedora is Red Hat's test-bed.  Some say Red Hat is "based" on Fedora, but I don't think it's quite as simple as that.  There's some history to Red Hat (and part of that history is why I turned my back on Red Hat years ago.)  Fedora is free and open source.  In general, if you want to know what Red Hat is all about (except for some of the Enterprise components), you'll find it in Fedora.

As for other distros, you SHOULD try as many as you can.  You should choose the one that best fits what you want to do.  Use what works for you. 

As far as languages go, we could sit here for days and each fan could extol the virtues of his language of choice.

In general, we used to say that the simpler a language was to write, the slower it was to execute.  That is probably not so true nowadays.

Among the high-level languages, C++ executes very fast.  But execution time is becoming less and less of an issue as hardware technology advances, as I said.  It is also not type safe in some respects, particularly with pointers.  Its type-safety is limited, but definitely an improvement over C.  C++ is ubiquitous.

Python has a couple of advantages in that it is type safe and can be better used for aspect-oriented programming.  It is easier on the eyes for some.  

Here's what you should do:  Using whatever language is most readily available to you, learn to PROGRAM.  Understanding that is the key.  The language is secondary.  I have seen a lot of code that is technically correct, but does a terrible job of implementing a solution.

Until you learn how to identify problems, develop solutions and implement them in a manner that will give you the results you want, purely technical knowledge of any language is useless.

The language is only a tool.  You might have a great grasp of the technical details of a particular make and model of shovel, but unless you can turn dirt with it, you can't dig a ditch.  If you don't know how to slope the sides of the ditch under different circumstances and you don't know how to angle the ditch as it passes over terrain, nobody will hire you to dig ditches.

Nobody is hired to write code.  They are hired to create solutions.

Is it "easy" to learn another language?  Not necessarily.  But it is doable.

What cannot be absent is the ability to formulate a conceptual understanding of the task at hand, its solution and its satisfactory implementation.  If you understand how and where to dig your ditch, the make and model of shovel is of little concern.

Very agreeable to what he said.  It isn't the language its what you you learn to do with it.  Learning to shorten a script by making it more readable for the actual program itself can increase speed which is often good but learning what sacrifices that makes to stability etc is equally important.  Also making sure you create as little errors as possible "Stability is more important than speed" and as an added note: "but that does not mean you cannot learn to program both"

---

### Post by QIII on 2010-05-28
> **oleink said:**
> Very agreeable to what he said.  It isn't the language its what you you learn to do with it.  Learning to shorten a script by making it more readable for the actual program itself can increase speed which is often good but learning what sacrifices that makes to stability etc is equally important.  Also making sure you create as little errors as possible "Stability is more important than speed" and as an added note: "but that does not mean you cannot learn to program both"

You know, I guess what I left out for the OP is this:

In a specific language class, you will learn a language technically.  Learning to program will take not only completion of the basic classes in your curriculum (which should include some classes on general programming practices), but a LOT of outside research and sweat on best practices and philosophy of problem solving in general. 

If your school has elective courses in general Philosophy (YES, I did mean that.  General Philosophy informs and enlightens all human endeavors) and, in particular, philosophy of problem solving, you should take them.

---

### Post by philinux on 2010-05-28
Moved to Recurring Discussions.

---

### Post by sydbat on 2010-05-28
> **thelionphoenix said:**
> Thanx everyone,

My choice of ubuntu was only due to it was the first linux distro i came across,

anywayz, if most of you r right then i m probably lucky:) 

By d way i dont mean to buy a mac only 4 linux, its only that i somehow for some reason hate windows, not sure why, but i do..

its odd u kno cuz since childhood i've been using microsoft prods,
may be thats the reason

And afterall a MAC is a mac, the most advanced operating system in the world, wouldn't u all agree..?? 

n thanx again.

> **lavinog said:**
> You should try and refrain from making these sort of statements on the forums.  They tend to lead to flame wars and stray off topic.

Also, similar statements can hurt your chances finding employment with some companies.Agreed.

To add - thelionphoenix, the way you write in "txt" speak tells me you are still very young. You need to write complete words and sentences to be taken seriously. If your first language is not English, people generally make allowances, but if you are from an English speaking country, writing like this only makes you appear uneducated and childish.

---

### Post by oleink on 2010-05-28
> **QIII said:**
> You know, I guess what I left out for the OP is this:

In a specific language class, you will learn a language technically.  Learning to program will take not only completion of the basic classes in your curriculum (which should include some classes on general programming practices), but a LOT of outside research and sweat on best practices and philosophy of problem solving in general. 

If your school has elective courses in general Philosophy (YES, I did mean that.  General Philosophy informs and enlightens all human endeavors) and, in particular, philosophy of problem solving, you should take them.

Yeah that is better than the way I put it.  In fact some companies will only take programmers who have taken these types of classes (Philosphy Psychology or any other class that has to do with reasoning based on any given ideal).  Thank you for expounding

---

### Post by libssd on 2010-05-28
> **thelionphoenix said:**
> Hey everyone.

Just joined this forum, and recently installed ubuntu.

(I am totally new to Linux!!:))

I plan to purchase a macbook, and was thinking to install ubuntu on that too...

So can someone tell me a little about ubuntu, and how much different is it from other linux distributions,and if i currently use linux just as a pc but further plan to practice computer programming **(m a computer student)** , web scripting and stuff, should i consider other distros like red hat or fedora.

someone smart enuff??
Pls Help!!
*[Ubuntu Pocket Guide and Reference]("http://www.ubuntupocketguide.com/download_main.html")*, by Keir Thomas. Free PDF download, well organized and written.

---

### Post by anewguy on 2010-05-29
+1 on conceptualizing a problem and seeing how to work out a solution.  This goes not just for programming (though here it is a must) but many other things in life.  Philosophy helps teach logic and logical approaches to problem solving.

+1 also on the language of choice normally doesn't matter (there are places for each language, and the closer to the guts of an OS the more prevalent C/C++).  As was mentioned, the entire point of any programming language, no matter what the choice, is being able to solve the problem.

It also helps if in your problem solving you learn how to break problems down into pieces until you come up with easy little pieces that add up to a whole that solves the problem.  People used to think that you had to make more complex programming statements to accomplish things, but the truth of the matter is that with modern optimizing compilers and the speed of processors, the amount of memory, etc., makes this a mute point for general programming.  System level programming and anything timing dependent are a different animal in that regard.  Thinking that way will lend itself to any modern programming language that uses classes and functions (don't most now ;) ).

Dave ;)

---

### Post by oleink on 2010-05-29
> **anewguy said:**
> +1 on conceptualizing a problem and seeing how to work out a solution.  This goes not just for programming (though here it is a must) but many other things in life.  Philosophy helps teach logic and logical approaches to problem solving.

+1 also on the language of choice normally doesn't matter (there are places for each language, and the closer to the guts of an OS the more prevalent C/C++).  As was mentioned, the entire point of any programming language, no matter what the choice, is being able to solve the problem.

It also helps if in your problem solving you learn how to break problems down into pieces until you come up with easy little pieces that add up to a whole that solves the problem.  People used to think that you had to make more complex programming statements to accomplish things, but the truth of the matter is that with modern optimizing compilers and the speed of processors, the amount of memory, etc., makes this a mute point for general programming.  System level programming and anything timing dependent are a different animal in that regard.  Thinking that way will lend itself to any modern programming language that uses classes and functions (don't most now ;) ).

Dave ;)

Yeah that is good stuff.  This is why I'm taking a class next semester most likely that is called "fundamentals of programming" but the basis isn't actually just learning programming it is a focus on problem solving which I believe is key to everything you do.

---

### Post by RobertoRecordo on 2010-06-03
Dive Into Python! The online tutorials, the book "Dive Into Python" and the language documentation all togeter are enough to get a motivated newb writing code. 
 
Don't be confused into thinking because it is a scripting language it is a toy.  It is a very modern object oriented laguage that is very fun to use. Oh, and fun, besides!
 
Dive in!

---

### Post by oleink on 2010-06-04
> **RobertoRecordo said:**
> Dive Into Python! The online tutorials, the book "Dive Into Python" and the language documentation all togeter are enough to get a motivated newb writing code. 
 
Don't be confused into thinking because it is a scripting language it is a toy.  It is a very modern object oriented laguage that is very fun to use. Oh, and fun, besides!
 
Dive in!

Yep.  It has adapted well over 30 years! haha.  Here is a link for python programming that makes me so happy

[http://code.google.com/edu/languages/google-python-class/]("http://code.google.com/edu/languages/google-python-class/")

---

### Post by RiceMonster on 2010-06-04
> **QIII said:**
> Red Hat is proprietary and it is not free. 

No, Red Hat is open source. This is why CentOS is able to exist.


As for BSD being written in Java, I have no idea where you got that idea. Free Open, and NetBSD are all written in C.

---

### Post by mickie.kext on 2010-06-04
> **jrothwell97 said:**
> 

Programming should be easy enough, as long as you stick to console programming. (If you're looking for something Visual Studio-like, dual-boot with Windows - this is not one of Ubuntu's strong points.)

What? Why do you spread such misinformation? 

Eclipse, NetBeans, InteliJ, QT Creator, Code::Blocks, Anjuta...

---

### Post by Shining Arcanine on 2010-06-05
> **thelionphoenix said:**
> Hey everyone.

Just joined this forum, and recently installed ubuntu.

(I am totally new to Linux!!:))

I plan to purchase a macbook, and was thinking to install ubuntu on that too...

So can someone tell me a little about ubuntu, and how much different is it from other linux distributions,and if i currently use linux just as a pc but further plan to practice computer programming **(m a computer student)** , web scripting and stuff, should i consider other distros like red hat or fedora.

someone smart enuff??
Pls Help!!

I usually avoid reading threads titled "Attention to all smarties...", but since this thread has received a great deal of attention, I decided to read it.

Anyway, I am a Computer Science student and I switched to Gentoo Linux in January. If you want to learn how to do programming, you are probably better off with Gentoo Linux. It is a much more developer oriented operating system and it will force you to learn how things work.

> **mickie.kext said:**
> What? Why do you spread such misinformation? 

Eclipse, NetBeans, InteliJ, QT Creator, Code::Blocks, Anjuta...

Having used Eclipse and Netbeans, which are usually considered to be the top two IDEs on Linux, as well as Visual Studio, I can tell you that Visual Studio is by far better than Eclipse and Netbeans. The only reason why you would want to do development using Eclipse or Netbeans is because they are better integrated with Unix systems. Aside from that, Visual Studio's editor and debugger are by far superior in terms of ease of use and general productivity.

Since I use Eclipse more than I use Netbeans, I would like to add that one major issue with it is that it tries to be a GUI wrapper for commandline tools, which tends to get in the way of doing things more than anything else. It is trivial to do things like making make files via the commandline and if you try to do the same thing with Eclipse to be able to have a nice GUI environment with an editor and a debugger, Eclipse will fight you all the way.

---

### Post by mickie.kext on 2010-06-05
> **Shining Arcanine said:**
> Having used Eclipse and Netbeans, which are usually considered to be the top two IDEs on Linux, as well as Visual Studio, I can tell you that Visual Studio is by far better than Eclipse and Netbeans. The only reason why you would want to do development using Eclipse or Netbeans is because they are better integrated with Unix systems. Aside from that, Visual Studio's editor and debugger are by far superior in terms of ease of use and general productivity.

Since I use Eclipse more than I use Netbeans, I would like to add that one major issue with it is that it tries to be a GUI wrapper for commandline tools, which tends to get in the way of doing things more than anything else. It is trivial to do things like making make files via the commandline and if you try to do the same thing with Eclipse to be able to have a nice GUI environment with an editor and a debugger, Eclipse will fight you all the way.

That is irrelevant. He practically said that you can't do any development in Linux beyond console editors. Which is not true, I use NetBeans and have zero problems with it. And then he recommended Visual Studio to someone who didn't even consider Visual Studio or Windows. The OP mentioned Mac and Linux, no Windows. So Visual Studio so good that you must trow out everything else and jump to Windows? I must say I do not miss Visual Studio one bit. Practically everything other than .NET and Microsoft Visual XXX languages are either impossible or plan suck in VS.

---

### Post by Shining Arcanine on 2010-06-05
> **mickie.kext said:**
> That is irrelevant. He practically said that you can't do any development in Linux beyond console editors. Which is not true, I use NetBeans and have zero problems with it. And then he recommended Visual Studio to someone who didn't even consider Visual Studio or Windows. The OP mentioned Mac and Linux, no Windows. So Visual Studio so good that you must trow out everything else and jump to Windows? I must say I do not miss Visual Studio one bit. Practically everything other than .NET and Microsoft Visual XXX languages are either impossible or plan suck in VS.

You appear to be trying to directly address someone in the third person. That makes it difficult to understand what you are trying to say.

---

### Post by oleink on 2010-06-05
These conversations are funny!

---

### Post by mickie.kext on 2010-06-05
> **Shining Arcanine said:**
> You appear to be trying to directly address someone in the third person. That makes it difficult to understand what you are trying to say.

I am saying that Visual studio have no place in this thread, and that it is not true that you can't develop on Linux because there is no Visual Studio on Linux.

---

### Post by Shining Arcanine on 2010-06-05
> **mickie.kext said:**
> I am saying that Visual studio have no place in this thread, and that it is not true that you can't develop on Linux because there is no Visual Studio on Linux.

You just used a triple negative. -_-

Attempting to make sense of that, I think you are trying to say that someone said that the lack of Visual Studio made it impossible to software development on Linux and then proceed to try to refute that. The only thing is that no one said that not having Visual Studio made it impossible to do software development on Linux. There was a comment that I made which was that the alternative IDEs are not as good as Visual Studio and that the original poster would be better off using the commandline to avoid having whatever IDE he tries fight with him.

Tell me, how much programming do you do on Linux and what languages do you use? Usually, I find that IDEs fight with me whenever I try to define my own make files and try to impose on me their automated makefile framework, which is a pain. I also find the debugging GUI more difficult to use. The functionality is there, but accessibility is an issue because of all of the clicking that is required. Eclipse requires that you click like nuts to view things while Visual studio just requires mouse overs to view things and you can view the values of variables inline with the text-editor, which is far superior to IDEs like eclipse.

---

### Post by jrothwell97 on 2010-06-05
> **mickie.kext said:**
> I am saying that Visual studio have no place in this thread, and that it is not true that you can't develop on Linux because there is no Visual Studio on Linux.

Let's get this straight.

Visual Studio is a tightly-integrated IDE which you can use to write software, in multiple languages, using the .NET framework.

Now, of course there are IDEs for Linux, and some of them are great: however, the development experience is neither tightly integrated nor convenient. Anjuta, Geany, Glade etc. all do a good job, but there's no "official" IDE for Ubuntu, and there's no official API, which means making careful decisions about which APIs, libraries and platforms to use.

To the OP, who seems relatively inexperienced and might be expecting something similar to Windows or Mac OS X (which *also* uses a managed API, Cocoa, and has a native development environment, Xcode) console programming is a good place to start. Writing a user-facing application on Ubuntu is very different to how it is on Windows or OS X.

---

### Post by thelionphoenix on 2010-06-05
Thanks Everyone....!!!!

That was a lot of information, i should say it again, A LOT!!

There is no way i will be able to digest it all (i feel nausea-tic)

Thanks anyway...

---

### Post by oleink on 2010-06-05
> **thelionphoenix said:**
> Thanks Everyone....!!!!

That was a lot of information, i should say it again, A LOT!!

There is no way i will be able to digest it all (i feel nausea-tic)

Thanks anyway...

Just look at the basic stuff and then look back at this post later.  Linux is an amazing place for programmers and ubuntu often makes it simpler (some would suggest Gentoo instead but yeah.)  There are so many languages to mess around with in linux.  I picked python just because I wanted to start light and I found it b4 the other simple languages

---

