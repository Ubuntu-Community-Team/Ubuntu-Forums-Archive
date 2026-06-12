---
title: "Licences Questions"
date: 2011-07-17
forum: Programming Talk
---

### Post by SavageWolf on 2011-07-17
I have several questions on OSource software licenses. And such. Yay!

Uh, I have no idea what are the "common" ones, I've only really seen the GNU GPL...

1. I am 17 and living in Scotland, does that affect anything?
2. Uh, HOW exactly do you license software? Do you put a link to the license at the top of all files.
3. Say I make a program and use pyGTK or something, does the license only apply to pyGTK itself (And allows me to use a different license for the rest of the program), or does the whole project have to be released under the same license.
4. If I make like say a game or something (that reads files for "missons" and/or "levels" and such), can I sell "premium content" which uses a different (more restrictive) liscense than the main game thing?

I bet these are all stupid questions... D:

---

### Post by haqking on 2011-07-17
> **SavageWolf said:**
> I have several questions on OSource software licenses. And such. Yay!

Uh, I have no idea what are the "common" ones, I've only really seen the GNU GPL...

1. I am 17 and living in Scotland, does that affect anything?
2. Uh, HOW exactly do you license software? Do you put a link to the license at the top of all files.
3. Say I make a program and use pyGTK or something, does the license only apply to pyGTK itself (And allows me to use a different license for the rest of the program), or does the whole project have to be released under the same license.
4. If I make like say a game or something (that reads files for "missons" and/or "levels" and such), can I sell "premium content" which uses a different (more restrictive) liscense than the main game thing?

I bet these are all stupid questions... D:

try the opensource initiative.

[http://www.opensource.org/licenses](http://www.opensource.org/licenses)

there are many

---

### Post by simeon87 on 2011-07-17
1. No.
2. You put a (short) version of the license at the top of each code file, you include the full license with your software and you mention it in the README file.
3. The license applies to your code. You can also license various parts under different licenses (e.g., your code under license A and your media/images under license B). However, a license can affect how others can use your code.
4. It is possible to give away your game under a free license and charge money for additional content. It's just that anyone can read / modify your free code so anyone can also see / remove any restrictions that you have built in to prevent sharing the level content. It might work, I'm just not aware of existing games that do it like this.

---

### Post by nvteighen on 2011-07-17
First, the usual disclaimer: I am not a lawyer.

> **SavageWolf said:**
> 
1. I am 17 and living in Scotland, does that affect anything?


It might in the unlikely case that you have to sue something for violating your copyright. If you are underage, you might have restrictions (But, IIRC in Scotland you become a legal adult when 16 years old, don't you?).

> 
2. Uh, HOW exactly do you license software? Do you put a link to the license at the top of all files.


Yes, and also add a file stating the copyright and licensing terms. That "Copyright" file is very useful when you're distributing a binary compiled program.

The usual way to do this is:
```

Copyright (C) YEARS NAME

TEXT STATING LICENSE TERMS OR WHERE TO FIND THEM

```

> 
3. Say I make a program and use pyGTK or something, does the license only apply to pyGTK itself (And allows me to use a different license for the rest of the program), or does the whole project have to be released under the same license.


You can only license things you have copyright for... so your license only applies for what you've done yourself.

But be aware that by using libraries, you have to follow their license terms. That means that you have to use a license that is compatible with the licenses of the libraries you've used.

> 
4. If I make like say a game or something (that reads files for "missons" and/or "levels" and such), can I sell "premium content" which uses a different (more restrictive) liscense than the main game thing?


Yes. The licensor isn't bound to any license term for his own work (of course, it's expected that the licensor provides reasonable means for the licensee to exercise the rights granted by the license).

The only issue there might be is that such "premium content" qualified as derivative of someone else's work... In that case, you aren't the original licensor (but a licensee for that work) and therefore, you're bound to whatever terms you were given for using that material.

> I bet these are all stupid questions... D:
I disagree. These are very important issues and it's good that you want to know about them at your age.

I hope this was helpful.

---

### Post by SavageWolf on 2011-07-17
Hmm... Take [http://img.savagewolf.org/tetris.py](http://img.savagewolf.org/tetris.py) for example.

It uses pyGTK, which is licensed under LGPL. If I wanted to, would I be able to sell it commercially (I don't want to...), or release it in the public domain (maybe...)? I'm not sure what they talk about "linking" and such...

I also assume the compiler and text editor and stuff make no difference to the license you can use...

---

### Post by JupiterV2 on 2011-07-18
There are, generally speaking, three types of open source licenses (I too, am NOT a lawyer):

1. Very permissive: Public Domain licenses - You can use the works and its derivatives any way you like. You relinquish your rights to the works and can no longer make intellectual property claims.

2. Semi-permissive: LGPL is an example - you may use whatever license you want provided: 1) You have dynamically linked the library. Static linking makes the work a derivative of the original, and therefore must follow under the same license or a stricter one (like the GPL); 2) You provide credit for, provide a method to get the source of, and otherwise provide the same rights given to you by the library to your users.

2. Non-permissive: GPL - Same as the LGPL except that any work based on it is a derivative of the original and must carry the same license. You'll want to read the agreement closely. You can, in specific situations, charge fees for the software. For example: 1) Service - since you're not charging for the program itself you may charge a fee, however, you must provide the full source of the program at no charge to anyone who requests it; 2) Non-Free plugins/resources - As long as whatever you are using is NOT directly linked to the program (but read at runtime only, again, NOT LINKED) then you can charge fees for that content. Picture a free game engine where you can charge for the levels/extra content.

There are many others: MIT, Apache, Creative Commons, et al. Some are for specific works like text and images, others pertain strictly to software.

The most important thing to understand is that you can make a license less permissive but not more. Public Domain > LGPL > GPL. You may not, for example, make a GPL program LGPL but you CAN make an LGPL derivative GPL. Bare in mind that you also have to look at contributors. If YOU have written a derivative work of an LGPL program you may change the license of your own work to a minimum of LGPL but can make it more restrictive and apply the GPL. Note, that is on a derivative. To change the license on someone else's work you must get the permission from (I think) the majority, if not all, of the contributors to change the license.

There is also the matter of contributors licenses but that's beyond the scope of this conversation I think.

The FSF and Project Harmony have more information on licensing. You'll also need to understand how licenses (ie, GPL vs. MIT) can, and can't, be used together.

---

### Post by nvteighen on 2011-07-18
> **JupiterV2 said:**
> 
The most important thing to understand is that you can make a license less permissive but not more. Public Domain > LGPL > GPL. You may not, for example, make a GPL program LGPL but you CAN make an LGPL derivative GPL. Bare in mind that you also have to look at contributors. If YOU have written a derivative work of an LGPL program you may change the license of your own work to a minimum of LGPL but can make it more restrictive and apply the GPL. Note, that is on a derivative. To change the license on someone else's work you must get the permission from (I think) the majority, if not all, of the contributors to change the license.


No. By default, copyright is assigned to individuals, not groups. So, if some collaborative project is licensed e.g. under the GPL and you want to use that code but want to get a special license (e.g. one that allows linking to proprietary code) from them just valid for you, you'd have to ask every single collaborator for doing that... Unless the project members at some point decide to assign copyright to the group as a collective; in that case, permission is given by whatever mechanisms are accepted for decision-making in that group.

Also, be aware that according to American case law dynamic linking does make your work a derivative of the libraries you've linked to. Nothing has been ruled about dynamic loading (dlopen... plugins in general...) yet, AFAIK, but the convention the FSF is is that it does not constitute derivation as long as you don't use dlopen with a constant set of libraries known at compile-time (because that would mimic dynamic linking).

So, the LGPL provision about allowing dynamic linking with proprietary code is just the same as the also much-used "GPL+Linking exception" (the GNU C++ Standard Library uses this).

Now, keep also in mind that GPL (and therefore LGPL) define some libraries as "System libraries". If something qualifies as a "System library" (according to the license's definition, which is pretty broad), it is excluded (by the license) from all of this. That's why no project using GTK+ ever states that it's a derivative of GTK+... (I asked the GTK+ guys once :P).

---

### Post by JupiterV2 on 2011-07-18
> **nvteighen said:**
> No. By default, copyright is assigned to individuals, not groups. So, if some collaborative project is licensed e.g. under the GPL and you want to use that code but want to get a special license (e.g. one that allows linking to proprietary code) from them just valid for you, you'd have to ask every single collaborator for doing that... Unless the project members at some point decide to assign copyright to the group as a collective; in that case, permission is given by whatever mechanisms are accepted for decision-making in that group.


Ya, I wasn't sure if it had to be EVERY contributor or if it was a majority (those who have done 90% of the work). I thought I might be wrong on that point after I posted. Thanks for clarifying. Correct me then if I'm wrong (again) but that is where a contributor agreement comes into play. By agreeing to the contribution agreement, whatever it may be, you are relinquishing your rights to the project, governing body, or whatever the agreement stipulates. Yes?

> **nvteighen said:**
> 
Also, be aware that according to American case law dynamic linking does make your work a derivative of the libraries you've linked to. Nothing has been ruled about dynamic loading (dlopen... plugins in general...) yet, AFAIK, but the convention the FSF is is that it does not constitute derivation as long as you don't use dlopen with a constant set of libraries known at compile-time (because that would mimic dynamic linking).

So, the LGPL provision about allowing dynamic linking with proprietary code is just the same as the also much-used "GPL+Linking exception" (the GNU C++ Standard Library uses this).

Now, keep also in mind that GPL (and therefore LGPL) define some libraries as "System libraries". If something qualifies as a "System library" (according to the license's definition, which is pretty broad), it is excluded (by the license) from all of this. That's why no project using GTK+ ever states that it's a derivative of GTK+... (I asked the GTK+ guys once :P).

Now, that I wasn't aware of. It hasn't affected me because all my one project has been released under the GPL. I thought that all LGPL projects, by definition of the LGPL, constituted a "system" library. Isn't that the whole point? That the technology is so widely available the only way to make it attractive is by allowing works which link to, but are not derived from, to be under a separate license? The "linking exception" rule as you stated? It makes me wonder why some projects would elect to be licensed under the GPL with a linking rule vs. LGPL.

---

### Post by nvteighen on 2011-07-18
> **JupiterV2 said:**
> Ya, I wasn't sure if it had to be EVERY contributor or if it was a majority (those who have done 90% of the work). I thought I might be wrong on that point after I posted. Thanks for clarifying. Correct me then if I'm wrong (again) but that is where a contributor agreement comes into play. By agreeing to the contribution agreement, whatever it may be, you are relinquishing your rights to the project, governing body, or whatever the agreement stipulates. Yes?


Yes, but be aware that contributor agreements only bind you if you're submitting code "back" to the project. You can always fork a GPL'ed project, host your modified version somewhere and never sign any agreement, even if the team working on the original project contacted you for merging changes back... You can refuse to sign the agreement and if after your refusal they really wanted your code, they'd have to attribute you.

> 
Now, that I wasn't aware of. It hasn't affected me because all my one project has been released under the GPL. I thought that all LGPL projects, by definition of the LGPL, constituted a "system" library. Isn't that the whole point? That the technology is so widely available the only way to make it attractive is by allowing works which link to, but are not derived from, to be under a separate license? The "linking exception" rule as you stated? It makes me wonder why some projects would elect to be licensed under the GPL with a linking rule vs. LGPL.

Linking is considered to be derivation by American courts and almost everyone, including the FSF. I won't get into this because I'm not sure about the arguments in favor and against this interpretation.

The LGPL's main feature is that it allows dynamic linking with code regardless of its license... but you still have to provide the source for the library. You can use some fictional library called MyLib, licensed under the LGPL, in proprietary software, but if someone asked you for its source code, you'd have to show it (specially if you modified the library)... or point to the MyLib project public repository.

The "System Library" definition is GPL's. It establishes that you're not obliged to provide the source of standard libraries, OS interfaces, compiler interfaces, etc. Now having read the licenses again, I'm not clear about the attribution thing (again)... and maybe you should nevertheless state that your project is a derivative (because it's linked to), e.g. GTK+ and the GNU C Standard Library... The fact is that nobody does that.

Like you, I don't get why some people use the linking exception when its practical effects seem to be the LGPL's. Maybe we're missing something.

---

