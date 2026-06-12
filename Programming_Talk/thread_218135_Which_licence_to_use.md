---
title: "Which licence to use?"
date: 2006-07-18
forum: Programming Talk
---

### Post by Laterix on 2006-07-18
Hi,

I would like to release my work as an open source project, but there is one complication. I have used one class in closed source project as well. So if I release my hobby under GPL, I think I would have to release my work too and that is not possible.

So, I need to use some classes in both open and closed source projects without revealing closed source project's source code. What are my options? Or should I just not to release my hobby project?

My project is web-gallery called Kuvatus. [Check it out here]("http://www.taimila.com/kuvatus.php").

EDIT: I have written all the classes by myself. So there is no worry about third parties.

---

### Post by bieber on 2006-07-18
Well, if you're gonna release it, it won't do much good if you keep parts of it hidden.  I'd reccomend GPL or AGPL for all of it.  You can still use your code in a proprietary project as well, if you wish, since you hold copyright.

---

### Post by ifokkema on 2006-07-18
I'm not too sure I follow you completely, but if you include code in an GPL open source project, that part of code becomes GPL. If you use that part of code in a different project, you don't necessarily have to release it, but if you do it's GPL and after release you can't prevent others from modifying and/or redistributing your code.

---

### Post by xtacocorex on 2006-07-18
I'm having the same problem with trying to license a program of mine that is yet to be completed. 

You could always use a Creative Commons License, which will allow you to choose what you want the license to be. [http://creativecommons.org/](http://creativecommons.org/)

As an aside, I looked at the preview site for Kuvatus and I'm really impressed. I'm hoping you resolve your license issue soon and release the program. I would be very interested in using it when I get webspace.

---

### Post by wmcbrine on 2006-07-18
> **Laterix said:**
> I would like to release my work as an open source project, but there is one complication. I have used one class in closed source project as well. So if I release my hobby under GPL, I think I would have to release my work too and that is not possible.I take it this is a class you've written. If so, no, there's no need to GPL the closed-source project. As the author and copyright holder, you can dual-license your code. (See Qt for the most famous example of this.)

---

### Post by Laterix on 2006-07-18
Thank you for your answers. How about LGPL? If I have understood it right, it gives very much freedom to use source code in any possible project (open or closed) without restricting user to release his code.

---

### Post by Note360 on 2006-07-18
Hmm I put something under the GPL but I haven released it yet (Built in the messages and stuff) However some code comes from a book I read and modules (It is a UI for some Perl Modules). I can obviously use it, but can I include use of the modules? and if I wanted to use some of my own code over could I use that in a proprietary project? I am thinking of putting it under the BSD license or MIT license instead.

---

### Post by GeoMX on 2006-07-18
> **Laterix said:**
> Thank you for your answers. How about LGPL? If I have understood it right, it gives very much freedom to use source code in any possible project (open or closed) without restricting user to release his code.
I'm not sure, but I think LGPL software/libraries may be used by others in commercial applications, but this software/libraries still need to release its sources. Other people using this software/library don't need to release their sources if the software/library is not the base of their new software/library.

---

### Post by bieber on 2006-07-18
Keep in mind that when you choose a license, you're in no way committing yourself to how you will use the code in the future.  As copyright holder, you can always release under different terms if you want, or even dual, tri, or more license.

That said, if you GPL your project, you will have to release complete source for all of it.  This is the license I reccomend for nearly all cases, because it allows you to provide the public with free software, and it guarantees that no one can ever take it and make it nonfree.  If it's a server-side application, mind you, anyone can use it and/or modify it to interface with users on a server without releasing code, because they aren't technically redistributing.  If you don't want people to be able to do this, you should use the Affero GPL, a modified license that closes that loophole (well, some consider it a loophole, others a feature.  It's up to you).

The LGPL is a license that can be used for a library, which allows it to be linked at compile time with a proprietary product, something not applicable to a web script, and something best only used for libraries for which there are already proprietary equivalents, but which free software in general could benefit from the wide use of (such as the GNU C library).

If you want anyone to be able to do whatever they want with your code, including integrating it into a proprietary project (something I'd never, ever advise allowing), you'd want to use a permissive BSD license or the MIT license, or else just throw it out in the public domain.

---

### Post by fdamstra on 2006-07-18
> **Laterix said:**
> 
I would like to release my work as an open source project, but there is one complication. I have used one class in closed source project as well. So if I release my hobby under GPL, I think I would have to release my work too and that is not possible.

...

EDIT: I have written all the classes by myself. So there is no worry about third parties.
Then you have no problem releasing it under the GPL.  As the original author of the class, you can use it in as many closed source projects as you'd like.

With the GPL, you are licensing other people to use the software according to that license, while retaining your original copyright.  You are well within your rights to use that class in a closed source project.

It might get tricky if somebody sends you a patch, however.

---

### Post by bieber on 2006-07-18
If someone sent him a patch, he'd have to either get a copyright assignment from the person sending it, or else release that patch under the GPL, and not use it in any proprietary applications.  Not that complicated.

---

