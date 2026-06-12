---
title: "novice, non-programmers, read before install"
date: 2013-08-10
forum: Recurring Discussions
---

### Post by marcretired on 2013-08-10
I just went thru a week of trying to figure out what went wrong with Ubuntu.
first of all, before doing anything go here [http://www.ubuntu.com/certification/desktop/](http://www.ubuntu.com/certification/desktop/)
if you don't see your computer on the list, forget ubuntu.  (if you bought a toshiba with win8 and don't like win8 do a google search for "Classic Shell', that's a safe, compatible little program that turns ugly win8 into win7, easy.)
of the hundreds of messages I've scoured thru to find some info and pointers, this is one of my favorites--
[http://answers.yahoo.com/question/index;_ylt=AjG.LBurv3gC04eOsRTVSFLq1KIX;_ylv=3?qid=20100908121540AAyaG0r](http://answers.yahoo.com/question/index;_ylt=AjG.LBurv3gC04eOsRTVSFLq1KIX;_ylv=3?qid=20100908121540AAyaG0r)
it starts with, "I want to access to a wireless connection in a PC with linux (ubuntu 10.04). But I can't find any connection."
Rickie answers with, "Weeks after weeks ppl keep asking this question. The answer is because you are using a free linux that mostly relies on opensource technology and insanely restrictive laws in the USA do not allow to integrate proprietary drivers in [COLOR=#366388]open source technology[/COLOR].
Ubuntu is a cute little linux but a nightmare for ppl using wifi, forget about installing the drivers yourself unless you are a programmer".
then Alessandro T gives a pointer to the Ubuntu Forums and some links for programmers like, [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
good luck.

---

### Post by ikt on 2013-08-10
> **marcretired said:**
> of the hundreds of messages I've scoured thru to find some info and pointers, this is one of my favorites--
[http://answers.yahoo.com/question/index;_ylt=AjG.LBurv3gC04eOsRTVSFLq1KIX;_ylv=3?qid=20100908121540AAyaG0r](http://answers.yahoo.com/question/index;_ylt=AjG.LBurv3gC04eOsRTVSFLq1KIX;_ylv=3?qid=20100908121540AAyaG0r)
it starts with, "I want to access to a wireless connection in a PC with linux (ubuntu 10.04). But I can't find any connection."
Rickie answers with, "Weeks after weeks ppl keep asking this question. The answer is because you are using a free linux that mostly relies on opensource technology and insanely restrictive laws in the USA do not allow to integrate proprietary drivers in [COLOR=#366388]open source technology[/COLOR].
Ubuntu is a cute little linux but a nightmare for ppl using wifi, forget about installing the drivers yourself unless you are a programmer".
then Alessandro T gives a pointer to the Ubuntu Forums and some links for programmers like, [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
good luck.

Ubuntu 10.04 is 3 years old, linux moves fast, the wireless on my laptop is supported out of the box. Have you tried Ubuntu 13.04?

---

### Post by prodigy_ on 2013-08-10
> **marcretired said:**
> Rickie answers with, "Weeks after weeks ppl keep asking this question. The answer is because you are using a free linux that mostly relies on opensource technology and insanely restrictive laws in the USA do not allow to integrate proprietary drivers in [COLOR=#366388]open source technology[/COLOR].
Ubuntu is a cute little linux but a nightmare for ppl using wifi, forget about installing the drivers yourself unless you are a programmer".
Now the only question is who the hell is Rickie and why does he talk about something he doesn't have a clue about? :)

Proprietary drivers aren't included in Linux kernel because Linux tries its best to be open source. There's no law that would prohibit kernel maintainers to integrate binary blobs but any such blob is essentially a "black box" - you never know what *exactly* it does and what bugs it could introduce.

And while getting Wi-Fi to work can take some effort sometimes, I have 3 *different* laptops running Linux and on all of them Wi-Fi worked out of the box. It mostly depends on Wi-Fi brand. Intel works like a charm, for Atheros and Broadcom you often need to edit some config files. Less known brands may not have Linux drivers at all.

---

### Post by wildmanne39 on 2013-08-10
I work with wireless issues and in most cases the wireless will work with a little tweak if not out of the box.

You are talking about Rickie's comments made about 10.04, and we are at 13.04 and while it is not perfect it has come a long way.

If you ask for help in the networking section there is usually someone there that can help get your wireless working.

How much easier could it be then to copy and paste commands that someone asks you to into the terminal to get your wireless working?

You do not even have to understand them or rewrite them.

Also when I started I was a windows user and had never seen linux, I am not a programmer that is way over my head but programming is not needed to get wireless working.

---

### Post by agillator on 2013-08-10
marcretired, there is obviously something you do not understand about Linux of any flavor vs. Windows. With Windows you are fairly well limited to doing what Microsoft, i.e. Bill Gates, wants you to do in the way they want you to do it. Linux, on the other hand intends you for the most part to do things the way you want to. With that power comes a certain amount of complexity and responsibility. The large, large majority of problems I have heard about installing Linux or Ubuntu arise from operator error or just simply not reading the instructions. To someone totally new and not particularly conversant with computers this may seem overwhelming, but most find it really isn't. The are many people here and elsewhere willing to help if you know how to pose a question. People are even willing to help you learn how to pose a question so others can help you. But, if you are afraid of the complexity and are not willing to take the responsibility for the way things work, please do not blame Linux or Ubuntu. That is generally not where the fault lies. In that case, and you are certainly not alone, you will be much happier in the more limited and confining world of Windows.

---

### Post by Boab1993 on 2013-08-10
> **marcretired said:**
>  

"forget about installing the drivers yourself unless you are a programmer".



As myself a programmer, i can say this is totally untrue.

When it comes to ubuntu, im about as amateur as it gets, the workings of an OS have very little to do with the programming unless you do it yourself, or put some research into. The programming does all the work in the background, thats what its there to do, you don't see it and barely touch it, what you do is use the tools that the people who did program ubuntu have made.

The people who know how to use these tools are the valuable ones when it comes to resolving problems with wifi, or resolving anything else in ubuntu and they are a damn sight better at it then i am.

---

### Post by prodigy_ on 2013-08-10
> **agillator said:**
> With Windows you are fairly well limited to doing what Microsoft, i.e. Bill Gates, wants you to do in the way they want you to do it.

You're taking it a bit too far. Windows is a general purpose OS, pretty much like common Linux distros. It's very hard to find a typical end user task that no Windows application could possibly perform. Advanced scripting is also possible, especially now with VBScript and PowerShell.

Windows does have limitations. It's closed source, so you cannot easily hack kernel or system libraries. It doesn't have a realtime kernel. It's not suitable (except Windows Server) for supercomputers or computer clusters in general. But those are special and rare cases. I've been using Windows for 20 years and the only serious obstacle I can recall is HDD SMART monitoring being blocked by drivers in fakeRAIDs.

---

### Post by marcretired on 2013-08-11
hehehehehehe, starting to look like a union meeting up in here.  
I just went thru an unpleasant experience and thought I'd leave a message for other computer illiterates to read and think about before venturing into ubuntu land.   the takeaway was, "first of all, before doing anything go here [http://www.ubuntu.com/certification/desktop/](http://www.ubuntu.com/certification/desktop/)
if you don't see your computer on the list, forget ubuntu."    good luck, happy computing.

---

### Post by Morbius1 on 2013-08-11
> **marcretired said:**
> "first of all, before doing anything go here [http://www.ubuntu.com/certification/desktop/](http://www.ubuntu.com/certification/desktop/)
if you don't see your computer on the list, forget ubuntu."    good luck, happy computing.
My computer is not on the list. The manufacturer of my computer isn't even on the list. I am running Xubuntu 12.04 without issue.

Please advise.

---

### Post by kurt18947 on 2013-08-11
> Originally Posted by **marcretired**                     [[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=12752871#post12752871")                                  "first of all, before doing anything go here [http://www.ubuntu.com/certification/desktop/](http://www.ubuntu.com/certification/desktop/)
if you don't see your computer on the list, forget ubuntu."    good luck, happy computing.



> 
                                                                                    [**[COLOR=#000000]Morbius1[/COLOR]**]("http://ubuntuforums.org/member.php?u=982144")
My computer is not on the list. The manufacturer of my computer isn't  even on the list. I am running Xubuntu 12.04 without issue.

Please advise.                 

:lolflag:

---

### Post by Rob Sayer on 2013-08-11
> **marcretired said:**
> hehehehehehe, starting to look like a union meeting up in here.  

Ah, ad hominem arguments.  The refuge of the ill informed.

I>  just went thru an unpleasant experience and thought I'd leave a message for other computer illiterates to read and think about before venturing into ubuntu land.   the takeaway was, "first of all, before doing anything go here [http://www.ubuntu.com/certification/desktop/](http://www.ubuntu.com/certification/desktop/)
if you don't see your computer on the list, forget ubuntu."    good luck, happy computing.

I've installed ubuntu/xubuntu/kubuntu on several machines.  Only had any significant problems with one of them.

That one, BTW, is an "acer aspire one" netbook.  Which is one of the 'certified' machines on that list, which is clearly not exhaustive.

It simply isn't true you need to be a programmer to configure ubuntu, though with some other linux distros you will want to have some skills.

I will fully acknowledge you should be willing to look under the hood to install ubuntu.  But that's not the same as needing programming skills, and the tech support on this forum is actually better than with many OS's that you *pay* for.

I have one laptop which still has a windows 7 partition on it.  It's feeling very neglected.  I don't use windows unless there's something I need to do for which there isn't a linux solution.  That hasn't been a problem for me.  But I'll admit that if you need to do powerpoint presentations, or use photoshop, you'll still want a windows partition.  But linux just works better, and it's the most secure OS anywhere.

---

### Post by oldos2er on 2013-08-11
> **marcretired said:**
> I just went thru a week of trying to figure out what went wrong with Ubuntu.
first of all, before doing anything go here [http://www.ubuntu.com/certification/desktop/](http://www.ubuntu.com/certification/desktop/)
if you don't see your computer on the list, forget ubuntu.  (if you bought a toshiba with win8 and don't like win8 do a google search for "Classic Shell', that's a safe, compatible little program that turns ugly win8 into win7, easy.)
of the hundreds of messages I've scoured thru to find some info and pointers, this is one of my favorites--
[http://answers.yahoo.com/question/index;_ylt=AjG.LBurv3gC04eOsRTVSFLq1KIX;_ylv=3?qid=20100908121540AAyaG0r](http://answers.yahoo.com/question/index;_ylt=AjG.LBurv3gC04eOsRTVSFLq1KIX;_ylv=3?qid=20100908121540AAyaG0r)
it starts with, "I want to access to a wireless connection in a PC with linux (ubuntu 10.04). But I can't find any connection."
Rickie answers with, "Weeks after weeks ppl keep asking this question. The answer is because you are using a free linux that mostly relies on opensource technology and insanely restrictive laws in the USA do not allow to integrate proprietary drivers in [COLOR=#366388]open source technology[/COLOR].
Ubuntu is a cute little linux but a nightmare for ppl using wifi, forget about installing the drivers yourself unless you are a programmer".
then Alessandro T gives a pointer to the Ubuntu Forums and some links for programmers like, [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
good luck.

Please don't spread FUD. If you're seeking support, post a request in the support areas of the forum.

Closed.

---

