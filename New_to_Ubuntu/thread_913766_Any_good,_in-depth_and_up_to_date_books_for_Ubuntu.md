---
title: "Any good, in-depth and up to date books for Ubuntu?"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by tnek on 2008-09-08
Hi,

I do know the basics and would like to have something which goes more in-depth than the usual beginners books.

Things I would like to learn at the moment are:

[LIST]
[*]How to install new hardware (like scanners, printers and other stuff) and configure them
[*]How to use ndiswrapper for my wireless card
[*]How to get video acceleration working for my Intel graphics card when I've installed ubuntu from the minimal mini.iso distribution. It works using the normal installation method. Yet the xorg.conf of them both are exactly the same. I want to know more so that I can add what's missing to my mini.iso installation and get direct rendering working and hardware accelleration.
[*]Exacly what events are available in Upstart. I would like to mount a file system automatically when I insert my USB thumb drive. I bet there are lots of other nice things possible using Upstart but I have a hard time finding good  documentation.
[*]What scripts should be in /etc/dhcp3/dhclient-exit-hooks.d/ and  /etc/dhcp/dhclient-enter-hooks.d and when do these get executed? And as what user? And I would like to know about other similar event based directories.
[*]Using wireless completely from the command line in a "minimal" way.
[/LIST]
Are there any books which cover these things? And if not. Any other source you recommend for learning more? Using the forum as a way to learn is cumbersome and I find that few answering users has any deeper knowledge. This could be a result of it being hard to find sources to learn from, just as I find it. :)

---

### Post by regala on 2008-09-08
> **tnek said:**
> Hi,

I do know the basics and would like to have something which goes more in-depth than the usual beginners books.

Things I would like to learn at the moment are:

[LIST]
[*]How to install new hardware (like scanners, printers and other stuff) and configure them
[*]How to use ndiswrapper for my wireless card
[*]How to get video acceleration working for my Intel graphics card when I've installed ubuntu from the minimal mini.iso distribution. It works using the normal installation method. Yet the xorg.conf of them both are exactly the same. I want to know more so that I can add what's missing to my mini.iso installation and get direct rendering working and hardware accelleration.
[*]Exacly what events are available in Upstart. I would like to mount a file system automatically when I insert my USB thumb drive. I bet there are lots of other nice things possible using Upstart but I have a hard time finding good  documentation.
[*]What scripts should be in /etc/dhcp3/dhclient-exit-hooks.d/ and  /etc/dhcp/dhclient-enter-hooks.d and when do these get executed? And as what user? And I would like to know about other similar event based directories.
[*]Using wireless completely from the command line in a "minimal" way.
[/LIST]
Are there any books which cover these things? And if not. Any other source you recommend for learning more? Using the forum as a way to learn is cumbersome and I find that few answering users has any deeper knowledge. This could be a result of it being hard to find sources to learn from, just as I find it. :)

would be pointless to write just another book on the way LINUX is set up. The Internet is full of this, and Ubuntu does things the way Linux always did before Ubuntu was born.

---

### Post by jemate18 on 2008-09-08
> **tnek said:**
> Hi,

I do know the basics and would like to have something which goes more in-depth than the usual beginners books.

Things I would like to learn at the moment are:

[LIST]
[*]How to install new hardware (like scanners, printers and other stuff) and configure them
[*]How to use ndiswrapper for my wireless card
[*]How to get video acceleration working for my Intel graphics card when I've installed ubuntu from the minimal mini.iso distribution. It works using the normal installation method. Yet the xorg.conf of them both are exactly the same. I want to know more so that I can add what's missing to my mini.iso installation and get direct rendering working and hardware accelleration.
[*]Exacly what events are available in Upstart. I would like to mount a file system automatically when I insert my USB thumb drive. I bet there are lots of other nice things possible using Upstart but I have a hard time finding good  documentation.
[*]What scripts should be in /etc/dhcp3/dhclient-exit-hooks.d/ and  /etc/dhcp/dhclient-enter-hooks.d and when do these get executed? And as what user? And I would like to know about other similar event based directories.
[*]Using wireless completely from the command line in a "minimal" way.
[/LIST]
Are there any books which cover these things? And if not. Any other source you recommend for learning more? Using the forum as a way to learn is cumbersome and I find that few answering users has any deeper knowledge. This could be a result of it being hard to find sources to learn from, just as I find it. :)

Try tutorials from the IBM Developer Works. Not pretty much of a distro dependent, but the knowledge there is LInux in General... That's were I learned a lot. Especially the LPI 101 and 102 series

---

### Post by tnek on 2008-09-08
Thanks I'll check out the IBM DeveloperWorks series you mentioned. I looked briefly at the index and it seems promising.

And of course there is reason to write another book if things are changing. And there must be some things happening? And if not, do you know any book which covers Upstart? It's one recent software I would like to know more about.

---

### Post by starcannon on 2008-09-08
Try some of these:
[http://www.amazon.com/s/ref=nb_ss_gw?url=search-alias%3Daps&field-keywords=linux&x=0&y=0](http://www.amazon.com/s/ref=nb_ss_gw?url=search-alias%3Daps&field-keywords=linux&x=0&y=0)

Here's an older article about Upstart:
[http://www.linux.com/articles/57213](http://www.linux.com/articles/57213)

Have fun

---

### Post by tnek on 2008-09-08
Someone else? :)

---

### Post by lukjad on 2008-09-08
There are some books about Ubuntu. I even bought one a while back. I never really used it after finding this forums. If you want to learn things about Ubuntu, may I suggest  the sub-forum: [Tutorials & Tips]("http://ubuntuforums.org/forumdisplay.php?f=100"). It is really useful.

---

### Post by starcannon on 2008-09-08
@OP, you already read the Amazon list? (if so you should be a gnu ascended master, capable of grepping all their is to grok, or would it be grokking all there is to grep?)

I really like the Linux Bible and the Linux in a Nutshell books.

GL

---

### Post by lukjad on 2008-09-08
Hmmm?

---

### Post by tnek on 2008-09-09
> There are some books about Ubuntu. I even bought one a while back. I never really used it after finding this forums. If you want to learn things about Ubuntu, may I suggest the sub-forum: [Tutorials & Tips]("http://ubuntuforums.org/forumdisplay.php?f=100"). It is really useful.You never read in the book? Did you learn everything you know about Linux and Ubuntu from this forum? Personally I don't think that is a good route to take, as I can imagine there will be huge knowledge gaps. It's the same with the Tutorials & Tips forum, there are opportunities to learn from those tutorials but in most of the cases they use a pure "write this, place this here" approach. I want a good book (or the above mentioned tutorial, I haven't had time to check it out yet).

Has anyone got any recommendations of up to date books which you found satisfying after actually reading them? (To say that I should search for Linux on Amazon is not an intelligent or nice answer.)

---

### Post by nothingspecial on 2008-09-09
This site has linux books you can buy and links to loads of online books and tutorials.

[http://www.linux.org/docs/](http://www.linux.org/docs/)

This is an excellent beginners tutorial to the shell.

[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)

---

### Post by lukjad on 2008-09-09
I'm not saying I never read the book. I read parts of it. I read other computer book as well. I am saying that in a few weeks the $50 book was being less and less helpful. I still read parts of it on and off but I focused more on web tutorials. I'll try to get a few of them to you. If you prefer to read things in a book (I usually do too) then, by all means, do so. It's just that in my experience, I bought a 6.06 Ubuntu book and then installed 7.04 a few weeks later and ended up with at very nice monitor support. I like books but at least for Ubuntu, it seems like I always chose the wrong one.

Here are a few links that I found useful (FINISHED):

[CENTER][Howto: Set up Hardy for speed, v1.0]("http://kmandla.wordpress.com/2008/05/04/howto-set-up-hardy-for-speed/")

[Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")

[Install CD Customization]("https://help.ubuntu.com/community/InstallCDCustomization")

[Live CD Customization]("https://help.ubuntu.com/community/LiveCDCustomization")

[Mounting Windows Partitions Third Party NTFS3G]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G")

[The (Other) Ubuntu forums]("http://theubuntuforums.org/")[/CENTER]

**[CENTER][Psychocats.net]("http://www.psychocats.net/ubuntu/") (I highly recommend this site)[/CENTER]**

[CENTER][USB Installation Images]("https://wiki.ubuntu.com/USBInstallationImages")

[Is Ubuntu for You?]("http://ubuntuforums.org/showthread.php?t=63315")

[Debian Admin]("http://www.debianadmin.com/")

[How to Dual Boot when (Fill in the blank) is preinstalled]("http://thevistaforums.com/index.php?showtopic=19902")

[FOSSwire]("http://fosswire.com/")

[How to block internet advertisements, banners and spyware in Linux]("http://ubuntuforums.org/showthread.php?t=110440")

[Howto Create your own Ubuntu]("http://ubuntuforums.org/showthread.php?t=869659")

[How to Get Help]("https://help.ubuntu.com/community/HowToGetHelp")

[How to reset your password in Ubuntu]("http://www.psychocats.net/ubuntu/resetpassword")

[Less is more: the hidden treasure of less command]("http://www.cyberciti.biz/tips/less-is-more-the-hidden-treasure-of-less-command.html")

[Lightweight Linux]("http://lightlinux.blogspot.com/")

[(Linux is Not Windows)]("http://linux.oneandoneis2.org/LNW.htm")

[Open MS-Word and MS-PowerPoint file under Linux/UNIX]("http://www.cyberciti.biz/faq/open-ms-word-and-ms-powerpoint-file-under-linuxunix/")

[Security on Ubuntu]("http://www.psychocats.net/ubuntu/security#recoveryrisk")

[Super Grub Disk]("http://www.supergrubdisk.org/index.php")

[The table of equivalents / replacements / analogs of Windows software in Linux]("http://www.linuxrsp.ru/win-lin-soft/table-eng.html")

[The Ubuntu Guide]("http://ubuntuguide.org/wiki/Ubuntu:Hardy")

[Ubuntu Tips (beta)]("http://www.ubuntutips.net/")

[A bunch of links to different tips on Ubuntu]("http://ubuntuforums.org/showthread.php?t=863575")

[Linux Distribution Chooser]("http://www.zegeniestudios.net/ldc/index.php")

[Ubuntu Security (Very interesting!)]("http://ubuntuforums.org/showthread.php?t=765421")[/CENTER]

---

### Post by Ohakune on 2008-09-09
I'm looking to start hosting some of our sites on an internal LAMP server as opposed to a paid host.  Thanks for the info, I'll get my learning on now and see if Ubuntu is the way to go.

---

### Post by AndyCooll on 2008-09-09
> **starcannon said:**
> I really like the Linux Bible and the Linux in a Nutshell books
If you're going to buy a couple of books, I'd recommend titles from the above series too.

I've bought books from the above series, and while not using them very often, occasionally they have proved useful.

Usually though, online resources are better simply because it's easier to find information that meets your particular need of the moment. The books are fine for general purposes, but even ones written for Ubuntu (for instance) are still too generic in their information.

:cool:

---

### Post by kpkeerthi on 2008-09-09
These are the books I read when I started using Linux:
1. [http://www.amazon.com/How-Linux-Works-Brian-Ward/dp/1593270356](http://www.amazon.com/How-Linux-Works-Brian-Ward/dp/1593270356)
2. [http://www.amazon.com/Practical-Guide-Commands-Editors-Programming/dp/0131478230/ref=sr_1_1?ie=UTF8&s=books&qid=1220965846&sr=1-1](http://www.amazon.com/Practical-Guide-Commands-Editors-Programming/dp/0131478230/ref=sr_1_1?ie=UTF8&s=books&qid=1220965846&sr=1-1)
3. [http://www.amazon.com/Classic-Shell-Scripting-Arnold-Robbins/dp/0596005954/ref=pd_bbs_3?ie=UTF8&s=books&qid=1220965865&sr=1-3](http://www.amazon.com/Classic-Shell-Scripting-Arnold-Robbins/dp/0596005954/ref=pd_bbs_3?ie=UTF8&s=books&qid=1220965865&sr=1-3)

---

### Post by SteveNorman on 2008-09-09
ubuntu unleashed and ubuntu toolbox. Good admin books, great for reading in bed or on the can.

---

### Post by lukjad on 2008-09-09
I've finished with the links.

---

### Post by barzam on 2008-09-09
For all Scandinavians I recommend this e-book *Att använda Linux och GNU* (*Using Linux and GNU*) by Linus Walleij: [http://www.df.lth.se/~triad/gnulinux/](http://www.df.lth.se/~triad/gnulinux/). The book is free to distribute in electronic form.

---

### Post by starcannon on 2008-09-09
> Has anyone got any recommendations of up to date books which you found satisfying after actually reading them? (To say that I should search for Linux on Amazon is not an intelligent or nice answer.)

That was not cool man, I took time to post what I thought was useful, I even told you I have had good experiences with the In a Nutshell books and the Linux Bible books. To come at me like that was absurd. You asked for advice, I gave what I had, and even made some recommendations. To call me unintelligent and not nice is less than polite. Indeed this is the first time I have experienced that sort of attitude on these boards, and I hope its the last time.

My recommendation at this point is to... meh! never mind! /ignore tnek.

---

### Post by tnek on 2008-09-10
Thanks for all these great suggestions! I'll compile these into a "to read" list and go through all the on-line tutorials first.

After (or maybe during) the recommended on-line tutorials I'll see which of the recommended books I should invest in. It's pretty hard as there are quite a few suggestions and I can't buy them all. I'm mostly interested in the operative system architecture, how to install and configure hardware, the role of the kernel, drivers. I already feel comfortable around ls, curl, cat, sed, grep and the commonly used commands.

> That was not cool man
Sorry for offending you!  I felt it was a good idea to point out that it's not the sort of help I or most people are in need of. Your first post was just posting the first link you get from Googling for "upstart tutorial" and telling me to search for Linux at Amazon. :) I stand by my comment, but it's not intended as an insult to you personally. If you feel like discussing it further you're welcome to send me a PM.

---

### Post by panhandle on 2008-09-10
I personally like and use regularly the "Linux Administration Handbook" by Nemeth, Snyder and Hein.

If you need advanced but accessible, this is a great place to start, as many have found through the years.

---

### Post by SunnyRabbiera on 2008-09-10
Really books have been rendered useless in terms of linux as Linux is always adapting.
There are books to get started yes but they are always becoming out of date before you know it.

---

### Post by Sef on 2008-09-10
If you get Hardy Heron, then the book will be good for 3 or 5 years, depending on if you are using the desktop or server.

---

### Post by tnek on 2008-09-10
Thank you for the book suggestion panhandle! I will check this one out too. A visit to a well renowned bookstore or a library to browse the recommended books a bit before buying is starting to look like a good idea. :)

About if I should use a book or not. I feel that I have so much I need to learn. If I start out with reading a book describing the operative system architecture with practical examples of setting things up I think it will give me a good basis. I do have some knowledge but I feel that I have large gaps I want to erase. When it comes to commands there's almost always a good man page showing me how to use the command. A book could "tie it all together", then I could use online tutorials to keep up with new things and deepen my knowledge further. Also, books are usually very well written and checked for errors by many people before publication.

A book lasting either 3 or 5 years would give me plenty of time. I'm sure it will be easier for me to update my knowledge for the next next 3/5 years as well. :)

---

### Post by kpkeerthi on 2008-09-11
> **tnek said:**
> Thank you for the book suggestion panhandle! I will check this one out too. A visit to a well renowned bookstore or a library to browse the recommended books a bit before buying is starting to look like a good idea. :)

About if I should use a book or not. I feel that I have so much I need to learn. If I start out with reading a book describing the operative system architecture with practical examples of setting things up I think it will give me a good basis. I do have some knowledge but I feel that I have large gaps I want to erase. When it comes to commands there's almost always a good man page showing me how to use the command. A book could "tie it all together", then I could use online tutorials to keep up with new things and deepen my knowledge further. Also, books are usually very well written and checked for errors by many people before publication.

A book lasting either 3 or 5 years would give me plenty of time. I'm sure it will be easier for me to update my knowledge for the next next 3/5 years as well. :)

Very well said. I too prefer reading books cover-to-cover over picking resources off the internet in bits and pieces.
:)

---

### Post by lukjad on 2008-09-11
I agree that a book is usefull for basic information. But once you really want to learn something new and exciting, you need to use the web. I wish it weren't so, but as it is, book are not updated monthly, much less weekly.

---

