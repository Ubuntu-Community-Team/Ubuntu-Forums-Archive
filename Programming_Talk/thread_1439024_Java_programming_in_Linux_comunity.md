---
title: "Java programming in Linux comunity"
date: 2010-03-25
forum: Programming Talk
---

### Post by Uubnewb on 2010-03-25
Hi everyone,

I've gone through the FAQ and searched the forums for previous posts but could not find a satisfactory answer, so I decided to open a new thread.

I recently started with a course in software development.  Part of this course includes one full programming language and another language that will be done only half-way (I can complete it later but it falls outside the scope of this course).

Quite a while ago, when I initially considered this course, I got the advise from someone to join an open-source project as soon as I start with my main language.  That way I can get some real-world experience while studying.

I decided to go with Java for my main language (mainly because of job opportunities in my local area) and googled around a bit to see if I can find a nice open source project to join.  This, however, sounds much easier than it really is.  Not because of a shortage of projects:  Oh no, quite the opposite!

The problem is I don't have any programming experience yet and reading through the descriptions of all those projects is a VERY arduous task if you don't understand half of what is being said (I know, I know... it sounds rather lame when I want to learn the language but I can't even follow the description properly; it kind of makes me wonder what I've gotten myself into here :)).

So here's my question:  Can anyone here maybe recommend a good Java project for me.  I'd prefer something related to Linux (and if I can be really picky, something related to Ubuntu), but most importantly, something that will ultimately help me master the language.  A project that has good, easy-to-follow instructions, lots of comments that explains things to newbies and something that is not too big to download (my internet is very slow :) )

Any and all help in this regard will be greatly appreciated.

---

### Post by Uubnewb on 2010-03-26
Bump.

---

### Post by LKjell on 2010-03-26
You can try re implement linked list in the java collection api using generics and interface.

---

### Post by Cracauer on 2010-03-26
Some Eclipse enhancement is probably a good bet, and it might benefit you for your own work.

The Apache project still has many Java projects.

You won't find much Java in OpenSource mainstream, though. Sun's political antics (in combination with some in hindsight stupid kicking and screaming around required technical enhancements) have successfully prevented Java from gaining any foothold in OpenSource projects, as I said with the exception of some server-side web packages. That's where we are, unfortunately.

---

### Post by Uubnewb on 2010-03-27
Thank you for the replies,

I've checked out Eclipse and Apache and both seem like good places to start out.

It's strange though, with Java being an open-source language one would expect a larger open source community attracted to it.  To be honest I kind-of got spoiled by the vastness of the Ubuntu community.  :)

---

### Post by Cracauer on 2010-03-27
> **Uubnewb said:**
> It's strange though, with Java being an open-source language one would expect a larger open source community attracted to it.  To be honest I kind-of got spoiled by the vastness of the Ubuntu community.  :)

Java is not anywhere close to OpenSource in those regards that really matter. Being able to gaze at the source is not the same thing as OpenSource. For most of us it's full OSI compliant license or nothing. If you don't have that command and control in OpenSource projects doesn't work and your project doesn't go anywhere. Unfortunately that is the position Sun has out us in.

---

### Post by ktzqbp on 2010-03-27
FreeMind might be an option for you; small codebase and developer circle so if you jump on IRC they should be able to help you out :)

---

### Post by Uubnewb on 2010-03-28
> FreeMind might be an option for you
I've checked it out, and I must say the fact that it is only 13MB to download is very nice.

I haven't decided on a project yet, I first want to play around with the programs before comitting myself.  Unfortunately I just do not have the time at the moment, but I'm going on a short holiday next week which will give me plenty of time.

> For most of us it's full OSI compliant license or nothing.
This is the first time I've come across the term "OSI compliant license" so naturally the first thing I did was Google it.  However, I'm still a bit in the dark.  They seem like just another organization trying to promote open-source.  Why are their license so important?

To be honest, I never even knew there were different kinds of open-source licenses.  I always thought that if I can view the source-code it must be open-source.

---

### Post by Shin_Gouki2501 on 2010-03-28
don't go there ( into the depth of license , laws and such ) u will drown there.

In fact Java is pretty much good in the "OpenSource" Space but Platform control is something diffrent.

Anyway if i wanted to start a pointless flamewar i would call that arrogant and false:
"The Apache project still has many Java projects.

You won't find much Java in OpenSource mainstream, though. Sun's political antics (in combination with some in hindsight stupid kicking and screaming around required technical enhancements) have successfully prevented Java from gaining any foothold in OpenSource projects, as I said with the exception of some server-side web packages. That's where we are, unfortunately."
Just for credits look how many projects use what languages on apache:
[http://projects.apache.org/indexes/language.html](http://projects.apache.org/indexes/language.html) 

Linux is not the one and only incarnation of OpenSource. In fact if you go to the depth of the FSF you will find interesting statements and such where every single person has to decide for himself what the term "free" or "open" means.

There are a lot of OpenSource licenses and many big projects don't use you GPL and there are reasons for that.
(Example: [http://en.wikipedia.org/wiki/Haiku_%28operating_system%29](http://en.wikipedia.org/wiki/Haiku_%28operating_system%29))

So spining back to topic, i do think apache has a lot growing number of java projects and you should be able to find there some project which would fit you.
Lucene seems nice!

---

### Post by Cracauer on 2010-03-28
> **Uubnewb said:**
> 
This is the first time I've come across the term "OSI compliant license" so naturally the first thing I did was Google it.  However, I'm still a bit in the dark.  They seem like just another organization trying to promote open-source.  Why are their license so important?

To be honest, I never even knew there were different kinds of open-source licenses.  I always thought that if I can view the source-code it must be open-source.

There are two basic kinds of "real" OpenSource licenses. GPL style and BSD/MIT style. The important part in those licenses, and that is what OSI compliance requires, is the right to split the project, and that is essential for command and control in OpenSource projects.  If I am insatisfied with what the current developers of -say- fvwm2 do I can take the whole source tree and split the project, opening a derivative under a different name on my own hardware.  I don't want to do that, but the threat of doing that keeps the original project owners in line. If the base of contributors (not users) is unhappy and might leave alongside me a compromise will usually be found.  GPL and BSD/MIT both allow that.

The "oh yeah you can look at the source" style licenses like Sun placed the JDK under initially don't do any good. Because the original project owner has full control. These licenses allow me to see the source and submit patches back. But the direction of development is dictated and the contributor base has no leverage. You are not allowed to take the whole thing and make a project fork, and that disables all control on part of the contributors.

A lot of people do not, ever, contribute to projects with the latter license, and that lead to severe damage for Java in the OpenSource community.  We liked the language when it came out but the license on the JVM and JDK required that the OpenSource community rolled their own JVMs. With no support by companies and they weren't much good. Many people wanted to get work done in Java other than hacking on the Java VM and just used Sun's version. So no big pressure to improve the OSI-compliant JVMs and hence OpenSource Java users (application programmers) and OpenSource Java implementors (JVM writers) pretty much never met.

And even today there are parts of the JDK that are not under OSI compliant licenses. Try to build the jdk from source in BSDs or Gentoo. You'll have to special-case at least some files. Sun just *"doesn't get it"*, like they say.

I'll also say that some changes that Microsoft wanted made to the language were just plain good and that Sun was just stubborn.

Related to that the there is the whole issue of finally "granting" us compile-time generics and printf - a decade too late, after all libraries were designed without them. And the half-baken inner classes falling short of full access to local variable scope. You would think that an old Lisper like Guy Steele would prevent them from jumping the shark that hard but it appears he didn't have or at least not exercise veto power.

Anyway. Understanding how command and control work in OpenSource will be critical to your personal involvement. There are a lot more organizations and individuals out there who don't understand that aspect and then are left puzzled when people don't work with them and that they can't predict what will take off community-wise and what won't.

---

### Post by Uubnewb on 2010-04-01
Sorry for my delayed reply, I had some internet troubles.  Thanks once more for the replies, I really appreciate it.

I guess it makes sense that more people will join a project that they have more controle over.  Especially if there are changes they eagerly await that are just never implemented.

It is sad though that a language that seems to have so much to offer can be pushed to the background so easily.

Please understand that I am neither trying to start a flame-war nor do I wish to offend; I am simply trying to learn. :)

As far as ignorance goes, I think I can relate (albeit in a very small manner).  In the college I go to there is only one instructor that knows anything about Linux.  When Linux is mentioned they usually look at me like I'm crazy.  That being said I can't exactly blame them for something I would have done too, had I not discovered the joys of Linux a short while ago.  :)

> So spining back to topic, i do think apache has a lot growing number of java projects and you should be able to find there some project which would fit you.
Lucene seems nice! 

It does seem nice, although I think I might try to go for Eclipse.  When I start with my second programming language (I've decided on C++) I'd like to join the [Gnome project]("http://live.gnome.org/GnomeLove").  It seems like fun. :)

---

### Post by The Cog on 2010-04-03
Hadoop, hbase and cassandra might be intetesting for you. They are all apache java projects.

---

