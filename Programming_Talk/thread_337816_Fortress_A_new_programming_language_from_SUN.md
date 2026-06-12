---
title: "Fortress: A new programming language from SUN"
date: 2007-01-13
forum: Programming Talk
---

### Post by derjames on 2007-01-13
This may be interesting, a new Open Source programming language from Sun, the name is Fortress... I am starting reading to give me an idea of what is all this about...

[http://research.sun.com/projects/plrg/](http://research.sun.com/projects/plrg/)
[http://fortress.sunsource.net/](http://fortress.sunsource.net/)

---

### Post by gpolo on 2007-01-13
sounds interesting, but needs java ;/ sounds logic, coming from sun

---

### Post by kleeman on 2007-01-13
Interesting language. Syntax is a lot like mathematical logic and its main application is as a replacement for Fortran on clusters. I will be keeping an eye on it as it develops. Fortran is my main language.

---

### Post by neoflight on 2007-01-15
A new programming language for high performance computing....

> Fortress is a new programming language designed for high-performance computing (HPC) with high programmability. In order to explore breakaway approaches to improving programmability, the Fortress design has not been tied to legacy language syntax or semantics; all aspects of HPC language design have been rethought from the ground up. As a result, we are able to support features in Fortress such as transactions, specification of locality, and implicit parallel computation, as integral features built into the core of the language....

From [here]("http://research.sun.com/projects/plrg/faq/index.html")....

i would like to have a flavor of it...

---

### Post by jvc26 on 2007-01-15
That looks pretty fascinating!
Il

---

### Post by neoflight on 2007-01-15
i was searching for a piece of code....but haven't gotten any. 

I would like to see some response from the Fortran people :-k

---

### Post by xtacocorex on 2007-01-15
Someone already posted about this a couple of days ago.

And I don't think FORTRAN will ever go away, as long as I still use it.

---

### Post by neoflight on 2007-01-15
i didnt know about this post....
when i searched, nothing came up.... i made a spelling mistake in the tag...

so a duplicate post.. mods please delete the other post...

---

### Post by Seine on 2007-01-15
Interesting! I recall reading about this almost two years ago, as it was a research project in Sun. Focus was on mathematical precision IIRC.

---

### Post by kleeman on 2007-01-15
> **neoflight said:**
> i was searching for a piece of code....but haven't gotten any. 

I would like to see some response from the Fortran people :-k
I have linked a sample program to do conjugate gradient optimization:

[http://www.math.nyu.edu/faculty/kleeman/NAS-CG.pdf](http://www.math.nyu.edu/faculty/kleeman/NAS-CG.pdf)

My impression in reading the site is that the project has a LONG way to go.
It is presently a buggy interpreter in need of features. For HPC apps they will need to turn it into a compiler and test it in parallel mode extensively.

Worth keeping an eye on however. The syntax is delightful.

---

### Post by neoflight on 2007-01-15
> **kleeman said:**
> I have linked a sample program to do conjugate gradient optimization:

[http://www.math.nyu.edu/faculty/kleeman/NAS-CG.pdf](http://www.math.nyu.edu/faculty/kleeman/NAS-CG.pdf)

My impression in reading the site is that the project has a LONG way to go.
It is presently a buggy interpreter in need of features. For HPC apps they will need to turn it into a compiler and test it in parallel mode extensively.

Worth keeping an eye on however. The syntax is delightful.

that looks weired! ... 
i guess they are concentrating on unicode. ... 
Since [Steele]("http://research.sun.com/people/mybio.php?c=476") is involved, i guess they do not forget about the speed and Parallel computing issues :mrgreen: 

Even a well established language such as fortran takes years to mature... i dont think fortress is gonna hit the clusters really that hard soon... may be a shot 10 yrs into the future, as i read somewhere, by 2010? i would say 2015... 

or may be by the time every country with a rocket lands on moon !!! 

who knows...

---

### Post by derjames on 2007-01-16
Today (16/jan/07) Fortress is the subject of discussion at Slashdot...

[http://developers.slashdot.org/developers/07/01/15/198212.shtml](http://developers.slashdot.org/developers/07/01/15/198212.shtml)

---

### Post by gh0st on 2007-01-16
This looks like an interesting project to watch for the future. Thanks for the heads up :)

---

### Post by laxmanb on 2007-01-17
Best of luck to Sun/everybody else!! hope Fortress does well!!

---

### Post by Dygear on 2007-01-17
When I saw the topic, I said out loud "Oh ****, not another Java." Good to see this is going for a different target.

---

