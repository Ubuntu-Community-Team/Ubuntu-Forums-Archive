---
title: "What do I need to learn now?"
date: 2008-12-23
forum: Programming Talk
---

### Post by psycovic23 on 2008-12-23
Hey,

I've been combing all the threads in this forum for a while and I've found some relevant threads, but nothing exact.  I have an idea for a new kind of media player, but I don't really know what I have to learn to make it.  I've done the academic side of C++ already and I know basic data structures and understand most of the syntax of C++ (class design, etc) but have never actually done anything useful yet besides a ton of projecteuler problems.  

My question is, what do I need to learn now? At this point, I still don't know how to read through someone else's source code to pick up the project, so I realize I have to learn how programs are organized using autoconf, automake, etc. I'm also working on learning how to use gtkmm.  What else should I add to the list before I try and tackle my project? I realize I'm still a long long ways away from starting a successful project, so I'm not afraid of taking my time and working on some smaller project for now. I just don't really know how to start.  Any advice would be great!

---

### Post by dwhitney67 on 2008-12-23
I'm working on a similar project, just for the sake of doing it.

If you have no knowledge of it, learn about multi-threaded programming.

Then once you feel that you have the technical prowess, develop your project's requirements and come up with a design.  Then you can either prototype or start the full-blown s/w implementation of your project.

Still interested?  I know... a lot of work for something that will never earn a nickel because it has already been done by countless others.

P.S.  Don't feel that you must stick with C++; there are other languages that one can use.

P.S.S.  If you plan to develop a server that delivers media, then spend some time learning about UDP (or TCP) sockets... creating a socket, using it to send/receive messages, etc.

---

### Post by psycovic23 on 2008-12-23
Well, my project is just an mp3 manager/player, so yea, nothing new, just styled to what I want. I just don't really know the things I have to learn.  I don't mind putting a lot of time into it. I'd just like to be able to have a small application I can say that I built and learning something new.

Right now I'm sticking with C++ cause it's the only language I can make a gameplan for, but if you can suggest an easier path, I'd definitely take a look.

---

### Post by ooobooontooo on 2008-12-23
A really cool language you might want to look into for making applications and such is Python. I've only dipped my feet in a little but I think it's really clean and it's a very nice programming language. I'd have to say right now it's my second favorite after C. It won't take that long to learn so go ahead and try unless you want to stick with C++.

---

### Post by kostkon on 2008-12-23
> **psycovic23 said:**
> Well, my project is just an mp3 manager/player, so yea, nothing new, just styled to what I want. I just don't really know the things I have to learn.  I don't mind putting a lot of time into it. I'd just like to be able to have a small application I can say that I built and learning something new.

Right now I'm sticking with C++ cause it's the only language I can make a gameplan for, but if you can suggest an easier path, I'd definitely take a look.
You could then use *GStreamer* as the multimedia backend of your mp3 manager/player.

---

### Post by monkeyking on 2008-12-24
> **ooobooontooo said:**
> A really cool language you might want to look into for making applications and such is Python...
hmm, everyone loves python in here.

It's beginning to get scary.

---

### Post by psycovic23 on 2008-12-24
Yea..I realize Python is handy. I have nothing against it, but I don't want to spend my time learning all these new languages. I have a decent foundation in C++, and I'd like to do something with it. Does anyone know a good route for me to take to be able to either 1) be able to contribute to a project or 2) learn how to write a functional app?

---

### Post by nvteighen on 2008-12-24
> **psycovic23 said:**
> Yea..I realize Python is handy. I have nothing against it, but I don't want to spend my time learning all these new languages. I have a decent foundation in C++, and I'd like to do something with it. Does anyone know a good route for me to take to be able to either 1) be able to contribute to a project or 2) learn how to write a functional app?
Maybe helping in an existing project would be the best. Look at [https://launchpad.net](https://launchpad.net), [https://savannah.gnu.org](https://savannah.gnu.org), [http://code.google.com](http://code.google.com)

---

### Post by psycovic23 on 2008-12-24
> **nvteighen said:**
> Maybe helping in an existing project would be the best. Look at [https://launchpad.net](https://launchpad.net), [https://savannah.gnu.org](https://savannah.gnu.org), [http://code.google.com](http://code.google.com)

The problem is, I don't know how to dive into a project at this point. I don't know what tools I need to learn to be able to understand the source code. Could you provide some suggestions?

---

### Post by meanburrito920 on 2008-12-24
The only tool you really need is your brain. When you join a new project, don't feel compelled to contribute at once. Grab the a working coppy of the repository and look over the code. Depending on the size of the code base and the libraries used, this could take quite a while. Once you feel a bit comfortable with the code, take a look at the reported bugs and see if you can figure out what the problem is. At that point, see if you can fix the problem. If your patch works, submit it. Don't feel discouraged if your patch is not accepted, you will have learned something in the process. 


As for finding projects, I would suggest looking at freshmeat.net

Hope that helps!

---

### Post by nvteighen on 2008-12-24
> **psycovic23 said:**
> The problem is, I don't know how to dive into a project at this point. I don't know what tools I need to learn to be able to understand the source code. Could you provide some suggestions?
The only tool you'll need to learn is the version control system the project uses (Bazaar, Subversion, CVS, Git, etc.). They're quite easy, so they shouldn't be a hazzle.

---

### Post by pmasiar on 2008-12-24
Big part of becoming a competent programmer is to write **a lot** of code - and make a lot of logical mistakes, and learn from them. This is the reason why Python is better language for beginner, because it allows her to make the logical mistakes faster, without strugling with tricky syntax and typing system.

Also, the more lines of code you have to comprehend, the harder the task is - so projects written in high-level languages (Perl/Python/Ruby) which allows you to accomplish more in less lines, are easier to join and contribute (and it is more fun, because you have to invest less time per feature).

Of course C++ is excellent language if you need  the performance, just many projects don't need it and use it anyway "just in case".

Consider getting "Etudes for programmers" by Wetherrell and solve problems from it - I have some in wiki in my sig.

---

