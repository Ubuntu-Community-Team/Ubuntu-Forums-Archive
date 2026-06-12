---
title: "Linux is not based on Unix?"
date: 2008-08-04
forum: Other OS Talk
---

### Post by icett on 2008-08-04
Just read on wikipedia and come to conclusion that GNU Linux is an entirely different OS from Unix, not based on Unix, not an extention of Unix, having no connection with Unix. But it is Unix like. Is that true? I dont have anything against Linux if it is an entirely different OS from Unix but is Unix like, I think its good that Linux in itself is an OS as strong and stable as Unix is but just want to clarify.:)

---

### Post by Bachstelze on 2008-08-04
GNU's Not Unix.

---

### Post by kostkon on 2008-08-04
> **icett said:**
> Just read on wikipedia and come to conclusion that GNU Linux is an entirely different OS from Unix, not based on Unix, not an extention of Unix, having no connection with Unix. But it is Unix like. Is that true? I dont have anything against Linux if it is an entirely different OS from Unix but is Unix like, I think its good that Linux in itself is an OS as strong and stable as Unix is but just want to clarify.:)
True.

ADDED: for Unix based OSes check the various BSDs.

---

### Post by MaxIBoy on 2008-08-04
Linux was designed to be *similar* to Minix, which was supposed to be *similar* to Unix. They share no code in common.

---

### Post by klange on 2008-08-04
The only way Linux is based on Unix is that it shares letters in its name.

However, Linux pretty closely follows POSIX, which came from Unix (when it comes to POSIX, Linux is in the same boat as the BSDs - still not completely compliant, but usually for good reasons).

---

### Post by tamoneya on 2008-08-04
Unix is closed source while linux is open source so there are no relationships at the source code level but they follow similar ideas.  They have similar layouts and are laid out similarly.

---

### Post by OutOfReach on 2008-08-04
> **MaxIBoy said:**
> Linux was designed to be *similar* to Minix, which was supposed to be *similar* to Unix. They share no code in common.

True.
[http://kerneltrap.org/node/14002](http://kerneltrap.org/node/14002)

> From: Linus Benedict Torvalds [email blocked]
Newsgroups: comp.os.minix
Subject: What would you like to see most in minix?
Date: 25 Aug 91 20:57:08 GMT

Hello everybody out there using minix -

I'm doing a (free) operating system (just a hobby, won't be big and
professional like gnu) for 386(486) AT clones.  This has been brewing
since april, and is starting to get ready.  I'd like any feedback on
things people like/dislike in minix, [b]as my OS resembles it somewhat
(same physical layout of the file-system (due to practical reasons)
among other things).[/b]

I've currently ported bash(1.08) and gcc(1.40), and things seem to work.
This implies that I'll get something practical within a few months, and
I'd like to know what features most people would want.  Any suggestions
are welcome, but I won't promise I'll implement them :-)

                Linus (torva... at kruuna.helsinki.fi)

PS.  **Yes - it's free of any minix code**, and it has a multi-threaded fs.
It is NOT protable (uses 386 task switching etc), and it probably never
will support anything other than AT-harddisks, as that's all I have :-(.



---

### Post by mips on 2008-08-04
> **tamoneya said:**
> Unix is closed source while linux is open source so there are no relationships at the source code level but they follow similar ideas.

Not true. Not all Unixes are close source. None of the BSDs are and neither is OpenSolaris.

---

### Post by Bachstelze on 2008-08-05
> **mips said:**
> Not true. Not all Unixes are close source. None of the BSDs are and neither is OpenSolaris.

The original AT&T UNIX wasn't. Nowadays, the term designates any OS that complies to the [Single UNIX Specification](http://icanhascheezburger.com/2008/08/03/funny-pictures-boring-and-uneventful/), which none of the BSDs, and neither OpenSolaris, do.

---

### Post by mips on 2008-08-05
> **HymnToLife said:**
> The original AT&T UNIX wasn't. Nowadays, the term designates any OS that complies to the [Single UNIX Specification]("http://icanhascheezburger.com/2008/08/03/funny-pictures-boring-and-uneventful/"), which none of the BSDs, and neither OpenSolaris, do.

I think you posted the wrong link.

My understanding is/was that the only reason why the BSDs are not certified as Unixes is that it costs a lot of money to get a product certified and it has to be done for each released version. The Open Group owns the Unix trademark and they want money for the certification and use of the name.

[http://www.unix.org/version3/](http://www.unix.org/version3/)
[http://en.wikipedia.org/wiki/Single_UNIX_Specification#Non-registered_Unix-like_systems](http://en.wikipedia.org/wiki/Single_UNIX_Specification#Non-registered_Unix-like_systems)
[http://www.opengroup.org/openbrand/Brandfees.htm](http://www.opengroup.org/openbrand/Brandfees.htm)
[http://en.wikipedia.org/wiki/Unix-like#The_term_.E2.80.9CUnix-like.E2.80.9D_and_the_UNIX_trademark](http://en.wikipedia.org/wiki/Unix-like#The_term_.E2.80.9CUnix-like.E2.80.9D_and_the_UNIX_trademark)
[http://www.apuebook.com/faqs.html#4](http://www.apuebook.com/faqs.html#4)  this is good ;)

---

### Post by Bachstelze on 2008-08-05
Yes ideeed ;) The link that was intended was the one to the Wikipedia page about SUS :

[http://en.wikipedia.org/wiki/Single_UNIX_Specification](http://en.wikipedia.org/wiki/Single_UNIX_Specification)

And yes, the reason most free OSes never ran for the certification is because it would be too expensive, but it is not certain they would get it if they did.

---

### Post by mips on 2008-08-05
> **HymnToLife said:**
> ...but it is not certain they would get it if they did.

Yes it is not certain but it would be interesting to find out whether they would make it on technical criteria. OSX 10.5 made the criteria and from what I have heard some things work a bit differently there.

---

### Post by SunnyRabbiera on 2008-08-05
For me I dont give a crap, as linux seems to do a good job for what it is.

---

### Post by nathanscottdaniels on 2008-08-05
Don't Linux and Unix share many of the same command-line commands such as chmod and others?

---

### Post by SunnyRabbiera on 2008-08-05
> **nathanscottdaniels said:**
> Don't Linux and Unix share many of the same command-line commands such as chmod and others?

Yes indeed.

---

### Post by Bachstelze on 2008-08-05
> **nathanscottdaniels said:**
> Don't Linux and Unix share many of the same command-line commands such as chmod and others?

Yes, GNU was intended to be a UNIX clone composed entirely of Free (FSF) Software, so the base utilities have the same name. They are not exactly the same, however, the code is different and there is usually a few usage differences, for example one version canhave an options the other hasn't, or there can be options that behabe slightly differently.

---

### Post by stream303 on 2008-08-05
Tracking the pedigree of Linux or any of the BSD's is a great learning experience to see where our joys and failures come from.  If we are fortunate, it might help us avoid repeating history. :)

Most OS' at the time had some sort of implementation of standard input and standard output, but it was *nix that brought the revelation of PIPES, which further cemented the "do one thing and do it well" and the "toolbox" approach as opposed to re-inventing the wheel every few years.

---

