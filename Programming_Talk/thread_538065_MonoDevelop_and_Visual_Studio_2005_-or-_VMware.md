---
title: "MonoDevelop and Visual Studio 2005 -or- VMware"
date: 2007-08-29
forum: Programming Talk
---

### Post by era86 on 2007-08-29
I am a student and class of mine requires using VS.NET and such for a project I am doing.  I was wondering how well the VS 2005 files "transfer" over to the MonoDevelop IDE.  Is it worth trying or should I just do a dual boot?

Also, an alternative I was thinking about was using VMWare and Visual Studio in XP.  I was wondering how people have faired using this method?  Will I run into any problems compiling projects and such?

Any input would be greatly appreciated!  Thank you so much!

---

### Post by cdenley on 2007-08-29
You can import VS projects into Monodevelop, but I don't think you can export back to a VS project. If your programs use Winforms, you won't have a form designer in Monodevelop.

---

### Post by era86 on 2007-08-29
So it seems like monodev is out of the question.  How about VMWare?  Will it run MSVS well?

---

### Post by pmasiar on 2007-08-29
> **era86 said:**
> using VMWare and Visual Studio in XP.  ...  Will I run into any problems compiling projects and such?


It depends what do you want to learn. Is it worth your time to learn VMWare?  If not, go dual boot. 

Most likely you **will** run into problems. For this kind of very specific question, ask at specialized VMWare forum (maybe someone can suggest good one - but nobody did, so you are on your own :-) ), and you will also test how responsible and civil/friendly they are.

I don't use VMWare and **personally** would prefer dual-boot.

---

### Post by fct on 2007-08-30
> **pmasiar said:**
> It depends what do you want to learn. Is it worth your time to learn VMWare?  If not, go dual boot. 

"Learning" VMWare is less than 30 minutes. It's actually quite nice, as long as you have the RAM and CPU to run the guest OS comfortably.

As far as VS2005 goes, a Windows XP installation with VS2005 should run fine on VMWare, performance apart.

---

### Post by Smygis on 2007-08-30
VirtualBox is a hell of a lot nicer then VMWare.

[www.virtualbox.org/](www.virtualbox.org/)

---

### Post by LaRoza on 2007-08-30
I like to use VirtualBox, as a VM, but I feel if you are doing a class you should use Windows, dual-boot, most likely.

---

### Post by kiv on 2007-08-30
This situation sucks.

I am in exactly the same position as era86.

I am about to start a degree in computing that uses C# & visual studio.
I have been using ubuntu for 8 months now on my pc. The other day i bought a laptop (core 2 duo, 2gb ram) for uni. I ripped vista out and installed ubuntu after about one week of having it. 

I love ubuntu & open source software. I would love there to be a solution to be able to create windows form based c# projects in ubuntu but it looks unlikely.

I have xp on virtualbox xp setup. But I don't see the point in this or dual booting as I might as well just install windows *shudders* if i'm going to be using it every day. My logic being that windows will do everything that I need to do and ubuntu will do some of the things, therefore, just have windows.

Only problem being .. I LOVE ubuntu. But logically it doesn't make sense to keep it unless I can use ubuntu & only ubuntu.

HELP ME!

---

### Post by LaRoza on 2007-08-30
> **kiv said:**
> 

Only problem being .. I LOVE ubuntu. But logically it doesn't make sense to keep it unless I can use ubuntu & only ubuntu.

HELP ME!

Dual-boot, make a third partition for sharing data.

---

### Post by kiv on 2007-08-30
> **LaRoza said:**
> Dual-boot, make a third partition for sharing data.

This is a good idea, but why would I bother?! I will be using my plaptop for programming c#, listening to music and internet browsing. Windows will be able to do all of these things .. ubuntu can do 2 out of 3.

I'm just wondering whether keeping ubuntu is worth the hassle of partitioning and dual booting on a new laptop. My heart says that I want to use ubuntu,. but my head is saying its only worth using ubuntu if I don't have to have windows installed.

---

### Post by pmasiar on 2007-08-30
make that shared partition FAT if you want peace of mind - NTFS is writable but IIRC still experimental - no docs, you know :-)

---

### Post by pmasiar on 2007-08-30
> **kiv said:**
> I'm just wondering whether keeping ubuntu is worth the hassle of partitioning and dual booting on a new laptop.

Depends what you want to learn. Value of knowing Linux is increasing, as many companies switch to it.

Besides, browsing web with Linux is safer, and learning linux is more fun.

---

### Post by LaRoza on 2007-08-30
> **kiv said:**
> This is a good idea, but why would I bother?! I will be using my plaptop for programming c#, listening to music and internet browsing. Windows will be able to do all of these things .. ubuntu can do 2 out of 3.

I'm just wondering whether keeping ubuntu is worth the hassle of partitioning and dual booting on a new laptop. My heart says that I want to use ubuntu,. but my head is saying its only worth using ubuntu if I don't have to have windows installed.

Interesting, I use Ubuntu for Programming more than Vista. Keep Ubuntu for yourselft. There isn't much hassle here. Shrink the windows partition, using the Windows tool, if it is Vista, GParted otherwise. Make partitions for ubuntu, swap, and the shared data. Install to those partitions.

---

### Post by kiv on 2007-08-30
> **pmasiar said:**
> Depends what you want to learn. Value of knowing Linux is increasing, as many companies switch to it.

Besides, browsing web with Linux is safer, and learning linux is more fun.

very true.. I'm racking my brains wondering what to do. 

I find xp works VERY well under virtualbox.. would this be a suitable solution?

Also is there  a way of enabling "drag & drop" and copy & pasting between ubuntu and xp on virtualbox? I have set up a shared folder but would like the drag-drop and c&P if possible.

---

### Post by Mirrorball on 2007-08-30
Why don't you talk to the teacher and ask him if using Monodevelop is OK for this class? At least he will be aware that some of his students prefer Linux to Windows. Ask him why not Java instead of C#. Java will make Linux and Mac users happy.

---

### Post by era86 on 2007-08-30
> **Mirrorball said:**
> Why don't you talk to the teacher and ask him if using Monodevelop is OK for this class? At least he will be aware that some of his students prefer Linux to Windows. Ask him why not Java instead of C#. Java will make Linux and Mac users happy.

He would laugh at me... he hates open source.  But no more about that...

I am thinking about just running it in VMWare.  I was just curious if there  were any problems with developing in a virtual machine.  For example, I tried running Gunbound (I know...) in VMWare using XP, but it didn't work.  Will I run into problems like this if I'm using VS2005?

---

### Post by tht00 on 2007-08-30
> **era86 said:**
> He would laugh at me... he hates open source.  But no more about that...

I am thinking about just running it in VMWare.  I was just curious if there  were any problems with developing in a virtual machine.  For example, I tried running Gunbound (I know...) in VMWare using XP, but it didn't work.  Will I run into problems like this if I'm using VS2005?

Games don't work in VMs very well... if at all.  They definitely should not be seen as the benchmark of usefulness of a virtual machine environment.

As long as you aren't going to need to code anything requiring graphical hardware acceleration (games) you should be fine.  The only other thing you probably couldn't do is to interface with devices attached to the computer... not something you'd do in an entry-level programming class.

Keep in mind that running a Virtual Machine will be like running the real thing.  It'll be a little slower (mostly because your CPU/RAM will be 'shared' between the host and guest OS) and you won't have advanced hardware features.

Give it a try and see how it goes.

---

### Post by era86 on 2007-08-31
Yea.  Well I'll be programming some web stuff.  Will that have many issues?  Just a web application in C#?

---

### Post by pmasiar on 2007-08-31
> **era86 said:**
>  Just a web application in C#?

Don't. C# was not designed to be language for flexible web apps: it is for writing efficient libraries.

Dynamically ("duck") typed "scripting" languages are **much** better choice for web apps. Python or Ruby have also excellent frameworks: Django and Turbogears for Python, and Ruby on Rails. You will be 20 times more productive than in C#, just check demo and tutorials.

---

### Post by emperon on 2007-09-01
MonoDevelop is an incomplete buggy software. Still it is OK once you gain a little knowledege about it. So if you are serious about linux mono development. MonoDevelop is a better choice than VS on VMWARE. Or you can go with vim + nant way.

Coming back to dynamic languages. you can run Boo (a static language with optional dynamic variables , Best of both worlds!) IronPython, IronRuby Ruby.NET so on

I've done some projects with Ruby on Rails. I still like ASP.NET better. For small projects Ruby on Rails is easier to setup. Since NHibernate , CastleWindsor stack is too hard to grasp at firsti But if you are doing large apps
 ASP.NET is better.

---

### Post by era86 on 2007-09-04
I ended up using VMWare and will be using MSVS 2003 on it to do my projects.  Thanks for everyone's help.  There are some issues though:

Resolution is blurry on my widescreen T61 in VMWare.  Is there a way to change the moniter type from standard to wide?

---

### Post by era86 on 2007-09-04
Solved the blurriness.  Go here to fix:

[http://ubuntuforums.org/showthread.php?t=300968](http://ubuntuforums.org/showthread.php?t=300968)

---

### Post by Smygis on 2007-09-05
> **era86 said:**
> Solved the blurriness.  Go here to fix:

[http://ubuntuforums.org/showthread.php?t=300968](http://ubuntuforums.org/showthread.php?t=300968)

VirtualBox >>>> VMware

[http://liquidat.wordpress.com/2007/09/03/virtualbox-15-released-with-seamless-windows-integration/](http://liquidat.wordpress.com/2007/09/03/virtualbox-15-released-with-seamless-windows-integration/)

:popcorn:

---

### Post by jenson on 2007-09-10
For the fact that my Toshiba laptop is about 2years+ old, I don't have the cutting edge hardware to support VirtualBox of VMware to do an excellent guest OS support, I dual-boot my laptop when I've decided to install Ubuntu, and I'm trying to shift over everything that I did on XP to Ubuntu, expect for things that I can only do with XP well, like ASP.NET programming, pen tablet, and etc. 

I would love to keep it dual-boot until a solution which is at reliable enough for me to do a complete switch =)

And if you have other gadgets that only come with drivers and software that only support or they are the partner of M$, then you would have hard time using all of them in Ubuntu, so that becomes the reason that I still dual-boot my laptop with Ubuntu and XP.

Regards,
Jenson

---

### Post by Sp4cedOut on 2007-09-10
Honestly I think you're setting your self up for a headache.  I'm not sure if the class will be using Windows-specific C# libraries or libraries not supported by Mono-develop, but if it does you'll be forced to switch.  Also, Virtual Machines also run into bugs (you've already hit one) which could hamper your progress.  I think learning programming enough to deal with without having to worry about the possible bug from Monodevelop or your VM or an unsupported library.  If you have a legal copy of Windows (like the one that came with your laptop) I think it'll be easier if you just use that for the class.   The programming you learn in that class will still be applicable to Linux, even if VS.NET is not.

---

### Post by jenson on 2007-09-10
> **Sp4cedOut said:**
> Honestly I think you're setting your self up for a headache.  I'm not sure if the class will be using Windows-specific C# libraries or libraries not supported by Mono-develop, but if it does you'll be forced to switch.  Also, Virtual Machines also run into bugs (you've already hit one) which could hamper your progress.  I think learning programming enough to deal with without having to worry about the possible bug from Monodevelop or your VM or an unsupported library.  If you have a legal copy of Windows (like the one that came with your laptop) I think it'll be easier if you just use that for the class.   The programming you learn in that class will still be applicable to Linux, even if VS.NET is not.

To put it simple, I think we should all say, Dual bot with your windows and Ubuntu since you also want to keep your Ubuntu for every other things than windows programming and etc, isn't it? :guitar:

---

### Post by eightballd on 2007-10-08
Aside from what has already been mentioned wrt 3D acceleration, there are no problems with developing from within a VM.   I have done this professionally for several months and am about to go back to it (because Vista sucks so hard).  The VM isn't going to cause any bugs with .NET (granted there is the possibility this will happen, but it is the same as there is a possibility that the next AMD processor will have a bug with .NET).

Seriously, VM is a much better option than dual booting (and I think VirtualBox is the way to go). 

I don't see how anyone can dual boot for any length of time....especially if you're trying to get work done.

My 2 cents

---

### Post by skeeterbug on 2007-10-08
> **emperon said:**
> MonoDevelop is an incomplete buggy software. Still it is OK once you gain a little knowledege about it. So if you are serious about linux mono development. MonoDevelop is a better choice than VS on VMWARE. Or you can go with vim + nant way.

Coming back to dynamic languages. you can run Boo (a static language with optional dynamic variables , Best of both worlds!) IronPython, IronRuby Ruby.NET so on

I've done some projects with Ruby on Rails. I still like ASP.NET better. For small projects Ruby on Rails is easier to setup. Since NHibernate , CastleWindsor stack is too hard to grasp at firsti But if you are doing large apps
 ASP.NET is better.

I would agree with this somewhat. Have you tried LLBLGen for .NET? It is a commercial ORM (very inexpensive). I have been using this for over 3 years now. When I changed jobs, I forced my new employer to purchase it (I think for around 200 bucks), and the development team to use it. His support is the BEST you will ever find, period. It has been that way for 3 years. If you can't stand NHibernate, check this out for sure.

For personal projects I use DJango and Python all the way.

---

