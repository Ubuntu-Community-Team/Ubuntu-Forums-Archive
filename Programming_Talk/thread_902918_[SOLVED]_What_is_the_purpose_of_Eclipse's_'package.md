---
title: "[SOLVED] What is the purpose of Eclipse's 'package' hierarchy"
date: 2008-08-27
forum: Programming Talk
---

### Post by meanburrito920 on 2008-08-27
I recently started learning Java, and I am using Eclipse as my IDE. I have noticed that Eclipse likes for you to create 'packages' within your projects to store your code. This is also the case with NetBeans. However, other IDEs such as JCreator do not have such a feature. Code seems to compile/run fine no matter if it is in a package. Because of this, I started to wonder what the advantage or purpose of using packages is. Is it really such a bad thing to use the 'default package' option in Eclipse, as it warns against it? Maybe some of you Java aficionados might shed some light on the topic?

---

### Post by CptPicard on 2008-08-27
It's just general "Java bad manners" to use default package. The whole idea of packages is to provide namespace separation so that there are no clashes... which is an ideologically Good Thing :)

---

### Post by Tomosaur on 2008-08-27
Yeah - packages are a Java thing (well, a general coding convention really - in other languages they might just be called 'namespaces') rather than an Eclipse or Netbeans thing.

Let's say you have a class called 'Tree'. Now let's say you need to use a library from somebody else, and suppose that this library also has a class called 'Tree'. If packages / namespaces didn't exist, there'd be a whole lot of confusion about these two identically named, but completely different classes, right? Not least with the compiler itself!

Namespaces and packages allow you to say 'this Tree class belongs in this package' rather than just having everything in one single 'default' package / namespace.

Generally speaking packages and namespaces aren't such a big thing if your project is just a tiny app - but when you have lots of developers and lots of libraries thrown into the mix, they become VERY important. It's best to get into the habit of defining packages / namespaces as early as possible, because you will almost certainly need to use them in larger projects. They're not that complicated, and a quick Google should tell you all you need to know about them :)

---

### Post by meanburrito920 on 2008-08-27
...so different applications could technically fall under the same project, because they would be in different packages? Or would seperate packages under the same project be necissary only for projects of a large nature, where seperation between states, ie. MVC is necissary?

EDIT: Whoops, I started my post before Tomosaur posted. So my question is answered, thank you.

---

### Post by jespdj on 2008-08-28
For more information about packages in Java, see: [The Java Tutorial - Creating and Using Packages](http://java.sun.com/docs/books/tutorial/java/package/packages.html)

---

### Post by howlingmadhowie on 2008-08-28
packages allow you not to spend so much time with naming conventions. if this is a good thing or not is open to debate. certainly the java class and object visibility choices are complicated (public, private, protected and [standard]). i sometimes think the main point of an ide such as eclipse or netbeans is to tell you if something is visible or not. 

of course, if you can get the developers to agree on a naming convention, you shouldn't really need this. as a friend of mine once remarked, if you spend your time trying to work out how best to hide parts of your work from colleagues, you have much more serious problems than namespaces.

---

