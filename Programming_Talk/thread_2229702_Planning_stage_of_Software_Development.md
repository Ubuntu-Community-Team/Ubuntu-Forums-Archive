---
title: "Planning stage of Software Development"
date: 2014-06-14
forum: Programming Talk
---

### Post by terminator14 on 2014-06-14
I'm not a professional programmer, but I have written quite a few programs for school, and for myself at home in my spare time.
My biggest problem with programming in any language is that past a certain point, a program that I am working on becomes too complicated to keep track of in my head, and reading my own source code a few days after I have written it requires enough effort that when I spend a minute trying to figure out what I did in a particular section, I forget what I was looking for, or what other sections do. I have plenty of comments, but they don't seem to help all that much.

What I want to know is - how do professional programmers approach a new program? Do they have some sort of planning stage? I know that some people used to use flowcharts and pseudo code, but I've seen people online mention that these techniques may be outdated. Are there better techniques out there? Is there software that helps with the planning stages of software development? Or are flowcharts and pseudo code still the industry standard when it comes to planning?

---

### Post by xb12x2 on 2014-06-15
> **terminator14 said:**
> how do professional programmers approach a new program? Do they have some sort of planning stage?

I am a professional developer, an independent contractor. 

The planning stage is the ***most important*** phase. This is where the customer and the developer create the documentation that describes concisely what and how it will be done. This is where the design specification gets done. 

When the specification is complete, if done properly, it should be possible for some other developer to read it and come quickly up to speed.

Here is a brief description of the process.

I talk/email with the customer to make sure I understand exactly what they need, and that they also understand exactly what they need, and the work that will be required, etc.

Then I start a Software Design Specification document. At this phase it's a high level brief outline of:
   __What functionality will be provided. 
   __The API that will be provided, i.e. the names and parameters of the interfaces, etc.
   __A complete list of the build tools, their versions, etc. For maintenance reasons this must be explicit! 
   __A description of formal tests to be provided which prove completion. 
 
This document gets passed back and forth and fleshed-out as many times as it takes to get everyone (marketing, engineering, manufacturing, finance, and me, etc) to understand, buy in, and accept it as the go-do-it version of the specification. Sometimes flowcharts help and are part of the design spec.

Flowcharts and pseudo code are not a required standard part of all design spec documents in my niche of the industry. But a comprehensive design specification is ***always*** a standard first requirement.

Once coding starts, comment your code ***only*** when necessary, when the code is not easily understood on its own. When you do need to comment your code, think if updating the spec is necesarry, for the benefit of the maintainers. Update the version number of the spec and keep the previous versions (just like you do with your sources).

So that's my suggestion: create a design outline, top-down. Continue the outline to  the API/function/object/procedure level. Answer the obvious design  questions in this document. In the future reading it  will get you right back up to speed.

---

### Post by terminator14 on 2014-06-15
I have come across this process in my research, and understand the need for a Design Specification when working as a professional programmer who must deal with customers, their own company, etc.
This is not what I'm after. The programs I write are open source (no customer), and I'm mainly the only developer.

When I say the "Planning Stage", I'm not referring to the project's planning stage, but the source code itself. I need a way to plan what classes, functions, loops, etc. my program will need before I start writing code.
I understand that flowcharts and pseudo code may not be required in the industry - I'm less concerned about what is required, and more concerned about things that may help me wrap my head around a complicated program's source code.
When your Design Specification document is complete, and everyone is in agreement about the features that the program should have, do you and your team not have a step before coding begins to discuss what the source code will look like,
and who is responsible for what part? Or, if you're working alone, is there no process you go through to plan out your code before you begin to program?

---

### Post by xb12x2 on 2014-06-15
> **terminator14 said:**
> I need a way to plan what classes, functions, loops, etc. my program will need before I start writing code.

The design of your program is what the design spec is for. It's so you write it down and think about it in detail until you're ready to code it without having to design it while you're coding it.

> **terminator14 said:**
> I understand that flowcharts and pseudo code may not be required in the industry - I'm less concerned about what is required, and more concerned about things that may help me wrap my head around a complicated program's source code.

The design spec, more than anything else, gets you thinking about and solving the details of the program, what you call "classes, functions, loops, etc".

I should have made it clear that there are other required documents as well, such as contracts which spell out the features, costs, schedule, etc.

> **terminator14 said:**
> do you and your team not have a step before coding begins to discuss what the source code will look like,
and who is responsible for what part? Or, if you're working alone, is there no process you go through to plan out your code before you begin to program?

Yes, the work does have to be divided up, among team members and/or for scheduling purposes, but with a comprehensive design spec that's easy to do. 

Again, all the questions about the design of your program can be put into a document ***before*** you start coding.  Then what remains to do during the coding phase is all about syntax and semantics.

---

### Post by terminator14 on 2014-06-15
I have never actually seen a Design Specification document, but from what I understand, the purpose of it is, as you said, to have a written agreement between you, the customer, and other departments in your company that may be involved that outlines what the program will do.

This is how I understand the few sections of it that you mentioned:

__What functionality will be provided. - The program is to store client information in a database, etc.
__The API that will be provided, i.e. the names and parameters of the interfaces, etc. - The main GUI window will have the following fields: "First Name", "Last Name", "Date of Birth", etc.
__A complete list of the build tools, their versions, etc. For maintenance reasons this must be explicit! - Visual Studio 2013, MySQL v123.45
__A description of formal tests to be provided which prove completion. - Not sure about this one

All this information is meant to be understood by the customer, and other departments in your company, which means that it clearly can't mention things like classes, functions, etc. because the customer, and your legal department (for example) have no clue what any of that is.
You mention that the design spec "gets you thinking about and solving the details of the program". Is this thinking done on paper? In what form?

If you had no one to answer to, and felt like creating an open source program to replace vlc, or xbmc, or firefox, the Design Spec doc is what you would create to keep track of the dozens/hundreds of source files you would use?

---

### Post by xb12x2 on 2014-06-16
> **terminator14 said:**
> I have never actually seen a Design Specification document, but from what I understand, the purpose of it is, as you said, to have a written agreement between you, the customer, and other departments in your company that may be involved that outlines what the program will do.

The software design specification document is about the ***design*** of it, whether you have customers or not. I'm suggesting that you create one as a way to begin thinking about the design, even though it's a small and simple program and you're the only developer and the only customer. Write it as if you're trying to describe the design to another developer. Read it as if you are the other developer, and ask yourself the questions the other developer would ask you. Then answer them in the document. 

If you're the only user and the only developer, it should be that much  easier for  you to get the go-ahead agreement from yourself once you're  satisfied with the design. 

Like any skill, you develop your ***design*** skills by starting with a small, simple programming goal, one so simple it doesn't actually require a document. This will help you to learn how to think about the design ***separately*** and ***before*** you start to code. Write down not only what you want but how you're going to code it. Start small with a simple high-level outline. Then continue to outline from top to bottom. Think how to make it modular, about natural dividing lines. Writing it down helps you visualize it. You can add and subtract and cut and paste until you feel you could code it from just reading the document. Questions such as *"what modules, classes, objects, functions, parameters, etc, will the program need"* will naturally present themselves as you're writing the document, and can be easily explored (designed) in the document. 

The goal is to do the design without the distraction of coding, and then to code without worrying whether it will actually work as intended. 

And the document brings you back up to speed long after you forget everything about it (which you will, sooner than you'd expect).

Coding is the building phase, not the planning/designing phase.  If you're thinking about what classes you need while you're coding you've put the cart before the horse, as the saying is.


-

---

### Post by terminator14 on 2014-06-16
Thanks for the great advice. I knew I was doing something wrong - I'll look up some design spec documents online to get a sense of what a real one might look like, and give it a try - it sounds like it's exactly what I need to help me understand my program before I try to build it.

---

