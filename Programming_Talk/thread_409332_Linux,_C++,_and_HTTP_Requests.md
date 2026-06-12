---
title: "Linux, C++, and HTTP Requests"
date: 2007-04-14
forum: Programming Talk
---

### Post by Bicx on 2007-04-14
I'm beginning to work out the details of a small project involving a C++ - based custom web server, and I am having some difficulty finding a library that allows the interception of HTTP requests. Does anyone know if such a library exists for Linux? Also, any other suggestions would be much appreciated. I'm sort of new to C++, and I am trying to gain some experience.

---

### Post by pmasiar on 2007-04-14
> **Bicx said:**
> C++ - based custom web server, ... a library that allows the interception of HTTP requests. ...I'm sort of new to C++, and I am trying to gain some experience.

Here is web server in 7 lines of Python: [http://learnpython.pbwiki.com/WebApplication](http://learnpython.pbwiki.com/WebApplication) :-) Hint: learn simple language before diving into C++

---

### Post by phossal on 2007-04-14
[A simple web server in C++ for Windows. ]("http://www.adp-gmbh.ch/win/misc/webserver.html")   This is a classic case for Google. I like the idea of programming a web server in C++. I like the idea of 7 lines of Python, too. We know *import CGIHTTPServer*, and *import BaseHTTPServer* means we aren't really writing a web server in 7 lines though. Useful, maybe, but not a good way to really learn much. Couldn't you wrap those seven lines *again*, and reduce it to a web server in 2, or even 1 lines? 


#/usr/bin/python
import ALL_HTTPServer;
httpd.start_and_serve_forever()

Other than learning, I don't get why people would write a web server anyway. If you don't need a fully functional, enterprise-level product, why are you *running* a web server? You can *buy* hosting space for about $3.00 month, and just upload your files. Writing a simple server in c++ is an educational experience.

---

### Post by Bicx on 2007-04-14
Thanks!

I've actually been programming in other more-or-less simpler languages, but as I'm about to enter my junior year of computer science classes, I want to really focus on getting C++ down. I could have probably done this in Perl just by modifying something I wrote for my job, but I want to do it the "hard" way (hard for me :P).

---

### Post by phossal on 2007-04-14
> **Bicx said:**
> Thanks!

I've actually been programming in other more-or-less simpler languages, but as I'm about to enter my junior year of computer science classes, I want to really focus on getting C++ down. I could have probably done this in Perl just by modifying something I wrote for my job, but I want to do it the "hard" way (hard for me :P).

I can relate. I've been trying to get a better grip on NASM lately, to keep up with whiz-kid, Wybiral. Even moving from MASM, writing stuff in NASM is tedious. lol Half a weeks work could be written by Pmasair in a few keystrokes. 

It's all about learning.

---

### Post by Bicx on 2007-04-14
Hehe, exactly. What I could done using Perl would be a short script that would ultimately give me the same result (although probably a bit slower). But looking at a lower level, I'm not really the one who wrote the code that actually makes it **work**. For me, C++ lets me get a little lower in the inner workings and actually learn something. Relatively lower anyway. If I really wanted to get hard-core, I could just write my own libraries.... or write it all in assembly language and custom-build my own compiler. :) But for now I'll stick with C++ since it gets more in-depth but still allows a degree of coding efficiency.

---

### Post by pmasiar on 2007-04-14
> **Bicx said:**
> I want to really focus on getting C++ down.

Of course you are free to do whatever you want in your free time, and reinventing the wheel (even if slightly squared) will teach you something, but... If you don't *have* to reinvent the wheel, why not dive into some project where your code has chance to be used by real people  to do something? There are many open source projects looking for developers. Tools, or even game projects. You can join and contribute code to community - contribute to some project you care about.

---

### Post by Bicx on 2007-04-14
That was actually my original goal.... to join a open source project of some sort. But at this point I think my limited experience with C++ would be more of a hindrance. That's why I'm just trying to think of something to get my skills sharpened. I chose programming a web server because I've done a lot of web programming before and it sounded interesting.

---

### Post by qpwoeiruty on 2007-04-14
> **pmasiar said:**
> Of course you are free to do whatever you want in your free time, and reinventing the wheel (even if slightly squared) will teach you something, but... If you don't *have* to reinvent the wheel, why not dive into some project where your code has chance to be used by real people  to do something? There are many open source projects looking for developers. Tools, or even game projects. You can join and contribute code to community - contribute to some project you care about.

I don't like that whole "reinventing the wheel" analogy. To me, it's more along the lines of working with wood and building yourself a table or desk. Sure, you can buy any number of premade products, but there's a lot to be said about building it yourself. You learn a lot about what works and what doesn't all while making something exactly how you like.

Libraries are like tools. They're the difference between a hammer and chisel, and power drills and lathes. If you want to chisel out your table by hand, that's fine. You become very skilled with the chisel and when you're done, you are exhausted but feel like you've learned a lot in the process, even though your table isn't completely level and the surface is not truly flat. Move up to power drills and lathes and you can make the same table with a lot less effort and the result is a level table with a level surface and maybe some fancy design on the legs. You don't learn as much as you would have with just your basic toolset but you're satisfied with the result.

Scripting is like buying one of those furniture-in-a-box sets. Some assembly required, but it's really fast. The downside? You only learn how to put pegs in holes and turn a screwdriver...

---

### Post by pmasiar on 2007-04-14
> **qpwoeiruty said:**
> I don't like that whole "reinventing the wheel" analogy.... If you want to chisel out your table by hand, that's fine. 

I agree with you that analogies might be misleading, but... lets stretch your analogy a little, maybe it won't break :-)

I agree it is important to learn how to use the tools properly, but I propose to use the chisel on fixing public playground, where children got hurt by splinters, instead of training on pieces of wood before throwing them to the fireplace. How do you like my analogy? :-)

Another positive from participating on open-source project is, that learner can read (hopefully clean and well-structured) code written by experts and learn from it, instead of learning own crappy solutions.

Most project are interested in recruiting new developers, and it never hurts to have deep understanding of a tool you use daily. Important part, learner should be deeply interested in learning insides of a project.

> Scripting is like buying one of those furniture-in-a-box sets. Some assembly required, but it's really fast. The downside? You only learn how to put pegs in holes and turn a screwdriver...

I am lost about how "scripting" is relevant here to anything? Is it becausue I mentioned Python?

---

### Post by Bicx on 2007-04-14
Yes, but what if I chisel too hard, slip, and put a gash in a small child's leg? ; )

The reason I'm doing this is to figure out the basics of dealing with sockets and fine-tuning my C++ skills without being a burden on a project or writing obviously erroneous code. I'm so used to Java that the transition is quite slow.

---

### Post by pmasiar on 2007-04-14
> **Bicx said:**
> Yes, but what if I chisel too hard, slip, and put a gash in a small child's leg? ; ) 

here - analogy breaks, because in programming:

If you did it by yourself, chances are, you may not even noticed it is subtly broken, only if it is broken badly.
In F/OSS project, your patch will not be accepted - and developers would tell you why, so you would learn *more*. IMHO, do as you want.

> The reason I'm doing this is to figure out the basics of dealing with sockets and fine-tuning my C++ skills without being a burden on a project or writing obviously erroneous code..

Now you disclosed the all-important *why*. Sockets! 

I would suggest looking into whiteboard-type application, sharing editing of a file. It is nice to know, because you can use it in real life. And of course couple online game engines would like to have one more socket hacker in their team. And you can get your hands dirty without writing and debugging pages and pages of scaffolding code. But again, up to you.

---

### Post by qpwoeiruty on 2007-04-15
Yep, all analogies have to break at some point, though I'd argue in the case about fixing a public playground before learning the basic tools (comparable to writing code for a lot of people to use without a firm grasp on a lot of the basics of the language) that you should either work on smaller projects for yourself or work in a team under or alongside the direction of people who do have a very good grasp on how things should be done. Though I've never heard of an apprentice carpenter, blacksmiths frequently had apprentices that would learn from the experience of the master. Submitting to a small, active open source project is where this part of the analogy comes in to play, especially if they're willing to help you debug your code, which a few are, especially if your code has the potential to add something interesting to the project.

I haven't used C++ in years and just started again once I switched to Ubuntu. I find it amazing how much I've forgotten or how much I learned that was Windows specific, but even I am currently submitting to a small project and it's forcing me to relearn things that were long forgotten. It's been a positive experience overall and is definitely something to consider if/when you feel you're ready.

---

### Post by phossal on 2007-04-15
I suggest you submit your 2-line python server to NASA and ask for input on how you could be a better programmer. Kidding aside, have you made any progress? Can you telnet yourself or anything?

---

