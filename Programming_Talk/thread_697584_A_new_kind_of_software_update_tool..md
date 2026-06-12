---
title: "A new kind of software update tool."
date: 2008-02-15
forum: Programming Talk
---

### Post by N'Jal on 2008-02-15
Hello all, I am writing a software update tool that is in no way designed to be a primary update tool, think of it as a way of separating default system software and user installed software. 

It will be able to install from deb's, source, shell scripts (for extra configuration) and so on. It's basically an app catcher, now while I know of one other project I found out about after beginning work on this it aim's to be more transparent where as my tool is designed to be more user centered.

Now if it's an app catcher it's obviously based upon RSS feeds, now my theory is say Pidgin comes out with a new release in between ubuntu releases, naturally I want it, and so do I imagine a lot of other people. So someone either builds a deb, writes a shell script or the developers just put an extra line of code in their RSS feed and this tool should be able to find a way to install it. By, grabbing the deb, running a shell script or manually downloading the source tarball and building the app itself. 

I am looking for some help, what people think of the idea, etc etc. It's written in C#, and build upon Mono (obviously) it's hosted here right now: [https://sourceforge.net/projects/warp](https://sourceforge.net/projects/warp)

I am aware my coding may not be the greatest in the world, so the project doubles as a learning experience for me, since I am being taught programming at university. Hence the asking for help, even if people don't want to contribute to actually building the app, if people can point out where I might be going wrong with my thinking I would appreciate it. Even your opinion would be a good thing, since I know if there would be interest once I get it into a reasonably good state.

Thanks,
Neil Munro

---

### Post by DrMega on 2008-02-15
Go for it. I had a similar idea a while ago, but my idea was limited to assist the user with compiling from source (it was going to try to identify uninstalled dependancies and go and get them - the really repetitive stuff that is tedious but not difficult).

I presume you've already had a good search of the net to see if there are any similar projects that you could work with?

---

### Post by N'Jal on 2008-02-15
See I want to incorporate your idea into my project, I always intended to, but right now might as well get all the basics done first. It always surprised me no-one ever wrote an application for installing from source tarballs. 

Yeah, I did look, and the one project is targeting Mac only and not written in C#, i chose C# because of the 'write once, run anywhere' idea, not coz it was quick and easy.

I intend on basically taking the task of installing new versions of software out of the users hands and making an automatic process they just click one button to do, as opposed to running a shell and all that stuff. My view is that Linux should be as graphical or terminal as the user requires, an area where this just has not happened yet is installing from source, so as is the nature, if something needs done, get on and do it. So I am.

I'm in the process of re-writing a lot of the code right now, the 0.1.2 release on the sourceforge site will be heavily changed once i release it. It's just taking a while.

---

### Post by DrMega on 2008-02-15
> **N'Jal said:**
> It always surprised me no-one ever wrote an application for installing from source tarballs. 

I suspect its because by the time a developer gets to know enough about Linux to feel comfortable compiling from source, they no longer see the point in such a tool for themselves.

I suspect you'd have a major job on your hands getting a one-click-wonder to work in all cases, but if you get get it to do 90% of the work in 90% of cases, and 100% in some cases, you'd have achieved something fantastic.

The last app I compiled from source took me about 2 hours work. They are no all like that, I've had some that worked straight away on the first compile attempt so it does vary significantly from package to package.

---

### Post by slavik on 2008-02-15
either way, go for it. personally, I do not like C#/Mono.

---

### Post by N'Jal on 2008-02-15
I am developing it, just need a bit of help sometimes, right now I have run into a bug, in vUpdateFeeds( ) the program I am in debugging mode right now and when i expect one GUID to be found, the program prints 4 or 7 messages that the guid in the text file has been found.

The code can be viewed here: [http://www.geocities.com/neil2earth/Main.txt](http://www.geocities.com/neil2earth/Main.txt)

If someone is able to point out where i might be going wrong I'd appricate it, I'm going to be continuing with this myself but if someone can point out if it's a silly mistake it would save me time.

---

