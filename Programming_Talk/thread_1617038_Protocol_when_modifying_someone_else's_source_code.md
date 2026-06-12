---
title: "Protocol when modifying someone else's source code"
date: 2010-11-08
forum: Programming Talk
---

### Post by Irihapeti on 2010-11-08
I found a program on SourceForge that looked useful to me. The project hasn't been touched for over 5 years. I made a minor modification to one of the source files to suit my needs - about a dozen lines of code in all.

Now a few of my friends/colleagues are interested in it, and I'm wanting to know how to do the right thing about distributing it.

According to the SourceForge project page, the project is licensed under the LGPL. However, when I look at the source files, there's absolutely nothing to indicate this. They are just marked Copyright to the original author, and some stuff about "absolutely no warranty" etc.

I've read through the GPL documentation, but the emphasis is on how to deal with original code, or maybe with patches if you are working through CVS/SVN or whatever. I'm wanting to know if there are instructions about how you should deal with copyright and so forth when making minor changes to existing code that's on my computer.

Can anyone point me to some examples of proper code markup in these circumstances?

(I've done the Google thing and I'm just going around in circles.:confused: )

---

### Post by amauk on 2010-11-08
It's GPL (well, LGPL but same difference)

Modify it however you want
Distribute your modifications to whoever you want
Send a patch to the author (he may or may not include it in his project)

If you modify a file, or create a new file within the project, you are fully entitled to add your name to that file's copyright notice

(in some large, high-profile projects, adding your name to the copyright block is required as it makes it easier to see who maintains certain bits - see the kernel as an example of this)

Basically, you can do anything you wish as long as you publish your modifications

---

### Post by Lux Perpetua on 2010-11-09
> **amauk said:**
> 

Basically, you can do anything you wish as long as you publish your modificationsNot quite. You can do anything you want as long as you **do not** distribute your modifications. You are also free to distribute your modifications, provided that you license them under a free-software (LGPL-compatible) license. So when Irihapeti sends the modified code to his friends and colleagues, he should preserve the original license. I would also document the modifications in the source code (or at the very least, state that they were modified by me). 
> **Irihapeti said:**
> 
According to the SourceForge project page, the project is licensed under the LGPL. However, when I look at the source files, there's absolutely nothing to indicate this. They are just marked Copyright to the original author, and some stuff about "absolutely no warranty" etc.It's advisable to mention the license in every source file, but the absence of that mention doesn't negate the license. So there's probably nothing to worry about.

---

### Post by Irihapeti on 2010-11-09
Thanks for the replies, people.

The program is in Java, and I've modified only one of the source files. I suppose that I should add something to that particular file about the mods I've done, even perhaps leaving the original lines there as comments. I certainly don't want the original author getting blamed for any coding errors that I've made. :)

Maybe I could add a comment block saying that my mods are copyrighted under the GPL, leaving the original author's contribution as whatever it currently is. Would that work?

---

