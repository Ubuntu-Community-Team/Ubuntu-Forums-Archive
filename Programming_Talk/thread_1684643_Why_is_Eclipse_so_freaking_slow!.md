---
title: "Why is Eclipse so freaking slow?!"
date: 2011-02-09
forum: Programming Talk
---

### Post by Mr. Matt on 2011-02-09
I recently got a new laptop - Asus G73JW.  This thing is fast and has 8 GB of RAM.

So why does it feel 5x slower running Eclipse than on my previous desktop?  It also freezes a lot.  Eclipse takes forever to do some things like searching and validating.  Is there anything I can do to increase the speed?  My eclipse.ini is exactly the same as on my old desktop.  I have tried increasing the memory sizes a bit but no difference.

BTW: I have installed Sun Java and made it the default and am running on Ubuntu 10.10

---

### Post by schmendrick on 2011-02-09
i have experienced that too.


see if eclipse is using openjdk. if it does, set java to use oracles version. 
then check again to make sure it REALLY doesnt use it.

an eclipse using openjdk can be very slow and very unstable (at least it was in ubuntu versions 1,5 years ago). 


i have made it my habit to uninstall the openjdk and installing the oracle version as soon as i do anything with java applications on linux, i fell too often into that openjdk pitfall.

---

### Post by juancarlospaco on 2011-02-09
Why do you use  Eclipse ?

---

### Post by Simian Man on 2011-02-09
> **juancarlospaco said:**
> Why do you use  Eclipse ?

Why do you bother posting things like this?

---

### Post by juancarlospaco on 2011-02-09
To try to solve the problem

---

### Post by Mr. Matt on 2011-02-09
I use it for PHP development so I have the PDT version installed.  

How can I check if Eclipse is using the OpenJDK version?  I have set the default Java version to sun so shouldn't it be using that then?

I will try removing openjdk anyway.

---

### Post by Queue29 on 2011-02-09
> **juancarlospaco said:**
> To try to solve the problem

How? By starting yet another omfgg use teh emaks!!1 thread?

Eclipse is an industrial strength IDE. Perhaps the OP is using it because it's the right tool for his job.

---

### Post by fct on 2011-02-10
> **Mr. Matt said:**
> How can I check if Eclipse is using the OpenJDK version?  I have set the default Java version to sun so shouldn't it be using that then?
Window -> Preferences -> Java -> Installed JREs

---

### Post by Mr. Matt on 2011-02-10
> **fct said:**
> Window -> Preferences -> Java -> Installed JREs

Thanks.  It is definitely using the Sun version now.  I have noticed Eclipse being much better this past day and hasn't been a problem.  I will keep an eye on it though.

---

### Post by rob1101 on 2011-02-10
> **Queue29 said:**
> How? By starting yet another omfgg use teh emaks!!1 thread?

I think it is a fair question. He just asked why. Eclipse is great so is Emacs, no doubt about that. However the OP my not be aware of his alternatives which he/she might prefer or it could be a better tool for the job depending on whatever he/she is doing.

> **Queue29 said:**
> Eclipse is an industrial strength IDE. Perhaps the OP is using it because it's the right tool for his job.

Perhaps, but how will we know if no one ask?

---

### Post by Simian Man on 2011-02-10
> **rob1101 said:**
> I think it is a fair question. He just asked why. Eclipse is great so is Emacs, no doubt about that. However the OP my not be aware of his alternatives which he/she might prefer or it could be a better tool for the job depending on whatever he/she is doing.

So if someone asks about a tool, they should be told of all the other tools for that task?  OK, in every General Help thread I'll ask people why they aren't just using Windows :).

It was a dumb flamebait response and you know it!

---

### Post by rob1101 on 2011-02-10
> **Simian Man said:**
> So if someone asks about a tool, they should be told of all the other tools for that task?  OK, in every General Help thread I'll ask people why they aren't just using Windows :).

It was a dumb flamebait response and you know it!

I like to give people the benefit of the doubt. From my point of view I saw someone ask a question then get flamed. I still think it is valid question the OP could have very well been using an extension that is not fully developed or one that effects the performance of eclipse. If that was the case then yes they should be told the other tools of the task.

Your analogy is not quite right. It would be more akin to someone asking "what do you use Ubuntu for?", when they make no specification about what they are doing?, which in some cases Windows could be a better tool.

---

### Post by Simian Man on 2011-02-10
> **rob1101 said:**
> I like to give people the benefit of the doubt. From my point of view I saw someone ask a question then get flamed. I still think it is valid question the OP could have very well been using an extension that is not fully developed or one that effects the performance of eclipse. If that was the case then yes they should be told the other tools of the task.
The OP said Eclipse used to be fast on their previous computer, so unless they totally changed the way they use it at the same time they upgraded, I don't think that's the case.  Plus the Eclipse hater is a known troll :).

> **rob1101 said:**
> Your analogy is not quite right. It would be more akin to someone asking "what do you use Ubuntu for?", when they make no specification about what they are doing?, which in some cases Windows could be a better tool.
Fair enough, but I know that wasn't the poster's thought process.

---

### Post by juancarlospaco on 2011-02-10
lol, is interesting to see the VaporPosting going on here...
:)

---

### Post by vanbeast on 2011-10-28
Hi! I found the solution for Eclipse+openJDK here  [https://bugs.launchpad.net/ubuntu/+source/freecol/+bug/499156](https://bugs.launchpad.net/ubuntu/+source/freecol/+bug/499156) Post #4 I added "-Dsun.java2d.pmoffscreen=false" (without quotes) to my eclipse.ini. It helped for Freecol also. The question is what this means? And why it helped? Does anyone know?

---

