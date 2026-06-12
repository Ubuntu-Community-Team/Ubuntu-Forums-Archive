---
title: "How can I make .deb packages? Need to include description, version # and dependencies"
date: 2009-02-17
forum: Packaging and Compiling Programs
---

### Post by Panarchy on 2009-02-17
Hi

Interested in making Debian/Ubuntu packages (.deb). Perhaps for use on a local repostitory, perhaps for use officially with either Debian or Ubuntu (or both!).

First things first, how do I do it?

I'd like to be able to do the following;
[LIST=1][*]Say that I am the maintainer of the package
[*]A description (and name) of the package
[*]The version of the package/program
[*]Any dependencies the packages needs to be installed[/LIST]

I've done a little research on my own, and checkinstall seems the best. As in, the easiest. However I don't know if it'll be possible to do the things listed above using that program.

Can I please have some advice on what the best/fastest/most reliable (stable) way of creating Debian/Ubuntu packages is?

Thanks in advance,

Panarchy

---

### Post by ikonia on 2009-02-17
Panarchy - I've got some serious questions to ask of you before you continue to push this sort of stuff.

1.) why are you posting in an ubuntu forum on this topic after you've just finished telling everyone in the irc channels ##linux and #debian that your operating system is based on Debris - not ubuntu.

2.) You've spent hours over the period of months telling us how you've built 10 - 15 releases of your own OS based on ubuntu and you've included packages and updated packages, if this is the case, how can you be asking how to make .deb packages ?

3.) you've asked the same question on the debian forums [http://forums.debian.net/viewtopic.php?t=35836](http://forums.debian.net/viewtopic.php?t=35836) as well as spamming multiple irc channels with the same question and both of these threads, you've been asked in multiple formats to STOP cross posting the same question in multiple places multiple times, and you don't seem to be able to grasp this, it's starting to put a real negative light on your posts and now you've moved beyond this on IRC to now doing the same behaviour in forums if you want help - you'll get a much better response if you stop ignoring peoples advice and start listening to what people are trying to tell you to help get the information you want and need.

This is not designed to put you off, but actually try to get you get the help and support you need, 

you're not coming across well on the medias I read post from you (forums/irc) on, cross posting, posting the same thing mutliple times after been given the answer, miss-leading people about what you have and have not done (or at least phrasing it badley) this takes away a lot of the good will and starts to get you a repuatation  - please please please, listen to what's being said to you and work with the people trying to help you rather than just keep blindly asking the same question in as many different places as you can find, it will get you much better support and good will from people trying to help you.

I am genuinly trying to help you - but your not making it easy.

---

### Post by Panarchy on 2009-02-17
Hello again Ikonia,

Yes, I have created many releases and version of my own OS. Yes, my next version will be built on Debris.

I don't see what you're getting at?

I mentioned in my 1st post on this topic, that I was thinking of creating a repository for use either officially or unofficially that can be used on Ubuntu/Debian [based] systems.

And the reason I want to package these, is because this would be pretty much a one time thing to do, (for most of them, since some haven't been updated in A-G-E-S).

Thus making it easier if I ever need to recreate my distribution from scratch, again, it should be a 'piece of cake'!

So what I am asking here, is **How do I package tools into .deb packages?**

Please tell me how!

Thanks in advance,

Panarchy

---

### Post by Panarchy on 2009-02-17
Best answer (so far), was from #ubuntu-motu on irc.freenode.net, here's a quote from **persia** and **directhex**;> Basically, you need to create four extra files: changelog, control, copyright, and rules.  In the simple case, rules can be copied form examples provided in the debhelper. Your first changelog entry usually says "initial packaging" and possibly a bug number for an ITP bug.

The description is in the control file.  The changelog for the first revision is typically "Initial Packaging" the package name, the version, and the packager's name.  dch --create will generate a template.
and
> build the skeleton with dh_make, fill in properly debian/control, debian/changelog, debian/copyright and debian/rules and delete the rest
by **Baby**

Panarchy

---

### Post by cjssmo on 2009-02-17
Please if you are interested in Debian/Ubuntu packaging (making a .deb's) please read and make yourself familiar with the below listed documents as they will answer most of your questions.   

[https://wiki.ubuntu.com/PackagingGuide](https://wiki.ubuntu.com/PackagingGuide)

[http://www.debian.org/devel/](http://www.debian.org/devel/)

[http://www.debian.org/doc/debian-policy/](http://www.debian.org/doc/debian-policy/)

[http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)

[http://www.debian.org/doc/developers-reference/](http://www.debian.org/doc/developers-reference/)

---

### Post by ikonia on 2009-02-18
I put a post in response to you detailing that you have to listen and read the threads and responses posted to you.

There is an excellent post with links detailing exactly what you want to do.

What do I find this morning.

Yes, 

you have spammed the ##linux and #debian freenode channel with exactly the same question/text as you did before you posted this thread,  

so after I ask you to consider what you're doing and read the responses, you ingnore it and post exactly the same question as this forum thread, and your original IRC question 24 hours earlier.

01:27 < Panarchy> What is the easiest way to create a .debpackage? I need one that can include: -That I am the maintainer of the package- | -A description (and name) of the package- | -The version of the package/tool- | -And any dependencies the packages needs to be installed-

02:02 < Panarchy> I just posted a question about the automation of .deb package creation here: [http://forums.debian.net/viewtopic.php?t=35860](http://forums.debian.net/viewtopic.php?t=35860) and here: [http://ubuntuforums.org/showthread.php?t=1072928](http://ubuntuforums.org/showthread.php?t=1072928)

you posted this exact text almost word for word 24 hours earlier ago and look - you've cross posted again.

READ the responses given to you, you say MOTU's gave you info and earlier in this thread cjssmo gave you great links - yet you're STILL asking "how do I do this" - if you'd read these links you'd have specific questions, rather than "how do I do it"

Why do you persist in ignoring advice and spamming as many media sources as you can find ??

As a side issue, I'd love to know what package you are (or want to be) the maintainer of.

---

