---
title: "LGPL as GPL"
date: 2009-08-20
forum: Programming Talk
---

### Post by kumoshk on 2009-08-20
I've made a derivative work of something with the GNU Library General Public License (version 2)—that's what they used to call the LGPL—as published by the Free Software Foundation. It says I can release my derivative work with a future version of the license.

However,

I'm wondering if I can release the derivative work as GPL (GPLv3 or even AGPLv3) instead of LGPL.

Is this possible? I know the reverse isn't true, though: GPL as LGPL.

---

### Post by shadylookin on 2009-08-20
[http://www.gnu.org/licenses/lgpl-2.1.html](http://www.gnu.org/licenses/lgpl-2.1.html)

> 
3. You may opt to apply the terms of the ordinary GNU General Public License instead of this License to a given copy of the Library. To do this, you must alter all the notices that refer to this License, so that they refer to the ordinary GNU General Public License, version 2, instead of to this License. (If a newer version than version 2 of the ordinary GNU General Public License has appeared, then you can specify that version instead if you wish.) Do not make any other change in these notices. 


I'm not a lawyer, but my understanding is that you can take any lgpl code and make a derivative under the gpl. However if you do this then the upstream will never be able to use your modifications.

---

### Post by kumoshk on 2009-08-20
> **shadylookin said:**
> I'm not a lawyer, but my understanding is that you can take any lgpl code and make a derivative under the gpl. However if you do this then the upstream will never be able to use your modifications.

Thanks for the information!

---

### Post by soltanis on 2009-08-21
Also not a lawyer, but it is a one-way process. You can convert LGPL -> GPL, but not the other way around. So like above poster said if you make modifications, then the original developers either can't use it or have to switch to GPL.

This is one of the main reasons I don't like the GPL.

---

### Post by kumoshk on 2009-08-21
Hmm.

Is it possible to use GPL code within LGPL code if there is no proprietary code included, or is that restriction only if it has proprietary code?

For instance, if I have a class that is GPL, can I use that GPL class in a full LGPL program (with no other licenses involved)?

---

### Post by Zugzwang on 2009-08-21
> **kumoshk said:**
> For instance, if I have a class that is GPL, can I use that GPL class in a full LGPL program (with no other licenses involved)?

No, you can't - that's the "viral" property of the GPL. If it is just one class, I would propose to write a similar class yourself.

---

### Post by kumoshk on 2009-08-21
> **Zugzwang said:**
> No, you can't - that's the "viral" property of the GPL. If it is just one class, I would propose to write a similar class yourself.
Ah, good to know. Thanks!

---

### Post by nvteighen on 2009-08-21
The LGPL is the most difficult license to comply with and should be avoided... You can get the same terms by using a BSD-like license or even Creative Commons BY. Anyway, as you're not the original author, you're lost.

Now that LGPLv3 is written as a set of "additional permissions" on top of the GPLv3 and GPLv3 Section 7 says:

[QUOTE=GPL]
  When you convey a copy of a covered work, you may at your option
remove any additional permissions from that copy, or from any part of
it.  (Additional permissions may be written to require their own
removal in certain cases when you modify the work.)  You may place
additional permissions on material, added by you to a covered work,
for which you have or can give appropriate copyright permission.
[/QUOTE]

So, ANY LGPLv3 code would be possible to be relicensed into GPL at any time... The provisions towards GPL-relicensing found at LGPLv3 are actually redundant, as GPLv3 Sect. 7 already states that.

---

### Post by kumoshk on 2009-08-21
Hmm. I have a question that is troubling me.

Are the PDF files made with GNU LilyPond (GPL) covered by the GPL license? What about the source ly files? That would be rather troublesome if so, and tons of people would be violating the GPL by not adding the license to every ly file.

The reason I ask is because I'm making an environment for making certain kinds of games and such. I want the code that it all relies upon to be GPL, but I don't want the files used to make creative works with it to have to be GPL.

Is there a positive solution to this? How do I have to implement it?

I originally wanted to make GPL modules that imported dynamic content of other licenses. But, I'm guessing there might be problems there. Are there? It sounds like it, but what's the difference between that and a non-GPL source code file for a GPL compiler? The compiler is effectively importing the code in one way or another, isn't it?

EDIT:
So, let's say I have some GPL code, and it has a portion that is designed to be dynamic, based on things outside the code that are dynamically entered. Do the dynamic entries have to be GPL?

In other words, I want the lower level stuff to be GPL, and the higher level stuff to be whatever whoever uses it wants. Is there a way that this can be possible (a way that's not a loophole)? My argument in favor of this is that the higher level stuff is meant to be comprised of various creative works, while the lower level stuff is more what the GPL seems to have targeted.

---

### Post by nvteighen on 2009-08-21
> **kumoshk said:**
> Hmm. I have a question that is troubling me.

Are the PDF files made with GNU LilyPond (GPL) covered by the GPL license? What about the source ly files? That would be rather troublesome if so, and tons of people would be violating the GPL by not adding the license to every ly file.

No. Copyright is much simpler... You own copyright of something to control the inclusion of your work into another one. If there's no material from the developers, those files are not a Derivative Work of their code.

Usually output is not considered a Derivative Work.

> 
The reason I ask is because I'm making an environment for making certain kinds of games and such. I want the code that it all relies upon to be GPL, but I don't want the files used to make creative works with it to have to be GPL.

Is there a positive solution to this? How do I have to implement it?

Interesting... depends on how you implement it. For example, if you rely on providing an API from a library, then the produced works would have to be GPL too. So, the easiest way would be to state an exception to the GPL in your code allowing the produced code to be licensed as wished... kinda what the GNU C++ Standard Library does.

> 
I originally wanted to make GPL modules that imported dynamic content of other licenses. But, I'm guessing there might be problems there. Are there? It sounds like it, but what's the difference between that and a non-GPL source code file for a GPL compiler? The compiler is effectively importing the code in one way or another, isn't it?

EDIT:
So, let's say I have some GPL code, and it has a portion that is designed to be dynamic, based on things outside the code that are dynamically entered. Do the dynamic entries have to be GPL?

In other words, I want the lower level stuff to be GPL, and the higher level stuff to be whatever whoever uses it wants. Is there a way that this can be possible (a way that's not a loophole)? My argument in favor of this is that the higher level stuff is meant to be comprised of various creative works, while the lower level stuff is more what the GPL seems to have targeted.

Hum... what's "dynamic" for you? If you talk about "dynamic linking" (e.g. linking to a .so library during compilation or importing a Python module through "import"), the community is split in two factions, one that thinks stuff linked dynamically constitutes Derivate Work (in FOSS, the Free Software Foundation* thinks this) and others than believe not (like Linus Torvalds in FOSS... and myself). And there are very good arguments in favor of both positions... As a matter of convenience, people tend to agree with the FSF as it is the most expansive interpretation of the GPL and therefore, it can't be a violation... maybe just an exaggeration.

But in the case of "dynamic loading" (e.g. loading libraries through the linker interface... plugin interfaces and similar), there's no doubt that that does not constitute Derivative Work and therefore each part has its own licensing terms untouched.

I am not a lawyer, but have some small law studies because of curiosity. And actually, if read and thought with some common sense, copyright is actually much easier than it looks like.

(*) Note on the FSF's position. While they endorse the idea dynamic linking produces Derivative Works by even enforcing the GPL of some of their code under what they consider to be violators, they cleverly don't endorse it in a public statement anywhere and have always elluded the question. This is because they want the GPL to be applicable to the most amount of code as possible until a court decides about this issue in a case. Don't blame them; it's a good idea... blame the international conventions and treaties on copyright that doesn't specify anything on the topic and therefore this will have to be resolved when a court case is opened.

---

### Post by kumoshk on 2009-08-21
> **nvteighen said:**
> &#8230; to state an exception to the GPL in your code allowing the produced code to be licensed as wished... kinda what the GNU C++ Standard Library does.
I think this is what I'll end up doing. Or, I plan to state that it uses the GPLv3 with some stated amendments, followed by a copy of the GPLv3.


> **nvteighen said:**
> Hum... what's "dynamic" for you?
I meant potentially several things, I suppose, but as it stands right now, here is the situation:
I have several Python modules that I created myself (just py files and no C code; it's all interpreted normally). The modules I created myself are the ones I want to be like the GPL. However, I want people who use my code to be able to import these modules (with such as the import statement) into their own Python modules, without their own Python modules necessarily becoming GPL, seeing as they are used to make a game, rather than to make the stuff to make making the game easier/nicer.

I think this is the case you said they were divided on.

---

### Post by nvteighen on 2009-08-21
> **kumoshk said:**
> I think this is what I'll end up doing. Or, I plan to state that it uses the GPLv3 with some stated amendments, followed by a copy of the GPLv3.

I meant potentially several things, I suppose, but as it stands right now, here is the situation:
I have several Python modules that I created myself (just py files and no C code; it's all interpreted normally). The modules I created myself are the ones I want to be like the GPL. However, I want people who use my code to be able to import these modules (with such as the import statement) into their own Python modules, without their own Python modules necessarily becoming GPL, seeing as they are used to make a game, rather than to make the stuff to make making the game easier/nicer.

I think this is the case you said they were divided on.

Ok, yes, it's dynamic linking... and being Python, the thing is a bit more complicated even... (you know, GPL is optimized for compiled languages) Well, actually who has to enforce a License is the licensor himself, so you **should have** a position and understand why you have it. That way, you'll know how to consider violations... Of course, if the licensee doesn't agree with your point of view, you will have to sue him in order to have your point proven... at the risk of losing the case, of course.

**My** argument against FSF's view on this is the following:

The issue is whether the libraries of some compiled work are part of that work's "Corresponding Source" or not. In the case of static linking, this is trivial, as it is almost like cutting-and-pasting code. In the case of dynamic linking, this is not so clear... Ok, I link my C or C++ code to "libhelloworld.so", a fictional GPL'ed library. What am I doing? Well, just telling the compiler that some symbols I am referring to are going to be resolved at runtime and in a file called "libhelloworld.so".

Ok, but what if I install another implementation of that same library with the very same filename? It will work and no relinking will be necessary... as long as the symbols are correct and the interface is the same, no matter what implementation I use, my program will work. So, under this point of view the library's code is not part of the "Corresponding Source" of my program.

The FSF considers the library to be part of the "Corresponding Source" because the program is designed to work by getting the library. So, the library is part of the program... and actually, as development is optimized to use a particular version of the library (and that in GNU/Linux usually the dynamic libraries are distributed alongside the project), it's the developer's library's terms which count. In my opinion, that's an abusive interpretation which also doesn't take account of what the technical procedure of linking is.

In the case of Python the additional problem is that your actually distributing source files... so the "Corresponding Source" is the source itself... So unless you consider the module to be part of your code somehow (e.g., by taking it from a standard installation path?), I guess the 3rd party imported module will never get into the "Corresponding Source".

Under my interpretation, the distinction between GPL and LGPL is just appliable in static linking.

Google on "GPL dynamic linking" or similar. There are some good articles by FOSS lawyers on the topic in layman language :)

---

### Post by kumoshk on 2009-08-21
Thanks for all the information! It's good to hear from someone who cares about such issues.

> **nvteighen said:**
> The FSF considers the library to be part of the "Corresponding Source" because the program is designed to work by getting the library. So, the library is part of the program...
What if it's the other way around? What if the library is designed to work by getting the 'program'. In my case, what you've named 'the library' is actually where the default GUI is (and hence, in some senses, that's where the program 'normally' runs). Code after the GUI starts doesn't make a lot of sense seeing as it won't execute until the GUI closes. However, I have a workaround.

Here's what my code for my game file should look like:
```
#BEGINNING OF MODULE
import gui
from uni import * #objects and code for all modules to access (including many modules that aren't listed here)

#Game-specific code goes here

gui.startup(__import__(__name__)) #calling the GUI mainloop
#END OF MODULE
```

The gui module has all the GUI code, but it doesn't start the mainloop there (although it contains a function that can start it, which I called gui.startup here). __import__(__name__) is to allow the gui module access to the game module if it needs it (which it might for some purpose or other&#8212;actually, it doesn't really need it, but I wanted to prove to myself that this was possible without them being in related directories).

Anyway, it might not look exactly like that, but this is the basic idea.

I could probably invent my own pseudo-Python language for the game code if that would help (although I'd rather not; Python is good enough), and just have it interpreted and stored in the right spot.

---

### Post by kumoshk on 2009-08-21
> **kumoshk said:**
> Here's what my code for my game file should look like:
```
#BEGINNING OF MODULE
import gui
from uni import * #objects and code for all modules to access (including many modules that aren't listed here)

#Game-specific code goes here

gui.startup(__import__(__name__)) #calling the GUI mainloop
#END OF MODULE
```
Hmm, I tried out that implementation and it works. I hadn't gotten it to load from the game file until now, but it turns out that __import__(__name__) is important to have as a parameter after all, with my setup. I'm just glad it works. Main code can actually be true importable modules now, and the user won't have to edit multiple files, although having to add a line of code at the end isn't ideal (but it's a whole lot better than having to run from the stuff I wanted only to import)&#8212;of course, that line is only for the default GUI (other people might want to use different ones).

---

### Post by kumoshk on 2009-08-21
> **kumoshk said:**
> I think this is what I'll end up doing. Or, I plan to state that it uses the GPLv3 with some stated amendments, followed by a copy of the GPLv3.
I think I'll take advantage of these amendments by making even the user-created files essentially GPL for organizations (such as corporations and educational entities), while giving more permission to real individuals who aren't trying to own the world by monopolizing on software patents.

---

### Post by nvteighen on 2009-08-22
> **kumoshk said:**
> 
What if it's the other way around? What if the library is designed to work by getting the 'program'. In my case, what you've named 'the library' is actually where the default GUI is (and hence, in some senses, that's where the program 'normally' runs). Code after the GUI starts doesn't make a lot of sense seeing as it won't execute until the GUI closes. However, I have a workaround.

Here's what my code for my game file should look like:
```
#BEGINNING OF MODULE
import gui
from uni import * #objects and code for all modules to access (including many modules that aren't listed here)

#Game-specific code goes here

gui.startup(__import__(__name__)) #calling the GUI mainloop
#END OF MODULE
```

The gui module has all the GUI code, but it doesn't start the mainloop there (although it contains a function that can start it, which I called gui.startup here). __import__(__name__) is to allow the gui module access to the game module if it needs it (which it might for some purpose or other—actually, it doesn't really need it, but I wanted to prove to myself that this was possible without them being in related directories).

Anyway, it might not look exactly like that, but this is the basic idea.


To me that sounds like a plugin architecture (and a little weird inversion of control)... and even though gui is calling the module by dynamically **loading** it (thus not a Derivative Work), your architecture requires your module to dynamically **link** the gui module and thus, under FSF's view, it would be a Derivative Work. The distinction applies, as the Python bytecode compiler will link the modules imported through import and the other will be resolved at runtime.

So, the best is to place in your COPYRIGHT file something like this:
```

(MY PROGRAM) is distributed under the following licensing terms:
    Copyright (C) (YEAR) (NAME)

    This program is free software: you can redistribute it and/or modify it
    under the terms of the GNU General Public License as published by the Free
    Software Foundation, either version 3 of the License, or (at your option)
    any later version.

    This program is distributed in the hope that it will be useful, but WITHOUT
    ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or
    FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for
    more details.

    You should have received a copy of the GNU General Public License along with
    this program. If not, see <http://www.gnu.org/licenses/>.

    Nevertheless, as an additional permission in the terms of Section 7 of the
    GNU General Public License version 3, any module designed to be run within
    this program through its provided Application Programming Interface is
    allowed to be distributed under the terms of your choice. This does not
    apply for the usage of this Application Programming Interface for the
    development of new applications designed to be run independently from this
    program.

```

I think it takes account of your situation. But be aware of the following: GPL explicitly says anybody can take away any additional permissions in any time when redistributing your code modified or not.

---

### Post by kumoshk on 2009-08-22
> **nvteighen said:**
> I think it takes account of your situation. But be aware of the following: GPL explicitly says anybody can take away any additional permissions in any time when redistributing your code modified or not.

Thanks for the helpful information.

About the GPL, though, I'm thinking perhaps it might be best to do one of the following:
&#8226; Add the provisions (I wouldn't mind if people took away those additional permissions in redistribution, actually)
&#8226; Just use the LGPL for everything (instead of just that one class I was talking about at the start of this thread; I've decided to make that LGPL instead of GPL, seeing as those are my only two options)
&#8226; Write my own license entirely (maybe gleaning ideas from other free licenses); I might do this, seeing as then I could have a lot more control and knowledge over the situation.

I've already actually written a few mock licenses for such purposes in my time (I haven't actually used any of them, though). I like to be thorough&#8212;I'll have to work on being more concise, probably, without sacrificing license functionality. (I like your example how it covers so many things with so few words and blends in with the other parts as if you had written them, too.)

I like to have fun with licenses, too&#8212;putting in provisions that most people never consider (such as issues with artificial intelligence, laws of other countries/worlds/dimensions/realms, distinctions between the rights of organizations and humans, and so forth). One thing that bothers me about a lot of licenses (if not all I've seen) is that they don't state the localities where the license is intended. For instance, if you release something to the public domain, that's pretty general. You might be able to argue later that you only meant in your own country (and that might even hold up in court, but who knows).

Anyway, I better be off. Thanks!

---

