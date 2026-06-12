---
title: "Participating in Ubuntu development"
date: 2010-10-07
forum: Programming Talk
---

### Post by Searock on 2010-10-07
I wish to participate in Ubuntu development.

And I am familiar with these languages and technologies.


[LIST]
[*]C
[*]C++
[*].Net
[*]PHP
[*]SQL
[/LIST]
I know some of basics of system-programming in posix like 


[LIST]
[*]Process (Forking)
[*]Threading
[*]Inter Process Communication (Pipes and socket)
[*]Memory Management (mmap,..)
[/LIST]
 
Currently I am learning GTK +.

What else should I need to learn if I want to participate in Ubuntu  community.

Can I participate in Ubuntu  community with my current skills ?

Thanks.

---

### Post by Queue29 on 2010-10-07
Definitely take a look at learning how to use version control systems. I'm not sure, but I think Ubuntu's stuff all uses bazaar, though a lot of other people tend to use hg (Mercurial) or git.

---

### Post by Vox754 on 2010-10-07
> **Searock said:**
> I wish to participate in Ubuntu development.

Exactly, what do you think Ubuntu is?

Ubuntu is not a single piece of software, Ubuntu is an entire Operating System, that is, a collection of
* The Linux kernel
* GNU standard tools
* Core libraries, such as the X Window system
* Desktop managers, window managers, package managers, base software for configuring the system
* And finally, user-level applications

Ubuntu, just like any other Linux distribution, just packages everything together, and provides custom configurations for some elements, thus giving it its particular feel.

The beauty of free software is that you don't need "permission" to contribute. Just look at the particular layer or application you are interested in, start reading how things are done, and start providing code to that project.

> 
And I am familiar with these languages and technologies.
...

You don't need to know all languages to contribute, just the ones that are used by a specific piece of software.

More important than knowing languages, is that you are familiar with the code and conventions of a particular piece of software. If you like Audacious, and you find that it uses C++ and GTK+ (GTKmm), subscribe to their mailing lists, read their developer's documentation, see what version control system they use, ask questions in the IRC channel, report bugs in the bug tracker, obtain a copy of the code, study it, and try to solve bugs yourself, then submit the solution back to the developers, build, test, and package your own solutions. It's an entire process of learning and working.

> 
What else should I need to learn if I want to participate in Ubuntu  community.

Can I participate in Ubuntu  community with my current skills ?

Thanks.
As described, most programmers don't contribute just to "Ubuntu", they contribute to specific applications they like, such as text editors, music players, video downloaders, browsers, etc. Then all these programs get together to constitute Ubuntu as a whole.

Of course, the core Ubuntu developers, lead by Canonical, actually do some specific programming, and make some decisions regarding the interface or the default programs to be included in each release. You can also subscribe to their mailing lists, and participate in their discussions, but be aware that usually this means you know exactly what you are doing.

If you are just a novice, I suggest you keep lurking, keep reading, keep learning. It will come the day you realize you know enough and are ready to actively participate in development of major components.

---

### Post by Searock on 2010-10-07
> **Queue29 said:**
> Definitely take a look at learning how to use version control systems. I'm not sure, but I think Ubuntu's stuff all uses bazaar, though a lot of other people tend to use hg (Mercurial) or git.


I have installed bazaar and specially this [Beginners Guide to Bazaa]("http://ubuntuforums.org/showthread.php?t=916132")r tutorial has really help me. Thanks.

> **Vox754 said:**
> 
Exactly, what do you think Ubuntu is?
Ubuntu is not a single piece of software, Ubuntu is an entire Operating System.


I know it is not a single software. What I meant to say was I wanted to contribute to Ubuntu Community either by doing some testing or some programming or anyother related stuff. May be my english is really bad. : )

> **Vox754 said:**
> 
If you are just a novice, I suggest you keep lurking, keep reading, keep learning. It will come the day you realize you know enough and are ready to actively participate in development of major components.

Thanks for the advice.

---

### Post by Vox754 on 2010-10-07
> **Searock said:**
> I have installed bazaar and specially this [Beginners Guide to Bazaa]("http://ubuntuforums.org/showthread.php?t=916132")r tutorial has really help me. Thanks.

I know it is not a single software. What I meant to say was I wanted to contribute to Ubuntu Community either by doing some testing or some programming or anyother related stuff. May be my english is really bad. : )

Don't worry, your English is not bad. It's just that I've seen this before, right here in this same forum. Some people arrive asking for Ubuntu's "source code", because they want to start "hacking" it... it just doesn't work that way. I just wanted to give a reasonable complete answer (hey, other people may read this post in the future).

With that said, learning version control systems like Bazaar is a great idea. You can go to Launchpad and start pulling branches, patching the sources and uploading it to your own branches, just to test things.

The definite answer to "how to contribute to Ubuntu?" is simply, contribute to the applications you like. If your code is good enough, it will eventually be packaged into Debian, Ubuntu, and other distributions. So it's about giving back to the free software world, not just one distribution.

I also have to mention that given Ubuntu's reputation, some developers decide to use Launchpad as their main source code repository, and thus their code becomes very well integrated into Ubuntu repositories and release cycle.

So my advice is, create a Launchpad account, set up your own branches and start experimenting with changing other people's code. Pick a project you like, that way you'll be motivated when you delve into it. Also, I do recommend having at least basic knowledge of GTK+ and QT, as they are the main platforms on which most user programs are built in Linux.

---

### Post by lisati on 2010-10-07
Being involved here and at Launchpad is a great start.

---

### Post by Searock on 2010-10-08
> **Vox754 said:**
> 
With that said, learning version control systems like Bazaar is a great idea. You can go to Launchpad and start pulling branches, patching the sources and uploading it to your own branches, just to test things.

The definite answer to "how to contribute to Ubuntu?" is simply, contribute to the applications you like. If your code is good enough, it will eventually be packaged into Debian, Ubuntu, and other distributions. So it's about giving back to the free software world, not just one distribution.

I also have to mention that given Ubuntu's reputation, some developers decide to use Launchpad as their main source code repository, and thus their code becomes very well integrated into Ubuntu repositories and release cycle.

So my advice is, create a Launchpad account, set up your own branches and start experimenting with changing other people's code. Pick a project you like, that way you'll be motivated when you delve into it. Also, I do recommend having at least basic knowledge of GTK+ and QT, as they are the main platforms on which most user programs are built in Linux.

> **lisati said:**
> Being involved here and at Launchpad is a great start.

Thanks for the advice and encouragement. :)

---

### Post by Searock on 2010-10-08
I have found one documentation on contributing to **[Ubuntu community]("https://wiki.ubuntu.com/UbuntuDevelopers")**.

---

