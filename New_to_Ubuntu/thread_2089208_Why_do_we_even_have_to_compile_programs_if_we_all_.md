---
title: "Why do we even have to compile programs if we all run the same kernel?"
date: 2012-11-28
forum: New to Ubuntu
---

### Post by venom104 on 2012-11-28
Okay, first off, to better explain my question, I should state that I am not talking about JUST Ubuntu Linux. I am wondering why for the vast majority of programs out there, we either need to install them though a package manager, compile them, or download a corresponding "packaged" file (deb,rpm, etc).

Think of it like this.... go here, and download firefox 17

[http://www.mozilla.org/en-US/firefox/all.html](http://www.mozilla.org/en-US/firefox/all.html)

Untar the file, open the firefox folder, open a terminal session there and type ./firefox . It works, and you didn't have to compile anything or install anything though a package manager to get it to work.

Firefox is not distributed as the source, a make file, and a bunch of other needed files to create it (I'm guessing like the corresponding object files and the like). 

I realize that you would probably run into dependency problems, but I cannot seriously imagine choosing a compiled program over one that simply works because you can't figure out how to open the README file that comes with the program.

As far as the kernel goes, I do realize that you can build your own with some modifications, and no distros probably run the EXACT same kernel (they all do stuff to make it better), but we are all probably using the same base from kernel.org.

So...what's the deal? Why do people that make these programs just not give out pre-made executables that work with any version of the kernel arch they want it to?

---

### Post by QIII on 2012-11-28
Because some of them have to spend at least a little bit of their time earning a living rather than developing and testing flawless installers for packages they already make no money on?

---

### Post by audiomick on 2012-11-28
Hmmm, there might be something in that... :-k

---

### Post by venom104 on 2012-11-28
> **QIII said:**
> Because some of them have to spend at least a little bit of their time earning a living rather than developing and testing flawless installers for packages they already make no money on?


I really don't think you understand what am saying.

Not everyone wants open source. I'm not saying you can't make money with an open source business model, but that seems to be the consensus among to the "average" people. 

If they just made exectuables, they wouldn't have to worry about however long it would take to put in the repos, or the people that mantain those packages.

So, by just making an executable, you can still keep your program runnable and distributable, but NOT HAVE to distribute the source.

If you think I am crazy, go and download any nvidia driver installer for linux. YES, IT DOES COMPILE THE DRIVER, my point is a self running executable, that runs fine AS LONG AS YOU HAVE THE DEPENDENCIES.

EDIT:

Also, I didn't say anything about installers. It sounds like you didn't click on the link and see that when you download firefox, it runs as is, no install required (although you'd be wise to put in a directory outside your home folder and provide symlinks so that other users can actually...use it...but it is NOT required).

---

### Post by nothingspecial on 2012-11-28
The whole point is that you can read the source and even modify it before you compile it.

---

### Post by MG&amp;TL on 2012-11-28
That would have to mean supplied libraries with programs (or a **lot** more discussion about standards...), which would balloon the size of installations.

Plus, what's wrong with package managers? Upstream guys make stuff they know how to build, tell the package maintainers how to make a script to build it, package maintainers compress and upload. Simples. :)

I see your point, and sometimes it would be helpful. But for the majority of the time (I don't care about *libc*!), I think package managers are easier.

---

### Post by Zill on 2012-11-28
One of the great advantages of FOSS is that most software sources are available for rigorous scrutiny, vastly reducing the chances of any malware getting through to the end user.  OTOH, simply supplying executable "binary blobs" is just asking for trouble IMHO.

---

### Post by QIII on 2012-11-28
> **venom104 said:**
>  It sounds like you didn't click on the link and see that when you download firefox, it runs as is, no install required (although you'd be wise to put in a directory outside your home folder and provide symlinks so that other users can actually...use it...but it is NOT required).

I guess "installers" are really unimportant in the frame of this discussion.

My point is that TIME *is often still an issue*.

For some applications, there are few complications or worries.

---

### Post by venom104 on 2012-11-28
> **MG&TL said:**
> That would have to mean supplied libraries with programs (or a **lot** more discussion about standards...), which would balloon the size of installations.

Plus, what's wrong with package managers? Upstream guys make stuff they know how to build, tell the package maintainers how to make a script to build it, package maintainers compress and upload. Simples. :)

I see your point, and sometimes it would be helpful. But for the majority of the time (I don't care about *libc*!), I think package managers are easier.

I never said there was anything WRONG with package managers, although there are numerous articles written about "why linux will never catch on mainstream", and they all include something about 1) The lack of a standardized desktop manager (and no, I am not talking about x server) and 2) The lack of a universal install type package (again, deb, rpm, etc) 3) "Each" (using the term loosely) linux distro has it's OWN package manager. Some do not even handle dependices. Not to mention that when you upgrade ubuntu (I must admit, I have not done this since I upgraded Fiesty Fawn to Guttsy Gibbon, so things MAY have changed), your /etc/apt/sources.list file remained the same, you have to edit it yourself...I am also not sure how an upgrade handles your PPAs either (I don't believe PPAs were around the time Ubuntu 7.04 was out) 4) Any updates to the source have to be cascaded though each and every repo...and there are QUITE a few different linux distros out there. 5) I am not saying installing programs on any linux distro is hard, but the term "hard" is relative to the individual. Ever hear of linuxsucks.org? I'm not sure what happened to the site, but a vast amount of users complained that they couldn't just "click a button and have stuff work" like on windows.

My overall point was that while it does seem someone illogical to do things the way they are now, I was simply asking for a reason why. I just seek understanding, I am not saying the way things are currently done is stupid.

EDIT: And just so everyone knows, the reason I like ubuntu is because it's debian derivative (which means it has the functionality of my favorite front end package manger apt-get) while still opening the doors to BLEEDING edge software. I make a choice to run ubuntu as my primary OS, not because I have to, but because I WANT to.

---

