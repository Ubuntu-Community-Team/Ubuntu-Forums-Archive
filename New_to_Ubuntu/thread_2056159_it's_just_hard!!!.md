---
title: "it's just hard!!!"
date: 2012-09-10
forum: New to Ubuntu
---

### Post by jcka005 on 2012-09-10
hello..can someone help me understand ubuntu's different technical terms??
i mean,their meaning..like for example, what is linux? how do you explain that using simple terms?? i am trying to learn ubuntu by just reading informations from google..it don't really help me because it's hard for me to understand technical terms..thanks a lot..replies are very much appreciated..

---

### Post by Vaphell on 2012-09-10
strictly speaking linux is the name of the open source 'engine' (kernel) that manages the computer resources. The term is commonly used to describe both the engine itself and the user land (desktop environments, programs) on top of it (as in most modern distros), though such a combination should be called GNU/Linux (where Linux is the engine and GNU = all the tools on top) - unfortunately for purists almost nobody cares and linux it is ;-)

Distro (like ubuntu, debian, fedora, ...) is a 'mix tape' of kernel and selected programs that people behind the distro compile and try their best to make sure everything works out of the box and the user can be productive right off the bat (commonly used programs are preinstalled). Note that these are only defaults and you can change pretty much everything in the system, install other desktop environments and what not. Modern distros maintain repositories of compatible software that can be installed in 2 mouse clicks in an uniform way, without the hunting for linux equivalent of setup.exes (think AppStore)


Linux shares many similarities with unix and started as an open source alternative to it (afaik).

---

### Post by newb85 on 2012-09-10
> **jcka005 said:**
> hello..can someone help me understand ubuntu's different technical terms??
i mean,their meaning..like for example, what is linux? how do you explain that using simple terms?? i am trying to learn ubuntu by just reading informations from google..it don't really help me because it's hard for me to understand technical terms..thanks a lot..replies are very much appreciated..

I will try, although some terms aren't well solidified in my mind.  Someone else will probably come to the rescue.  Note that in the worlds of Windows and Mac, these things are usually all lumped together as the "Operating System".

*Linux* can mean many things.  To begin with, you should know that if you're using Ubuntu, your operating system is technically Gnu.  Gnu was developed to be an open-source OS styled after Unix--specifically, mimicking its modularity.  (That modularity is part of the reason for the confusion.)

A *Kernel* is the portion of your system that carries out the most basic functions of a computer.  You never interface directly with the kernel, but other parts of your system do.  The kernel can carry out all its functions without any other part of the system.

When Gnu was first developed, the kernel was a large hurdle.  For a while, Gnu was only run using the kernel from Unix.  Then Linus Torvalds (not part of the Gnu team) created his own open-source kernel, which he called Linux.  It became common for Gnu to be run with the Linux kernel before the Gnu team produced their own kernel.  Today, many distributions of the Gnu operating system still use the Linux kernel rather than the Gnu kernel, and Ubuntu is one of those distributions.

A *Distribution* is a set of packages that have been put together to comprise an entire operating system and desktop environment, with some common applications.  Distributions exist so that the user doesn't have to choose, collect, and put together all the different parts of the system.  Also, they act as a great starting point in describing your system, especially when you're seeking help on a forum.  Ubuntu is an example of a distribution.

The *Shell* is like the opposite of the kernel.  It's the portion of the operating system you interface with, and includes panels, launchers, your window manager, etc.  The default shell in recent versions of Ubuntu is Unity.  Prior to that, it was Gnome.  Shell and Desktop Environment are similar terms that are sometimes used interchangeably, although there are slight differences in meaning.


If people ask what OS you use, you could say Gnu (which is correct), but that wouldn't mean anything to most people.  Some would say Gnu/Linux.  Some would say Ubuntu/Linux.  Some would just say Ubuntu.


To the average person in everyday conversation, "I use Linux" means "I don't use Windows or Mac because I'm a smart computer geek."  Most don't realize that there are distributions of Gnu/Linux that don't require a smart computer geek to learn.

---

### Post by coldcritter64 on 2012-09-10
Here is a list of some of the common terms in Linux/Unix/computing, [[COLOR=Blue]http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/5026-glossary-common-linux-computer-terms.htm[/COLOR]l]("http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/5026-glossary-common-linux-computer-terms.html")

If something confuses me here, either an acronym or a term, I do a google search with,

> definition "insert acronym or terminology here" and within the first few links find a bit of information to describe what it is.

Example, [[COLOR=Blue]--definition linux--,[/COLOR]]("http://www.google.com/search?num=30&hl=en&safe=off&q=definition+linux&oq=definition+linux&gs_l=serp.12..0l2j0i30l8.556170.563916.0.567048.20.18.2.0.0.0.535.4765.1j6j2j7j1j1.18.0.les%3B..0.0...1c.1.VvGxxenWxx4") <--click the link to get a google search results page. Then follow the link to Wikipedia or [noparse]whatis.com[/noparse] for example, to get to the information you want. Can be used with any term or acronym. Good sites like wikipedia or [noparse]whatis.com[/noparse] will have further terminology used linked to an "explantion" of that word to help you.

Just takes a bit of practice and you will soon pick up on what is being discussed.  Cheers.

---

### Post by cortman on 2012-09-10
> **newb85 said:**
> II will try,

Nice write-up. Although I would make one minor correction-

> **newb85 said:**
> IMost people don't realize that both Mac and Android also implement the Linux kernel

Mac OS X uses a variant of the BSD kernel, which is Unix-like (as is Linux) but quite different from Linux.
Android uses a modified Linux kernel and the Dalvik virtual machine to run the Android OS.

---

### Post by jcka005 on 2012-09-10
thanks for the reply sir..or mam..
honestly, i didn't get most of your words..but i am trying to understand by reading it word by word :)
can you make it like this :
ubuntu = OS
wine = emulator for windows based programs
linux = ???
explain as simple as you can..sorry to disturb you :(
please do notify me if i have posted wrong words..

---

### Post by jcka005 on 2012-09-10
> **newb85 said:**
> I will try, although some terms aren't well solidified in my mind.  Someone else will probably come to the rescue.  Note that in the worlds of Windows and Mac, these things are usually all lumped together as the "Operating System".

*Linux* can mean many things.  To begin with, you should know that if you're using Ubuntu, your operating system is technically Gnu.  Gnu was developed to be an open-source OS styled after Unix--specifically, mimicking its modularity.  (That modularity is part of the reason for the confusion.)

A *Kernel* is the portion of your system that carries out the most basic functions of a computer.  You never interface directly with the kernel, but other parts of your system do.  The kernel can carry out all its functions without any other part of the system.

When Gnu was first developed, the kernel was a large hurdle.  For a while, Gnu was only run using the kernel from Unix.  Then Linus Torvalds (not part of the Gnu team) created his own open-source kernel, which he called Linux.  It became common for Gnu to be run with the Linux kernel before the Gnu team produced their own kernel.  Today, many distributions of the Gnu operating system still use the Linux kernel rather than the Gnu kernel, and Ubuntu is one of those distributions.

A *Distribution* is a set of packages that have been put together to comprise an entire operating system and desktop environment, with some common applications.  Distributions exist so that the user doesn't have to choose, collect, and put together all the different parts of the system.  Also, they act as a great starting point in describing your system, especially when you're seeking help on a forum.  Ubuntu is an example of a distribution.

The *Shell* is like the opposite of the kernel.  It's the portion of the operating system you interface with, and includes panels, launchers, your window manager, etc.  The default shell in recent versions of Ubuntu is Unity.  Prior to that, it was Gnome.  Shell and Desktop Environment are similar terms that are sometimes used interchangeably, although there are slight differences in meaning.


If people ask what OS you use, you could say Gnu (which is correct), but that wouldn't mean anything to most people.  Some would say Gnu/Linux.  Some would say Ubuntu/Linux.  Some would just say Ubuntu.


To the average person in everyday conversation, "I use Linux" means "I don't use Windows or Mac because I'm a smart computer geek."  Most people don't realize that both Mac and Android also implement the Linux kernel.  Also, most don't realize that there are distributions of Gnu/Linux that don't require a smart computer geek to learn.


***thankyou very much..it won't be easy to understand what you have just said, but i know i'll be able to cope with it..

---

### Post by jcka005 on 2012-09-10
> **coldcritter64 said:**
> Here is a list of some of the common terms in Linux/Unix/computing, [[COLOR=Blue]http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/5026-glossary-common-linux-computer-terms.htm[/COLOR]l]("http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/5026-glossary-common-linux-computer-terms.html")

If something confuses me here, either an acronym or a term, I do a google search with,

 and within the first few links find a bit of information to describe what it is.

Example, [[COLOR=Blue]--definition linux--,[/COLOR]]("http://www.google.com/search?num=30&hl=en&safe=off&q=definition+linux&oq=definition+linux&gs_l=serp.12..0l2j0i30l8.556170.563916.0.567048.20.18.2.0.0.0.535.4765.1j6j2j7j1j1.18.0.les%3B..0.0...1c.1.VvGxxenWxx4") <--click the link to get a google search results page. Then follow the link to Wikipedia or [noparse]whatis.com[/noparse] for example, to get to the information you want. Can be used with any term or acronym. Good sites like wikipedia or [noparse]whatis.com[/noparse] will have further terminology used linked to an "explantion" of that word to help you.

Just takes a bit of practice and you will soon pick up on what is being discussed.  Cheers.

***thanks very much too..i appreciate it very much..thanks guys! yeah, i will be practicing more of ubuntu to learn..

---

### Post by jcka005 on 2012-09-10
> **cortman said:**
> Nice write-up. Although I would make one minor correction-



Mac OS X uses a variant of the BSD kernel, which is Unix-like (as is Linux) but quite different from Linux.
Android uses a modified Linux kernel and the Dalvik virtual machine to run the Android OS.


thanks for the correction..might be useful..

---

### Post by Hadaka on 2012-09-10
Hi, to hopefully wrap you mind around Linux, or the differences between linux
and windows. Think of an automobile. With linux, the kernel is the engine, a very
adaptable engine, you can use a standard transmission or an automatic, or direct
drive,you can paint the car any color want, have any interior you want, any suspension,
wheels,brakeing system,stereo, you can pretty much design any type of automobile
you want all using the "linux" engine. with windows, you get what they make, and if
you want any add on's, you pay for them.If you attempt to remove the windows supplied
wheels,the engine wont start. And lastly linux is open source code, you can even change the kernel code....if you dare, and it's FREE ! The terminology will come to you in time
and with use. If you read a term you dont understand, highlight it,right click and google
it,read about it. Jump in and do stuff, if you break something, thats when you learn.

---

### Post by jcka005 on 2012-09-10
> **Hadaka said:**
> Hi, to hopefully wrap you mind around Linux, or the differences between linux
and windows. Think of an automobile. With linux, the kernel is the engine, a very
adaptable engine, you can use a standard transmission or an automatic, or direct
drive,you can paint the car any color want, have any interior you want, any suspension,
wheels,brakeing system,stereo, you can pretty much design any type of automobile
you want all using the "linux" engine. with windows, you get what they make, and if
you want any add on's, you pay for them.If you attempt to remove the windows supplied
wheels,the engine wont start. And lastly linux is open source code, you can even change the kernel code....if you dare, and it's FREE ! The terminology will come to you in time
and with use. If you read a term you dont understand, highlight it,right click and google
it,read about it. Jump in and do stuff, if you break something, thats when you learn.

***thanks for giving example :)

---

### Post by Kopkins on 2012-09-10
> **jcka005 said:**
> 
wine = emulator for windows based programs

It is hard to make terms that are so complex fit so simply into a basic definition.

WINE=**W**ine **I**s **N**ot an **E**mulator. WINE is a compatibility layer for windows based applications.
Linux=The type of operating system. For example, Ubuntu is one type of 'linux'. There are many others such as debian, gentoo, arch, chrunchbang.

Kopkins

---

### Post by jcka005 on 2012-09-11
> **Kopkins said:**
> It is hard to make terms that are so complex fit so simply into a basic definition.

WINE=**W**ine **I**s **N**ot an **E**mulator. WINE is a compatibility layer for windows based applications.
Linux=The type of operating system. For example, Ubuntu is one type of 'linux'. There are many others such as debian, gentoo, arch, chrunchbang.

Kopkins

***thanks for elaborating..sorry if i've posted wrong..could you give me some more terms? i have so much to ask, sorry to disturb..

---

### Post by GregA on 2012-09-11
There's just SO MUCH to tell about your question, but, maybe it's just best to know you won't be seeing these error messages in "Linux" . . 

>  Stay the patient course
Of little worth is your ire
The network is down.

>  Having been erased,
The document you're seeking
Must now be retyped.

>  Serious error.
All shortcuts have disappeared.
Screen. Mind. Both are blank.

>  Chaos reigns within.
Reflect, repent, and reboot.
Order shall return.

>  Windows NT crashed.
I am the Blue Screen of Death.
No one hears your screams.

>  Three things are certain:
Death, taxes, and lost data.
Guess which has occurred.

Greg

---

### Post by anewguy on 2012-09-11
BTW - BSD stands for Berkely Standard Distribution - it was sort of the "standard" for Unix for many years.

EDIT:  I'm showing my age, eh?

---

### Post by jcka005 on 2012-09-11
> **GregA said:**
> There's just SO MUCH to tell about your question

***yeah i know..but thanks for the reply sir/mam...

---

### Post by mastablasta on 2012-09-11
> **jcka005 said:**
> 
ubuntu = OS
wine = emulator for windows based programs
linux = ???

 
wine = wine is as explained compatibility layer. basically and in simplest terms it provides various windows files and some reverse engineered stuff so you can run some windows applications in Linux. it is not an emulator becuase it doesn't emulate windows.
 
Linux in itself is only kernel. kernel is the core of the operating system. in windows the kernel is NT4. in linux kernel version is important as opensource drivers are inside. so newer kernel = newer drivers
 
if you add various packages like programmes and various modules to kernel you get the operating system.
 
if you want to learn more about Ubuntu in a simple way i suggets reading Ubuntu manual (link in my signature)

---

### Post by newb85 on 2012-09-11
> **cortman said:**
> Nice write-up. Although I would make one minor correction-



Mac OS X uses a variant of the BSD kernel, which is Unix-like (as is Linux) but quite different from Linux.
Android uses a modified Linux kernel and the Dalvik virtual machine to run the Android OS.

Oops! I was misinformed.  Corrected.

---

### Post by grahammechanical on 2012-09-11
Here is something about Ubuntu that you have not asked about but it will be useful to know:

[https://wiki.ubuntu.com/DevelopmentCodeNames]("https://wiki.ubuntu.com/DevelopmentCodeNames")

Also, it is clear that you have limited understanding of English. Perhaps you would like support in another language?

[http://www.ubuntu.com/support/community/locallanguage]("http://www.ubuntu.com/support/community/locallanguage")

Regards.

---

### Post by cortman on 2012-09-11
> **jcka005 said:**
> ***thanks for elaborating..sorry if i've posted wrong..could you give me some more terms? i have so much to ask, sorry to disturb..

Please use Google. There's nothing we've given here that can't be found online in a simple search. Wikipedia, etc. are your friends. Search and read.

---

