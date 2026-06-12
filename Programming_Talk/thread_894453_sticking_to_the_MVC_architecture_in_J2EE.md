---
title: "sticking to the MVC architecture in J2EE"
date: 2008-08-19
forum: Programming Talk
---

### Post by dexter.deepak on 2008-08-19
i feel myself to be quiet familiar to servlets and jsps, but i wonder how to stick to the MVC architecture in making a serious project in my near future.
i have heard and read about STRUTS framework, but it still seems to  complicate the issues further. i feel like there must be something better in industrial practice nowadays....is spring what am i looking for ??
plus, can someone alo guide me to some good tutorials for struts (or spring if its worth any of my needs)...the reason for this being i have already wasted 2 of my weeks reading "complete-reference" like stuff for struts, and i am running out of time now :(
thanks.

---

### Post by pmasiar on 2008-08-19
> **dexter.deepak said:**
> how to stick to the MVC architecture in making a serious project in my near future.
i have heard and read about STRUTS framework, but it still seems to  complicate the issues further. i feel like there must be something better in industrial practice nowadays

I feel your pain. Even more than you, because i did web apps using MVC done right, in Python/Turbogears.

In Java, everything is designed to scale up and up, to projects with 1000 programmers and 10zillion pages. And because of static typing in Java, the dynamic part of application is done in XML. And nothing in J2EE scales down, where single developer is struggling with simple 5 page app.

Yes, consider Spring if you can. At least, it will be easier to eliminate obsolete docs and how-to from obsolete Struts1.1, which are all over the google.

I found really neat framework: Stripes. It uses  cool new features of Java to avoid big part of XML config, but you hardly can call it 'industrial' - it's a cool niche player. Using it was never option for me, we are forced by people with no clue to use the most conservative (retarded) solution we can get.

Good luck.

Next time when you want to waste two weeks, get Python and Django, and follow tutorials. You will be surprised how far you can get in two weeks.

---

### Post by tinny on 2008-08-19
> **dexter.deepak said:**
> i feel myself to be quiet familiar to servlets and jsps, but i wonder how to stick to the MVC architecture in making a serious project in my near future.
i have heard and read about STRUTS framework, but it still seems to  complicate the issues further. i feel like there must be something better in industrial practice nowadays....is spring what am i looking for ??
plus, can someone alo guide me to some good tutorials for struts (or spring if its worth any of my needs)...the reason for this being i have already wasted 2 of my weeks reading "complete-reference" like stuff for struts, and i am running out of time now :(
thanks.

First off, good on you for wanting to stick with MVC.

Ive found that the best way to stick to MVC in J2EE is to use a Framework that pretty much forces it on you (This will help stop other members of your team breaking your nice MVC pattern).

I would strongly suggest you have a look at [Spring MVC]("http://en.wikipedia.org/wiki/Spring_framework#Model-view-controller_framework").

---

### Post by dexter.deepak on 2008-08-20
thanks for your replies.
i would like to admit the point that i am new to struts, and have been through it for about 2 weeks.
what i want to know is that can i still move on to spring or stripes (as suggested by pmasiar) ?
i am planning this for my end semester web project,but our teacher wants us to use XML as much as possible... i wonder which path to take, and i dont have enough time to taste all these technologies.
hope to get some more help.
thanks.

---

### Post by CptPicard on 2008-08-20
> **dexter.deepak said:**
> 
what i want to know is that can i still move on to spring or stripes (as suggested by pmasiar) ?

Spring is fairly easy to get going with. Don't get spooked by all the IoC mumbo-jumbo in the docs, you can pick it up as you go from examples.

> 
i am planning this for my end semester *web project*,but our teacher wants us to use *XML as much as possible*...

Oh My God :o

Well, your teacher is... uh... developmentally challenged, then.

---

### Post by pmasiar on 2008-08-20
> **CptPicard said:**
> Well, your teacher is... uh... developmentally challenged, then.

XML is not part of the solution: it is part of the problem :-)

Stripes is nice that it does not need or uses XML for configs. Ugliness of Struts and Spring is that you have to program not only in Java, but also in XML config files for your project (because Java is statically typed, XML is simplest (for Java) way to circumvent this limitation).

Good luck, you may need it!

MVC is good decision, but let your teacher decide about the framework, and ask him instantly if you are stuck - neither Struts or Spring are easy to begin for beginners. You need a guru to guide you, let your teacher earn his salary!

---

### Post by dexter.deepak on 2008-08-20
> **CptPicard said:**
> 

Well, your teacher is... uh... developmentally challenged, then.

:lolflag: you got it absolutely right, this is what the majority of our batch says !!
yet the minority, who stand in favour of xml (and the teacher too), say that using xml gives you a farely good idea not only of the data-flow, but also the control-flow...and i think they mean a point (atleast for learners like me, who are not yet into proper web-development)

---

### Post by CptPicard on 2008-08-20
The idea behind all the XML is probably that you could define somehow independent and reusable components that you could then mix and match and combine and move around and... by just redefining the configuration file.

In reality this is rarely so; and in the XML you just end up repeating what you probably do in code already, or alternatively, would at least prefer to do in code, where the flow logic and settings are at least closer to the actual code. XML forces, at its most *benign*, separating the system into two nonsensical parts just for the fun of having the XML.

---

### Post by tinny on 2008-08-20
> **dexter.deepak said:**
> 
What i want to know is that can i still move on to spring or stripes (as suggested by pmasiar) ?


Yes (Just use Spring to wire up your beans, (system components)), but you shouldn't use Spring MVC and Struts together.

> **dexter.deepak said:**
> 
i am planning this for my end semester web project,but our teacher wants us to use XML as much as possible... i wonder which path to take, and i dont have enough time to taste all these technologies.
hope to get some more help.
thanks.

](*,)

Has you teacher told you why you should do this? Have you been told about dependency injection? Dependency injection is probably completely over kill for you project, but should be a good learning exercise. (dependency injection makes all that XML config worth while)

If you dont use dependency injection you are pretty much wasting your time with Spring IMO.

---

### Post by CptPicard on 2008-08-20
> **tinny said:**
> 
If you dont use dependency injection you are pretty much wasting your time with Spring IMO.

And even dependency injection is a huge "waste" of XML...

---

### Post by tinny on 2008-08-20
> **CptPicard said:**
> And even dependency injection is a huge "waste" of XML...

Then you must like EJB3 :)

XML wiring is a pain! That's why I was originally trying to get dexter.deepak to look at Spring MVC, then he could use convention over configuration to minimise this XML bloat.

[http://www.memestorm.com/blog/convention-over-configuration-in-springs-mvc/](http://www.memestorm.com/blog/convention-over-configuration-in-springs-mvc/)

But that suggestion seemed to be quite invisible :(

---

### Post by CptPicard on 2008-08-20
> **tinny said:**
> Then you must like EJB3 :)

Yes, why it IS why I should like it (more)... and why you turned me around slightly regarding J2EE... Java is getting better, but it is doing so only by stealing stuff from dynamic typing languages' playbook ;)

---

