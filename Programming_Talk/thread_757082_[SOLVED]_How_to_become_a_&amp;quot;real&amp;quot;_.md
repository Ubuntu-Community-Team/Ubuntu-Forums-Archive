---
title: "[SOLVED] How to become a &amp;quot;real&amp;quot; developer"
date: 2008-04-16
forum: Programming Talk
---

### Post by Palu on 2008-04-16
Hello! :)

**Intro**
I've been following Ubuntu closely for 6 months (reading articles every day!) but haven't tried Linux at all in 6 or 7 years (tried SuSe back then and it was very difficult because I was also young and more easily frustrated; also tried the Everex gOS computer in December but don't count that because I got frustrated too quickly with how easily it crashed the cheap hardware--now I plan to move my main hardware to Ubuntu instead). Now I'm a recent college graduate with a marketing degree and a "soft" programming job (not a lot of oo concepts used). Mostly I use JavaScript, PHP, a little ASP, a little mySQL, and I excel in CSS2 standards doing small tweaks of code or (more commonly) scripts. In my spare time I love to use C++. I have never done any project that took longer than 30 development hours, never made a GUI interface (except through very simple tutorials) or gotten GL/SDL/etc integration to compile without errors, haven't fiddled with streams a ton, and usually get confused looking at other people's libraries. I can, however, make simple terminal programs that have multiple files, decent abstraction, classes with well-defined access protection, variable naming conventions, pointers (thus some dynamic memory usage), and a few other things.

**Question**
What can I do for Ubuntu? For a long time, I have not learned many new things in C++. It would be my dream to work on a project like Ubuntu (especially if in C++)... and at 22 years of age, I'm sure I have the time to work towards such a goal. Tutorial websites such as cplusplus.com and cprogramming.com are excellent, but I am at a point where I've taken all the "beginner" and "intermediate" tutorials and either need some good direction on what to study, formal computer science schooling, or a mentor who will patiently help me understand increasingly complex programs until I am able to actually contribute myself. Any suggestions? Books? Links? Funny jokes?
:popcorn:

---

### Post by lnostdal on 2008-04-16
if you want to help the open source movement(#1) or an open source project and/or me then learn Common Lisp ..  i got tons of work that needs to be done using that language (all open source license of course), and i don't mind helping people getting started with Lisp or "mentoring" them


#1: or something like that .. point is; we get to watch MS fall .. haha

---

### Post by LaRoza on 2008-04-16
> **Palu said:**
> Hello! :)

**Question**
What can I do for Ubuntu? For a long time, I have not learned many new things in C++. It would be my dream to work on a project like Ubuntu (especially if in C++)... and at 22 years of age, I'm sure I have the time to work towards such a goal. Tutorial websites such as cplusplus.com and cprogramming.com are excellent, but I am at a point where I've taken all the "beginner" and "intermediate" tutorials and either need some good direction on what to study, formal computer science schooling, or a mentor who will patiently help me understand increasingly complex programs until I am able to actually contribute myself. Any suggestions? Books? Links? Funny jokes?
:popcorn:

Hello.

You will find that Linux has come a long way for desktops. In everyway, it is better than Windows for me. (I am not a gamer, and I don't use Windows specific software)

OpenSUSE, Ubuntu, PCLinuxOS, and others are quite good at working out the box (depending on hardware you have, most works fine)

I suggest learning some more abstract concepts and data structures/algorithms. Learning a syntax is pretty easy, learning how to be a programmer is a lifetime goal.

My wiki might be of use (the Programming Library has links to some interesting sites)

(And don't mind Lars, he's probably drunk (jk))

---

### Post by pmasiar on 2008-04-16
What do you want to do for ubuntu? Depends on what you want to do. Do not restrict yourself to C++ hacking only. Or maybe your dream is hacking as a hobby, regardless of what is your day job?

As a marketing/web design expert, you may check some projects and improve how they look and how they are promoted.

You can also pick some project using C++, learn it inside-out, and add some patches. Warning: it may take you many months to know C++ and that project enough to be useful: C++ is very picky about who are it's friends. :-)

Or if your goal is to have fun programming, you may even decide to learn other languages and participate in projects you like. You can do whatever you want, if you have patience and determination to learn the skills you would need to do that.

So real question is: what excites you so much that you are ready to spend many months to learn and hack? Some specific program area? Helping to promote projects better? Or you want to become 'master of the universe' and help packaging/maintaining programs for Ubuntu?

---

### Post by skeeterbug on 2008-04-16
You could also create a new project. For ideas, check out [http://brainstorm.ubuntu.com/]("http://brainstorm.ubuntu.com/")

---

### Post by lbotha on 2008-04-16
For some programming challenge, try [project euler]("http://www.projecteuler.net")

---

### Post by fyplinux on 2008-04-16
programming is somehow  an engineering work.

I think you need more practice on programming. I only realized that I beginning to understand some concepts of programming(like system architecture) after I finish a project, with code line of moe than 10000 lines, which was the first time for me to manage such a somehow big project.

I think a real developer should have the ability to manage a real project, rather than some pieces of code.

There 's a big gap between the small programs and a real project. for example, when dealing with a real project, you need to design the project carefully.

someone said it's good to read someone else 's code[citation needed :)] or join in an open source project.

 But I am wondering could you really understand the code , or could you do some meaningful contribution to the open source project, as you don't have much programming experience?

It might be a good start to rewrite some project you are interested in. As the techiniques are easy to be traced following the existing samples.

---

### Post by Ferrat on 2008-04-16
fyplinux >> he has programming experience but not under any major projects as I understand it.

Well learning a new language like Lisp might not be what you want from what I read, there are a few ways to go depending on what you want to do?

Game programming is a bottomless pit (good and bad) when it comes to learning but also somewhat limited if your goal is advanced science or as it seems you are more interested in OS related stuff etc, but then you got the question, on what in the OS do you want to work? 
Maybe give a go at making a driver for some odd hardware?  Make nice GUI effects? Debug programs? Make programs more effective? Create totally new programs?

---

### Post by Palu on 2008-04-16
Correct--I have programming knowledge but not experience. I haven't been able to jump the gap from intermediate tutorials and non-gui mini-tools to useful projects. I look at complex code and I'm fairly lost.

I guess I need to specify goals better. I'd like to eventually...
[LIST]
[*]Develop drivers for wider ranges of hardware
[*]Work on integration and the usability experience
[/LIST]

What areas are best for me to look into for this? I would not mind studying at the University next to me, but they only offer Java. I also somehow need to gain MUCH more experience with complex architectures before I'd be of any use. I'm not sure how to start in that direction.

---

### Post by pmasiar on 2008-04-16
> **Palu said:**
> 
[LIST]
[*]Develop drivers for wider ranges of hardware
[*]Work on integration and the usability experience
[/LIST]


Very different areas, and neither will be helped much by studying Java.

With your marketing background, I would focus on usability first: contribute with suggestion to any project you are interested in, while learning C. I expect most drivers are in C (which is good news for you: it is simpler than C++, but syntax is very close). There is a kernel project to create free drivers for all devices, they are inviting developers (I forgot project name but someone around will remember it :-) ). Drivers are in a sense simpler to start because they are smaller and functionality is somewhat limited. Consider learning simple scripting language like Python to help with creating/managing test data, and bash to manage builds.

You need to solve many training tasks before you will be able to tackle real problems, see wiki in my sig for links to tasks.

---

### Post by nanotube on 2008-04-16
> **lnostdal said:**
> if you want to help the open source movement(#1) or an open source project and/or me then learn Common Lisp ..  i got tons of work that needs to be done using that language (all open source license of course), 


link to project[s] and/or existing code? :)

---

### Post by Palu on 2008-04-17
I know they're two very different areas, and I figured Java would help me in little considering the things I want to do. Both areas I mentioned (drivers and usability experience) inspire me because my marketing background helps me grasp the common user's sense of usability a little better. Drivers inspire me because it's very technical (makes me feel smart, I guess, haha) and still can make or break a user's experience.

I don't know a thing about Lisp. I'll probably read a wikipedia entry on it this weekend and maybe look up a hello world tutorial. It might be far from my core competencies and thus not be useful at the moment. Never hurts to look at new things, though.

I think this will be my gameplan: I'll start looking at code for open source drivers. I should catch on to C fairly well. Pointers and classes will change the most from what I'm used to, I think. As I weave through them, I'll start asking questions to help me understand how that sort of architecture is handled. Then, perhaps I'll run across someone willing to chat regularly in hopes of me being able to contribe to his/her project.

Thank you all for the advice.

---

