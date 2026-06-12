---
title: "Help choosing licences, please"
date: 2008-05-11
forum: Programming Talk
---

### Post by bcw on 2008-05-11
Hello,
I'm going to make a sourceforge project for an app I've developed.  I need some help deciding what licenses I can use.

Currently, it's two parts:
1) Client written in Java (1.5) running on Linux.
2) C# .NET backend for some features running on IIS (in a Windows XP or Vista VMware session).

In the future, I hope to have a WINE component using the Microsoft libraries directly from disk to dispense with the VMware session, or possibly some other third party libraries.   Eventually, I hope for free software libraries to replace all of this part, but I'm dependent on MS for now as above.

The client does not link with any MS stuff - it's stand-alone java now, and I imagine even with the (hypothetical) WINE component, the separation will still be quite clear, so I'm thinking I can GPL it - but is there a concern library-wise to pick between GPL 2 & 3 for the java client?  The java client talks to the .NET server over the local VMware network only.

And what license may I use for the C# .NET part on XP?  I developed it in VisualStudio Express 2005, and it does link/use MS libraries - but nothing I've had to sign any special agreement for.

I really appreciate any help with this, as I want to put the project up on Sourceforge and release it.  I need to choose licences that won't cause trouble for anyone later - the freer the better as far as I'm concerned.

Thanks in advance,
Bret

---

### Post by nvteighen on 2008-05-11
I'm not a lawyer, so don't take this as professional advice!

Under that scenario your Java client to my understanding can be GPL'ed without any issue. I suppose it falls into GPLv3 Section 1 exceptions (open /usr/share/common-licenses/GPL in your favorite text editor)

But probably you'll get licensing issues with MS libraries. Isn't there any license agreement stored in Visual Studio's documentation? I guess there are surely restrictions on how to link to those libraries... Be aware that you're using Visual Studio Express, which is freeware, so restrictions may be even harder than in the paid edition.

---

