---
title: "Can  I create commercial(closed source) softwares using linux"
date: 2010-03-18
forum: Programming Talk
---

### Post by merincooper on 2010-03-18
I'm asked to create a network tool in C and a GUI API in linux platform by my company. 
I'm aware of the GPL & GLPL licenses , but not clear whether I can create a proprietary commercial software with the tools & libraries available in Linux:
My tool will be written in C and will be using the some network library functions in the Linux and some header files .(Their license is GPL) , also the GUI i'm planning to develop is using GTK and Glade / Anjuta, (GTK is based on GLPL license) , 
I will be using GCC compiler for C programs, 

Please let me know whether it is possible to create a closed source-commercial software using the above tools/libraries, if not possible is there any workaround is there for creating commerical tools in linux ??
Can I make some part of my code closed and some parts open? 
Also please let me know which is the best GUI building programming language/IDE that can be used with C programs in linux

---

### Post by ndefontenay on 2010-03-18
You can do a closed source program that works on Linux OS but you can't re use linux Os code, develop a tool based on linux code and make it close.

So Linux compatible and close yes, but based on linux and closed no.

---

### Post by Some Penguin on 2010-03-18
Read the licenses.  Just 'GPL' isn't sufficient as there have been a few versions over the years.

You might want to look at [http://en.wikipedia.org/wiki/GPL_linking_exception](http://en.wikipedia.org/wiki/GPL_linking_exception)

*Without* such an exception, linking to GPL libraries would mean that your code has to be made available under the same terms.

---

### Post by nvteighen on 2010-03-18
You can. Copyright works on the basis that you took something from someone else. Using someone else's program to write your code on it is not even related to copyright...

The issue is, of course, libraries and interpreters and the current interpretation of the GNU licenses promoted by the FSF that states that dynamic linking consistutes a derivative work though dynamic loading doesn't. I won't get into the details of this argument, as currently no court case has ever ruled about this issue and all we have are opinions of different lawyers... some of which (the FSF's) are of course interested in an most-extensive-as-possible interpretation of the GPL.

Anyway, for your own good, the C Standard Library is LGPL and the C++ Standard Library is GPL with linking exception, so the requisites you have to follow don't include making your program Free Software. Other languages have similar terms... Free Software programming languages tend to be very permissive to what you can do with your own code and their standard libraries will usually be LGPL or even less restrictive (Python License, etc.).

Third-party licenses are, of course, a completely different case.

---

### Post by uljanow on 2010-03-18
If you have a GPL library dependency you can't even write a GPL plugin that the non-GPL software uses because it is considered as a derivative work.

---

### Post by derekeverett on 2010-03-18
I realize this is a bit off-topic.. so forgive me but I am very curious.

If closed source software is created, how would anybody ever know if the source contained some open-source code?

I'm no expert... so I'm asking...

---

### Post by dwhitney67 on 2010-03-18
> **derekeverett said:**
> I realize this is a bit off-topic.. so forgive me but I am very curious.

If closed source software is created, how would anybody ever know if the source contained some open-source code?

I'm no expert... so I'm asking...

Disgruntled employees who took part in creating the software!

---

### Post by saulgoode on 2010-03-18
> **merincooper said:**
> I'm asked to create a network tool in C and a GUI API in linux platform by my company.

**If your tool will not be distributed outside of your company then you are basically permitted to use any Free Software code available** with the exception of code that has been licensed under the [Affero General Public License]("http://www.gnu.org/licenses/agpl-3.0.html").

Should you be planning on marketing or distributing your network tool outside your company and still keep parts of it closed then you can not use GPLed code; and if you use LGPLed code then you must provide a method for users to substitute alternate versions of the LGPLed code (this is typically addressed automatically by dynamic linking, but not by static linking). 

If you distribute the LGPLed software with your closed software then you will be obliged to provide the source code (upon request) of that LGPLed software (but not to your own software). If you do not ship any LGPLed code (for example, if it is presumed to be already on the user's system) then you are not under such obligation.

Most other Free Software licenses -- such as most of [those certified by the Open Source Initiative]("http://www.opensource.org/licenses/alphabetical") -- place fewer conditions upon distribution. 

This post is not presented as legal advice, merely as an overview at the most basic level of the options available.

---

### Post by soltanis on 2010-03-18
Bottom line:

If it is GPL, look for a linking exception (it's usually labeled GPL with linking exception or something like that). If you have that, you may link to libraries under that code, but you may NOT create derivative works without making it also available under the GPL.

If it is LGPL, you may create software which links to that library or uses those headers, so long as they're dynamically linked (the "substitution" thing) and so long as you aren't creating a derivative work.

If it is BSD you can basically do whatever the hell you want (subject to its conditions which are short).

If it is public domain, you can also do whatever the hell you want, but remember that you cannot copyright code in the public domain (you don't have to make it available, but you can't claim a copyright to it).

The whole "linking"/"using headers from" thing is generally a mess I don't like about the GPL, which is why I do BSD/public domain. With Linux my understanding is you can use their header files (you sort of have to if you want to make a Linux program) as well as link to the libc, so long as it's not a derivative work, and have it closed source.

But I'm no lawyer so you should check more carefully with one.

---

### Post by leandromartinez98 on 2010-03-18
You can always write some code that depends on GPL libraries and distribute your
code as closed source and, separatelly, the GPL libraries. Clearly you can 
say that your program depends upon the instalation of some GPL program or library. I think that you can also distribute the GPL part along with your code, whenever the license you make users to accept is clear and separate for your part of the code and the GPL one.

---

