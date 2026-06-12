---
title: "In need of advice..."
date: 2008-12-23
forum: Programming Talk
---

### Post by untappedpilot2 on 2008-12-23
So I'm in the process of learning C++ right now. This is my first programming language (although I'm pretty fluent in HTML and web-scripting languages) and I'm hoping this will take me to contributing in Ubuntu Developement. Whether I'm working on future projects / debugging code / whatever. Anyway I'm at the bridge where I've picked up the basics and what comes next will give me the bad habits of either the C or C++ language depending on which one I decide to go with. If I want to participate in Ubuntu Developement should I learn C or C++?

---

### Post by slavik on 2008-12-23
Ubuntu as a whole makes use of many different languages. You are also asking a tough question to which I would say, try to not get into bad habits at all. :)

My personal opinion is that C is simpler to learn for someone new to programming than C++ because C++ adds some concepts that need to be understood from the beginning (OO, operator overloading), but other than that, if C++ isn't giving you many problems, by all means go for it! Once you do run into problems, feel free to start a thread, there are many people who read this forum who are knowledgeable and helpful (even if we all disagree and butt heads over trivial issues).

---

### Post by monkeyking on 2008-12-23
I'm in no way an expert, but I think the lower level of ubuntu development. Like kernel and driver stuff are strictly c.
whereas most other stuff would be c++. (not counting other languages)

---

### Post by namdung on 2008-12-23
I suggest C++ which is the next level after C. You might want to consider other languages like Perl, Python, PHP etc if you want to contribute to the FOSS world.

---

### Post by Arylon on 2008-12-23
I thought D was the next level after C. ;) But seriously...

Ubuntu is made of many different projects. If you want to contribute to an existing project, I suggest learning the language that project uses. If you want to create something new, then you can use any language you want.

There's no such thing as unbiased advice when it comes to language recommendations. I myself am biased toward C or C++, but they really are well suited for the types of programs I like to write.

I am going to buck the trend and say if you want to learn C++, you should start with C++ and **not** learn C first. I say this because of the very large number of things which are done in C, that C++ does differently. So there's a lot to unlearn when transitioning.

---

### Post by roelpeeters on 2008-12-23
+1 On learning C++ first. There are some constructs you may pick up when learning C, which do not apply, or even behave different in C++. In my opinion every language has its advantages and disadvantages. As mentioned in some posts before, the kernel, drivers and (parts of) GTK and Gnome are written in C, where as KDE (if I am not mistaken) has been written in C++. It certainly doesn't hurt to know both and their differences. But it all depends on which development you want to take part.

---

### Post by untappedpilot2 on 2008-12-24
Thanks so much for all the great advice. So it sounds like the baser core of Ubuntu is strictly C. I would like to write some of my own drivers down the line for pesky devices that I know others would benefit from. However, I think I'll go with C++ first. I'm also told that once you learn C++ you then know 90% of C, Java, and C#. Is this true? If this is the case I guess it really doesn't matter which one I start with. 

But since I am going with C++ now where could I look for existing projects to work on to contribute to future Ubuntu Releases? How do I get involved basically? I would like to re-iterate. My thanks for all your advice and input and that goes to everyone. Thank you!

---

### Post by jimi_hendrix on 2008-12-24
keep going until you get stuck

we normallly dont recommend C++ as a first language but since you've been doing well with it just keep going

find what you want to do in C++ (or C...their fundamentally not very different (most C programs compile in a C++ compiler with the inclusion of the proper headers)) and wor towards that thing

---

### Post by pmasiar on 2008-12-24
> **untappedpilot2 said:**
> I'm also told that once you learn C++ you then know 90% of C, Java, and C#. Is this true? 

Not at all.

Languages are 90% similar, but that's true for any strongly typed algol-like language: All are descendants of C. There are many languages quite different from those three you mentioned, and your programmer's brain would benefit from learning those, like Lisp, Perl/Python/Ruby (preferrable to user-facing apps), Prolog, possibly Forth if you like be close to the metal. 

And to be competent programmer in any of C++/C#/Java, you need to know libraries well, and libraries are completely different and incompatible by design - they define the platform, not the language with trivial differences.

To participate in a project, you need to learn language it uses, and projects use all sorts of languages. Canonical, the commercial entity behind Ubuntu, strongly prefers Python, but it's 100% irrelevant to all upstram projects which can pick any language they want.

So you either pick a project and learn it's language, or pick a language and find a interesting project which uses it.

---

