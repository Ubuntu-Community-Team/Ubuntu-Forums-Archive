---
title: "unable to use the 'insight' debugger"
date: 2010-06-18
forum: Programming Talk
---

### Post by SteelCore on 2010-06-18
I'm currently reading a programming book in which I need to use a debugger called 'insight'. It should be invoked by the command
```
insight *filename*
```
but this returns a 'command not found' error.
The book was written for 8.10 but I'm using 10.04
Thanks for any help.

---

### Post by SteelCore on 2010-06-18
I'm currently reading a programming book in which I need to use a debugger called 'insight'. It should be invoked by the command
```
$insight *filename*
```
but when used it returns a 'command not found' error.
The book mentions that there is no need to install 'insight' on Linux because it is already there. I using 10.04 yet the text was written for Intrepid (8.10).
Would appreciate any help on this issue.

---

### Post by SevenMachines on 2010-06-18
insight was deleted from debian, (and hence from 10.04) due to, i quote
"Insane packaging; unmaintained; low popcon;  [Debian bug #566579]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=566579")"
see [https://launchpad.net/ubuntu/lucid/+source/insight/6.7.1.dfsg.1-10.1ubuntu2](https://launchpad.net/ubuntu/lucid/+source/insight/6.7.1.dfsg.1-10.1ubuntu2)

you may want to try the version direct from the homepage, or try nemiver or ddd, which seem essentially the same thing, at least at a first glance

---

### Post by lisati on 2010-07-16
Threads merged

---

### Post by Ishipaco on 2010-08-08
I encountered the exact same problem. As others have noted, Insight has been dropped from Ubuntu. It doesn't even seem to be available in any repositories I can see with 10.4.

It sounds like you must be studying from Jeff Duntemann's book, *Assembly Language, Step By Step*. I contacted Jeff and he told me he's trying to deal with the problem. What a rude blow to his new book!

FYI, I went to the home site for Insight, downloaded **insight-6.8-1.tar.bz2**, which has the source code. I followed the directions in the README file, compiled it, ran make install, and nothing worked; bash reported "unknown command." I then downloaded an older version, **insight_6.1+cvs.2004.08.11-1ubuntu1_amd64.deb**, from a Ubuntu repository and, although a deb package and it seemed to install with no problems, it failed to find shared libraries when I tried to use it.

If anybody has figured out how to get Insight installed and working on Ubuntu 10.4. please advise.

---

### Post by SteelCore on 2010-08-08
> **Ishipaco said:**
> 
It sounds like you must be studying from Jeff Duntemann's book, *Assembly Language, Step By Step*. I contacted Jeff and he told me he's trying to deal with the problem. What a rude blow to his new book!


That's right, I am reading Jeff's book and it's a shame indeed. 
If I were Canonical I'd pay serious attention to compatibility of Ubuntu with academic textbooks as this would eventually lead to a much greater market share. IT students eventually dictate computing policies in the market.
I hope Jeff will be able to find a solution to this problem. In the mean time I've reverted to 9.10 which will give me another 8 months to finish this book on a supported Ubuntu platform.

---

### Post by SevenMachines on 2010-08-08
as mentioned before, you can use nemiver or ddd, i used gdb itself with this book with no problems, not the easiest way though :) I can understand that it would be better to have insight available to make going through the book easier though so i'll look into packaging insight into a ppa later in the week if it'll help

---

### Post by SteelCore on 2010-08-08
> **SevenMachines said:**
> ...so i'll look into packaging insight into a ppa later in the week if it'll help

That would be quite generous of you. Thanks.

---

### Post by Ishipaco on 2010-08-09
Be advised that I've been in contact with Jeff for the last two days and can report that he's working hard on a fix. Meanwhile, I posted info on this and another potential problem in a comment I just posted for a review of the book I wrote for Amazon. You can get there with the following link:

[http://www.amazon.com/review/RE0ZFQZMVCMLK/ref=cm_cr_rev_detup_redir?_encoding=UTF8&cdPage=1&asin=0470497025&store=books&newContentID=MxLKAFT3NYR5TG#MxLKAFT3NYR5TG](http://www.amazon.com/review/RE0ZFQZMVCMLK/ref=cm_cr_rev_detup_redir?_encoding=UTF8&cdPage=1&asin=0470497025&store=books&newContentID=MxLKAFT3NYR5TG#MxLKAFT3NYR5TG)

Given Jeff's expertise in this kind of thing, I don't think it will take him long to come up with a solution. :D

---

### Post by SteelCore on 2010-08-09
Great. Thanks for the update.
I'm actually self studying this book and facing such a problem sort of affected my enthusiasm. I must say that your post encouraged me to continue espcially that it came from a probable friend or colleague of the author. I'll monitor your Amazon review for further news.
Thanks again.

---

### Post by Jeff Duntemann on 2010-08-09
Just wanted to jump in here to thank Ishipaco for his kind words and provide some status.  Alas, fixing Insight so it works under Lucid may not be something I can do. I'm not an ace at creating packages, so if SevenMachines can fix the package and put it somewhere we can all find it, I would be tremendously grateful, as would my readers.  

I want to point out here that Insight is an odd bird. It's not a front end to gdb in the same way that KDbg and DDD are. What the Insight team did was take the source code for gdb and create a new version of gdb by grafting on a GUI written in Tcl/Tk. In effect, it's a fork of gdb, with all the awkwardness and potential problems that that implies.  

The Debian team has characterized Insight as "insanely packaged," and from what I can tell (not being experienced in package lore) it has hard-coded references to specific older versions of some Tcl/Tk libraries, possibly due to code being embedded in the project rather than linked to it. This makes rebuilding Insight from source problematic, and I get the impression that there's nobody currently maintaining it over at Red Hat.  

So we may be looking at something here that should rightly be considered "dead software." That's a shame, because Insight works better with assembly language than either DDD or KDbg, both of which are used mostly with C/C++.  

The short-term solution is to install an instance of Ubuntu 9.10 in a new partition or VM, or (if you're primarily a Windows person) under Wubi. For the purposes of learning assembly at the level I teach it (entry level!) using a slightly older release of Ubuntu won't make any difference at all. There's no GUI programming in my book; it's all very basic console stuff and actually not specific to any particular distro. I've been able to install Insight under Fedora 13, and if you're using GNOME, you can get Kate by installing the kdesdk package, and Konsole (which Kate uses) by installing the kdebase package.  But the easiest way is just to fall back to Karmic until we figure out some way to make Insight work under Lucid and later.  

I'll be posting solutions or band-aids as I find them at the book's Web page:  [http://www.duntemann.com/assembly.html](http://www.duntemann.com/assembly.html)  

Thanks for allowing me to jump in, and I wish I had an easy, magic-wand style solution.

---

### Post by SevenMachines on 2010-08-09
Thanks for the explanation Jeff, i enjoyed your book! I do have a working insight package in maverick, still need to test lucid though. Its a bit inelegant and the packaging is probably even more insane :) but sadly its beyond my abilities to do a better job. I'm a bit concerned about all the different versions of gdb, tcl and so on flying about but it *seems* to work ok. All being well i'll post a link to the ppa in the next day or so. Suffice to say I'd only recommend it if people need it to follow the book, I can understand why it was dropped from debian. There seems to be cvs activity so maybe it'll be reintroduced at some point after someone has a proper look at packaging it.

---

### Post by SteelCore on 2010-08-09
Good to have you here Jeff. Thank you for personally clarifying the issue.
Never realized my post could attract that much attention :D

---

### Post by SevenMachines on 2010-08-09
I've put insight here,
[https://edge.launchpad.net/~sevenmachines/+archive/dev](https://edge.launchpad.net/~sevenmachines/+archive/dev)

It seems to work on maverick but i havent tested it on lucid yet so if anyone finds it works let me know. If not i'll get it on lucid and have a look sometime tomorrow

---

### Post by Jeff Duntemann on 2010-08-09
> **SteelCore said:**
> Good to have you here Jeff. Thank you for personally clarifying the issue.
Never realized my post could attract that much attention :D

You raised an issue that a lot of people have been raising in the last few months. I'd sure like to see it solved somehow, granting that Insight is a very strange piece of software.

There is a new release only a year old (the version in Karmic dates back to 2007) and it's possible that with some massaging a decent deb package could be made from it.

This is not an isolated problem. The Lazarus GUI for FreePascal has not been kept up to date in deb format, and people who want to use it sometimes install the deb and wonder why it's a year or more old. Package management is a bit of a black art, and I have the highest respect for people who do it well, especially in a volunteer context like Linux.

---

### Post by Jeff Berry on 2010-08-17
> **SevenMachines said:**
> I've put insight here,
[https://edge.launchpad.net/~sevenmachines/+archive/dev](https://edge.launchpad.net/~sevenmachines/+archive/dev)

It seems to work on maverick but i havent tested it on lucid yet so if anyone finds it works let me know. If not i'll get it on lucid and have a look sometime tomorrow
I just tested this on lucid and everything seems to be working.

---

### Post by edge2022 on 2010-08-23
Thank you so much SevenMachines.  Insight seems to be running fine on lucid, but I didn't really test it that much.  Great book Jeff, I am really enjoying it.

---

### Post by SevenMachines on 2010-08-23
good stuff, i'll leave in the ppa then. if people are having problems with other releases of ubuntu or debian let me know and i'll do my best. it's a good book and worth a read no matter what language you program in

---

### Post by Jeff Duntemann on 2010-08-24
I just installed it here under Lucid Lynx, and it went in without a hitch and appears to run. I haven't tested it at length yet, but I'll do so as soon as time allows and will report back here.

Many thanks to SevenMachines for even getting us this far!

---

### Post by Jeff Duntemann on 2010-08-25
Well, I spent some time with Insight and a few of the example programs from the book. Insight runs, loads an executable, sets breakpoints, and steps. As long as the Registers view is *not* set to "general", everything seems to work correctly. However, if you set the Registers view to "general" the following error pops up in a dialog:

i386-linux-nat.c:562: internal error: Got request for bad register number  41.
A problem internal to GDB has been detected,
further debugging may prove unreliable.
Quit this debugging session?

Interestingly, all the other subsets of the Registers view appear to work, except for "general".

This was run under Lucid on a Dell SX280 with 2 GB RAM.

I'd be curious to see if anyone else who's installed the new .deb from SevenMachines can duplicate the problem.

And once again, thanks to SevenMachines for getting the package untangled and installable, even if it has glitches.

I'm going to try installing the package on Karmic in a VM and see if the same message pops up.

---

### Post by SevenMachines on 2010-08-26
Yes, i get that bug on 'general' registers too on maverick. I also get it on the unpackaged svn snapshots of insight too so i dont know if its an insight bug or a subtle problem of the different versions of gdb on the system. 

The main problem with the deb package is

* the insight source bundle comes with its dependency programs all bundled, builds with them, then installs the whole lot, dependency versions and all. gdb, tcl, etc

* the package builds insight against all its own bundled dependency versions, then removes all these files from the package and just installs insight with new dependencies on the repository versions, and hopes for the best.

Hopefully the general register bug is the only (obvious) one and 'all' registers are fine. I'm actually surprised it works reasonably well at all.

---

### Post by edge2022 on 2010-08-27
I don't get any such error when looking at the general registers only.  I tried with a couple of your programs.  Attached a screenshot.  I am on Lucid 64 bit.  The reason the 64 bit registers are not present, is because it was assembled as elf, not elf64.  The 64 bit registers work fine under the general view when assembled with elf64 as well.  
Specs: 
Rampage Extreme Motherboard X48
Core 2 Quad Q9400

---

### Post by puppi on 2010-09-15
Jeff,
I've just recently started reading your book, and literally minutes ago got to the part where you introduce Insight. It was truly disturbing when I realized Insight was no longer within Ubuntu (and even more when I discovered it wasn't officially mantained anymore), right after reading in your book about the considerable relevance it has in learning assembly and that your book's examples make such big use of it. I'm really enjoying your book, and I'd very much like to solve this issue.

Thank you SevenMachines for the aid, your solution seems to be the best of the (admittedly few) I've seen so far. I'll definitely give it a try.

---

### Post by jerg on 2010-09-15
Nice first thanks SevenMachines for PPA of insight....and Jeff you rock ...reading the book and so far the best computer book I've ever read ...hope you do more wonders and also thanks to SteelCore for bring the issue up in the forum

j3rg

---

### Post by bstcpext on 2010-09-30
Thank You SevenMachines. PPA work perfectly (using 2.6.32-34). Very nice introductory book Jeff. I did assembly back in the late 70's and guess what ... here I go again.

---

### Post by FromWithin on 2010-10-07
Fantastic. Insight is easily my favourite GDB-based debugger. I tried compiling myself a few weeks ago to no avail. Thanks so much for getting this working and packaging it up.

---

### Post by jerg on 2010-10-18
Have anyone have this issue with insight?

When stepping through the code:

```

section .data
section .text
  global _start
_start:
  nop
; Put your experiments between the two nops...
  mov ax,-42
  mov ebx,eax
; Put your experiments between the two nops....
  nop

section .bss

```

in the insight debugger i can't see the number as -42 in eax register. I already right-clicked and selected "Decimal" from the pop-up menu. The value show as an unsigned decimal it shows the value 65494.

Discard this question as the book explains the reason why...

---

### Post by kem83 on 2011-02-18
Thank You SevenMachines!

---

### Post by jerg on 2011-03-03
Can any explain to me why my gdb console is reporting the wrong information take a look at the screenshot and see what I'm saying:

[Insight Error]("http://s1100.photobucket.com/albums/g414/j3rg/?action=view&current=Screenshot-gdb.jpg")

The book says that the CF, OF, SF and PF flags should be set. However from the image you can see that only the CF, AF, IF and OF flags were set.

Is SF not set because MUL only handles unsigned values?

An the Parity Flag (PF) should be set as the results is:

0x03b71ffffc48e = 65360812295310 = 1110110111000111111111111111111100010010001110

There are 32 1 bits in the binary equivalent value so why the parity flag is not set? ...lol really don't know

Thanks in Advance

---

### Post by kronick on 2011-06-15
Thank you SevenMachines

---

### Post by Fancycakes on 2011-06-30
I was *going* to say that compiling the newest Insight from source on Karmic works just fine for me, but then I saw the PPA, so what I will say is thanks for the PPA, SevenMachines; and thank you Jeff for a wonderful Assembly book.

Assembly still seems like magic to me and whenever I see source code, it looks like Moon Runes, but I'll get there... some day.

---

