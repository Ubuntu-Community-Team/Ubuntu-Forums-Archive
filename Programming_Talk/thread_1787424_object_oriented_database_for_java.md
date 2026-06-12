---
title: "object oriented database for java"
date: 2011-06-21
forum: Programming Talk
---

### Post by RobikShrestha on 2011-06-21
Which is the best object oriented database system for java?

---

### Post by r-senior on 2011-06-21
OODMBS haven't really caught on. Oracle introduced OO features about 10-12 years ago (which I assume are still there) but mainstream applications still tend to be RDBMS.

Much more common than OODBMS is the use of an Object-Relational Mapping layer. For Java, the most common solutions are EJB3/JPA or plain Hibernate. These layers allow you to persist object structures with the mapping layer handling translation from objects into relational form. Such layers have some traps for the unwary but can give excellent performance by using caching and write-behind.

You can use Hibernate without Spring but Spring and Hibernate is a powerful combination. The drudgery of writing data access code and managing database transactions is largely removed through templates. Implemented well it allows you to work with object structures and concentrate on your application rather than spending most of your time just shunting data around.

EJB3 is similar, with more of a focus on distributed systems - multiple nodes running the persistence logic local to distributed databases.

---

### Post by RobikShrestha on 2011-06-22
Thanks for the reply. I will look into those systems.

---

