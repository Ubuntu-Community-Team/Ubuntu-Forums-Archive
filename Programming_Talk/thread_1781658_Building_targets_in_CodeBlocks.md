---
title: "Building targets in Code::Blocks"
date: 2011-06-13
forum: Programming Talk
---

### Post by ProbePLayer on 2011-06-13
Hi all.

Here is the thing: I've been programming in Code::Blocks for a couple of months, and yet I haven't understood how to create a working executable! I have debugged and run many small programs, but never had the need to run them outside the IDE of Code::Blocks...until now. I mean, I just run them in the IDE and that is all I needed so far.

But only now have I realized that I don't really know how to make a program in Code::Blocks! Someone can ask me "Hey, can you make  Hello world program?", and I cant say yes...

So what is the problem, you say? Well I am aware that there is a debug and a release target, and I know that the release target is the one I should give to my curious friend, but when I try to start the executable(at least that's what it says in Properties), nothing happens. Should I link it with the object file that ends with ".o" somehow? Is there something I missed when I created the project? Maybe a shell must be implemented? Or a post-step to be written? I don't know! :]

Therefore, I would be thankful for any tips and advice about this. 

Thanks in advance.

p.s. and I also attached an image with the Properties window alongside the path of the executable.

---

### Post by Vox754 on 2011-06-13
> **ProbePLayer said:**
> Hi all.

Here is the thing: I've been programming in Code::Blocks for a couple of months, and yet I haven't understood how to create a working executable! I have debugged and run many small programs, but never had the need to run them outside the IDE of Code::Blocks...until now. I mean, I just run them in the IDE and that is all I needed so far.

But only now have I realized that I don't really know how to make a program in Code::Blocks! Someone can ask me "Hey, can you make  Hello world program?", and I cant say yes...

So what is the problem, you say? Well I am aware that there is a debug and a release target, and I know that the release target is the one I should give to my curious friend, but when I try to start the executable(at least that's what it says in Properties), nothing happens. Should I link it with the object file that ends with ".o" somehow? Is there something I missed when I created the project? Maybe a shell must be implemented? Or a post-step to be written? I don't know! :]

Therefore, I would be thankful for any tips and advice about this. 

Thanks in advance.

p.s. and I also attached an image with the Properties window alongside the path of the executable.

This is why you notice that many people recommend learning to compile from the terminal, because in this way you know what you are doing.

IDEs (Integrated Development Environments), such as Code::Blocks, often hide these details from you, making you think you know more than you actually do. As soon as you are faced with a different IDE, or no IDE at all, you realise you cannot just click "Build" and get your executable working.

The fact that you double-click your executable and see no window opening may be indication that the program is just command-line based, in which case, you are supposed to open a terminal first, navigate to the correct directory, and then call your executable.

```

./my_executable

```

I recommend you search a little this forum and others, and try to learn to compile from the terminal first. Then you will understand the three basic steps of (1) writting code, (2) compiling, and (3) linking. Often, steps 2 and 3 are done immediately after another, so you don't notice, but the result is the same, a ready-to-run, executable file.

---

### Post by ProbePLayer on 2011-06-14
Thanks a lot! Really helpful reply. I'll get to learning to compile from the terminal right away.

Oh, and how do I mark this one as done?

Third edit:what do "beans" mean here? I've got 2 of 'em.

Fourth edit and hopefully my last :]:I did what you told me, running it from the terminal, and it worked. Thanks again. By the way, if you know someone familiar with Code::Blocks, send him in, so that he can show me how to build properly. Thanks x3!

---

### Post by Vaphell on 2011-06-14
thread tools -> mark as solved

beans = number of posts

---

### Post by ProbePLayer on 2011-06-14
thanks Vaphell.
btw,you have 1800 posts?

---

