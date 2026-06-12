---
title: "Scope problem with GTK Callbacks"
date: 2006-08-30
forum: Programming Talk
---

### Post by spawn968 on 2006-08-30
I've always had learning C and GTK+ in the back of my mind.  Ever since I started running linux six years ago, I've wanted to bridge the gap from patching to actually writing applications.  Everytime, though, I manage to run into the same problem.  Keep in mind that I have taught myself C and GTK, so I have no doubt there are some severe design issues.
Anyway, here's the problem.  When I go to write a callback, I know you can either declare a widget as global or pass a pointer to it.  I honestly hate having global variables, so I want to go with pointers.  The problem is scope, I know that for sure, but I don't know how to remedy it.  So, here is the code: [http://pastebin.com/780268]("http://pastebin.com/780268").  This will eventually have a list of computers with associated IP addresses running VNC server, but for right now I'm stuck with my scope issue.  Can anyone point me in the right direction?

---

### Post by tbrownaw on 2006-08-31
> **spawn968 said:**
> Anyway, here's the problem.  When I go to write a callback, I know you can either declare a widget as global or pass a pointer to it.  I honestly hate having global variables, so I want to go with pointers.  The problem is scope, I know that for sure, but I don't know how to remedy it.
How do you know this? What is it doing (or not doing) that's wrong? What errors are you getting? What, exactly, *is* this problem you're referring to?

> **spawn968 said:**
> Can anyone point me in the right direction?

[http://catb.org/~esr/faqs/smart-questions.html#symptoms](http://catb.org/~esr/faqs/smart-questions.html#symptoms)

It compiles and runs, and doesn't give anything that looks like an error message. Nobody can help you unless you learn to ask better questions.

---

