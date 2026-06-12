---
title: "linux and object oriented database programming???"
date: 2008-08-23
forum: Programming Talk
---

### Post by mihalisla on 2008-08-23
Dear community,
               I would like your help ,so I will be clear with what I would like your help on!
1. I have knowledge on rdbms and sql but I would like to get started with object oriented databases with c# (sharp)
2. How "deep" should I go in c # so as to be effecient with database programming?
3.are there any resources to getting started with the philosophy behind designing object databases.Like the relational model design !
(I need the basic concepts of oodatabases)
4.can all these be done with mono and if yes what are the needed libs?
Or if there is a lib how do i make it run with the mono framework???

Thanks a lot !!!

---

### Post by CptPicard on 2008-08-23
You want an ORM...

[http://www.hibernate.org/](http://www.hibernate.org/)

Originally for Java, seems to have a .NET version as well!

---

### Post by mihalisla on 2008-08-23
thank you a lot I will try it even though i don t have a clue so far about what it is talking about ...

---

### Post by tinny on 2008-08-23
> **mihalisla said:**
> Dear community,
               I would like your help ,so I will be clear with what I would like your help on!
1. I have knowledge on rdbms and sql but I would like to get started with object oriented databases with c# (sharp)
2. How "deep" should I go in c # so as to be effecient with database programming?
3.are there any resources to getting started with the philosophy behind designing object databases.Like the relational model design !
(I need the basic concepts of oodatabases)
4.can all these be done with mono and if yes what are the needed libs?
Or if there is a lib how do i make it run with the mono framework???

Thanks a lot !!!

Im a little confused about what you are asking.

1. Do you want to use an object oriented database, or a relational database? (the two are different)

2. Are you wanting to use ORM (an object oriented interface to a relational database)? If so the more widely supported ORM API for C# development is DBLinq

have a read of this
[http://tirania.org/blog/archive/2007/Oct-24.html](http://tirania.org/blog/archive/2007/Oct-24.html) (a blog entry from Mr Mono)

3. Can you use Java instead? Java is much more mature in this area. Also you will get a lot more help in this forum if you are using Java and ORM (IMO).

---

### Post by pmasiar on 2008-08-24
> **tinny said:**
> 3. Can you use Java instead? Java is much more mature in this area. Also you will get a lot more help in this forum if you are using Java and ORM (IMO).

ORMs are completely different beast of course.

But I disagree that Java has more mature ORMs. Maybe compared to C# :-) 

Static foundation of Java and C# forced Java hackers to think about it harder, yes, and there are many solutions, yes. But flexibility of dynamically typed languages simplifies ORMs in scripting languages significantly (to the level that you can whip your own trivial mapper in a day, so many ORMs exists, and it takes longer to consolidate.

Take look at SQLAlchemy, part of Python/Turbogears. And no XML config files in sight! :-)

---

### Post by CptPicard on 2008-08-24
> **pmasiar said:**
> 
But I disagree that Java has more mature ORMs. Maybe compared to C# :-) 


Yes, Java has very *mature* ORMs. You can argue the technical merits separately of course :)

---

### Post by drubin on 2008-08-24
> **CptPicard said:**
> Yes, Java has very *mature* ORMs. You can argue the technical merits separately of course :)

I would rather use java, You are trying to write an application in c# and then run it through a kinda hacked together "VM" any way, Why not just go the full VM style and have your application work the same on both windows and Linux.

I have used hibernate before it is pretty good. (For java at least)

---

### Post by tinny on 2008-08-24
> **pmasiar said:**
> 
But I disagree that Java has more mature ORMs. Maybe compared to C# :-) 


Compared to C#. (Cant comment on the Python world yet...)

> **pmasiar said:**
> 
Static foundation of Java and C# forced Java hackers to think about it harder, yes, and there are many solutions, yes. But flexibility of dynamically typed languages simplifies ORMs in scripting languages significantly (to the level that you can whip your own trivial mapper in a day, so many ORMs exists, and it takes longer to consolidate.

Take look at SQLAlchemy, part of Python/Turbogears. And no XML config files in sight! :-)

Are you saying it would take you a whole day in Python? Why so long? :lolflag:

BTW: Hibernate no longer requires the use of XML config. All the Hibernate config can now be done with annotations (J2EE 5).

@pmasiar not that you're probably that keen, but you should have a look at J2EE 5, EJB3 and Hibernate annotations. There have been some very big improvements :-)

---

### Post by pmasiar on 2008-08-24
> **tinny said:**
> BTW: Hibernate no longer requires the use of XML config. All the Hibernate config can now be done with annotations (J2EE 5).

@pmasiar not that you're probably that keen, but you should have a look at J2EE 5, EJB3 and Hibernate annotations. There have been some very big improvements :-)

non-XML config - finally! Thanks for that info. That certainly **is** major improvement. Time to look again at Hibernate! Yes, I also have a day job, and it's not in Python yet - but I am working on it :-)

---

### Post by tinny on 2008-08-24
> **pmasiar said:**
> non-XML config - finally! Thanks for that info. That certainly **is** major improvement. Time to look again at Hibernate! Yes, I also have a day job, and it's not in Python yet - but I am working on it :-)

(No offence) Maybe you should have another good look at the least J2EE tools etc. Sounds like your impression of J2EE development may be one generation behind.  :)

J2EE 4 (1.4) EJB2.X, Hibernate < Version 3 (I think) where much, much harder to use (I hate using them).

---

### Post by skeeterbug on 2008-08-25
For C# I highly recommend LLBLGen Pro. It is a commercial ORM, but well worth it for the support alone. It is pretty cheap (150 USD or something).

I have been a customer for 4 years now, LLBLgen has been around for 5. It works under Mono as well. No xml config files either!

[http://www.llblgen.com/Pages/customers.aspx](http://www.llblgen.com/Pages/customers.aspx)

DLinq is going the wrong direction: [http://weblogs.asp.net/fbouma/archive/2005/09/13/425063.aspx](http://weblogs.asp.net/fbouma/archive/2005/09/13/425063.aspx)

---

### Post by drubin on 2008-08-25
> **tinny said:**
> (No offence) Maybe you should have another good look at the least J2EE tools etc. Sounds like your impression of J2EE development may be one generation behind.  :)

sure it is greater then one generation behind. As most peoples impressions of Java is still of JDK1.2

---

### Post by mihalisla on 2008-08-25
What I really want to do is an object oriented database and not relational.
Could you please tell me what is an ORM ???

Thank you very much guys I'm grateful for your replies! 
I liked the debate too!!!

---

### Post by Shin_Gouki2501 on 2008-08-25
JPA is a godsend thing if you want ORM and Java you can do so nice things with that :D



@mihalisla
Please specify why you want to use object oriented database?What is you general apporach? XML processing?

BTW: seems you use OQL with OO databases too , and JPA uses OQL too!

---

### Post by mihalisla on 2008-08-25
No xml processing  Idon t know what this is!(If you can explain to me)
I d like to make databases for my business so as to have better management!
rdbms does it s work but I want new things to explore!!!

---

### Post by CptPicard on 2008-08-25
> **mihalisla said:**
> 
rdbms does it s work but I want new things to explore!!!

If you are comfortable with RDBMSes and are interested in the object-side of the whole thing, then yes, an ORM (Object-Relational Mapper) is what you want. It is a software layer that does the translation back and forth between the relational data model and the object-oriented data model. In Java with Hibernate it can be as easy as just JPA-annotating your classes and letting the system generate database tables from that. All the SQL generation etc is handled by the mapper. At easiest you can just work with objects and let the mapper handle all the relational stuff under the hood.

---

### Post by mihalisla on 2008-08-25
thanks a lot u were great help

---

### Post by tinny on 2008-08-25
> **CptPicard said:**
> If you are comfortable with RDBMSes and are interested in the object-side of the whole thing, then yes, an ORM (Object-Relational Mapper) is what you want. It is a software layer that does the translation back and forth between the relational data model and the object-oriented data model. In Java with Hibernate it can be as easy as just JPA-annotating your classes and letting the system generate database tables from that. All the SQL generation etc is handled by the mapper. At easiest you can just work with objects and let the mapper handle all the relational stuff under the hood.

+1

@mihalisla, this is a modern approach.

---

