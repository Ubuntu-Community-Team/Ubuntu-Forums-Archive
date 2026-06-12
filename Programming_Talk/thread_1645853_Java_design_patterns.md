---
title: "Java design patterns"
date: 2010-12-15
forum: Programming Talk
---

### Post by _joachim_ on 2010-12-15
Generally speaking, how do you know which design pattern to implement?  I  mean what's the method you use to know if you need to implement x or y  pattern in your program?  What kind of process do you go through to find  this out?

I've been mulling over this site [http://www.fluffycat.com/Java-Design-Patterns/](http://www.fluffycat.com/Java-Design-Patterns/)  though it still leaves me asking, how do I know which to use.

---

### Post by r-senior on 2010-12-15
Remember there are no prizes for using a design pattern. A design pattern is just a proven way of solving a problem with a design. It's best not to get caught up on "I have to use xyz" because it's there. Been there, done that. ;)

Design patterns can usually be described in terms of a problem, a motivation and a solution. If you have the problem and you share the motivation, implementing the solution is probably a good idea.

For example, you've written some JDBC code that interacts with a database and performs some business logic. You are required to support different databases but the *problem* is that your business logic is becoming cluttered with switches between database-specific code. Your *motivation* is to clean up your business logic and make it easier to support different databases. The data access object (DAO) pattern fits this problem and motivation, so implementing DAOs is a good *solution*.

Seek out resources that describe design patterns in terms of the problem and the motivation, rather than just the solution. The classic sources are the [GoF]("http://en.wikipedia.org/wiki/Design_Patterns:_Elements_of_Reusable_Object-Oriented_Software") book, or Sun's [Core J2EE Patterns]("http://java.sun.com/blueprints/corej2eepatterns/Patterns/index.html"). Then look for specific code examples if they are too conceptual.

---

### Post by nvteighen on 2010-12-15
As r-senior said, design patterns are *just* well-known solutions. 

Don't worry too much on them, really. Focus yourself on solving problems, always researching if there already exists a solution for it or part of it. Sometimes, the solution you find is one of these "patterns", sometimes it's not and sometimes you'll have to find your own solution. It's all about practice :)

(Of course, you can check some patterns you hear about and google them)

---

### Post by KdotJ on 2010-12-15
And occasionally, you will think up a solution for your problem and it turns out that your solution actually is one of these "patterns". There are some good books about patterns in OO, but I agree with the above replies. Don't get caught up thinking "I must use one of these patterns", just continue your way... You will pick up patterns as you progress

---

### Post by shadylookin on 2010-12-15
design patterns are abstracted solutions to problems that frequently occur. You don't pick and choose a design pattern since there's only one pattern that makes sense for a problem(assuming your problem can even be solved with a design pattern). 

you really just have to keep designing and reviewing patterns until you're able to come to a problem and realize that using design pattern X is what you need to do.

---

