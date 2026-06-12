---
title: "Working on both Ubuntu and Windows"
date: 2009-10-02
forum: Programming Talk
---

### Post by Ultra Magnus on 2009-10-02
Hi,

It's not strictly a programming question but I was wondering if there is anyone else who has to work on windows at work but also does work at home on Ubuntu.

I'm looking for a way of taking the work I've done at work in windows and continuing as painlessly as possible on Ubuntu when I get home. It's not a problem of cross-platform programming, I don't use any MS specific stuff in my code so it all works. 

My problem is that up until now I've just been copying over files I've modified onto Ubuntu and vice versa; however, the larger the project becomes, the more hassle this is. I've been using monodevelop rather than makefiles recently but while it can create a solution, it can't create or read .vcproj files.

If you work on both windows and Ubuntu how do you get round this annoyance? Is there an easy way to sync files between windows and ubuntu. (Btw, I'm not system admin in the lab so I can't set up some sort of CVS server or anything so I'm pretty much stuck with copying files onto a memory stick or over the internet.)

Thanks,

James

---

### Post by scragar on 2009-10-02
[http://en.wikipedia.org/wiki/List_of_revision_control_software](http://en.wikipedia.org/wiki/List_of_revision_control_software)

Personally I like git, but the free hosting on github is only usefull if you don't mind it being a public project.

---

### Post by chrisjsmith on 2009-10-02
rsync over SSH would probably work.

We use an SVN server running over HTTPS as an apache module.

Are you building C#?

---

### Post by grayrainbow on 2009-10-02
You can check [https://one.ubuntu.com/](https://one.ubuntu.com/)
It's not design for source code stuff(and honestly I never use it by now, and not sure is it work with windows, but one can always run Ubuntu inside windows :) ), but seems to me as interesting technology for one man projects. You can also check google docs.
In any case it's way better to use hosting services specified on source code stuff :)

---

### Post by cszikszoy on 2009-10-02
> **grayrainbow said:**
> You can check [https://one.ubuntu.com/](https://one.ubuntu.com/)
It's not design for source code stuff(and honestly I never use it by now, and not sure is it work with windows, but one can always run Ubuntu inside windows :) ), but seems to me as interesting technology for one man projects. You can also check google docs.
In any case it's way better to use hosting services specified on source code stuff :)

Ubuntu one is ubuntu only, no cross platform.  If you don't mind your stuff being public, launchpad is a great solution.  Bzr is clean and easy to use on both windows and linux.  

Another option that I've used before is dropbox.  It's similar to ubuntu one (basically an online multi-computer file synchronization service), but it works very well on all platforms (osx, win and linux).  They give you 2gb free, which should be more than enough.  Actually, if you use [this link]("https://www.getdropbox.com/referrals/NTEyNDExOTQ5") you (and I) will get an extra 250 MB.

---

### Post by Can+~ on 2009-10-02
SVN, Git, Mercury, all are great alternatives.

[Google code]("http://code.google.com/projecthosting/") provides free svn hosting btw. And if you install TortoiseSVN on windows and [NautilusSvn]("http://code.google.com/p/nautilussvn/") on Ubuntu, you can work with the right click context menus.

---

### Post by matburton on 2009-10-04
> **Ultra Magnus said:**
> I've been using monodevelop rather than makefiles recently but while it can create a solution, it can't create or read .vcproj files

I use both Windows and Ubuntu (mainly Ubuntu) when programming at home, and I prefer to use IDEs where possible

If your problem is related to having to maintain both makefiles and vcproj files then I would give [[COLOR="Blue"]_premake4 _[/COLOR]]("http://industriousone.com/premake")a try

I've been extremely impressed by it since:
[LIST]
[*]it can generate project files for a range of IDEs on different platforms
[*]you get the bonus of only having to describe your projects once
[*]the format is declarative and friendly but based on Lua so you have the power of scripting built-in if you need it
[/LIST]

And yes, maintaining makefiles or IDE projects sucks

---

### Post by abhishek.malhotra35 on 2009-10-04
If you have issue of synchronizing files only, you can try svn or cvs. You can host your own servers or there are many servers available on net(both paid and free).

---

### Post by osgZach on 2009-10-04
if its a matter of keeping files synced and not over-writing new work with old stuff..  and you are working off  source files that are always the same, and you aren't keeping separate versions..   Could you just  carry them around on a USB stick ?    

I know I would consider keeping files in a single place like an external or USB stick that is portable and can be accessed from any OS, etc.   Of course  if your stick or drive fails your screwed...   But you could still just use the stick as your  version control?

Do your thing at work,  then drop the directory structure onto the stick.   Get home,  drop the DIR structure from the stick onto your working DIR on the PC.   When you're done for the night, just copy the DIR structure back onto the stick and you're ready to go again.   And if for some reason you lose net access you still have access to your most recent source and can remain productive.

Using this process with a cross-platform IDE that has a sync feature would be pretty nice too, although I'd prefer the manual way, just to make sure.

---

### Post by cszikszoy on 2009-10-04
> **osgZach said:**
> if its a matter of keeping files synced and not over-writing new work with old stuff..  and you are working off  source files that are always the same, and you aren't keeping separate versions..   Could you just  carry them around on a USB stick ?    

I know I would consider keeping files in a single place like an external or USB stick that is portable and can be accessed from any OS, etc.   Of course  if your stick or drive fails your screwed...   But you could still just use the stick as your  version control?

Do your thing at work,  then drop the directory structure onto the stick.   Get home,  drop the DIR structure from the stick onto your working DIR on the PC.   When you're done for the night, just copy the DIR structure back onto the stick and you're ready to go again.   And if for some reason you lose net access you still have access to your most recent source and can remain productive.

Using this process with a cross-platform IDE that has a sync feature would be pretty nice too, although I'd prefer the manual way, just to make sure.

Using dropbox (or ubuntu one if only ubuntu computers are being used) will solve exactly this problem, except you don't have to do *anything* manually.  No copying files 2 times a day, no carrying around a usb stick.

---

### Post by scragar on 2009-10-04
Be warned that dropbox is unencrypted and propietary. You have very little say on what happens to your data or the security of the connection. Do not use for anything you would be afraid to send via an unencrypted connection.

---

### Post by forrestcupp on 2009-10-04
I hate to say it, but if you're developing in C# at work with straight .NET, you'd be a lot better off doing your work at home using Windows with Visual C#.  It's not good to try to mix Mono with real .NET.  And that would solve your .vcproj file problem, too.

This is one area where it's not worth it to be stubborn.

---

### Post by TheStatsMan on 2009-10-04
> **scragar said:**
> Be warned that dropbox is unencrypted and propietary. You have very little say on what happens to your data or the security of the connection. Do not use for anything you would be afraid to send via an unencrypted connection.

Dropbox is encrypted, it is however the people that run dropbox that hold the encryption keys. This issue including encrypting dropbox yourself is discussed here.

[http://pragmattica.wordpress.com/2009/05/10/encrypting-your-dropbox-seamlessly-and-automatically/](http://pragmattica.wordpress.com/2009/05/10/encrypting-your-dropbox-seamlessly-and-automatically/)

---

### Post by Zugzwang on 2009-10-05
As already mentioned here, you can use a USB pen drive for synchronization.

I would recommend it in connection to some distributed version control system such as Mercurial, for example. You just synchronize your home and work computer with it each time you are leaving home/work and you'll be fine. I'm using this combination myself and I have to say that it works quite well. You just have to remind yourself to check in all new files to the repository before leaving. ;-)

This way, you don't even need internet access.

---

### Post by Ultra Magnus on 2009-10-06
Hi Thanks, for all the replys,

> I hate to say it, but if you're developing in C# at work with straight .NET, you'd be a lot better off doing your work at home using Windows with Visual C#.

Being research related I have quite allot of freedom in the tools I use, so I have been using standard C/C++ and QT for user interfaces so portability isn't so much of a problem.

> If your problem is related to having to maintain both makefiles and vcproj files then I would give premake4 a try

I've just had a look at premake, although haven't had time to try it yet. It looks like a good solution to the problem of maintaining the projects on different systems!

> As already mentioned here, you can use a USB pen drive for synchronization.

Unfortunately, due to admin staff losing confidential information all USB sticks are now encrypted and don't work with linux. Since my work doesn't involve such information I've been told it's acceptable to transfer work by email to get around this - this is what I've been doing so far, which as you can imagine is far from ideal! 

I would like to find a more secure way of transferring the data so I might try out DropBox, or if Ubuntu One becomes cross platform I may give that a go. I think the IT department would go mental if I created an svn, git etc server outside the Network. This probably goes for setting up ssh connections as well.

Anyway, thanks for all the ideas.

James

---

### Post by directhex on 2009-10-06
> **forrestcupp said:**
> I hate to say it, but if you're developing in C# at work with straight .NET, you'd be a lot better off doing your work at home using Windows with Visual C#.  It's not good to try to mix Mono with real .NET.  And that would solve your .vcproj file problem, too.

This is one area where it's not worth it to be stubborn.

The file extension for C# projects is "csproj", and MonoDevelop supports these projects.

The issue here is "vcproj", i.e. Visual C++, which hasn't had remotely as much time or effort thrown at it by the MonoDevelop folks (and does not use anything Mono-related at compile time anyway - Mono does not support anything C or C++-related)

---

### Post by lifestream on 2009-10-06
How about [http://aws.amazon.com/s3/]("http://aws.amazon.com/s3/")? It's ridiculously cheap. For me it was cheaper than buying my own domain and SSHing into it.
It's what I used when I was in the same situation as you. 
It's pretty easy, enter the domain name and the port, your username and password. Done. You can open and work with files just like they were local files. You don't have to do that whole FTP Download-Open-Work-Save-Upload thing.
(ok, to be honest, I don't remember if it uses SSH, but I believe it does. It's been a long time since I used it)


Another good open is Jungle Disk, but you'll have to install software for it.



Ofcourse, if you have a good web host, you can just ask for SSH access.

---

### Post by lifestream on 2009-10-06
How about [http://aws.amazon.com/s3/]("http://aws.amazon.com/s3/")? It's ridiculously cheap. For me it was cheaper than buying my own domain and SSHing into it.
It's what I used when I was in the same situation as you. 
It's pretty easy, enter the domain name and the port, your username and password. Done. You can open and work with files just like they were local files. You don't have to do that whole FTP Download-Open-Work-Save-Upload thing.
(ok, to be honest, I don't remember if it uses SSH, but I believe it does. It's been a long time since I used it)


Another good open is Jungle Disk, but you'll have to install software for it.



Ofcourse, if you have a good web host, you can just ask for SSH access.

---

### Post by forrestcupp on 2009-10-06
> **directhex said:**
> The file extension for C# projects is "csproj", and MonoDevelop supports these projects.

The issue here is "vcproj", i.e. Visual C++, which hasn't had remotely as much time or effort thrown at it by the MonoDevelop folks (and does not use anything Mono-related at compile time anyway - Mono does not support anything C or C++-related)

Interesting.  That's why I was confused.  The OP mentioned vcproj files, which I knew was for Visual C++, but he also mentioned MonoDevelop, which I thought was only for C#/Mono stuff.  I've never messed with MonoDevelop.

> **Ultra Magnus said:**
> 
Being research related I have quite allot of freedom in the tools I use, so I have been using standard C/C++ and QT for user interfaces so portability isn't so much of a problem.
If your company allows you that much freedom, you're pretty lucky.

---

### Post by directhex on 2009-10-06
> **forrestcupp said:**
> Interesting.  That's why I was confused.  The OP mentioned vcproj files, which I knew was for Visual C++, but he also mentioned MonoDevelop, which I thought was only for C#/Mono stuff.  I've never messed with MonoDevelop.

Monodevelop is an IDE for Vala, Java (IKVM-only, not pure Java), Boo, C, C++, C#, VB.NET. It's actually the most fully-featured Vala IDE, which is ironic.

---

### Post by forrestcupp on 2009-10-06
> **directhex said:**
> Monodevelop is an IDE for Vala, Java (IKVM-only, not pure Java), Boo, C, C++, C#, VB.NET. It's actually the most fully-featured Vala IDE, which is ironic.

Nice.  I'll have to check it out.

---

### Post by jpkotta on 2009-10-06
> **Ultra Magnus said:**
> 
I would like to find a more secure way of transferring the data so I might try out DropBox, or if Ubuntu One becomes cross platform I may give that a go. I think the IT department would go mental if I created an svn, git etc server outside the Network. This probably goes for setting up ssh connections as well.

Can you use an ssh *client*?  You could set up an SCM server on your home machine and push your changes at work up to it, and pull changes you made at home down to work.  I prefer Mercurial, and one of the reasons I initially picked it is how well it works on Windows, but you could do this with git, svn, etc.  If you use hg, it's enough to create the repo and have an ssh server running.  You also probably want a dynamic DNS service like no-ip so you don't have to figure out your home IP address, and you'll have to forward a port if you have a NAT router.  You can also set up an https server with just about any SCM, but it's a bit more complicated.

---

### Post by cszikszoy on 2009-10-07
> **jpkotta said:**
> Can you use an ssh *client*?

Any IT department that remotely monitors network traffic would go crazy over this.  Depending on the industry you work for, you could get in a ton of trouble for this.  Where I work there are tons if import / export controls and sending any type of encrypted traffic to an external address would certainly look *very* suspect.

---

### Post by jpkotta on 2009-10-07
> **cszikszoy said:**
> Any IT department that remotely monitors network traffic would go crazy over this.  Depending on the industry you work for, you could get in a ton of trouble for this.  Where I work there are tons if import / export controls and sending any type of encrypted traffic to an external address would certainly look *very* suspect.

A valid point, but here's the part of OP's post that I didn't quote before:

> Unfortunately, due to admin staff losing confidential information all USB sticks are now encrypted and don't work with linux. Since my work doesn't involve such information I've been told it's acceptable to transfer work by email to get around this - this is what I've been doing so far, which as you can imagine is far from ideal!

Also OP, if you can't do as I suggested above, you can also export Mercurial changesets as a file with "hg bundle" (again, I'd be surprised of git and others couldn't do this as well).

The reason I'm pushing for an SCM-based solution so hard is because you're syncing code -- you should probably be using an SCM anyway.

---

