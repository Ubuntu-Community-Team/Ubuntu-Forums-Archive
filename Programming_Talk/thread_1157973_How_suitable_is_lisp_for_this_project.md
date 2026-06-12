---
title: "How suitable is lisp for this project?"
date: 2009-05-13
forum: Programming Talk
---

### Post by dbd on 2009-05-13
Hi,

I've recently started to learn lisp, I'm a competent C++ programmer and wanted to learn something radically different, and so I turned to lisp. But so far I've only been dawdling my way through "practical common lisp", and have not managed to really get into it because there's not had anything I've actually wanted to write. Now I have an idea, but because I'm such a beginner I have no idea how appropriate lisp is as a language for my problem.

I basically want a fancy web site change notification system, for use when a site changes in a specific way which I'm interested in or just for changes in sites without RSS feeds. Here's a few examples of things I'd want it to do:

[LIST]
[*]Notify me when a particular web page changes
[*]Notify me when there is a change containing specific text (say a band adds to their gig listings page a line containing the word "Birmingham")
[*]Notify me when a web site which I have to log into / get into using cookies changes (such as the board games site itsyourturn.com, or a facebook page)
[/LIST]
I thought the best way to do this would be for the program to create an RSS feed to notify me of what changes on the net it has detected, since that would be accessible by a broad range of apps, from standard RSS feed readers, to KDE desktop widgets.

So how good would lisp be for this? There seem to be a fair few XML libraries, so generating the RSS feed should be pretty straightforward (any recommendations on the best XML library for this?). As for reading websites, after a brief search it looks like [drakma]("http://weitz.de/drakma/") should do the job (any better suggestions?). So once I've got the hang of these libraries it looks like the bulk of the work will be getting the program to go through the text, and to work out the appropriate parts to add to the RSS feed. Is this a natural "lispy" problem, and will tacking it help me learn lisp? Or am I simply crazy for even thinking about doing this in lisp?

Thanks

Paul

---

### Post by hessiess on 2009-05-13
Carn't say how sutable Lisp would be for that spasific problem, as I have only recently started lt learn it also. But if you want to learn Lisp then give it a go :)

If you want it to run as a web app then you will have a hard time finding hosting which provides Lisp scripting capability, so you will propably have to go dedicated and set it up manually.

---

### Post by dbd on 2009-05-13
> **hessiess said:**
> If you want it to run as a web app then you will have a hard time finding hosting which provides Lisp scripting capability, so you will propably have to go dedicated and set it up manually.

I was just planning to run it on my home computer, and have the RSS feed as a file on the hard drive. So hosting isn't really a worry (although if anyone knows of a free (or paid for) host with lisp capability I'd be interested to know for future reference).

---

### Post by CptPicard on 2009-05-13
Well, I would say that there are very few problems Lisp *isn't* suitable for, if you can just find the libraries so that you don't need to write them from scratch yourself... this particular problem here sounds quite good for a practice project indeed. :)

---

### Post by dbd on 2009-05-13
> **CptPicard said:**
> Well, I would say that there are very few problems Lisp *isn't* suitable for, if you can just find the libraries so that you don't need to write them from scratch yourself... this particular problem here sounds quite good for a practice project indeed. :)

Awesome, that's exactly what I wanted to hear. Thanks for the help :D

---

