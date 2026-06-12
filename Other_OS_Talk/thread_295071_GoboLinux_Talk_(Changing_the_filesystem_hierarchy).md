---
title: "GoboLinux Talk: (Changing the filesystem hierarchy)"
date: 2006-06-14
forum: Other OS Talk
---

### Post by RAV TUX on 2006-06-14
**[[B]GoboLinux** - the alternative Linux distribution]("http://www.gobolinux.org/")[/B]



[URL="http://www.ubuntuforums.org/showthread.php?t=196286"]
[/URL]

---

### Post by RAV TUX on 2006-07-30
I'm downloading GoboLinux now:

here is what distrowatch says:

> GoboLinux is a Linux distribution that breaks away from the historical UNIX directory hierarchy. Basically, this means that there are no directories such as /usr and /etc. The main idea of the alternative hierarchy is to store all files belonging to an application in its own separate subtree; therefore we have directories such as /Programs/GCC/2.95.3/lib. To allow the system to find these files, they are logically grouped in directories such as /System/Links/Executables, which, you guessed it, contains symbolic links to all executable files inside the Programs hierarchy. To maintain backwards compatibility with traditional Unix/Linux apps, there are symbolic links that mimic the Unix tree, such as "/usr/bin -> /System/Links/Executables", and "/sbin -> /System/Links/Executables" (this example shows that arbitrary differentiations between files of the same category were also removed).

This is a Independently Developed Distro so am interested to see how it works.

---

### Post by basketcase on 2006-07-31
> **yozef said:**
> I'm downloading GoboLinux now:

here is what distrowatch says:



This is a Independently Developed Distro so am interested to see how it works.
based on the description, I'm curious also.  

Let us know how it works out for ya.

---

### Post by RAV TUX on 2006-07-31
> **basketcase said:**
> based on the description, I'm curious also.  

Let us know how it works out for ya.

Verifying the burn now but Gobolinux may have to wait until tomorrow, I also started a download of eLive...I have to wait for it too finish and my bed is calling me....

---

### Post by RAV TUX on 2006-07-31
some more GoboLinux reading:

> **Documentation**

   This website is the primary source of information about GoboLinux. 
  **Starting points**

   Things you'll probably want to read first: 
  [LIST]
[*][Frequently Asked Questions]("http://www.gobolinux.org/index.php?page=faq") - the first question is "what the heck is GoboLinux", so, if you're still wondering... check it out!
[*][Installation instructions]("http://www.gobolinux.org/index.php?page=install") - the installation guide as included in the distribution. Updated for 010.
[*][Installing programs]("http://www.gobolinux.org/index.php?page=doc/006/scripts") - You installed it. What now? This doc contains useful information for the newcomer. Explains how to make packages and have them integrated with the system.[/LIST]  **Articles**

   Informal pieces written by GoboLinux developers, which hopefully will shine some light on the spirit of the project and on what goes on the dev's heads. :) Most of these are just emails sent to gobo-l which were considered worth keeping. 
  [LIST]
[*][I am not clueless]("http://www.gobolinux.org/index.php?page=doc/articles/clueless")  - by Hisham Muhammad. Or, "Myths and misconceptions about the design of GoboLinux". Makes for good bed-time reading. Also in printer-friendly [PDF]("http://gobolinux.org/doc/articles/clueless.pdf").
[*][The ideas behind Compile]("http://www.gobolinux.org/index.php?page=doc/articles/compile")  - by Hisham Muhammad. The ideas on which Compile and the Recipes tree  are based on.
[*][Quick-and-dirty Porting Guide]("http://www.gobolinux.org/index.php?page=doc/articles/porting_guide") - by Hisham Muhammad. An overview on what would it take to make GoboLinux run in a different architecture.
[*][Going Embedded with  GoboLinux]("http://www.gobolinux.org/index.php?page=doc/articles/going_embedded") - by Lucas C. Villa Real. A step-by-step guide to port GoboLinux to an embedded architecture.
[*][Organization: is there any?]("http://www.gobolinux.org/index.php?page=doc/articles/organization") - by Hisham Muhammad. A long answer to the "who is in charge of what" question.
[*][GoboHide: surviving aside the legacy tree]("http://www.gobolinux.org/index.php?page=doc/articles/gobohide") - by Lucas C. Villa Real. An explanation on how GoboHide was developed and how it works.[/LIST]  **Docs**

  [LIST]
[*][Roadmap for 012]("http://www.gobolinux.org/index.php?page=roadmap012") - The things  we aim for the next release.
[*][Differences between GoboLinux and a traditional Linux system]("http://www.gobolinux.org/index.php?page=differences") - a brief summary of the differences. Not detailed, but still recommended reading if you are installing.
[*]["Registered" users]("http://www.gobolinux.org/index.php?page=hall_of_fame") - Not really documentation, but cool nonetheless. Check it out, and get your name in here![/LIST]  **Links**

  [LIST]
[*][GoboLinux on DistroWatch]("http://distrowatch.com/table.php?distribution=gobo")
[*][GoboLinux on Linux Central]("http://linuxcentral.com/catalog/index.php3?prod_code=L000-258&id=C1C4a22ekmACI")[/LIST]  **Older docs**

 [LIST]
[*][Roadmap for 011]("http://www.gobolinux.org/index.php?page=roadmap011") - The things  we aimed for 011. Did we skip the roadmap on 010???
[*][Roadmap for 007]("http://www.gobolinux.org/index.php?page=roadmap") - The things  we aimed for 007. Nice to read now and see that we actually did those things. :)
[*][006 To-do list]("http://www.gobolinux.org/index.php?page=todo") - a proto-roadmap.[/LIST]  **Publications**

  Articles on GoboLinux written by team members. The user interested in GoboLinux is directed to read these: 
 [LIST]
[*][The Unix tree rethought: an introduction to GoboLinux]("http://www.kuro5hin.org/story/2003/5/9/05015/62649") - published on [Kuro5hin]("http://www.kuro5hin.org/"); [local copy]("http://www.gobolinux.org/index.php?page=k5").[/LIST]  **Press**

   Websites that covered GoboLinux: 
  [LIST]
[*][Linux+]("http://www.lpmagazine.org/") - Distro of the August month.
[*][Slashdot]("http://developers.slashdot.org/developers/03/05/10/1636245.shtml") on [The Unix tree rethought]("http://www.gobolinux.org/index.php?page=k5").
[*][Slashdot]("http://slashdot.org/article.pl?sid=04/06/05/1949213") on [The ideas behind Compile]("http://www.gobolinux.org/index.php?page=doc/articles/compile")
[*][Slashdot]("http://slashdot.org/articles/04/06/17/2326207.shtml?tid=108&tid=126&tid=156&tid=163&tid=167&tid=99") on [I am not clueless]("http://www.gobolinux.org/index.php?page=doc/articles/clueless")
[*][Symlink.ch]("http://www.symlink.ch/articles/03/05/12/2037213.shtml") (in German)
[*][LinuxFr]("http://linuxfr.org/2003/05/13/12411.html") (in French)
[*][Bittivuoto]("http://bittivuoto.net/uutiset.php4?v=1&kat=6&id=1570#GoboLinux") (in Finnish)
[*][Slashzone.ru]("http://slashzone.ru/opensource/03/05/12/0946203.shtml") (in Russian)
[*][HUP]("http://www.hup.hu/modules.php?name=News&file=article&sid=3427") (in Hungarian)
[*][WhatsUp]("http://www.whatsup.org.il/article.php?sid=1319") (in Hebrew)
[*][PuntBarra]("http://puntbarra.com/node.php?id=1120&PHPSESSID=58d7c9382bb885baeb2d5ed3b80489ea") (in Catalan)
[*][Portal.bg]("http://portal.bg/news.php?cat=main&read=20031205002") (in Bulgarian)
[*][Slashdot Japan]("http://slashdot.jp/developers/03/05/11/0842218.shtml?topic=2") (in Japanese)
[*][Linux.pl]("http://www.linux.pl/?id=news&show=1060") (in Polish)
[*][OSNews]("http://www.osnews.com/comment.php?news_id=3511")
[*][Linux Weekly News]("http://lwn.net/Articles/66290")
[*][CapnKirby]("http://www.capnkirby.com/GoboLinux.html")
[*][Root.cz]("http://www.root.cz/zpravicky/gobolinux-012/?SID=8D53F86C5E40429F3F4E3F7AA747E80B") (in Czech)[/LIST]  **Academic publications**

   This section will list scientific articles related to GoboLinux published by members of the team. 
  [LIST]
[*] MUHAMMAD, Hisham. DETSCH, André. **Uma nova proposta para a arvore de diretorios UNIX.** Proceedings of the III WSL - Workshop em Software Livre, Porto Alegre, 2002. [PostScript (Portuguese)]("http://www.gobolinux.org/doc/wsl2002/gobolinux_wsl2002.ps"), [LyX (Portuguese)]("http://www.gobolinux.org/doc/wsl2002/gobolinux_wsl2002.lyx"), [HTML (English)]("http://www.gobolinux.org/doc/wsl2002/gobolinux_wsl2002_english/"), [PostScript (English)]("http://www.gobolinux.org/doc/wsl2002/gobolinux_wsl2002_english.ps"), [LyX (English)]("http://www.gobolinux.org/doc/wsl2002/gobolinux_wsl2002_english.lyx").
[*] DETSCH, André. BEDIN, Guilherme B.;. **Distribuição GoboLinux.**  Proceedings of the IV WSL - Workshop em Software Livre, Porto Alegre, 2003. [PostScript (Portuguese)]("http://www.gobolinux.org/doc/wsl2003/gobolinux_wsl2003.ps").
[*] MUHAMMAD, Hisham. JEFFMAN, Rafael G.v **Portabilidade e flexibilidade em software livre: a experiencia do GoboLinux**  Proceedings of the IV WSL - Workshop em Software Livre, Porto Alegre, 2003. [PostScript (Portuguese)]("http://www.gobolinux.org/doc/wsl2003/portabilidade_wsl2003.ps"), [PDF (Portuguese)]("http://www.gobolinux.org/doc/wsl2003/portabilidade_wsl2003.pdf").
[*] DAMASIO, Felipe W. VILLA REAL, Lucas C.**GoboHide: Uma Solução Flexível e Escalável para Inodes Ocultos no Kernel Linux**  Proceedings of the IV WSL - Workshop em Software Livre, Porto Alegre, 2003. [PDF (Portuguese)]("http://www.gobolinux.org/doc/wsl2003/gobohide_wsl2003.pdf"),[/LIST]  **Presentation slides**

   This section will list the slides of some GoboLinux presentations. 
  [LIST]
[*] **GoboLinux.** Presented on IV FSL - Fórum Internacional de Software Livre, Porto Alegre, 2003. [OpenOffice Impress (Portuguese)]("http://www.gobolinux.org/doc/fisl2003/gobolinux_FSL2003.sxi"),
[*] **GoboLinux.** Presented on SDSL 2003 - Semana de Desenvolvimento em Software Livre, São Leopoldo, 2003. [OpenOffice Impress (Portuguese)]("http://www.gobolinux.org/doc/sdsl2003/gobolinux_sdsl2003.sxi").[/LIST]

---

### Post by basketcase on 2006-07-31
I came home and downloaded it.  After playing with it for about 30 mins or so, here are my thoughts. 

[http://basketcase.wordpress.com/2006/07/31/gobolinux-012/](http://basketcase.wordpress.com/2006/07/31/gobolinux-012/)

I can't believe how fast firefox is.  I'd load the CD up just to have a quicker browser.  

Up next is Knoppix 5.0.1 and GoblinX

---

### Post by adamkane on 2006-07-31
Use Swiftfox, if you want a faster Firefox.

Pay attention, people!

---

### Post by richbarna on 2006-07-31
> **basketcase said:**
> I came home and downloaded it.  After playing with it for about 30 mins or so, here are my thoughts. 

[http://basketcase.wordpress.com/2006/07/31/gobolinux-012/](http://basketcase.wordpress.com/2006/07/31/gobolinux-012/)

I can't believe how fast firefox is.  I'd load the CD up just to have a quicker browser.  

Up next is Knoppix 5.0.1 and GoblinX

Hey basketcase, could you add your review to [this thread]("http://www.ubuntuforums.org/showthread.php?t=225788") ? It's the "sticky" at the top of the page, where we are posting our reviews.
Thanks :)

---

### Post by basketcase on 2006-07-31
> **richbarna said:**
> Hey basketcase, could you add your review to [this thread]("http://www.ubuntuforums.org/showthread.php?t=225788") ? It's the "sticky" at the top of the page, where we are posting our reviews.
Thanks :)
Done

---

### Post by RAV TUX on 2006-08-07
I have decided to start a series of threads specifically for technical help for other Distros...the Distro is listed in the thread title. This is primarily for Ubuntu users who test or use other distros and feel most comfortable seeking help in our own community. In no way does this superceed the help you should also be getting from the perspective Distro., in fact I encourage you to be as active in their forums as you are here and post ideas, knowledge and solutions here to provide a reference point to share, reference links are encouraged.

***GoboLinux Tech Talk***

Threads merged:

[http://www.ubuntuforums.org/showthread.php?t=226198](http://www.ubuntuforums.org/showthread.php?t=226198)
[http://www.ubuntuforums.org/showthread.php?t=231285](http://www.ubuntuforums.org/showthread.php?t=231285)

---

### Post by RAV TUX on 2006-11-04
moving to other OS talk

---

### Post by IYY on 2006-11-07
I don't know if you've heard about this experimental distro, but here's the link:

[http://www.gobolinux.org/](http://www.gobolinux.org/)

[http://www.gobolinux.org/index.php?page=at_a_glance](http://www.gobolinux.org/index.php?page=at_a_glance)

Instead of the usr, bin, lib, etc, Gobo has Programs, Users, System, Files, Mount and Depot. 

I think this might be a step in the right direction. What is your opinion?

---

### Post by aysiu on 2006-11-07
I think it's an excellent idea--somewhat like Mac OS X--maintaining a similar file structure but tweaking it a little bit to make more sense to the uninitiated.

---

### Post by .t. on 2006-11-07
I think it is a terrible idea. Why not just have people learn the correct way, and they'll soon see why it's better! Immediate impressions aren't all that counts, you know!

---

### Post by maagimies on 2006-11-07
> **.t. said:**
> I think it is a terrible idea. Why not just have people learn the correct way, and they'll soon see why it's better! Immediate impressions aren't all that counts, you know!Explain to me what's so much better about "the correct way" compared to the Gobolinux one. And no, "because it has always been so!" isn't a good argument.
I like that Gobolinux layout, it makes sense.

---

### Post by .t. on 2006-11-07
[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

My opinion is that it's good cos it's well laid out, and it's shorter to type.

---

### Post by aysiu on 2006-11-07
As far as I can tell, based on [this description](http://www.gobolinux.org/?page=at_a_glance), GoboLinux maintains the traditional *nix-like structure through symlinks the end-user doesn't have to know about.

---

### Post by .t. on 2006-11-07
Bah. Just means lazy people don't have to learn. Makes it more like Windows. People should learn it; it's a good exercise! It will help them later on, especially if they deal with programs referring to the "old" conventions.

---

### Post by MedivhX on 2006-11-07
Cool idea... I'm really confused with those existing names...

---

### Post by maniacmusician on 2006-11-07
people shouldn't have to learn about it if they don't give a crap. Most people nowadays are like that. They just want to use something, not understand how it works. And if you know what you're doing, you can still do stuff the traditional way. I think it's a good thing.

---

### Post by .t. on 2006-11-07
What about conventions? Old programs? All the work? The simplicity (I DONT WANT TO HAVE TO USE TAB ALL THE TIME!!!)!

---

### Post by chickengirl on 2006-11-07
Ehh... I don't think it's a terrible idea, but I'm not crazy about it either.

ETA: It's a little shinier and noob-friendlier, but noobs really *shouldn't* be poking around in the filesystem. And if they're savvy enough to know what they're doing, then they're savvy enough to deal with the old names.

---

### Post by po0f on 2006-11-07
This would break all Linux packages out there right now, that haven't been custom-packaged and bastardized by these people.

---

### Post by aysiu on 2006-11-07
> **.t. said:**
> What about conventions? Old programs? All the work? The simplicity (I DONT WANT TO HAVE TO USE TAB ALL THE TIME!!!)!
Why don't you read about it before you judge it? Here's an excerpt, but I suggest you read [the whole page](http://www.gobolinux.org/?page=at_a_glance): > But what about Unix compatibility?

The GoboLinux system layout seems to be a major departure from the Unix tradition. Does this mean all programs need to adjusted so that they work with the new layout? Fortunately, the answer is no. Through a mapping of traditional paths into their GoboLinux counterparts, we transparently retain compatibility with the Unix legacy.

```
~] ls -l /dev/null | cut -b 45-
/dev/null

~] ls -l /bin/sh | cut -b 45-
sh -> /Programs/Bash/3.0/bin/bash

~] ls -l /usr/include/stdio.h | cut -b 45-
stdio.h -> /Programs/Glibc/2.3.6/include/stdio.h
```

There is no rocket science to this: /bin is a link to /System/Links/Executables. And as a matter of fact, so is /usr/bin. And /usr/sbin... all "binaries" directories map to the same place. Amusingly, this makes us even more compatible than some more standard-looking distributions. In GoboLinux, all standard paths work for all files, while other distros may struggle with incompatibilites such as scripts breaking when they refer to /usr/bin/foo when the file is actually in /usr/local/bin/foo.

You may have noticed that the Unix paths did not show up in the system root listing in the very first example. They are actually there, but they are concealed from view using the GoboHide kernel extension. This is for aesthetic purposes only and purely optional, though: GoboLinux does not require modifications in the kernel or any other system components. But our users seem to like it a lot. :-) 

---

### Post by shining on 2006-11-07
By reading the comments, it looks to me you didn't even read anything about GoboLinux. I apologize if I'm wrong, I just want to make sure everyone checked out the docs on their website, and this article in particular:
[http://www.gobolinux.org/index.php?page=doc/articles/clueless](http://www.gobolinux.org/index.php?page=doc/articles/clueless)

That's just in order to avoid pointless comments :)

---

### Post by maniacmusician on 2006-11-07
like aysiu said, everything would still work. It doesn't break anything. It's a little radical, and it's really cool....especially the total compatibility.

And if you don't want the zany symlinking stuff, then you can disable it. No biggie.

---

### Post by 23meg on 2006-11-07
Yes, good idea, but I'm not sure if I'd like to see it implemented in Ubuntu as a default.

---

### Post by ember on 2006-11-07
It is a good idea, I think. 

Yet it imposes different problems. For me as a German it is disputable whether it makes sense to have shortforms of English words mapped to longer English words. 

On the other hands I like the structure Gobo Linux makes. 

Eventually it just leaves the question whether symlinks will work as expected in all situations.

---

### Post by po0f on 2006-11-07
I did glance through the page very quickly and came to the conclusion that this is the Linux distribution for the completly new Linux convert.

It will help people out that are first moving to Linux, but when they feel that they have "graduated" beyond the need for GoboLinux and start to shop around for another distribution, they will be redumped into the world of Linux.  Face it, the only people that are going to use this distribution are Windows people, and they will think they "know" Linux and try to install another distribution.  Guess what?  Everything that they have learned using GoboLinux is useless to them if the distro itself hides the underlying filesystem structure from them.  They will be used to "unzippping files to Programs to install something new".

[quote=GoboLinux]/Programs is where all programs reside. No exceptions.[/quote]
This is stupid, and very OSX-ish.  BTW, what is /System for if **all programs, no exceptions** are installed in /Programs?

---

### Post by SunnyRabbiera on 2006-11-07
I dunno, its kind of windows like to me and the two should keep apart in terms of system layout.
usr/bin is like C:\program files
/home/ your name is like My doccuments
Its not that hard to figure out honestly.

---

### Post by bastiegast on 2006-11-07
I like the approach, but voted neutral cuz in the transition period it might only make things more complicated. If you just use /home/username all is fine for most users I think. Just have an icon My Computer on the desktop or in "Places" which contains CD Drive, Hard Disks and network locations.

---

### Post by .t. on 2006-11-07
Errr... I have read the page... I believe that even though it provides compatibility, it will stop users learning the methods that are used by the system. That way, if an application unwittingly says "Look at file in /usr/share" or "/var/crash", the user won't have any clue what it's on about.

---

### Post by angkor on 2006-11-07
Neutral.

I don't think the current hierarchy (although I understand it can be tricky to the new user) is 'broken' in any way. So why 'fix' it? I didn't read all the gobo pages but is the only reason to change to make it more easily understood by new linux users or are there other advantages?

I wouldn't use it on my box because it would probably confuse the hell out of me. :)

---

### Post by aysiu on 2006-11-07
> **SunnyRabbiera said:**
> I dunno, its kind of windows like to me and the two should keep apart in terms of system layout.
usr/bin is like C:\program files
/home/ your name is like My doccuments
Its not that hard to figure out honestly.
Well, it's not a matter of hard versus easy.
It's more like manageable versus extremely easy.

By the way, in Windows, not all files related to a program are in C:\Program Files. Likewise, in traditional Linux distributions, not all files related to programs are in /usr/bin, either (in fact, not even all executables are in /usr/bin--some are in /usr/sbin or /bin, or /sbin).

Most of the time, in Ubuntu, you have some files (configuration files) in /etc, some (libraries) in /usr/lib, some (executables) in /usr/bin, and some (images) in /usr/share/pixmaps. In other words, they're all over the place.

---

### Post by SunnyRabbiera on 2006-11-07
Well it is possible to have a "my computer" icon in ubuntu:
For gnome you can use the configuration editor (just start gconf-editor in a terminal, or just unhide it via alacarte, just open up alacarte {its in accessories} move your way down to "system tools" and click on the box next to "configuration editor")
anyhow once the configuration editor opens click on "apps" and make your way down to "Nautilus"
click on that and then click on "destop"
On the other side you will have an array of options, there are many options here but for now just click on the box next to "computer icon visible"
You can click on "trash icon visible" "doccuments icon visible" and "home icon visible" if you wish as that will make it more windows ish for all yah.

---

### Post by .t. on 2006-11-07
But more sorted!
And the education!

---

### Post by shining on 2006-11-07
> **po0f said:**
> I did glance through the page very quickly and came to the conclusion that this is the Linux distribution for the completly new Linux convert.


Thanks, you just proved my point.

> 
Did you redesign the tree to make it more newbie-friendly?

No. In fact, it was motivated to fulfill the needs of users who prefer to install applications from the original source packages instead of relying on the distribution. That is the main reason why each application gets its own directory: so you can install it from source there and then remove it with an "rm -rf". So, you see, GoboLinux was designed focusing the experienced user who doesn't like things to be automagical. Our scripts merely automate procedures, but they don't "make decisions", and whenever they have to, they ask first.


---

### Post by SunnyRabbiera on 2006-11-07
> **aysiu said:**
> Well, it's not a matter of hard versus easy.
It's more like manageable versus extremely easy.

By the way, in Windows, not all files related to a program are in C:\Program Files. Likewise, in traditional Linux distributions, not all files related to programs are in /usr/bin, either (in fact, not even all executables are in /usr/bin--some are in /usr/sbin or /bin, or /sbin).

Most of the time, in Ubuntu, you have some files (configuration files) in /etc, some (libraries) in /usr/lib, some (executables) in /usr/bin, and some (images) in /usr/share/pixmaps. In other words, they're all over the place.

Well yes installation may vary, but i rather linux stay its own course as much as possible. Sure make it look like windows all you want, but not laid out like windows... they are different for a reason

---

### Post by aysiu on 2006-11-07
> **SunnyRabbiera said:**
> Well yes installation may vary, but i rather linux stay its own course as much as possible. Sure make it look like windows all you want, but not laid out like windows... they are different for a reason
GoboLinux isn't laid out like Windows. I'm not sure where you're getting that from.

Even Windows does not stick all program-related files in C:\Program Files.

---

### Post by SunnyRabbiera on 2006-11-07
well they say things like /Programs
Kinda like C:\Program files
that kinda thing.

---

### Post by maniacmusician on 2006-11-07
just because something is similar to windows doesn't mean it's copying it. Gobo Linux is more similar to OSX than windows, but I don't like Apple so naturally Gobo Linux seems better to me. It's not like windows at all. 

And Windows isn't all bad...They did have mostly good concepts, just horrible implementation.

---

### Post by aysiu on 2006-11-07
> **SunnyRabbiera said:**
> well they say things like /Programs
Kinda like C:\Program files
that kinda thing.
But the revolution isn't just in the naming--it's in the whole structure. If it were really copying Windows, it wouldn't have called the user directory *Users*--it would have called it *Documents and Settings*.

"Programs" and "Program Files" are not the same, but they share one word, and that word makes sense, because it describes what's in there.

---

### Post by maniacmusician on 2006-11-07
I'm planning to wipe out my dapper installation soon and do a server install + kde...I think I'll also throw in Gobo Linux at the same time. Sounds interesting.

Off topic; It is amazing how much faster server + KDE is than just Kubuntu. I installed Kubuntu on my mom's old laptop, and server + KDE on my old laptop. Very similar specs...mine was much faster. Weird. But i'm happy.

---

### Post by angkor on 2006-11-07
Ooops!

---

### Post by SunnyRabbiera on 2006-11-07
> **aysiu said:**
> But the revolution isn't just in the naming--it's in the whole structure. If it were really copying Windows, it wouldn't have called the user directory *Users*--it would have called it *Documents and Settings*.

"Programs" and "Program Files" are not the same, but they share one word, and that word makes sense, because it describes what's in there.

But I like the linux structure as it is, there is no need for this in my opinion... just another way of making a windows like OS and Linux should stay linux.

---

### Post by ericesque on 2006-11-07
*Unrelated to file structure*

I know it's all configurable, but looking at the screenies... 

thatsa whole lotta ugly!

---

### Post by red_Marvin on 2006-11-07
I'm not that impressed.
I'd rather see the distros following the already standard setup.
But a some "standard" distros could be better at that too...

---

### Post by IYY on 2006-11-07
> well they say things like /Programs
Kinda like C:\Program files
that kinda thing.

The directory is called 'Programs' because it stores programs. It has nothing to do with Windows or Linux.

---

### Post by po0f on 2006-11-07
> **shining said:**
> Thanks, you just proved my point.

Thanks, for totally disregarding the rest of my post.

From your quote:
> ... and then remove it with an "rm -rf". ...

```
$ rm -rf /Programs
```

[quote=Some Hypothetical Newb]Whoops, I just mis-tabbed and lost all my programs!  **With no expcetions!**  Thank God they put them all in one convenient place![/quote]

---

### Post by shining on 2006-11-07
> **maniacmusician said:**
> I'm planning to wipe out my dapper installation soon and do a server install + kde...I think I'll also throw in Gobo Linux at the same time. Sounds interesting.


Yep, I've to try it too :)

> 
Off topic; It is amazing how much faster server + KDE is than just Kubuntu. I installed Kubuntu on my mom's old laptop, and server + KDE on my old laptop. Very similar specs...mine was much faster. Weird. But i'm happy.

Right, many users report the same, but it still surprises me. I wouldn't think just a few more services running would affect performance so badly that it's noticeable. Unless some of them are very hungry, in this case, which ones? Did someone investigate this?

---

### Post by .t. on 2006-11-07
It just encourages further segregation! If it ain't broke don't fix it.

How many Windows users know how the %SystemRoot% folder is laid out?

---

### Post by banjobacon on 2006-11-07
I voted "Good idea", but on second thought, I'm neutral.

Ideally, users should not have to deal with anything outside of their home directory, so it shouldn't matter where system files are.

---

### Post by aysiu on 2006-11-07
> **banjobacon said:**
> I voted "Good idea", but on second thought, I'm neutral.

Ideally, users should not have to deal with anything outside of their home directory, so it shouldn't matter where system files are.
Users don't have to install programs or launch them?

---

### Post by maniacmusician on 2006-11-07
> **ericesque said:**
> *Unrelated to file structure*

I know it's all configurable, but looking at the screenies... 

thatsa whole lotta ugly!
if you use gnome :rolleyes: most of the kde screenies look fine. Their default gnome sucks, but it's not that hard to add a theme and make it look good. I prefer KDE anyways.

---

### Post by angkor on 2006-11-07
> **aysiu said:**
> Users don't have to install programs or launch them?

Of course they do, but they don't need to know the location (path) of the actual files they're launching or installing. 'Users' (generalisation) just want to click an install button and double-click a shortcut in a menu or on their desktops.

---

### Post by Christmas on 2006-11-07
They look very good as they are now, they worked very good in the past 30 years, why change?

---

### Post by aysiu on 2006-11-07
> **Christmas said:**
> They look very good as they are now, they worked very good in the past 30 years, why change?
They've worked fine for X number of users the past 30 years. Why not make it work for X+Y users?

GoboLinux still maintains a traditional structure through symlinks.

I don't know if you buy this explanation, but GoboLinux does give one: > **``There is a reason why things are the way they are''**

This is something I hear constantly, often followed by an explanation about the difference between /, /usr and /usr/local, and/or /bin and /sbin. I do understand the difference1. If I did away with this three-level distinction, is because I believe there are other ways to approach the problems this distinction tries to solve. In a GoboLinux system, the argument for having separate /usr and /usr/local trees in order to separate programs shipped by the distribution and compiled by the user clearly does not hold. Each program is naturally separated, and this was the prime intention of creating GoboLinux in the first place.

The historical reason why Unix systems have some of its tree directly at the root partition (/bin, /lib, /sbin) as opposed to having it under /usr, is because this way you can boot in a bare-bones single-user rescue mode using those files only, in order to fix problems in the /usr tree. This is arcane. When I need to rescue my system, I can use a fully-featured live CD that runs a complete Linux distribution with a graphical desktop, that allows me to browse the web and search for the solution to my problem, and use all of the features of a regular system to fix it. I understand the rationale for having a bare-bones rescue mode decades ago, but we have a better solution in our hands now.

The distinction between bin and sbin makes no sense, in the present context. Historical evolution led to crazy arbitrary distinctions, like ping and traceroute lying in different directories (I fail to see how can they be of distinct ``program classes'', by any measure). Unix systems have a permissions system. If one wants only the superuser to be able to run a command, then chmod 700 it. I suspect the separation could have been conceived to reduce the number of programs in the $PATH of regular users. In today's Linux systems, having 400 or 500 programs in your $PATH, does not make any difference.

There is one last argument, however, that is still valid for Linux systems to day: partitioning and remote mounting. Those two are really different shades of the same color, with remote mounting being, to my eyes, the most valid concern of those two. I've seen arguments about this among the lines of ``hard drives today are cheap, and you'll most likely have all software installed locally anyway, for performance''. I agree with this, but I also understand the ones who'd like to maintain things centralized for administrative purposes. But imposing additional complexity on the overall system because of one particular scenario is usually not a good thing, and even then, the traditional Unix solution is not general enough: what if you have three or four application servers? You'll mount one at /usr, one at /opt, and then what? There goes the traditional Unix tree. In fact, in most of the larger Unix networks I had contact with, particular needs of the site configuration led to non-standard directories added to the Unix tree.

Fortunately, like with the live CD, we have nowadays a technological advancement that serves as a real solution to the problem: union mounts, also known as overlay filesystems. The idea is that you can mount several partitions in the same directory. This way, the semantics of /Programs as ``the collection of all programs available in the system'' is retained, independently of the physical location of the actual data. File systems are all about abstraction (we don't refer to files based on their track, sector and cylinder address), this progresses a step further. Overlay filesystems are very flexible: the sysadmin, for example, can overlay site-specific settings for an application on top of the defaults exported over NFS. Unfortunately, it is not in widespread use, for reasons beyond by understanding. The Plan 9 operating system has it as one of its basic filesystem operations: the bind command (in Plan 9, for example, you don't need a $PATH variable, because all directories containing executables are ``bound'' in a single directory). There is an implementation of an overlay filesystem for Linux: ovlfs.  By the way, in life, rarely do things either "work" or "not work." Plenty of things that "work" could work better or be improved upon.

After all, for eons before computers arrived, not having computers "worked" for people. Does that mean we should have never adopted computers?

---

### Post by jc87 on 2006-11-07
To be honest i don't see a real need in changing the filesystem,
you can set Nautilus to show only the directories you need, for me that has been only /home and /media, ocasionally /etc by the CLI and that is all.

---

### Post by jpkotta on 2006-11-07
> **Christmas said:**
> They look very good as they are now, they worked very good in the past 30 years, why change?

++

It seems that the Gobo layout doesn't quite preserve all of the same notions as the traditional layout.  /bin, /usr/bin, and /usr/local/bin are all different for a reason*.  And I completely agree with everyone who said that users shouldn't really be poking around in the file tree anyway; those that should can learn.  As my signiture says, "Those who do not understand Unix are condemned to reinvent it, poorly."

*The reasons are as follows, I think:  /bin is for absolutely essential programs, /usr/bin is for things that the user will use, i.e. applications, and /usr/local/bin is for programs that are specific to *this* machine (/usr may be a network drive shared by many computers).

---

### Post by chaosgeisterchen on 2006-11-07
I have a rather neutral point of view.

It could become great as a new standard but no one sticks to the standards in the Linux world nowadays.. every distributor tries to be individual by reinventing the wheel.

That's another story but I like the idea but do not think that it's needed. Might be better for newbies to accomodate to Linux. It's a more human readable file tree.

---

### Post by aysiu on 2006-11-07
If you don't like GoboLinux's model, that's fine, but please **understand** it before you criticize it.

---

### Post by chaosgeisterchen on 2006-11-07
> **aysiu said:**
> If you don't like GoboLinux's model, that's fine, but please **understand** it before you criticize it.

Could you please next time quote the user briefly before responding?

I do not know whether your posting went towards mine or the one above the mine.

---

### Post by sethmahoney on 2006-11-07
> **ember said:**
> It is a good idea, I think. 

Yet it imposes different problems. For me as a German it is disputable whether it makes sense to have shortforms of English words mapped to longer English words. 

On the other hands I like the structure Gobo Linux makes. 

Eventually it just leaves the question whether symlinks will work as expected in all situations.

Actually, funny thing that: This exact same idea could be used to translate the filesystem.  There's no reason that /Programs HAS to be in English if its all symlinked anyway.  By simply mapping the various symlinks to the appropriate folders in whatever language you want your system to work in, native-language folders could be implemented, and with a little planning this wouldn't break anything.

---

### Post by banjobacon on 2006-11-07
> **aysiu said:**
> Users don't have to install programs or launch them?

Isn't that what package managers and application menus are for?

---

### Post by sethmahoney on 2006-11-07
> **banjobacon said:**
> Isn't that what package managers and application menus are for?

It seems to me that, to some degree, either the underlying system should reflect the visual representation of the GUI, or the GUI should reflect the underlying system.  Taking a look at those two options, changing the file structure around seems to make for a much better user experience than graphically representing the file structure as it is now...

---

### Post by theicyj on 2006-11-07
This could be a good idea, probably won't happen though.

---

### Post by Jucato on 2006-11-07
I voted yes, for a few reasons:

1. The UNIX/Linux Filesystem Heirarchy Standard has not really been that easy to understand, specially for a new user trying to get into Linux. True, the FHS has worked for decades, but that doesn't mean it will work forever in the same way. Also, the FHS was originally made for the sake of system administrators, not end users.

2. My (emphasis on **my**) own philosophy is that users should learn about the FHS only when they need to or if they want to. In other words, when they are predisposed to do so. Pushing them to learn stuff on the go would only increase the probability of committing errors. And we all know how dangerous it is to commit errors on system directories. sudo can only do so much when there is a PEBKAC error (Problem Exists Between the Keyboard and Chair). Don't get me wrong. I do want users to learn about the FHS, but in their own time. What GoboLinux is doing is letting users not worry about the FHS until that time. This isn't about dumbing down the FHS, but presenting it in a way that would be meaningful and useful to users.

3. Innovation. Just because something already works doesn't mean there's absolutely no room for change. The "if it ain't broke, don't fix it" philosophy is true only in a certain sense, but not always. If we all waited for something to be broken before thinking of new ways to do things, we'd be living a pretty boring life.

I think the best part of what GoboLinux is doing is that (if I read it right) it still preserves the original FHS while doing their own setup. If they can do that, without messing up the "old way", then why not? New users can stick to the default, and probably learn from there. 

Kubuntu has already done something quite similar, but less revolutionary, by hiding the root directories except for /home and /media. The directories are still there, but hidden. And you can configure, through the editing of a config file (but hopefully through a GUI, soon) which directories will be hidden, or if they'll be hidden at all.

---

### Post by hanzomon4 on 2006-11-07
I like it mainly because it appears to allow you to install an app by just moving the apps directory in your PATH. Reminds me of Rox appdirs and OSX .apps
If this was standard would it make debs and rpms unnecessary?

---

### Post by ember on 2006-11-07
> **sethmahoney said:**
> Actually, funny thing that: This exact same idea could be used to translate the filesystem.  There's no reason that /Programs HAS to be in English if its all symlinked anyway.  By simply mapping the various symlinks to the appropriate folders in whatever language you want your system to work in, native-language folders could be implemented, and with a little planning this wouldn't break anything.

Yet the problem is the same as it is with Windows. If an application is not localised properly, it will just try to install into the "English" folder.

---

### Post by Polygon on 2006-11-07
interesting. if it doesnt really break anythng, it couldent hurt. I mean mac os x pulled this off somehow, and it works fine for them.

---

### Post by hanzomon4 on 2006-11-08
This could really change things for linux. If all the stuff an app needed to run was included in its appdir then stuff like updating a lib to get some app to work, breaking dependences for other apps in the process, would be a thing of the past.

---

### Post by henriquemaia on 2006-11-08
My opinion: bad idea.

But my opinion doesn't count much.

---

### Post by sethmahoney on 2006-11-08
> **ember said:**
> Yet the problem is the same as it is with Windows. If an application is not localised properly, it will just try to install into the "English" folder.

Since everything is simlinked, couldn't you just install using the standard unix paths?  That is, since /usr/bin is a link that points to /Programs (or whatever name in whatever language), when a program tries to install to /usr/bin, it will install to the proper folder.  It really shouldn't require any localization whatsoever on the part of the installer so long as the system is correctly set up.

---

### Post by Chayak on 2006-11-08
Change it to make it easier? It makes me type more just to be more 'readable' for people who don't want to take the time to learn the standard system that everyone else will continue to use because it's a set standard across Unix hence you step outside of gobo and you have no idea what other *nix system structures are.

---

### Post by sethmahoney on 2006-11-08
> **henriquemaia said:**
> My opinion: bad idea.

But my opinion doesn't count much.

Why do you think its a bad idea?

---

### Post by argie on 2006-11-08
> **Chayak said:**
> Change it to make it easier? It makes me type more just to be more 'readable' for people who don't want to take the time to learn the standard system that everyone else will continue to use because it's a set standard across Unix hence you step outside of gobo and you have no idea what other *nix system structures are.

Apparently they symlinked the "standard" directories to these new directories so you shouldn't have to type more after all. Nothing to say about the rest of the post.

I have one problem with it, and it's rather unique to my old computer. If each application has its own directory with its own libraries in there, wouldn't that take up lots of space? I mean, imagine KDE libs repeated again and again for every KDE program. My old computer has a 2.1GB hard drive. This isn't going to work for me there, at least.

I really have no trouble with the current filesystem though, and I'm far from an expert. I don't even know what /usr or /opt are for, or even why /proc is supposedly special. And life's been fine in Ubuntu. Is this even necessary?

---

### Post by sethmahoney on 2006-11-08
> **argie said:**
> Apparently they symlinked the "standard" directories to these new directories so you shouldn't have to type more after all. Nothing to say about the rest of the post.

I have one problem with it, and it's rather unique to my old computer. If each application has its own directory with its own libraries in there, wouldn't that take up lots of space? I mean, imagine KDE libs repeated again and again for every KDE program. My old computer has a 2.1GB hard drive. This isn't going to work for me there, at least.

I really have no trouble with the current filesystem though, and I'm far from an expert. I don't even know what /usr or /opt are for, or even why /proc is supposedly special. And life's been fine in Ubuntu. Is this even necessary?

Oh, the impression I got wasn't that each proggy gets its own folder, but that there is one folder where they all go, /Programs, unlike standard *nix, which has a few places programs live.

---

### Post by argie on 2006-11-08
> **sethmahoney said:**
> Oh, the impression I got wasn't that each proggy gets its own folder, but that there is one folder where they all go, /Programs, unlike standard *nix, which has a few places programs live.
Well that too. They're all in /Programs, but they each have their own folder.

[quote=http://www.gobolinux.org/index.php?page=at_a_glance]
GoboLinux is a modular Linux distribution: it organizes the programs in your system in a new, logical way. Instead of having parts of a program thrown at /usr/bin, other parts at /etc and yet more parts thrown at /usr/share/something/or/another, **each program gets its own directory tree,** keeping them all neatly separated and allowing you to see everything that's installed in the system and which files belong to which programs in a simple and obvious way.
[/quote]
It's all very clear here:
[http://www.gobolinux.org/index.php?page=at_a_glance](http://www.gobolinux.org/index.php?page=at_a_glance)

---

### Post by TheWizzard on 2006-11-08
>  Originally Posted by [http://www.gobolinux.org/index.php?page=at_a_glance](http://www.gobolinux.org/index.php?page=at_a_glance)
GoboLinux is a modular Linux distribution: it organizes the programs in your system in a new, logical way. Instead of having parts of a program thrown at /usr/bin, other parts at /etc and yet more parts thrown at /usr/share/something/or/another, each program gets its own directory tree, keeping them all neatly separated and allowing you to see everything that's installed in the system and which files belong to which programs in a simple and obvious way.

this i don't like: 
1) i'm really fond of the /etc directory. i always make backups of /etc and this is my first aid kit when i run into trouble. 

2) i like the use of package managers (instead of removing complete directories). see above. for building from source i use checkinstall to make a deb package so my package manager can use it. 

3) for normal users there's no reason to look outside their home directory. 


nevertheless, i think the current filesystem can use some cleaning-up.

---

### Post by mssever on 2006-11-08
Good idea as it simplifies program installation. I have no objection to the standard format (and I use it without difficulty), but if you don't use a package manager, you can end up with a bit of a messy filesystem after a while. As I understand Gobo, all you need to do to compile from source is to do ```
./configure --prefix=/Programs/foo/1.2.3 && make && su -c 'make install'
``` and everything is automatically installed neatly without needing a package manager. And it works for *any* program, even if it doesn't use make. And uninstalling is a snap, as well. If you try this in a standard distro, you're likely to end up with stuff scattered all over the system--not as badly as Windows, but worse than MacOS. Gobo's way makes RPM pointless, and the only missing features from APT are automatic updates and rependency resolution. Of course, this is only what I've gleaned from the website. I'll be trying the Gobo live CD soon.

One minor objection: IMO, the names of standard directories should be all lowercase (/programs, not /Programs) to facilitate typing. Plus, if everything is in lowercase, it's one less thing to remember. I have the same complaint with the various X11 directories on normal distros. They should all be x11.

A final point: All the complaints about not having the standard directories or having more to type are ignorant. The website *clearly* states that the standard paths work. Period.

---

### Post by argie on 2006-11-08
> **argie said:**
> 
I have one problem with it, and it's rather unique to my old computer. If each application has its own directory with its own libraries in there, wouldn't that take up lots of space? I mean, imagine KDE libs repeated again and again for every KDE program. My old computer has a 2.1GB hard drive. This isn't going to work for me there, at least.


I just wanted to say that this is wrong. The libraries are shared just like usual. So that problem really doesn't exist.

---

### Post by RAV TUX on 2006-11-08
moving to other OS forum

---

### Post by Erik Trybom on 2006-11-08
I read the "clueless" article and it straightened up most things. I think Gobo Linux have some good ideas.

However, there is one thing I'm worried about - he said that it's not worth it using another package manager with Gobo Linux. Is this because of the file system or something else? 

I like the new hierarchy, but if it's incompatible with apt-get we cannot have it in Ubuntu. Apt is the best thing about running a Debian-based distro.

---

### Post by megamania on 2006-11-08
> **aysiu said:**
> But the revolution isn't just in the naming--it's in the whole structure. If it were really copying Windows, it wouldn't have called the user directory *Users*--it would have called it *Documents and Settings*.

"Programs" and "Program Files" are not the same, but they share one word, and that word makes sense, because it describes what's in there.

right, Aysiu. And I think we should all stop thinking "if it's like Windows, it's wrong". Otherwise, we could end up calling the desktop windows "doors", just because "windows" was adopted by Microsoft and it *has* to be wrong.

And if "program files" makes more sense (and I repeat "if" - it's just an example), why not use it in Linux?

I'm starting to hate this "we have to be different, no matter what" story. I think sometimes we miss some steps in the right direction just because of this attitude.

---

### Post by frup on 2006-11-08
For those who say new users should learn the file system or not go poking around I have one question: How long had you been using linux before you were told to edit sources.list or fstab or whatever. Usually within the first 3 weeks I'm guessing. New users are often intimidated by the file system, They dont have any idea about how programs are installed etc etc etc.

Being able to install are program in one place will make things appear easier. I think this is a great example of how open source development should work too. Experimentation. watch it if it works, copy it.

I like it the way it is now, but it took time to get used to. I didn't understand repositories. I wanted 3rd party software, the latest versions, I wanted to install things myself just by click on an install.exe or whatever. If it's not for you, it could be for some people.

:-k

---

### Post by chuckyp on 2006-11-09
Well its not really a file structure but their way of hiding the mess that linux file system creates.

[http://gobolinux.org/index.php?page=at_a_glance](http://gobolinux.org/index.php?page=at_a_glance)

Look like a neat idea for feisty.  Hiding many of the directories would be nice.

---

### Post by Amon_Re on 2006-11-09
Reminds me of OS X....
The idea is sound tho, i even played with an idea like this  way back (making my own "linux distribution" with an AmigaOS like directory structure), but i lost intrest once it became aperant that i hadn't had the faintest idea about rolling my own distro :-k

---

### Post by Lord Illidan on 2006-11-09
It looks nice...but I don't think it is a priority for the devs. How many people go through /usr/bin or /etc anyway?

Read this, illuminating : [http://gobolinux.org/index.php?page=doc/articles/clueless](http://gobolinux.org/index.php?page=doc/articles/clueless)

---

### Post by aysiu on 2006-11-09
Merged the Feisty thread with this Other OS Talk thread. If people get very serious about proposing the change for Feisty, we can move this merged thread to Feisty, but it makes sense to have all the discussion about this in one place. How many GoboLinux threads can you have?

---

### Post by paparucino on 2006-11-09
> **chuckyp said:**
> Well its not really a file structure but their way of hiding the mess that linux file system creates.

[http://gobolinux.org/index.php?page=at_a_glance](http://gobolinux.org/index.php?page=at_a_glance)

Look like a neat idea for feisty.  Hiding many of the directories would be nice.
I don't agree since I like to see all the files on my disks. Hiding files is like to work under windows. :-)

---

### Post by sethmahoney on 2006-11-09
> **paparucino said:**
> I don't agree since I like to see all the files on my disks. Hiding files is like to work under windows. :-)

It doesn't actually hide any files.  It just cleans up the folder structure.  And Linux systems already hide folders anyway.

---

### Post by po0f on 2006-11-10
From Lord Illidan's link posted above:

[quote=GoboLinux]... typing /Programs takes the exact same number of keystrokes as typing /usr: slash, lowercase p, Tab.[/quote]

So is their filesystem also case-insensitve?  I really hope Ubuntu devs decide this is all stupid and don't include it in Fiesty, Fiesty+1, or ever.

---

### Post by paparucino on 2006-11-10
> **.t. said:**
> Bah. Just means lazy people don't have to learn. Makes it more like Windows. People should learn it; it's a good exercise! It will help them later on, especially if they deal with programs referring to the "old" conventions.
I don't agree with the structure of Gobo and I don't agree with your opinion.
People need a very very simple machine, what we, her, call idiot proof and the only way to obtain this is to show them a box, an icon and the way to change desktop backgrounds.

---

### Post by paparucino on 2006-11-10
> **aysiu said:**
> Users don't have to install programs or launch them?
They have, but like in windows, if the program runs everything is ok otherwise they call a friend or assistence. Final user, imho, must have a lot of icons and box to play with. Stop. He is not interested in learning what's a sym link or a library or what is a database. It must run.

---

### Post by aysiu on 2006-11-10
> **paparucino said:**
> They have, but like in windows, if the program runs everything is ok otherwise they call a friend or assistence. Final user, imho, must have a lot of icons and box to play with. Stop. He is not interested in learning what's a sym link or a library or what is a database. It must run.
Who says a user has to learn what a symlink or a library is?

Users still have to install programs, and if they're all in one directory called *Programs*, that makes it pretty simple, doesn't it?

There are many things Mac OS X does **not** do well, but one of the things it does do well is have a balance of complexity in file structure (basically your typical *nix-like breakdown) and simplicity for the end user. Most end users see Documents and Applications and whatever devices they plug in. That's it. You install applications by dragging them to the Applications folder. That's it.

That's how it should be. I love package management, but there's no reason you couldn't have Apt **and** a sensible file structure for the end-user.

---

### Post by TheWizzard on 2006-11-10
> **aysiu said:**
> Who says a user has to learn what a symlink or a library is?

Users still have to install programs, and if they're all in one directory called *Programs*, that makes it pretty simple, doesn't it?

There are many things Mac OS X does **not** do well, but one of the things it does do well is have a balance of complexity in file structure (basically your typical *nix-like breakdown) and simplicity for the end user. Most end users see Documents and Applications and whatever devices they plug in. That's it. You install applications by dragging them to the Applications folder. That's it.

That's how it should be. I love package management, but there's no reason you couldn't have Apt **and** a sensible file structure for the end-user.


i agree that a sensible file structure and a package manager can be compatible. 
however, in traditional *nix, *all files are grouped according to purpose* and i think this should be remained. e.g. i do really like the /etc folder, a backup doesn't take much space and is extremely usefull for troubleshooting and for re-configuring after a clean install. 

basically i think cleaning up the file-system is a great idea, but the functionality should determine the grouping. 
cleaning up the file-system can also be done by hiding the folders in konqueror. this is the osx way to make stuff easier. 

> You install applications by dragging them to the Applications folder. That's it.

this is - in the end - more complicated than just using a package manager. or, download the deb, richtclick -> install package.

---

### Post by aysiu on 2006-11-10
> **TheWizzard said:**
> i agree that a sensible file structure and a package manager can be compatible. 
however, in traditional *nix, *all files are grouped according to purpose* and i think this should be remained. e.g. i do really like the /etc folder, a backup doesn't take much space and is extremely usefull for troubleshooting and for re-configuring after a clean install. 

basically i think cleaning up the file-system is a great idea, but the functionality should determine the grouping. 
cleaning up the file-system can also be done by hiding the folders in konqueror. this is the osx way to make stuff easier. 


this is - in the end - more complicated than just using a package manager. or, download the deb, richtclick -> install package.
I don't see how dragging an application to the Applications folder is more complicated than downloading a .deb and right-clicking on it.

You're right, though, that it's more complicated than using the package manager to install/remove applications.

Still, ideally, you could set up a system that allows you to have a drag-to-applications-folder capability **and** a package manager.

---

### Post by TheWizzard on 2006-11-10
> **aysiu said:**
> I don't see how dragging an application to the Applications folder is more complicated than downloading a .deb and right-clicking on it.

You're right, though, that it's more complicated than using the package manager to install/remove applications.

Still, ideally, you could set up a system that allows you to have a drag-to-applications-folder capability **and** a package manager.

ok, but how about miming a user-level file structure, while remaining the purpose-oriented file structure under the hood? 
then we can have the best of two worlds, can't we.

---

### Post by aysiu on 2006-11-10
> **TheWizzard said:**
> ok, but how about miming a user-level file structure, while remaining the purpose-oriented file structure under the hood? 
then we can have the best of two worlds, can't we.
I thought that's what GoboLinux sought to do. Maybe I'm not understanding it correctly.

My understanding is that the Programs folder has everything for the programs, but that the appropriate symlinks are in place to mimc the file structure under the hood you're talking about.

---

### Post by tehkain on 2006-11-30
Is the gobuntu name taken? With the symlinks working I do not see it being a bad idea. Maybe as an option at install, assuming it works nicely with the package manager, it could be great for a starter linux user who is overwhelmed. To the "makes it more like Windows"  comments, the proposed way gobo works is cleaner then even windows. I know the names might be similar but who cares if it accurately describes the files it contains. If it works then i don't care if its "windows like" since there are alot of things that do not work in windows and ubuntu is doing great with, so if you are going to build a usable OS why not use the best ideas?

I would stick with the standard structures on my pc but this would help my friends who are competent in their native OS but have yet to touch linux.

---

### Post by Grog140 on 2006-11-30
This system is wonderful. I would drop Ubuntu and switch right now if I didn't loath KDE so much.

I think it would do the Linux world wonders to have this ported to a distro that is popular...*cough*Ubuntu*cough* If you want to attract new users then there is absolutely no reason NOT to implement it since the current method is very complicated for an average person.

If you can give me a reason why it is a bad idea without saying because its the way it has always been, or simply saying that it builds character to learn the way it is now or something like that then I will listen.

The problem that Linux faces which prevents it from widespread adoption is the Linux hardcores who tent to have final say over the matter not seeing what will attract more users. And is some cases don't want to attract more users. They think they are in some sort of 1337 club because they can memorize the Linux file hierarchy and wishes it were still that fact that only the "hackers" could use it.

So basically it is my opinion that what really prevents Linux from widespread use on the desktop is these kinds of debates. And similar ones like the proprietary drivers debate. When the Linux veterans resist change for the better because it is different but will allow a more user friendly experience then there is an even more urgent problem that needs to be fixed.

---

### Post by angkor on 2006-12-01
> **Grog140 said:**
> This system is wonderful. I would drop Ubuntu and switch right now if I didn't loath KDE so much.

What's stopping you from uninstalling kde and replacing it with your favorite DM?

[QUOTE=Grog1]
The problem that Linux faces which prevents it from widespread adoption is the Linux hardcores who tent to have final say over the matter not seeing what will attract more users. And is some cases don't want to attract more users. They think they are in some sort of 1337 club because they can memorize the Linux file hierarchy and wishes it were still that fact that only the "hackers" could use it.[/quote]

Nobody has a final say about anything. If you want to change something you can go right ahead and build your distro according to your wishes. That's what GoboLinux has done.

[QUOTE=Grog1]So basically it is my opinion that what really prevents Linux from widespread use on the desktop is these kinds of debates. And similar ones like the proprietary drivers debate. When the Linux veterans resist change for the better because it is different but will allow a more user friendly experience then there is an even more urgent problem that needs to be fixed.[/QUOTE]

How can a debate prevent anything? Of course people are going to debate changes before making a decision. I wouldn't want to install Gobo on a mission critical machine without at least reading about the experiences of Gobo's users. The only thing stopping Linux from widespread use (world domination?) is money.

---

### Post by RAV TUX on 2006-12-01
GoboLinux is a pretty basic concept, which I think is a good idea:

> [B]I am not clueless  
[SIZE=+1]or[/SIZE]  
Myths and misconceptions about the design of GoboLinux[/B]

 [CENTER]**Hisham H. Muhammad**[/CENTER]
 [INDENT] [RIGHT] *``Those who do not understand Unix * 
*are doomed to reinvent it, poorly.''* 
*- Henry Spencer, 1987* [/RIGHT]
 [/INDENT] This week we had another release of GoboLinux, and again a number of people, even if indirectly, called me ``clueless'' for coming up with such a structure for a Linux distribution, for a number of reasons. None of those reasons was new; I heard all of them many times. This article is an attempt to sum them up, and explain why I chose the design decisions I made, hopefully clearing any pending misconceptions. I don't have illusion this will prevent them keep happening, but at least I'll have a text to point people to. This article ranges from common misconceptions from those who have never used GoboLinux, to well-intentioned but poorly-thought-out ideas that keep coming from time to time to the GoboLinux mailing list, often causing long debates. I'll be separating the points in sections and they are meant to be self-contained, so feel free to skip directly to the ones that interest you, if you don't feel like reading the whole thing.    
** ``There is a reason why things are the way they are'' **

   This is something I hear constantly, often followed by an explanation about the difference between /, /usr and /usr/local, and/or /bin and /sbin. I do understand the difference[1]("http://www.gobolinux.org/index.php?page=doc/articles/clueless#foot176"). If I did away with this three-level distinction, is because I believe there are other ways to approach the problems this distinction tries to solve. In a GoboLinux system, the argument for having separate /usr and /usr/local trees in order to separate programs shipped by the distribution and compiled by the user clearly does not hold. Each program is naturally separated, and this was the prime intention of creating GoboLinux in the first place.  
 The historical reason why Unix systems have some of its tree directly at the root partition (/bin, /lib, /sbin) as opposed to having it under /usr, is because this way you can boot in a bare-bones single-user rescue mode using those files only, in order to fix problems in the /usr tree. This is arcane. When I need to rescue my system, I can use a fully-featured live CD that runs a complete Linux distribution with a graphical desktop, that allows me to browse the web and search for the solution to my problem, and use all of the features of a regular system to fix it. I understand the rationale for having a bare-bones rescue mode decades ago, but we have a better solution in our hands now.  
 The distinction between bin and sbin makes no sense, in the present context. Historical evolution led to crazy arbitrary distinctions, like ping and traceroute lying in different directories (I fail to see how can they be of distinct ``program classes'', by any measure). Unix systems have a permissions system. If one wants only the superuser to be able to run a command, then chmod 700 it. I suspect the separation could have been conceived to reduce the number of programs in the $PATH of regular users. In today's Linux systems, having 400 or 500 programs in your $PATH, does not make any difference.  
 There is one last argument, however, that is still valid for Linux systems to day: partitioning and remote mounting. Those two are really different shades of the same color, with remote mounting being, to my eyes, the most valid concern of those two. I've seen arguments about this among the lines of ``hard drives today are cheap, and you'll most likely have all software installed locally anyway, for performance''. I agree with this, but I also understand the ones who'd like to maintain things centralized for administrative purposes. But imposing additional complexity on the overall system because of one particular scenario is usually not a good thing, and even then, the traditional Unix solution is not general enough: what if you have three or four application servers? You'll mount one at /usr, one at /opt, and then what? There goes the traditional Unix tree. In fact, in most of the larger Unix networks I had contact with, particular needs of the site configuration led to non-standard directories added to the Unix tree.  
 Fortunately, like with the live CD, we have nowadays a technological advancement that serves as a real solution to the problem: *union mounts*, also known as *overlay filesystems*. The idea is that you can mount several partitions in the same directory. This way, the semantics of /Programs as ``the collection of all programs available in the system'' is retained, independently of the physical location of the actual data. File systems are all about abstraction (we don't refer to files based on their track, sector and cylinder address), this progresses a step further. Overlay filesystems are very flexible: the sysadmin, for example, can overlay site-specific settings for an application on top of the defaults exported over NFS. Unfortunately, it is not in widespread use, for reasons beyond by understanding. The Plan 9 operating system has it as one of its basic filesystem operations: the bind command (in Plan 9, for example, you don't need a $PATH variable, because all directories containing executables are ``bound'' in a single directory). There is an implementation of an overlay filesystem for Linux: ovlfs.  
  
** The alleged user-friendliness of longer names **

   Many, many people, when they stumble upon GoboLinux, look at the long, descriptive directory names and say ``Look! They changed the Linux directory names by making them longer and descriptive to make the system friendly!''. There is some people who say this as if this were a good thing, and some people who say this as if this were a bad thing. Both are wrong.  
 There is a number of reasons why the names in GoboLinux are the way they are, and none of them is ``to attract new users who are scared by /etc and the like''. The number one reason is: to not conflict with the Unix namespace. And when I say Unix namespace I actually mean the Linux namespace, which is not a very well settled thing. This is not like a set of reserved keywords from a programming language that says not to use if, while, repeat, etc. as variable names and the rest is okay. You never know what directories, files and programs will show up tomorrow, so the best I could do was to pick names that were very unlikely to be ever used. Others did that before me, and that worked, so I followed their example: NeXT and Mac OS X had to make their own directories coexist with Unix directories, so they capitalized the names, and while they were at it, they used full words instead of abbreviations. The abbreviations were a sign of the times from the origins of Unix. Dennis Ritchie once said that if he could go back in time and change only one thing in Unix, he'd rename the creat system call to create.  
 The one thing that reassures me that my decision was right is that, when we started with GoboLinux, back in the days of Linux 2.4.something, someone asked me ``why didn't you pick /sys instead of /System? That would be easier to type''. You can guess what would have happened, now that the kernel guys reserved /sys for their own use. In fact, the concerns on typing-friendliness always comes up in discussions about the GoboLinux tree. To that, I can only respond that, in a properly configured shell like the one that comes by default with GoboLinux, typing /Programs takes the exact same number of keystrokes as typing /usr: slash, lowercase p, Tab.  
 One could also ask: but why change the directories, for starters? Why not simply use the regular directory tree and make it behave like GoboLinux? Yes, I suspect it could be possible, but from an operating system design standpoint, I don't like the idea. I am not comfortable with the concept of a system where well-known directories have different semantics to those that most people expect. AtheOS, for example, has this problem. You see a /usr directory, but that is no /usr. In AtheOS, it behaves more like /opt, but unexplicably keeping the name that historically stood for ``user'' and then was turned into a backronym for Unix System Resources. Even if Kurt Skauen called it /opt, it would still be strange; those are not ``optional packages''.  
 The GoboLinux directories, too, have different semantics from the Unix directories. /Programs is the collection of all programs available in the system, where each subdirectory contains all files from a given program (the distinction of a program package is up to the developers of each project; the various tools from CoreUtils form a single program). Each subdirectory in /System/Links contains a *view* (in the database sense of the term) of each file class from the programs collection: libraries, executables, headers, and so on[2]("http://www.gobolinux.org/index.php?page=doc/articles/clueless#foot177"). You see, these directories are not the Unix directories, they function differently, from an administrative point of view. I believe it is good design to make this explicit in the names.  
 For strict compatibility reasons, however, we have an extra set of symbolic links with the Unix names pointing to the closest GoboLinux equivalents (even making a few concessions in the GoboLinux side of the equation in order to preserve this compatibility). The fact that these are links, and we call them the *legacy* tree keeps this notion very clear. The work of Lucas Villa Real and Felipe Damasio on GoboHide, the kernel patch for true hidden directories on Linux, further isolates the legacy tree as an isolated accessory.  
  
** Do you want to change the standard? **

   Of course not. For starters, we're not that naive to think that we could. But the actual reason why we don't want to change the standard is because we believe *there should be no standard*. I know this statement may sound even bolder than talking about changing a standard, but the reason I say that is because we believe it is the duty of each application to allow itself to be installed anywhere and to accept that other applications it needs to work with may be installed anywhere (more on this in the next section). Now, if there was a standard stating this, I'd even sign a petition to support it. In fact, there is: the GNU release standards, when they recommend the usage of GNU Autotools, supporting the -prefix family of switches, and probing for the location of applications with the configure script, do just that. But when a proposed standard like the FHS gives me an arbitrary list of binaries that should be, for unexplained reasons, in a separate directory, I laugh at that.  
 Different situations imply different needs, and so-called standards that attempt to fit every feet in the same shoe are doomed to failure. Standardize on flexibility instead. That's not we don't propose the GoboLinux tree as a standard to be followed by anyone else. In five, ten or twenty years, we may have completely different needs from the ones we have today. I don't want that the move away from the GoboLinux tree then to be as hard as the move away from the traditional Unix tree is today. Which leads us naturally to our next section...  
  
** An uphill battle to change all applications **

   This is not as hard as it seems. Before the first version of GoboLinux was fully built, I had already worked on and improved this model for about a whole year. When André Detsch and I got around to build, in two days, a system from scratch built around those concepts, I already knew that this was perfectly feasible.  
 I work in an university environment, and I have for many years. There, I am not the superuser, so I have to install every extra app I need in my $HOME directory. This is a perfectly common situation, it is expected that any decent application will allow this, and the vast majority of them do. In fact, one could argue that an app that doesn't has a broken build system. If you can install Gimp on /usr, or /opt, or /home/hisham, then you can install it on /Programs/Gimp/2.0/. Experience has shown that very few applications need to have their Makefiles dissected in order to cooperate. Even superuser-oriented software has (or should have) this flexibility: in a regular Unix system, the superuser should have the option to choose between, say, /sbin and /usr/sbin. There is no reason to have hardcoded paths in programs and installers[3]("http://www.gobolinux.org/index.php?page=doc/articles/clueless#foot179").  
 A more delicate problem arises when a program, even though it allows itself to be installed under any directory, wrongly assumes that another programs it depends on is installed under the same directory. As you can guess, this is a major source of problems for GoboLinux, but I advocate this needs to be fixed for the benefit of the entire free software community. Let's return to the $HOME directory scenario. What if my favorite GNOME component was not installed by the system administrator, and I want to install it in my $HOME, while still using the rest of GNOME installed at /usr? Situations like this, especially in big multi-component software, is often problematic. There is a number of programs that solve this problem using a $PATH-like environment variable: $GTKPATH, $PERL5LIB, $KDEDIRS, $PYTHON_PATH, and so on. There is no reason to make a monolithic installation a requirement.  
 So, the battle GoboLinux is fighting with regard to installation paths is not specific to us; we are only exposing problems on the flexibility of installation of applications, that happen not only in our tree, but anywhere a user has a custom installation need. I see that the situation has improved greatly in the last few years, with more and more projects adopting GNU Autotools.  
  
** ``It's easier to compile all programs relative to the same tree'' **

   Sure it is. This is a point that comes up from time to time on the GoboLinux mailing list, when people suggest us to either model /System/Links after a regular Unix tree, with subdirectories such as bin, lib, etc., or just compile everything relative to /usr and let the legacy tree ensure that everything keeps working. People who suggest this are also implicitly suggesting one of two things: to compile relative to a tree and then install relative to another; or to compile relative to a tree and then use a redirection hack on installation. I don't like any of the two approaches. In the first one, you are expecting a certain flexibility from the build system that is not always there, but unlike the points I raised on the previous section, it is not justifiable that this flexibility *should* be in the application's build system in the first place[4]("http://www.gobolinux.org/index.php?page=doc/articles/clueless#foot107"). As for the second approach, I don't like the idea of an operating system built around a hack that can be at any moment circumvented by a new system call or some unorthodox access method. Some might say that GoboHide, for example, also falls in this ``low-level hack'' territory. I point out, then, that GoboHide is not mandatory: GoboLinux is designed to work with a vanilla Linux kernel[5]("http://www.gobolinux.org/index.php?page=doc/articles/clueless#foot181").  
 But instead of pointing flaws in the proposed alternatives, I'd prefer to constructively defend my original design decision. Our idea, with GoboLinux, is to exercise this new approach with self-contained directories and assess its impact on system management, and we have been collecting exciting results. If instead we just used every possible stratagem to make apps ``easier to compile'', I believe we would be detracting ourselves from this goal. When I run ls -l /System/Links/Executables and see *all* executables from my system, and the programs they belong to, I see a clean system design. I would hate to look at /System/Links (or whatever the directory would be called) and see within the Unix mess emulated, with /bin, /sbin, and ($DEITY forbid!) /usr/X11R6.  
  
** ``You want to turn Linux into a Windows-like!'' **

   If you read everything up to this point, I believe it should be clear enough that we're not. If we were doing this to attract the Windows users, a structural reorganization would be the last thing we would do. Instead, we would concentrate on making the user interface look like Windows, applying Windows-like themes, moving icons around, perhaps integrating Wine tightly into the distribution, and so on. And that's what Lindows, Lindash, Linspire, or whatever their name is today is doing, not us.  
 It may sound extremely paradoxical, but we strive to keep the Linux identity on the system. To be more precise, we strive for each project to keep its own identity. Whenever possible, we ship every application with unmodified sources. If you ever took the time to look inside the .src.rpm files of any major distribution, you know what I'm talking about: the vast majority of packages have patches to apply little modifications here and there to modify this and that behavior; be it to change the default state of a checkbox, or even to remove the ``About'' box of an application! We don't do that. Our K menu shows the KDE logo, and so does the KDE splash screen. We do ship a theme with a custom wallpaper, but that is presented as an option in the installer.  
 We go through great distances to ensure that our packages do not have GoboLinux-specific bugs. The worst thing as a Linux user is to discover that a given software works on distro X and doesn't on distro Y, and not know if that is because distro Y introduced a custom patch that caused the bug, or if it's because distro X introduced a patch that fixed the bug. Speaking now as a developer, this is also a major headache. Alexandre Julliard from Wine once said that the constant changes on Linux distributions slow down the project more than the changes from the Win32 API.  
 The fact that on GoboLinux all Unix library directories present all libraries from the system, all header directories present all headers, and so on, neutralizes many common compatibility problems between distributions, causing us to be, ironically, one of the most compatible distros, despite the unorthodox directory layout.  
  
** The scope of a distribution **

   Some people, perhaps excited by the fact that we made such a ``big change'' in the structure of the operating system, occasionaly come to us through the mailing list with this great idea about doing some other big system-wide change that would improve GoboLinux considerably. Sometimes this great idea is applicable, and we do apply them, like when Carlo Calica integrated a daemon managing tool, Runit, into GoboLinux[6]("http://www.gobolinux.org/index.php?page=doc/articles/clueless#foot183"). But most of the time the idea is something that would require all applications to be greatly modified, if not rewritten. That is, obviously, something we can't and are not willing to do. If we were talking about a limited number of programs, some of them might even be feasible, but people need to keep in mind that the universe of programs to be used with GoboLinux is potentially infinite, as new Linux apps are written every day.  
 To list just a few of the unfeasible ideas we were suggested, I could mention:  
  
[LIST]
[*]make all programs relocatable - I would love to see that, but that would either mean: rewrite every app in the world to use libprefix, store every dependency inside each program directory and have some libraries on disk one hundred times (and deal with the clashes that arise in a system that is not prepared for this), compile everything relative to the same tree (I devoted an entire section above for this).
[*]make all programs use a unified configuration file format - Of course, the rewrite effort that this would require is even greater than the one from the previous item. Every idea that starts with ``make all programs...'' tends to have the same problems: the effort is potentially infinite; you can't make every project in the world agree to use your solution; even if you could, there are many legacy systems out there that just can't change even if they wanted, so incompatibility issues would happen no matter what. Another idea of this class would be to make all programs use the same graphic toolkit. Yeah, that would look great and unify the Linux desktop, but it's just not going to happen.
[*]turn entries on /Programs into AppDirs, because they look so much like RiscOS - They may look like, but they are pretty different. Yes, /Programs/Emacs could be made into an AppDir. /Programs/LyX too. Hey, a lot of them could. But what about /Programs/FindUtils? Or /Programs/KDE, what would happen when you click on that? Another key issue is that AppDirs are relocatable by nature and GoboLinux packages are not, a problem which I already covered above.[/LIST]    
** Internationalization **

   An often raised point is that ``changing'' names from things like lib to things like Libraries is too English-centric (``at least the old names were equally meaningless for everyone'') and that we should do an effort to make the directory tree translatable. I could dismiss this point raising a number of technical issues that make this impractical, unless we are talking about hacks involving symbolic links and the GoboHide kernel patch. But I won't do that. I will, instead, assume that a clean and elegant way to translate all GoboLinux directories existed, and ask ``then what?''.  
 If people are willing to translate the directory tree in order to make the system more friendly to those who don't speak English, I'm sorry, but that won't help. A user that is defeated by the fact that /System/Settings is not called /Sistema/Configurações won't go very farther, once they reach this directory and need to edit httpd.conf. The point I am trying to make is that the kind of users that need internationalization won't be helped by a translated directory tree. Efforts for translation should instead be directed towards documentation and the user interface of programs. If the user can read a manual in his/her language that tells him/her to go to /System/Settings and do such and such change in httpd.conf, this is much more useful than having the name of the directory changed. If the user has a friendly GUI for configuring Apache like the one provided by Mac OS X, he/she will probably like it much more.  
  
** Integration with other distros **

   This is another point that is raised from time to time, in different shapes, sizes and colors. The one reason I see people leaning towards this idea is because of the huge libraries of ready-to-use software provided by the other distributions. At first sight, the idea of combining all the innovations of GoboLinux with the enormous package base of distro X seems amazing. Looking closer, we'll see it's not.  
 First of all, there is the issue of the dependency systems. GoboLinux has a very loose dependency system, designed to be resilient to user customizations[7]("http://www.gobolinux.org/index.php?page=doc/articles/clueless#foot147"). If you take advantage of these GoboLinux features, you won't be able to auto-update system of distro X, and vice-versa. This way, you would have to choose between using GoboLinux as if you were using distro X, giving up much of the GoboLinux flexibility, or ignoring the cool auto-update features from distro X. Either way, you would give up on one of the reasons you started this integration project in the first place.  
 Then, there are all of the little peculiarities of both distributions, which you would have to be constantly dealing with: different boot scripts, possible library incompatibilities, the ``value-added'' package customizations of distro X... Not to mention the inability to properly use Compile or the GoboLinux binaries repository, due to, for example, different naming conventions of packages.  
 In short, even if you convert a whole system to use distro X's packages, what you'll end up with is not a ``turbo'' GoboLinux, but a quirky distro X. It is trivial to take, for example, all RPM's that compose a RedHat system, unpack them, and symlink them to look like a GoboLinux system. The resulting system, in the end, would pretty much be still RedHat. Different people have done this, with different goals (some to build a full distro, others just to convert a binary package or two), with RedHat, Slackware, Debian and more recently Gentoo. The general lesson I learned, from watching them do it, is that it is not worth it.  
  
** The root user **

   Of course, I saved the best for last. The decision of naming user zero something other than root is among the ones we are most criticized for. The origins of this predate GoboLinux. On my experimental system, my regular user was named hisham, and the superuser lode. I never liked the Unix notion of ``an arbitrary root versus regular users'' and wanted to see how well a Linux system would behave without a root user. After a few adaptations here and there, it worked very well. It was nice to know that every time someone would try to log as root in my machine, they would always fail.  
 When we made the hackathon that resulted in the first version of GoboLinux, André and I decided to keep doing it. We chose gobo, an inside joke. The intention of course, was to have a system that could support a non-root superuser cleanly, but the users (a handful of people back then) never changed the default and gobo somehow got stuck. It is still possible to change the default without much effort, though. For a short while I administered a set of machines at the university, and, to have them blend with the NIS environment more easily (the network was basically composed of RedHat boxes), I changed the superuser from gobo back to root. Now that GoboLinux has a graphical installer, we are considering putting the superuser name as an installation-time option.  
 Now that I'm through with the historical explanation, one thing I would like to point out that it is a well-known fact that the existence of a single god-like entity is one of the weaknesses of the Linux security model, and that is what bothered me with the notion of an arbitrary root versus the rest of users; it is akin to a single point of failure in a distributed system. The first thing every project aiming to improve the security of Linux does is to increase the granularity of the security model, do dilute the power of root: ACLs, capabilities, SELinux... It may be argued that some of those add excessive complexity to the model, but I won't dive into this discussion here. The one thing that is clear is that the root model is overly simplistic for today's complex systems, and that the ``setuid'' kludge is the source of most security issues. Plan 9, for example, doesn't have a superuser at all; it offers a virtualized view of the file system to each process. The gobo experiment was an interesting assessment on how ingrained in the Linux world is the expectation on having a root user; fortunately, not much (it does not measure how attached the security model is to the user #0, of course). One future direction I would like GoboLinux to take (and in fact Linux in general) is to adopt some of the technologies listed above as a way to improve the control over the system security and administration; to detach ourselves from root was the first step in this direction.  
  
** Conclusions **

   Well, I believe I covered a lot of ground in this article. I'm sure I forgot many issues, but I think the most important ones are all here. But the main idea I hope I passed here is that GoboLinux is not just a cosmetic change in the filesystem. We are pretty much aware of what we are doing, and what are the implications of the things we are doing.  
 It is no secret that when I came up with the first versions of this directory layout, I did not expect it to turn into a Linux distribution used by people all around the world (even though it was shaped as a distribution project as early as when Guilherme Bedin joined). The one thing I'm most happy about is that the original goal, from way back when it was not a proper distro, remains: a clean design.  
 I wholeheartedly agree with the quote in the beginning of the article, and I definitely believe this is not the case.   
** Postscript: Errata **

   Thanks to Varga Peter for pointing out that who said that the famous "creat()" quote is by Ken Thompson, not Dennis Ritchie.  
** About this document ... **

  [B]I am not clueless  
[SIZE=+1]or[/SIZE]  
Myths and misconceptions about the design of GoboLinux[/B] This document was generated using the [**LaTeX**2HTML]("http://www.latex2html.org/") translator Version 2002 (1.62) 
 Copyright © 1993, 1994, 1995, 1996, [Nikos Drakos]("http://cbl.leeds.ac.uk/nikos/personal.html"),  Computer Based Learning Unit, University of Leeds. 
Copyright © 1997, 1998, 1999, [Ross Moore]("http://www.maths.mq.edu.au/%7Eross/"),  Mathematics Department, Macquarie University, Sydney. 
 The command line arguments were: 
 **latex2html** -split 0 clueless.tex 
 The translation was initiated by Hisham Hashem Muhammad on 2004-06-13 

**Footnotes**

 ... difference[1]("http://www.gobolinux.org/clueless.html#tex2html1")For those who always wondered (and those who want to check if I really understand the difference), the three main trees divide, respectively, files that need to be available in the root partition for single-user rescue mode, program files managed by the distribution, and programs added separately by the site admin (this distinction varies on different Unices, but this is mainly how it works on Linux distributions, read on for more). Regular programs go in /bin, and programs intended for the superuser in /sbin.  ... on[2]("http://www.gobolinux.org/clueless.html#tex2html2")On Plan 9 that could be done with a bind command; since we don't have this in a vanilla Linux kernel, we do this with symbolic links. But I have to admit I like the notion that the views are stored in a persistent manner.  ... installers[3]("http://www.gobolinux.org/clueless.html#tex2html3")An installer per se is a rare concept in Linux; what I mean by installer here is usually the install target of a Makefile.  ... place[4]("http://www.gobolinux.org/clueless.html#tex2html4")For those interested in this approach, I point you to GNU Stow. I do not know, however, of any system built 100% with it, though.  ... kernel[5]("http://www.gobolinux.org/clueless.html#tex2html5")If it were not, we could also, for example, build the /System/Links views as union mounts using ovlfs.  ... GoboLinux[6]("http://www.gobolinux.org/clueless.html#tex2html6")The current trend on GoboLinux development is to loosen this integration, making Runit an optional component, but still providing the required framework to make it work.  ... customizations[7]("http://www.gobolinux.org/clueless.html#tex2html7")It's beyond the scope of this article to describe the GoboLinux dependency system, but for example, if you install app A and it depends on B, it won't complain if B was not installed with a vanilla package, and if B is missing, it will report, but not refuse to install.    Hisham Hashem Muhammad 2004-06-13
[http://www.gobolinux.org/index.php?page=doc/articles/clueless](http://www.gobolinux.org/index.php?page=doc/articles/clueless)
(not sure if this has been posted or linked already but it makes for a good read, for basic understanding of what the dev is doing)

---

### Post by steven8 on 2006-12-01
I wanted to try goblinX, but the download was going so slow on my cable, it was going to take 25 hrs @ 7kbps.  Ouch!!  The http mirror link was a not found, and the torrent threw an error!

:-(

---

### Post by RAV TUX on 2006-12-01
> **steven8 said:**
> I wanted to try goblinX, but the download was going so slow on my cable, it was going to take 25 hrs @ 7kbps.  Ouch!!  The http mirror link was a not found, and the torrent threw an error!

:-(

I don't recall download problems, but I am pretty patient, doing a Ktorrent download of the new Sabayon build which is taking about 3 days...no worries for me...time will pass the same wether or not I download it or not.

---

### Post by steven8 on 2006-12-01
I don't usually worry about the length a download takes, either.  I'll try it again this weekend at night.  Maybe the traffic will be less.  I love the look and sound of the distro.  I also want to try gobolinux next.

Oh yes, I am a distro junky as well.  My wife picks on me about it.  She can't understand why, when I have Dapper and it works just fine, why I need to mess with other distros.  She just doesn't understand. :-)

---

### Post by triplep on 2006-12-01
Users would become somewhat arbitrarily bound to Gobo, right now I can use my knowledge of the file structure across pretty much all linux distros, as well as Solaris and BSDs, to me, that counts for something. You also lose out on support from other distros' documentation and user help, because you don't understand any of the paths that they are talking about.

Capitialization sucks on the command line, period.

This whole structure is for folks that aren't ever going to click on anything but the 'K' or gnome foot to start programs, and save things to the default path that an application chooses for them. I'm not looking down on them either, because what works, works. 

It's not that big of deal IMO, and won't actually provide any more utility in the long run, and upon moving to another distro, you get to learn all over again, instead of learning the different quirks of the distro, you get to learn the quirks and the filesystem.

---

### Post by mssever on 2006-12-01
> **triplep said:**
> Users would become somewhat arbitrarily bound to Gobo, right now I can use my knowledge of the file structure across pretty much all linux distros, as well as Solaris and BSDs, to me, that counts for something. You also lose out on support from other distros' documentation and user help, because you don't understand any of the paths that they are talking about.

Capitialization sucks on the command line, period.

This whole structure is for folks that aren't ever going to click on anything but the 'K' or gnome foot to start programs, and save things to the default path that an application chooses for them. I'm not looking down on them either, because what works, works. 

It's not that big of deal IMO, and won't actually provide any more utility in the long run, and upon moving to another distro, you get to learn all over again, instead of learning the different quirks of the distro, you get to learn the quirks and the filesystem.
Did you read the article RAV TUX posted? it addresses all your points.

---

### Post by triplep on 2006-12-01
> **mssever said:**
> Did you read the article RAV TUX posted? it addresses all your points.

At first my brain shutdown seeing a huge article post, but I've read it now.

It doesn't address fragmenting user support, the CLI savvy of users vs GUI file manager, capitalization on the CLI, or the lack of portable knowledge of the FS.

I mean, I could have misread the *entire* article, but I'm fairly confident that I haven't.

---

### Post by hoagie on 2006-12-01
Maybe it would be a good idea...oh damn I shouldn't spend all those hours  tolearn the current one!

---

### Post by smoker on 2006-12-03
> people shouldn't have to learn about it if they don't give a crap. Most people nowadays are like that. They just want to use something, not understand how it works. And if you know what you're doing, you can still do stuff the traditional way. I think it's a good thing.

totally agree, anything that makes things simpler. anyone wanting to look 'under the hood' will do so anyway.

---

### Post by argie on 2006-12-05
> **triplep said:**
> At first my brain shutdown seeing a huge article post, but I've read it now.

It doesn't address fragmenting user support, the CLI savvy of users vs GUI file manager, capitalization on the CLI, or the lack of portable knowledge of the FS.

I mean, I could have misread the *entire* article, but I'm fairly confident that I haven't.
Either the shell is setup to match case insensitively with Tab auto-completion, or the whole setup is case-insensitive. So capitalisation isn't a point.

---

### Post by clive5 on 2006-12-09
I have used Linux for a few years now, but for some reason I always have to return to Winblows for something that is either not available in Linux or is not as simple as windows. The one thing that plagues Linux is the many different forms of application distributions. Why should anyone and more importantly should I have to use a package system such as apt with precious time being wasted on updating the sources. Why should there be a need to recompile an application package and not just be able to download a file and double click on it and its all done. To uninstall i just delete the specific folder. :-k What is rather curious to me is that some of the very people who love Linux are also the ones holding it back with their inexorable arrogance.  When I was studying a few years back I had a lecturer who taught us that the key to our futures in the IT world is to be more open-minded than our predecessors.Open you mind and stop being consumed by power of your acquired knowledge. No one is trying to take it from you. 

I love Ubuntu and will continue to look forward to the future, but I just hope that a Gobo-like file hierarchy is adopted.

---

### Post by .t. on 2006-12-09
I have always found package management to be much better than any system offered by OS X or Windows. It gets dependencies for you, whereas in Windows, you often have hundreds of copies of the same libraries that programs ship with them as they cannot be sure you have them installed. You're saying this is a better way? I think not. Updating the sources only means that you will get the most up to date packages. On a stable release, there shouldn't be many updates, and this process should take very little time.

Moreover, you can download an executable and double-click it, deleting when you're done, so that "advantage" that Windows or OS X has is non-existent. Download IceWeasel for a good example: [http://gnuzilla.gnu.org/download/iceweasel-1.5.0.7-g2-i386.tar.bz2](http://gnuzilla.gnu.org/download/iceweasel-1.5.0.7-g2-i386.tar.bz2). 

Finally, choice is often seen as one great advantage in the free software world. I agree that at first it is daunting, but soon you'll see it as I see it. But you confuse me by jumping so suddenly from talking about choice to talking about package management...

---

### Post by Phasmus on 2006-12-09
I have no special preference in the matter personally.  However it does occur to me that if conditions were reversed and the gobo-hierarchy was the old standard for desktop Linux systems(I am aware of the far-out-ness of this hypothetical situation), people suggesting that it be replaced by FHS for general use would probably be facing rather more opposition.

It might not be worth the bother of changing over now, but side by side gobo seems to have less cruft and be more intuitive.  And if you prefer the original recipe hierarchy, it's still there under the hood.

---

### Post by clive5 on 2006-12-10
You couldn't have placed your finger on it any better. Just because Windows uses a similar hierarchy doesn't mean its wrong. If Windows has it wrong it wouldn't be the most used desktop today and MS knows it. Gobo has it right by keeping the original structure but making it hidden. Give the lesser informed the chance to enjoy what knowledgeable Linux users have experienced.

P.S. Don't tell me to use Gobo because I really **like** Ubuntu and believe it is doing a **great** job overall.

---

### Post by infinitelink on 2007-01-22
Correct me if I'm wrong, and I warn that I've only been skimming-through (not reading the whole) the thread, but Gobolinux doesn't "maintain" the unix hierarchy, really, it uses the more organized one...but uses the symlinks to allow traditional programs to run: they're still organized in the new way--but faking-out the programs that won't run that way yet.

I agree with those who say that using this system would be much better: Unix users may/not like it, however the file-system thing is one of the biggest hindrances to linux adoptance not only to end-users, but to a lot of techies too: and this is one of the things that those looking at linux are BEGGING for: if I was running the development of Ubuntu I'd take the work from Gobo and re-work Ubuntu (secretly, maybe), then release it when ready for prime-time. The work was done in Gobo, it's a user-friendly system, and no need for a pkg manager (except organizing types of programs to download!). I guess this "could" become an issue for debian-compatibility, and sure for LFS and other standards that have been set, but the problem with those agreements are that 1) nobody wanted to take the time to clean-up, and 2) tech-junkies. 

Imagine saying to an enterprise that their techs and admins don't have to learn all about linux file management and packages! Think about it: Gobo DOESN'T CARE ABOUT PACKAGES. It uses (a) the one the program needs...period. Oh, and a project like Ubuntu has the scale it could probably tool the system to symlink programs to the available packages for newest versions (if the program would work with it) and cut-down on size.

People have suggested this type of thing in the launchpad and it keeps getting shot-down, but personally I think it's a bad idea to disregard what your users are begging for. Sure, people complain about bugs in windows: but on my system, for instance, take-away the crappy drivers written for the Graphics card and I'd never have a problem. And when MS makes a piece of software they ASK THE USER. Ubuntu wants wide adoption? They'll have to stop listening to just the linux fan-boys. Listen to the broader user-base and you'll get results. It's not that hard. It might be a PAIN, but no pain, no gain.

---

### Post by mirak63 on 2007-01-29
The only inconvenient with each application in it's folder is will the devs still bother of creating a coherent structure inside the own application folder ????
It's the only risk.

---

### Post by mirak63 on 2007-01-29
The only inconvenient with each application in it's folder is will the devs still bother of creating a coherent structure inside the own application folder ????
It's the only risk.


lol, funny smiley :guitar:

---

### Post by hizaguchi on 2007-02-26
I like the idea quite a bit.  The logical folder names (at least for us English speakers) would be nice for newer users, but more importantly the fact that all files of a given type are stored in the same folder is wonderful.  As it stands now, different programs tend to install parts of themselves into different places (/bin, /usr/bin, /usr/sbin, /usr/share/bin, /usr/local/share/bin, /usr/share/local/bin, etc.)... especially if you have to install them from source.  On top of that, I administer a computer lab and cluster where the machines are running 3 different Linux distros, all of which use a slightly different scheme for where they install the same software.  It's crazy trying to keep up with all of that.  I'm surprised my l, o, c, a, t, and e keys aren't worn out by now.  Anything that keeps the file system more focused and organized sounds good to me.

I've not had a chance to play with it yet though, so I can't say for sure that I'd like it once I had used it for a while.  The impression I'm getting though is similar to the shock I encountered on my first FreeBSD installation... logical uses for symlinks!  I thought the fact that /home was just a link to /usr/home was genius because it meant that I didn't have to partition my hard drive with a full idea of how much space I'd need for software vs file storage.  I just made a big /usr partition.  It was great.  This sounds like a combination of that idea and the ports tree, so I can't imagine it being a bad thing.

---

### Post by Nils Olav on 2007-02-26
> **clive5 said:**
> I have used Linux for a few years now, but for some reason I always have to return to Winblows for something that is either not available in Linux or is not as simple as windows. The one thing that plagues Linux is the many different forms of application distributions. Why should anyone and more importantly should I have to use a package system such as apt with precious time being wasted on updating the sources. Why should there be a need to recompile an application package and not just be able to download a file and double click on it and its all done. To uninstall i just delete the specific folder. :-k What is rather curious to me is that some of the very people who love Linux are also the ones holding it back with their inexorable arrogance.  When I was studying a few years back I had a lecturer who taught us that the key to our futures in the IT world is to be more open-minded than our predecessors.Open you mind and stop being consumed by power of your acquired knowledge. No one is trying to take it from you. 

I love Ubuntu and will continue to look forward to the future, but I just hope that a Gobo-like file hierarchy is adopted.

=D>

---

### Post by TheWizzard on 2007-02-28
> **hizaguchi said:**
> I like the idea quite a bit.  The logical folder names (at least for us English speakers) would be nice for newer users, but more importantly the fact that all files of a given type are stored in the same folder is wonderful.  As it stands now, different programs tend to install parts of themselves into different places (/bin, /usr/bin, /usr/sbin, /usr/share/bin, /usr/local/share/bin, /usr/share/local/bin, etc.)... especially if you have to install them from source.  On top of that, I administer a computer lab and cluster where the machines are running 3 different Linux distros, all of which use a slightly different scheme for where they install the same software.  It's crazy trying to keep up with all of that.  I'm surprised my l, o, c, a, t, and e keys aren't worn out by now.  Anything that keeps the file system more focused and organized sounds good to me.


the different places of binaries are quite logical. from an administrator's view. 
if you compile from source, use checkinstall to make a deb file. now you can use dpkg to install it. no worries where what goes any more.

---

### Post by Nils Olav on 2007-02-28
> **TheWizzard said:**
> the different places of binaries are quite logical. from an administrator's view. 
if you compile from source, use checkinstall to make a deb file. now you can use dpkg to install it. no worries where what goes any more.

:-s 
Your second sentence didn't explain the summary of your conclusion.

---

### Post by disgustingangel on 2007-03-07
I think we're not really addressing the point of this new filesystem hierarchy there... We're not talking about package installation/removal, but about "information hiding"... if hiding the traditional way of distributing "programs files" (:D) can make finding of application informations (from binaries to configuration files) more intuitive, keeping also the old structure usable.. I think we should try that way!
I mean...
[LIST=1]
[*] A user will still not be able to read/write inside the /Programs/$ProgramName/$Configuration/ directory, 'cause it'll need to be root for doing this...
[*] You could still backup your /etc as you're doing now, 'cause of the backward compatibility
[*] A new user could be no more frightened 'bout the strange /etc directory... and for a "normal" user like me it'll be like the same thing to go inside /Programs/[..]!
[*] OSX users could feel home :D
[*] That way we're not (sadly) making configuration easyer, we're only making finding where to configure easyer! (not to forget: also keeping things properly arranged). I reaaly think that "Knowing about Linux" (or, better, "knowing about Ubuntu") should not mean knowing where the information is, but how to use it! so we will only be making learning curve more light...
[/LIST]

So I see no problems with this kind of double visibility of the filesystem... whereas I see some good points about it!

But.. how 'bout doing the contrary? I mean: keepink the files, phisically, on the old directory structure,and having a kernel module and/or a symlinks structure simulating the gobolinux structure! :) That will make (I suppose) it easyer to implement, expecially if we would like to keep it optional...later on, with wide acceptance, we could thing about having it as a default and so start repackage everything :D

My vote goes , conclusively, to "It's time for a change"... but i think we've not to defocus on the "user must choose" idea! :)

---

### Post by TheWizzard on 2007-03-07
> **Nils Olav said:**
> :-s 
Your second sentence didn't explain the summary of your conclusion.

if you use checkinstall, you can simply remove an application (and all files) with aptitude remove package.

---

### Post by hizaguchi on 2007-03-08
> **TheWizzard said:**
> the different places of binaries are quite logical. from an administrator's view.
if you compile from source, use checkinstall to make a deb file. now you can use dpkg to install it. no worries where what goes any more....

...if you use checkinstall, you can simply remove an application (and all files) with aptitude remove package.

Sure, that's great.. except that it doesn't solve the problem at all.  It's great to have a system that knows where it puts things, but that isn't always a suitable replacement for letting *me* always know where it puts things.  More importantly, package managers are intended to replace old packages with newer ones over time.  But that isn't always what I want to do.  Sometimes I want to keep an older version around for users who still use code that relies on it, but also install a newer version so everybody else isn't held back.  I also have both 32 and 64 bit versions of some software installed on the same machines... and occasionally a need for keeping older versions of both.  And to top it all off, all of these versions need to be kept in a logical enough place that even new users can find them when they need them.  All of this is maintained by a succession of student workers who pass the system down as they graduate, with varying degrees of documentation.  So what has developed is a /software folder where all software not related to the OS itself is installed in various subfolders for each version.  It works very well that way, which is why the idea of a whole system that is so logically organized is so appealing to me.

---

### Post by Jelly2003 on 2007-04-02
I voted YES because I believe this is the future for Linux and I think the concept behind Gobolinux is **excellent**. Firstly, I've used various distributions over several years, from early Red Hat, to Ubuntu 7.04. 

I am not a Linux noob, but I am not a guru either. The one thing that ALWAYS confused me is the file system. I understand that it has a "grand order" to things, and everything can be logically explained. 

Linux package managers for the most part ALSO work great. They're dead simple to use, so for a novice, there is no doubt that they make life lots easier.

What about when things go wrong? What about when there is no package for your distro? What about is "make install" doesn't work properly? What if I download a binary copy of an application?
This is where I believe the Gobolinux structure really shines because I could install the application by dragging a folder containing the binary files into the "/Programs/X" folder. 

In the current system I have to drop files in a number of directories, and frankly I woudln't even consider doing it. In fact in the past I've just created a "~/Programs/" directory and placed downloaded binaries in there to install them.

Also, just because the file system itself can act as a package manager doesn't mean that we should abandon package managers. I love package managers! Although a new file system would sure it easier if a package manager can't do the job.

From a simplicity point of view it makes sense to arrange the file system logically in plain English using whole English words.

Perhaps for non English speakers a standard system of symbolic links could be provided to help them navigate, it doesn't 100% solve the problem, but standards need to be established. Also, the current file system uses abbreviated English words anyhow, for non English speakers a system of symbolic links (standardised for all languages) would be BETTER than the current system IMO.

In no way do I think it's a "lazy" file system. Once Gobolinux proves itself, I think it'd be wonderful for other distros to adopt something similar.

---

### Post by metnik on 2007-04-11
I think this is one obstacle to solve [http://theosib.livejournal.com/1742.html?thread=14286](http://theosib.livejournal.com/1742.html?thread=14286)

Current file organization is uncomprensible

---

### Post by briansvgs on 2007-04-14
I also believe that it is time for a change. Although I haven't seen this as much in Ubunutu, too often have I tried to install a program only to find out that the version of a program or library on which this new program depends is incompatible with other programs in this system. If we used the gobolinux directory hierarchy, then it sounds like this problem would disapear. Also, the gobolinux hierarchy is a lot easier to understand then the current linux/unix directory structure.

---

### Post by TheWizzard on 2007-04-18
> **briansvgs said:**
> I also believe that it is time for a change. Although I haven't seen this as much in Ubunutu, too often have I tried to install a program only to find out that the version of a program or library on which this new program depends is incompatible with other programs in this system. If we used the gobolinux directory hierarchy, then it sounds like this problem would disapear. Also, the gobolinux hierarchy is a lot easier to understand then the current linux/unix directory structure.

i can't see why your dependency problems would disappear with the gobolinux structure. 
i also never encountered the problem you mention here. can you give an example?

---

### Post by zorkerz on 2007-04-18
An far as im concerned if something is easier to learn and allows tasks to be completed faster without any side effects it is undoubtedly a better solution. I am not yet sure this is the case with the gobolinux design.

As far as opinions go we have heard alot of them. Few of us im sure want to learn a new file hierarchy. However if you had to learn one which is better in the long run. I risk the assumption that in the short run the gobo method seems much simpler to learn. 

What are the advantages to the FHS hierarchy (besides that its already know and a standard)?  If magically everyone switched to the gobo hierarchy would there be any major downsides? The gobo layout does not seem to prevent anything we do already. You can even easily use a package manager if it was built correctly. There also seem to be some distinct advantages to gobo's design.

I think another safe assumption to make is that all distros will never completely unify/standardize under one hierarchy. FHS is a standard general layout but most distros appear to differ in one way or another form it and then theres this crazy little distro called gobolinux that shakes things up.

Oh wow thats alot of rant. I guess im just looking for a pro/con list comparing the hierarchy's. I don't much care about the current state of things rather an ideal state were things are instantly learned and perfectly efficient. Does such a pro/con list exist or should we start to create one?

---

### Post by rai4shu2 on 2007-04-18
Pro: Easier to find stuff in a traditional file manager.
Con: Not standard, which can disrupt the way some apps work.

Pro: Easier to install multiple versions of apps and libraries.
Con: Encourages bloat.

Pro: No need to run ldconfig.
Con: A user shouldn't *need* to run ldconfig in the first place.

---

### Post by zorkerz on 2007-04-18
Alright i like this start! I think i will comment and add a few of my own

> Pro: Easier to find stuff in a traditional file manager.
Con: Not standard, which can disrupt the way some apps work.
 *On the site (no personal xp) it says that most apps work and ones that follow GNU autotools have the flexibility to be installed on non standard hierarchies.

>  Pro: Easier to install multiple versions of apps and libraries.
Con: Encourages bloat. *true however, I don't think the system itself would prevent the design of update and package managers and other new methods to discourages bloat that don't prevent mult versions when necessary.

>  Pro: No need to run ldconfig.
Con: A user shouldn't *need* to run ldconfig in the first place.*whats idconfig

con: longer directory names could slow down cli speed

pro: a side note but the ability to change the root name is good security wise at least

please get me if im wrong here

---

### Post by theredcross on 2007-04-22
> **rai4shu2 said:**
> Pro: Easier to find stuff in a traditional file manager.
Con: Not standard, which can disrupt the way some apps work.

Pro: Easier to install multiple versions of apps and libraries.
Con: Encourages bloat.

Pro: No need to run ldconfig.
Con: A user shouldn't *need* to run ldconfig in the first place.

quite possibly the most rational points I've seen brought up in several threads about Gobo. I'll be downloading the livecd and testing it tomorrow, but so far the site hasn't offered me anything that I find particularly convincing and the dubious "don't need a package manager" title makes me a bit wary. Apt is the best freeware program I've ever used, and if it could be combined with this new FHS than it may be worth a shot.

But there seems to be a lot of debate saying that people oppose the gobo FHS because they are archaic ape-men throwing bones at large black obelisks. This is insulting, as I'm sure more than one person meant, and is a misinterpretation. We are not opposed to it because we hate change, we're opposed to it because we run a stable operating system that -for most of us- works perfectly fine. When GoboLinux survives for a few years and establishes itself then more people will try it and so on and so forth. Linux is not a corporation, we have no singal consciousness, and people do things as they see fit. There are no Dark Lords of Linux that keep us in the dark ages, personal preference and usefulness are what drives change. Change is not immediate, and if gobo creates a new standard this will become known as a "transitional phase." One can hardly blame people for being cautious when they have a computer that is working and someone offers something new that "should" work. People will try it and the populace will decide where to go with the idea.

Personally, I think symlinks are a very interesting idea and am in favor of the flip-sided use someone else presented. Keeping the FHS and using symlinks to create a more user-friendly frontend seems to me like it would stop the bloat issue, as well as make it more backwards compatible. I know gobo says it works fine, but problems arise. If you remove that layer of complexity then less problems will arise, that's one thing I've learned from playing with linux for years.

I think I've run out of steam for the moment, but I would love to see more point-counterpoint of the cailber that rai4shu2 has added. Hopefully when I test Gobo out myself I'll be able to add more constructive criticism.

---

### Post by briansvgs on 2007-04-22
Sorry that it took me so long to respond. I didn't recieve anything in my email or anything notifying me that another post had been made on this thread. One example of problems with dependencies I ran into with ubuntu edgy. I tried to install a new program, which I forget what the name was, but it was from the fiesty beta repositories. My computer told me that I did not have a new enough version of libc6 installed to install this program. I installed the new libc6, and it screwed up everything. Synaptic stopped letting me install new stuff, and X started acting unusual. If we used the gobolinux file system, then, theoretically, we could have several versions of the same library installed on the same system, removing compatibility problems like this. And, at the same time, it would be easier to understand.

---

### Post by theredcross on 2007-04-23
Well it certainly does seem to offer some interesting options, got the .iso going to test run later tonight.

---

### Post by briansvgs on 2007-07-06
I definitely think that a filesystem without a package manager is a bad thing. Although I like slackware, without a package manager, nothing is available, and it is harder to install programs than with a program like apt-get. With apt-get, you just type apt-get install ..., whereas with slackware, you either have to download and install slapt-get, then add a whole bunch of repositories to install a program, or find and download a tgz of the program, then run installpkg ... I don't know about you, but having a package manager by default definitely looks a lot better to me.

However, it sounds like with the GoboLinux filesystem, the default directory structure still exists, but is just hidden. If this is true, then I would think that a package manager such as apt-get could download and install programs to their default directories, while the user would only see the visible, simpler file structure.

---

### Post by init1 on 2007-07-06
I thought Gobo was more confusing than the usual system. I'll stick to the old system.

---

### Post by louieb on 2007-07-08
It may not be a clone of the Win _program files_ structure. But when I went to the web site and read the description that was the first thing that comes to mind.  

As someone that wrote his first program in FORTRAN and has seen programming languages and operating systems come and go. The better ones just stick around longer. Perhaps this is a better way to organize an operating system I don't know.

  > In GoboLinux you don't need a package manager because **the  filesystem is the package manager**: I do a lot of work for sales organizations and I think I know hype  when i see it. It looks like GoboLinux is off to a good start with their **Dog and Pony Show**.

---

### Post by bread eyes on 2007-07-08
> **init1 said:**
> I thought Gobo was more confusing than the usual system. I'll stick to the old system.

...........

---

### Post by Poiema on 2007-10-17
> **po0f said:**
> This would break all Linux packages out there right now, that haven't been custom-packaged and bastardized by these people.
Someone said something about Gobolinux bastardizing all software that it touches. This would definitely not be the case, as Gobo's recipes are in place only to help install source software that has not been well/correctly formatted by the developer. RPM's and DEB's, etc use the same **_source_** that Gobo does and then essentially have a 'recipe' that allows them to work on the respective system. Gobo in fact is not adding anythinG to the program, unlike many distros who patch the software for optimization and sometimes cause breakage when doing so. (At the very least their patched versions may not be compatible with other distros.)

---

### Post by Poiema on 2007-10-17
> **briansvgs said:**
> 
However, it sounds like with the GoboLinux filesystem, the default directory structure still exists, but is just hidden. If this is true, then I would think that a package manager such as apt-get could download and install programs to their default directories, while the user would only see the visible, simpler file structure.

I think the problem with other package managers is that they would have to be configured to recognize the Gobo file structure otherwise they would be defeating the entire purpose of that structure.

---

### Post by Poiema on 2007-10-17
Is anyone up for trying to remaster a minimal Ubuntu using Gobo Rootless? From what I've read there may be a bit of work to make it work correctly on Ubuntu. You could then start putting the remaster together from there. However, it is my understanding that unless you make some changes in APT, anything you add using APT will not apear correctly in the Gobo file structure. Essentially you would be remastering a source/recipe based version of Ubuntu. I might be willing to try but I'm not as adept as many of you here, and with work, school, and a family time is very limited. I would be interested in testing.

---

### Post by smartboyathome on 2007-10-17
> **Poiema said:**
> Is anyone up for trying to remaster a minimal Ubuntu using Gobo Rootless? From what I've read there may be a bit of work to make it work correctly on Ubuntu. You could then start putting the remaster together from there. However, it is my understanding that unless you make some changes in APT, anything you add using APT will not apear correctly in the Gobo file structure. Essentially you would be remastering a source/recipe based version of Ubuntu. I might be willing to try but I'm not as adept as many of you here, and with work, school, and a family time is very limited. I would be interested in testing.

I would think that apt wouldn't break with the installation of Gobohide. Reason is that it installs with the same folder structure as its source, and source installs have been known to work with gobo (recipes only offering a faster way to install the files). I am currently trying to recompile the kernel on a Xubuntu Gutsy install with Gobohide. I will report back with results.

---

### Post by otttx33 on 2007-11-20
Linux is not a clone of Windows. It is a better unix, with gui. Let's keep it like this. Back to the roots.

---

### Post by Harpalus on 2007-11-20
This is absolutely pointless. It doesn't make things simpler, it makes things more complicated by cluttering up the filesystem. All of the original symlinks are still in place, remember. Just because it looks simpler when you open up your file manager, doesn't mean it's simpler under the hood.

It also means I have to keep track of installed applications. I always run BSD systems. When I want to upgrade, I know that EVERY application I installed is in /usr/local. I know to backup /etc. And of course, /home. Under this new system, every application has it's own folder, making it an annoyingly difficult task to back up applications and settings that aren't in the base install.

It's more complex, it makes life a lot harder for administrators, all in the name of...helping out grandma when she does a 'ls /'? Allow grandma to drag a .deb file to the Programs directory? We already have a nice fancy user-friendly method of installing applications. Why invent another?

And no, linking me back to the same GoboLinux page isn't a decent response. I've already read it. I still think the idea's retarded.

>  Internationalization

An often raised point is that ``changing'' names from things like lib to things like Libraries is too English-centric (``at least the old names were equally meaningless for everyone'') and that we should do an effort to make the directory tree translatable. I could dismiss this point raising a number of technical issues that make this impractical, unless we are talking about hacks involving symbolic links and the GoboHide kernel patch. But I won't do that. I will, instead, assume that a clean and elegant way to translate all GoboLinux directories existed, and ask ``then what?''.
If people are willing to translate the directory tree in order to make the system more friendly to those who don't speak English, I'm sorry, but that won't help. A user that is defeated by the fact that /System/Settings is not called /Sistema/Configurações won't go very farther, once they reach this directory and need to edit httpd.conf. The point I am trying to make is that the kind of users that need internationalization won't be helped by a translated directory tree. Efforts for translation should instead be directed towards documentation and the user interface of programs. If the user can read a manual in his/her language that tells him/her to go to /System/Settings and do such and such change in httpd.conf, this is much more useful than having the name of the directory changed. If the user has a friendly GUI for configuring Apache like the one provided by Mac OS X, he/she will probably like it much more.

I would use his same arguments to argue against the entire idea. 

> Efforts for translation should instead be directed towards documentation and the user interface of programs. If the user can read a manual in his/her language that tells him/her to go to /System/Settings and do such and such change in httpd.conf, this is much more useful than having the name of the directory changed. If the user has a friendly GUI for configuring Apache like the one provided by Mac OS X, he/she will probably like it much more.
Let me fix that.
> Efforts to reinvent the wheel and clutter up the file hierarchy should instead be directed towards documentation and the user interface of programs. If the user can read a manual in his/her language that tells him/her to go to /etc and do such and such change in httpd.conf, this is much more useful than having the name of the directory changed. If the user has a friendly GUI for configuring Apache like the one provided by Mac OS X, he/she will probably like it much more.

 I love how he argues against his own ideas in one paragraph, then tries to refute the same arguments elsewhere. Here, I'll do it again.

> A user that is defeated by the fact that /System/Settings is not called /Sistema/Configurações won't go very farther, once they reach this directory and need to edit httpd.conf.
> A user that is defeated by the fact that /etc is not called /System/Settings won't go very farther, once they reach this directory and need to edit httpd.conf.

---

### Post by jclmusic on 2007-11-25
enough of the stupid 'holy wars', please, linux is all about choice :). each to their own.

any luck with patching the kernel?

---

### Post by smartboyathome on 2007-11-25
Unfortunately, I couldn't get the kernel fully patched, and there isn't one out for 2.2.23 (at least, there wasn't since I last tried it).

---

### Post by Fbot1 on 2007-11-25
> **briansvgs said:**
> I definitely think that a filesystem without a package manager is a bad thing. Although I like slackware, without a package manager, nothing is available, and it is harder to install programs than with a program like apt-get. With apt-get, you just type apt-get install ..., whereas with slackware, you either have to download and install slapt-get, then add a whole bunch of repositories to install a program, or find and download a tgz of the program, then run installpkg ... I don't know about you, but having a package manager by default definitely looks a lot better to me.

GoboLinux has a package manager just not in a normal sense. What they mean by "the file system is the package manager" is the file system is the package manager's database. They still have stuff similar to apt-get ("InstallPackage" and "Compile") and handle dependencies.

---

### Post by ippokratis on 2007-12-08
I like Gobo!  But I think it isn't ready for a stable desktop use.  It has some problems especially in grub procedure.  The installation runs perfect, but when you restart your PC...  Errors and errors again!:(

---

### Post by ZephyrXero on 2007-12-09
There is nothing more that I would love for Ubuntu than for it to have something like this happen....however, there's absolutely no chance that it'll ever happen. The changes it would require would be far too great.

A much more realistic goal would be to have people start working on a brand new distribution that's a derivative of Gobo in the same way that Ubuntu is of Debian, and then apply all of Ubuntu's goals and philosophies to it.

I've been playing around with the idea of starting such a project for the last year or two, but it would be a massive undertaking and I don't know if I'll ever find the time to get it started... Then again, another part of that idea includes the fact that I'm still not 100% satisfied even with Gobo's filesystem hierarchy.

---

### Post by BLTicklemonster on 2008-01-01
I found this on distro watch and looked in here to see if anyone was paying any attention to it. 

I like the idea of putting stuff in one place.

I'm downloading it now, and will run the live cd to see how I like it.

(also dl-ing pclinuxos to see how I like it, too :) I guess I'm wanting to look around and see what else is out there. Other than that Slackware 7.1 monstrosity sitting in a box on my book shelf across the room, that is)

---

### Post by smartboyathome on 2008-01-01
If you are downloading PCLOS, don't dualboot it with Ubuntu, it will end in disaster (it did for me). Also, I am paying a lot of attention to this. I asked on their forum about the gobohide patch, they said that it wouldn't be a good idea to use it outside of Gobohide. :(

---

### Post by BLTicklemonster on 2008-01-01
Thanks. I was wondering about dual booting PCLinux. Perhaps if I like it enough (live cd), I'll see about putting it on my laptop and giving it a whirl. Or just drop a blank HD into the box and install it for some yucks (disconnecting the other three hooked up at present, of course).

---

### Post by Meson on 2008-01-09
I'm all for this.  Change is a good thing.  If you read the article on the gobolinux website [http://www.gobolinux.org/index.php?page=doc/articles/clueless](http://www.gobolinux.org/index.php?page=doc/articles/clueless) which describes all the rationale behind the gobo-decisions, it all makes sense.

I think it's pretty clear that the Gobo directory structure is a good idea, but it's also necessary to prove that our traditional structure is no longer needed, this article explains why and I couldn't agree more.

This well organized hierarchy not only helps with system maintenance, but with managing users.

I've also read through this entire thread and couldn't find a single compelling reason not to change.  I agree that changes should be a slow process and carefully selected.  But we shouldn't resist change all together.  This is a good thing (and could probably even be refined a little further)

---

### Post by fsando on 2008-01-20
I very much agree with the suggestion.
I'm a one year user of Ubuntu (and linux in general). I have a good example of the problems:
I use a program whose installation files are scattered over the following folders:

/usr/lib/R
/usr/bin (the executable)
/usr/local/lib/R
/usr/share/R

The unfortunate result is that its help system is broken. The problem is that the help files could reasonably be placed three different places and different functionality of the program expect them to be different places.

Yes, this i not the Ubuntu intall but made directly from R-sources.
And why? Because I need this program to be up-to-date in order for it to work with various packages (most notably rkward).
Unfortunately Ubuntu is usually 1 year behind in this specific area so I see no other option than to get the newest version and live with this mess.

I have similar experiences with custom install of mozilla products when I tried to 'integrate' them into Ubuntu. Fortunately they run completely self contained if you want them to.

So yes, the GoBolinux idea seems great.

---

### Post by Aposp on 2008-02-17
well , its clearly negative to have a more windowz perspective on keeping program fiels. unix logic on build is clearly superior on that.


Cant see a YES without a doubt. 
after alll i might be hardcore ut yeah, i think that gog distro failed on that.

---

### Post by ar2000jp on 2008-05-15
Well, this is definitely a good idea, not just for change, but for the benefits.

I don't know for sure, but I think the UNIX FSH is composed of short coded names because of historical reasons, maybe because back in the old days, programmers used to leave out some comments, or use short names for variables and functions, and use some other tricks just to make the source code's size smaller, because disk space was expensive, which is not the case anymore.

Now what I care about is code and FSH readability, and I'm already working on getting rid of the alphabet-soup variable and function name habits.

To me, Windows's FSH is totally ugly and useless, the "Windows" folder looks like it was hacked in 10 minutes, and the "Program Files" folder looks like Corporation turf wars field, and the user folders is totally scary, that's one of the things that makes me hate Windows more and more, but sadly, I'm forced to use it.

But GoboLinux looks different, it looks elegant, useful, and open minded.

I really wish that everyone put's aside his other non-technical reasons, and really think about the benefits of GoboLinux's way, and also realize that good OS's is not just technically amazing, but also aesthetically appealing to everyone, even programmers.

Sorry for the long post and my bad English :D

---

### Post by dsiembab on 2008-05-18
I have to agree with their file system, What is your time worth? What I mean by that is why should you have to go to 4 different folders just to change one application?

---

### Post by smartboyathome on 2008-05-21
I tried gobolinux. I like the filesystem structure, but not much else. Especially their package "installer". :(

---

### Post by MetalheadGautham on 2008-05-27
I think its about time linux based distros started concidering single folder containing entire app as a reality. Having an application in a single folder where all configuration is also stored essentially adds much more customisability to placement of programs in one's OS. You can also have portable programs.

Already games like Urban Terror for linux are using the one folder per app approach and I think its awssome. This is one of those few feilds where windows and macintosh beat linux.

While the older placement should not be removed, as centralised locationing helps us a lot, an inbuilt support and encouragement for one folder per app style programs should be there. We can have something like JAR files, with a app.tar style archieve containing the entire app, and the configurations stored in an app.conf text doccument. The archieve can be given a custom extention and made recoganisable by the OS, and this concept advertised, sponsered and encouraged.

.deb packages and .rpm packages of programs can start having an install option that installs the application as a single file app.

But other than this, I don't think the original filesystem hierarchy needs to be changed. It will prove to be hardly useful, and only break older packages. Instead, enabling users to install single file apps anywhere they like is a good idea.

---

### Post by smartboyathome on 2008-05-27
For the last time, this *wont break any packages*. It uses symlinks, so it keeps full compatibility with the current structure.

---

### Post by omar8 on 2008-06-21
Gobolinux file structure is such a great idea, I just wish more Linux distributions would break away from the mould and try something new! I thought the whole idea of open source meant that there would be a greater degree of customisability, someone with the skills should make a GoboLinux styled Ubuntu distro.
some people think its just a copy of Windows, I don't but I always thought that there was nothing wrong with stealing ideas if they can help improve the product.

---

### Post by aysiu on 2008-06-21
> **omar8 said:**
> I thought the whole idea of open source meant that there would be a greater degree of customisability That *is* the whole idea of open source. That's why GoboLinux can exist. The other key to open source, though, is that just because you think someone "should" make a certain customization doesn't mean someone will. It offers you freedom but not the right to make demands.

If you want a customization, you make it yourself, ask someone nicely to make it for you (with no expectations that it will or should happen), or pay someone to make it for you.

---

### Post by dsiembab on 2008-06-21
> **aysiu said:**
> That *is* the whole idea of open source. That's why GoboLinux can exist. The other key to open source, though, is that just because you think someone "should" make a certain customization doesn't mean someone will. It offers you freedom but not the right to make demands.

If you want a customization, you make it yourself, ask someone nicely to make it for you (with no expectations that it will or should happen), or pay someone to make it for you.
I thought I read should, now should doesn't sound like a demanding word. I also think it would be neat to see an ubuntu flavor like gobo you could call it fubuntu for file-system  ubuntu. I am not demanding.:)

---

### Post by aysiu on 2008-06-21
Well, it's very nice for you to think something would be neat if you don't have to do the work to make it happen. Whether you make demands or not, something isn't going to magically appear just because you think it's a neat idea.

---

### Post by dsiembab on 2008-06-21
Let me tell you something aysiu, gobolinux rocks

---

### Post by dsiembab on 2008-06-21
Another thing you mean linux distro don't get brought by the stork? After hardy how where your backers I am sure they where understanding about releasing a beta distro as a rock solid distro, funny the distro came out and their is over a hundred updates already. I'm not trying to bash anything it's just funny in my eyes. But I guess I would have to fix all the updates myself, right, and not make any suggestions. Ubuntu it just loads, sorry wrong crowd. I am sure a faulty distro sure is profitable with paid support.

---

### Post by JeevesBond on 2008-08-14
Was just looking through the blueprint and brainstorm for this idea again. It seems -- I just did a search -- there was never a link to the related brainstorm idea posted in this thread, so thought I'd put it up: [http://brainstorm.ubuntu.com/idea/12137/](http://brainstorm.ubuntu.com/idea/12137/)

Strangely the brainstorm site seems to have a lot more people against the idea than these forums do! :)

---

### Post by aysiu on 2008-08-14
> **JeevesBond said:**
> 
Strangely the brainstorm site seems to have a lot more people against the idea than these forums do! :) It's actually not that surprising.

1. The phrasing in the poll options here are biased in favor of voting for the idea ("It's time for a change").

2. This poll allows you to vote on a neutral option instead of just Yes or No.

3. People who don't care about changing the filesystem are less likely to click on this thread and then vote on the poll than people who browse Brainstorm are to just click an up or down arrow while browsing.

---

### Post by MaxIBoy on 2008-08-15
"Alternative distro?" That's how Windows does the directories. 


I'm skeptical.

---

### Post by smartboyathome on 2008-08-15
I've tried this on an Arch install, and ruined that install (I needed to reinstall anyway, and had everything backed up, so no biggy). It is much more than simply symlinking the directories and such. The patches and user space applications install run fine, but the problem comes when you try to symlink. The kernel freaks out and dies because it doesn't see it as the same structure as it should be. I tried this a couple times, and both times I had it tell me this wasn't a known file system. Obviously, the patches and app are not the only stuff they did to get this working. I am guessing their hacked grub set up the environment as well, if not something else they hacked. I don't even know if anyone can tell you how it was originally set up, perhaps the creator can? Either way, I did what I could, and it didn't work. Just thought I would inform you that this would *have* to be a separate project from Ubuntu, and would take tons of hacking.

EDIT: The package installer also helps by linking everything up, but thats a different situation than just trying to change the file system structure.

---

### Post by MONODA on 2008-08-16
I dont think it matters at ll actually, if anything it's a bad thing since it makes things a lot more complicated and prone to bugs etc.

---

### Post by jrothwell97 on 2008-08-16
> **smartboyathome said:**
> I've tried this on an Arch install, and ruined that install (I needed to reinstall anyway, and had everything backed up, so no biggy). It is much more than simply symlinking the directories and such. The patches and user space applications install run fine, but the problem comes when you try to symlink. The kernel freaks out and dies because it doesn't see it as the same structure as it should be. I tried this a couple times, and both times I had it tell me this wasn't a known file system. Obviously, the patches and app are not the only stuff they did to get this working. I am guessing their hacked grub set up the environment as well, if not something else they hacked. I don't even know if anyone can tell you how it was originally set up, perhaps the creator can? Either way, I did what I could, and it didn't work. Just thought I would inform you that this would *have* to be a separate project from Ubuntu, and would take tons of hacking.

EDIT: The package installer also helps by linking everything up, but thats a different situation than just trying to change the file system structure.
I don't claim to be an expert, but AIUI the system needs to be built from scratch with the new directory structure. The kernel and init will live wherever you want them to - you just need to tell them, *from the start*, where everything else is. Then the symlinks are created once the kernel and a toolchain are installed - *I think*. I may be completely wrong, which is, it has to be said, more likely than me being right.

---

