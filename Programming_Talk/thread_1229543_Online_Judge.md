---
title: "Online Judge"
date: 2009-08-02
forum: Programming Talk
---

### Post by progfool on 2009-08-02
Hey,
I am new to ubuntu....so would qppreciate it better if youll explain in a bit details....

now the problem .... :)

I am designing a online judge to test c/c++ codes....what it does is receive codes from different programmers on the web, saves it to my computer, compile and execute it and checks its correctness........I have designed it using  Java/JSP/mysql

Now, a user may submit a malicious code which tries to create/modify/delete files from my system. It may also try to change the system environment setting ( I have ulimit setting to control the amount of memory and CPU time).

So I want to restrict the user programs from making any changes in my harddisk...and also stop it from changing any settings which I have done.....

Please if someone could help me regarding how to do it...

Regards,
Vivek

---

### Post by dwhitney67 on 2009-08-02
It sounds like a complex project, but why would you think anyone would use your site for something they can already do themselves?

As for restricting access to the hard-drive, that will be difficult.  You could always run the program from within a grunt-user's account; that way the application at best, could only affect that user's home directory.

There are probably other means to isolate a user's application; for instance running chroot into a particular folder that has the basic shell tools.

At the end of the day, though, you are going to face a lot of headaches setting up everything, and for what... a site that maybe reaches out to a few developers?

---

### Post by progfool on 2009-08-02
well...rite...I agree to it.....I just wanted to orgnize a online programming contest in my college fest......so I decided to develop it...
I have already had  many headaches with mysql ad java things.....but I just want to develop this project....dont really care if it reaches many out thr....

So back to work....can you please explain me in details whatever you meant to say......
I am sorry, but I installed ubuntu couple of days back....soo I dont have much idea about it..

---

### Post by dwhitney67 on 2009-08-02
> **progfool said:**
> ...
I am sorry, but I installed ubuntu couple of days back....soo I dont have much idea about it..

Ouch!  You may want to familiarize yourself with Linux permissions before proceeding any further with this effort.

The option of using chroot to setup a temporary work-area is not trivial; but with a little research on the web, you probably could figure it out.  But if you are only a few days into Linux, you may find yourself overwhelmed with the information.

The concept you are proposing is something that is accomplished by a seasoned Linux operator, if not a guru.

---

### Post by NovaAesa on 2009-08-02
I can see one potential problem that you might run into. [http://en.wikipedia.org/wiki/Halting_problem](http://en.wikipedia.org/wiki/Halting_problem) It's called the halting problem. Basically, you cannot tell if a program will always halt or just keep running forever. If you can solve the halting problem, you might just get this project working very well (plus if you can solve the halting problem, I be you would get a Turing Award out of it :P).

---

### Post by slavik on 2009-08-02
> **NovaAesa said:**
> I can see one potential problem that you might run into. [http://en.wikipedia.org/wiki/Halting_problem](http://en.wikipedia.org/wiki/Halting_problem) It's called the halting problem. Basically, you cannot tell if a program will always halt or just keep running forever. If you can solve the halting problem, you might just get this project working very well (plus if you can solve the halting problem, I be you would get a Turing Award out of it :P).
and tenured professorship at stanford ...

create a bunch of chmodded environments and recreate them for each run?

---

