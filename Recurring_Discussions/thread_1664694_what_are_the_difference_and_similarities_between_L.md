---
title: "what are the difference and similarities between Linux and Mac OS"
date: 2011-01-11
forum: Recurring Discussions
---

### Post by asifnaz on 2011-01-11
Originating from Unix both share common background . I know gnu/Linux is FOS and Mac OS X is closed .

But I think they are quite similar in file handling and resource utilizing .

what are differences and similarities between two...????

---

### Post by Paqman on 2011-01-11
Off the top of my head: Bash, permissions and a similar file structure. OS X uses an entirely different kernel though, so i'd be surprised if the way they tackled resources was that similar.

---

### Post by Spice Weasel on 2011-01-11
Mac OS is completely different from OSX.

OSX borrows from BSD and Nextstep, and the underlying system is free software (Read: Darwin). People are all OMFG APPLE ARE EVIL, but they have contributed the Linux print system, Webkit which is used in many different free web browsers and their underlying system, far more than most. 

Apple computers also use EFI instead of BIOS.

---

### Post by asifnaz on 2011-01-11
> **Spice Weasel said:**
> Mac OS is completely different from OSX.



How..?? I think only dock thing is from Next

---

### Post by Paqman on 2011-01-11
> **asifnaz said:**
> How..?? I think only dock thing is from Next

Mac OS was what Macs used before OS X, Apple developed it themselves, it has no Unix heritage. When OS X came along they chucked out the whole lot and started again with a BSD/Nextstep code base. You can't run apps written for Classic OS on OS X (although early versions of OS X did have a compatibility mode to ease the pain of transition).

---

### Post by 3rdalbum on 2011-01-11
> **Spice Weasel said:**
> People are all OMFG APPLE ARE EVIL, but they have contributed the Linux print system, Webkit which is used in many different free web browsers and their underlying system, far more than most.

CUPS existed long before Apple took it over, and Webkit is a fork of KHTML. Apple still contributes to Webkit: it introduces the security flaws in Webkit, and Google fixes them.

Really, there's so little that's similar. OS X has POSIX-style file handling and permissions underneath, but these are often obscured by userspace hacks. Much of OS X's real Unix-style stuff is obscured or mutilated by Apple's hack-happy engineers.

A lot of OS X's important systems (such as management of users) are not implemented in-kernel, but are add-on daemons. While I'm sure this has some benefits of stability, it also makes it a royal pain to do anything in OS X's recovery (single-user) mode because you need to start all the daemons by hand in order to actually do anything.

OS X does have an X11 server available for it, but as far as I know it's not by default. OS X doesn't use it.

Apple does include things like Python and Apache inside OS X, but these are often crippled versions; there exists the real possibility of security flaws in Apple's modifications. And finally, OS X is showing its age - there are a number of problems in the system design that open up security flaws, which can only be fixed by breaking existing applications.

Yep, OS X has more in common with Linux than Windows does; but there is not really any "shared heritage" between them.

---

### Post by kaldor on 2011-01-11
> **Spice Weasel said:**
> Mac OS is completely different from OSX.

OSX borrows from BSD and Nextstep, and the underlying system is free software (Read: Darwin). People are all OMFG APPLE ARE EVIL, but they have contributed the Linux print system, Webkit which is used in many different free web browsers and their underlying system, far more than most. 

Apple computers also use EFI instead of BIOS.

Yep... the evil Apple is the main developer behind what makes printers work on Linux.

Keep this in mind next time someone says they refuse to use Apple products :)

[quote=www.cups.org]Comments are owned by the poster. All other material is copyright 2007-2010 Apple Inc. All rights reserved. CUPS and the CUPS logo are trademarks of Apple Inc. All other trademarks are the property of their respective owners. Please report site problems to 'webmaster@cups.org'.[/quote]

---

### Post by DarkAmbient on 2011-01-12
reading this makes me wanna ask about "the history" about desktop effects and compositing window manager in GNU/Linux and OSX.

Got some various effects activated on my "music/movie computer". And some friends/ that notice them says something like "It's copied from Mac/OSX" or "it's just like OSX". 

But sometime ago (I think) I recall reading that desktop effects/behaviours in Linux & OSX both origin from something/somewhere else. Couldnt find the site where i read it now only... Anyway, does anyone know anything about this, I refuse to believe that compiz or similar is based on some Apple Comp. windows manager. :-/

---

### Post by MarcusW on 2011-01-12
> **DarkAmbient said:**
> reading this makes me wanna ask about "the history" about desktop effects and compositing window manager in GNU/Linux and OSX.

Got some various effects activated on my "music/movie computer". And some friends/ that notice them says something like "It's copied from Mac/OSX" or "it's just like OSX". 

But sometime ago (I think) I recall reading that desktop effects/behaviours in Linux & OSX both origin from something/somewhere else. Couldnt find the site where i read it now only... Anyway, does anyone know anything about this, I refuse to believe that compiz or similar is based on some Apple Comp. windows manager. :-/

I think we can be pretty sure it's not "based on" as in contains any code from it. But the obvious answer to things like "Apple did it first!" is "So?". IMO there's nothing wrong with being inspired by others, why reinvent the wheel? :)

---

### Post by KL_72_TR on 2011-01-12
> **asifnaz said:**
> Originating from Unix both share common background . I know gnu/Linux is FOS and Mac OS X is closed .

But I think they are quite similar in file handling and resource utilizing .

what are differences and similarities between two...????
Because LINUX is a friendly community and they are "COSA NOSTRA' :-(
In Linux everything is a helping hand. 
In Mac. they don't help you, they work in secret laboratories and than deliver in market a - LINUX with a different GUI...!!! :-O
Happy LINUX everybody :-)

---

### Post by MisterGaribaldi on 2011-01-12
Here's a good video which will at least explain the Mac OS X end of this question. [Inside the Mac OS X kernel]("http://video.google.com/videoplay?docid=-8486570970228087945#")

And, as Spice Weasel and Paqman have both said, Mac OS and Mac OS X are two completely different operating systems, just like the OSs used on Apple II-series computers and those used on Macs are completely different.[URL="http://video.google.com/videoplay?docid=-8486570970228087945#"]
[/URL]

---

### Post by rg4w on 2011-01-12
> **asifnaz said:**
> How..?? I think only dock thing is from Next
Look at the APIs.  NSView, NSArray, NSEnumerator, etc. - "NS" stands for NextStep.

---

### Post by asifnaz on 2011-01-12
> **KL_72_TR said:**
> Because LINUX is a friendly community and they are "COSA NOSTRA' :-(
In Linux everything is a helping hand. 
In Mac. they don't help you, they work in secret laboratories and than deliver in market a - LINUX with a different GUI...!!! :-O
Happy LINUX everybody :-)

I think you are right though I can not give any proof . what is "cosa nostra " btw

---

### Post by slackthumbz on 2011-01-13
OP said "Both originating from Unix..."

Sorry but this is just plain wrong. Linux is not a Unix derivative in any way. It doesn't contain any Unix (i.e BSD/AIX/HPUX/SVR4/etc) code. Linux is better defined as a Unix clone. It's built on the same principles and runs very similarly but it is not in anyway a derivative.

---

### Post by MisterGaribaldi on 2011-01-14
> **asifnaz said:**
> I think you are right though I can not give any proof . what is "cosa nostra " btw

It's a reference to the Italian Mafia.

---

