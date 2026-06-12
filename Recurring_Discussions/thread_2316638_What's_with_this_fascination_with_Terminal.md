---
title: "What's with this fascination with Terminal?"
date: 2016-03-09
forum: Recurring Discussions
---

### Post by stevemid on 2016-03-09
I love Ubuntu; I bought a new machine to run it on. It's better than Windows. It's mostly because I'm old enough to remember the hegemony of IBM, then Microsoft, then Google and Apple.  I just switched off my Mac Mini for the last time.  I first used Ubuntu in 2006 to give life to an old Windows machine that I moth-balled to move on to Apple's first Intel machine.   But I'm even more 'experienced' than that.   I used the original DOS (a:=b: *.*) and recall how proud I was to be able to drop out of those crappy early versions of Windows to "get stuff done" in the command line.  But that was 35 years ago! Even Microsoft got away from that.  What is it with this continuing encouragement for the use of Terminal? Yes it's incredibly powerful - elegant even.  But in order to solve most little problems should an ordinary user have to:
[LIST]
[*]Research the forums
[*]Find and answer that 'may' be correct
[*]Copy lines of incomprehensible command structure 
[*]Paste these into Terminal, and 
[*]Execute, many times with the Sudo prefix?
[/LIST]

Granted, I've always been able to get to a solution via this process.  Granted, I've never been led to do something harmful.  Granted, this is FREE. And granted, I'm not paying for licenses or support to enrich some future Bill Gates. Oh...have I  answered my own question?

---

### Post by oldfred on 2016-03-09
I have not used Windows since XP over 5 years ago. 
So to fix my one Windows 10 system that is only used for streaming video in browser, it gives low memory.

[LIST]
[*]Research the forums
[*]Find and answer that 'may' be correct
[*]Copy lines of incomprehensible command structure
[*]Paste these into Terminal, and
[*]Execute, many times using Admin terminal.
[*]Find that instructions did not work my version
[/LIST]

Not that it is any different.

And with Ubuntu there are many flavors. So we cannot easily post instructions for each DE or gui as they all are different, where terminal for underlying system is the same.

You cannot copy gui instructions from forum into your system. For Windows I litterally had to look up commands in Ubuntu's Firefox to find how to fix Windows. And many had older Windows Gui and screen I wanted was not where they said it was. And once I got to the actual screen I wanted it looked almost identical to the XP screens. Memory not as good as it was, so maybe not identical.

---

### Post by goofprog on 2016-03-09
Nothing is absolutely free.  There is a cost.  The cost is time.
Anyways..the terminal is important because there are still terminal based applications.  Why?  It is linear in development.  Programming in a GUI usually is not linear and usually has to play nice with the message system in order to work correctly.

---

### Post by ajgreeny on 2016-03-09
As oldfred says it is all the different versions of GUI that can make it so much easier to give answers using terminal commands.

Ask me how to do many things using Ubuntu with unity and I simply can not answer you as I so seldom use it; I use Xubuntu with XFCE-4.12 and if I answer your question in GUI terms for that it will be useless info for a unity user.

---

### Post by Habitual on 2016-03-09
Terminal is just a GUI'fied console.

---

### Post by Bashing-om on 2016-03-09
stevemid; Well ...

My take.

CLI is universal across all linux distributions . And as well most of  bash relates as well . There is nothing you can do in the GUI that can not be done in terminal. The reverse may not be so true ( albeit, there are some things easier done in the GUI).

Now me, I came up in this world in terminal long before there was a GUI, so my mind is set to a terminal mentality. I work from terminal because it is faster and my comprehension of the what and why is deeper .

My work system is terminal, and IF I want I can activate a GUI. That GUI is but a layer on top of my operating system and is but another tool to get the job done.

caveat; Working a large database sure is nicer in a GUI ! Look and then touch.

Can not know the power of linux
[INDENT][INDENT]'til you have some familiarity and comfortability with the terminal
[/INDENT][/INDENT]

---

### Post by buzzingrobot on 2016-03-09
I don't think there's a fascination with the terminal.  Linux media tend to over-represent it because they're so fond of publishing little snippets that most people will copy blindly without ever making an effort to know what's going on. 

Using a competent well-designed and well-maintained Linux desktop certainly does not require use of the terminal. (It's the "well-maintained" part many people tend to abuse, I think.)

When you enter and execute commands in a terminal, you are using a program that deliberately emulates the only practical interface in existence when Unix was created: a screen that could only display characters. Both then and now, command line entries adhere to syntax rules and structure that permit them to be accurately interpreted by the program that acts on them -- the shell, usually Bash in Linux.  Like any GUI interface, the shell parses out commands, options, etc., and dispatches the result to the appropriate tool, waits for a response, and acts on that response.

Using the shell effectively requires time and effort comparable to what you need to acquire useful expertise in any other computer language. Learn a litte, and you can do a little (like enter commands in a terminal window). Learn a lot, and you can do a lot.

So, impressions that things are "incomprehensible" are misplaced.  Would you look at a few thousand lines of kernel code and expect to find them comprehensible if you weren't well acquainted with C?

You can't gain a solid knowledge of Bash by sampling forum posts when something goes wrong.   You need to get your hands on some books, or some book-length sites, and study.

---

### Post by QIII on 2016-03-09
The terminal is universal.  It's the *lingua franca*.

A DE is specific.  It's a language of your native country.

If you are in an open air market in Outer Bumblefritters looking for cough syrup, you don't speak Bumble and nobody there speaks English, it is sure nice if everyone knows a common language.

---

### Post by grahammechanical on 2016-03-09
One of the things that drew me to Ubuntu was the reputation that computer journalists gave Ubuntu as being for ordinary people. I have not been disappointed these last 9 years. Linux on the other hand does deserve its reputation as being for geeks.

Ubuntu limits the amount of modification that a user can do to the user interface. But there is a way around that. We can install GUI utilities that will let us tweak the UI even to the point of messing it up. And then there is, dare I say it? The terminal, which gives us access to the underlying Linux.

I do not agree with your conclusions about Ubuntu at all. Over the last 9 years I have learnt a bit about Ubuntu & Linux (including some commands). I did that because I wanted to give something back for the gift of Ubuntu by giving help on this forum. I did not need to learn this stuff in order to use Ubuntu everyday.

Regards

---

### Post by vasa1 on 2016-03-09
Smells very much like this recent one: [Is command line usage really better than GUI? Terminal vs GUI megathread]("http://ubuntuforums.org/showthread.php?t=2314057") and many, many others.

---

### Post by cariboo on 2016-03-09
Again? Moved to recurring.

---

### Post by SeijiSensei on 2016-03-10
I manage servers, usually remotely.  For that I use SSH and the shell.  I've been building and managing Linux servers for two decades now.  The GUI and desktop Linux came much later in my experience.

Unix was designed to run in text-mode and to be administered in text-mode.  That's why so many programs have plain-text configuration files.  If you're going to manage a DNS server running BIND9, you need to know how to edit named.conf and create a zone file.  It just comes with the territory.

---

### Post by gordintoronto on 2016-03-10
It's only marginally relevant to this discussion, but if you are going to manage Windows Server 2012 R2, you will need to use the terminal quite frequently. There are even thousands of downloadable terminal scripts to perform specific tasks.

---

### Post by user1397 on 2016-05-18
> **vasa1 said:**
> Smells very much like this recent one: [Is command line usage really better than GUI? Terminal vs GUI megathread]("http://ubuntuforums.org/showthread.php?t=2314057") and many, many others.
As the creator of that thread I feel like I should chime in on this one.

I agree OP, whether people want to admit it or not, there is some level of fascination with the terminal in the linux world.  You have higher degrees of it in the more manual distributions like Arch and Gentoo, while there's less in distros like Ubuntu or openSUSE.  

Now, before I get burned at the stake, NO I'm not saying the CLI is not useful or should never be used or anything idiotic like that.  Of course the CLI has its place, and it is invaluable for power users, server admins, IT professionals, etc.  

I, personally, am of the opinion that one of the things all Linux distributions lack is consistent GUIs for settings/configs/options in general.  Some distributions are far better at this than others (and many explicitly state this is not one of their goals, which is fine).  As others have said in this thread, this can be attributed to many factors such as the very nature of open-source software (e.g. forking), maintaining software over long periods of time (maintainers come and go, and sometimes just leave forever and no one picks up their slack), all the different desktop environments and their different GUIs (each uses different programs, libraries, toolkits), etc.

On the other hand, Ubuntu is a bit of an exception because it IS trying to gain as much marketshare is possible, and tries to "dumb things down" for the average user because that is their target market.  No other commercially-backed distro has as much ambition as Ubuntu, so it is on Ubuntu to try to be as easy to use as possible for as many people as possible.

So you can say whatever you want, sometimes even on Windows you'll have to follow a guide online where it asks you to open up the command prompt, but the chance of a guide asking you to use the CLI is WAY smaller than an ubuntu guide.

So I think that one of the things Canonical should focus on is to make most things (not everything obviously) configurable via GUI, because nothing turns a new user away as much as opening a terminal (can't ignore this fact).  It already does have many, many functions available via GUI (although some are not installed by default so a new user would not know to download it), but it could be more complete.

P.S.  Yes these are my opinions, please spare me the "well if you think this is how it should be then contribute to Ubuntu" ...I understand that, but I personally don't care enough to do it.  I am merely interested in this subject and enjoy opining and discussing it; I'm not trying to start a "flame war" or think myself above other's opinions.  It can be exhausting to have to state all of these obvious things in posts like these, but from experience, if I don't then people assume the worst and treat you like an idiot so I have to state the obvious.

Regards.

---

