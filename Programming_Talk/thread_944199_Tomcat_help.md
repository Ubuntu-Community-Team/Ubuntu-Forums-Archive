---
title: "Tomcat help"
date: 2008-10-11
forum: Programming Talk
---

### Post by gjj391 on 2008-10-11
Needing some help on deploying a war with tomcat (the app is the railo cfml engine).

I deployed a war through the manager and as long as my files are on the root of the deployed directory they will run, but but when I add a child directory... when it comes to pointing my browser to it, it is not invoking my classes i guess.

Not much of a java guy so im not quite sure If I should be doing something special.

---

### Post by jespdj on 2008-10-11
Which version of Tomcat are you using? What are you doing exactly (what are you deploying and how, and what URL are you typing into your browser) and what is the exact error message that you get?

You need to be as specific as possible, otherwise it's difficult to help you with the problem.

---

### Post by gjj391 on 2008-10-12
I am running tomcat6, and i am deploying a war app. It seems that it works fine with child directory just fine until i hook up mod_jk to forward my apache request on port 80 over to tomcat on 8080.

so when it is myapp.com:8080/parent/child/ ... this works fine.

but when mod_jk listens ( jkmount /* ) myapp.com/parent/child/ ... this will return a 404 .

I am trying to deploy the railo coldfusion engine.

---

