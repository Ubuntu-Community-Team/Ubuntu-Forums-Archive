---
title: "Java web applications connecting to a database"
date: 2010-04-28
forum: Programming Talk
---

### Post by wotsit on 2010-04-28
I am struggling to find anything decent on how to do this.

I want to use tomcat and mysql or apache derby, and I would prefer not to do it in an IDE, because then I would just be clicking buttons and not knowing why.

Tutorials are either for tomcat 5.x or 4.x, and everything seems to be a bit outdated and 'fuzzy' - the amount of forum posts about people struggling with web apps and databases is unreal.

So how is it done? Could someone talk me through it or at least suggest some resources?

I already know a tiny amount of servlets and jsp stuff.

---

### Post by ju2wheels on 2010-04-28
You will need JDBC with the appropriate driver for the database.

---

### Post by CptPicard on 2010-04-29
The learning curve for Java web applications is nasty enough, I would suggest you simply use the IDE. You gain nothing by trying to hack it together using some self-written ant scripts, because as you've noticed, documentation is what it is, and you're just spending time pulling together the information you could get simply by clicking that button and looking at the kind of project that the IDE gives you.

There are various database connectivity libraries, but the underlying technology is JDBC as noted above... then there is all kinds of stuff built on top of that, such as Hibernate.

---

### Post by ja660k on 2010-04-29
download netbeans...
im usually against the whole IDE's but it will make life easier, 
it can handle any J2EE enterprise system you wish to develop. also there is great documentation on J2EE on the netbeans website...

but as both posts said, your going to need to use JDBC, or a framework on top of it.

---

### Post by dragos2 on 2010-04-29
You can try Hibernate but its not as easy as it looks.

There is Java Persistence API which may help if I remember well.

You can try to have a look at Glassfish but its 10x harder than in Tomcat and no free
documentation.

---

### Post by slavik on 2010-04-29
Tomcat should come with a sample datasource xml definition, copy and modify ... at least this is how Jboss is usually handled.

---

