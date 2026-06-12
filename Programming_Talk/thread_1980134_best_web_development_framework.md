---
title: "best web development framework?"
date: 2012-05-14
forum: Programming Talk
---

### Post by F.G. on 2012-05-14
Hi folks,

i'm about to embark on a side project with a friend of mine, and were going to need a decent, scalable website with a db, on the cheap. currently the plan is to use postgres for the database and tomcat with spring and java for the website, and git for the vcs. another option, which i quite like is the idea of is using ruby on rails. i suppose groovy on grails could be another option (although i don't really like groovy).

so my question is what are you guys opinions on this? The website needs to bee potentially scalable and able to use things like stored procedures, i'm happy to learn something new and open to suggestion.

thanks for any suggestions.

ps i guess cheap web hosting is also something were going to need (currently thinking of amazon with ubuntu).

---

### Post by PaulM1985 on 2012-05-14
I have had to do some work with web development and databases recently.  I originally wanted to use Java, but it was really difficult to find somewhere that allowed me to run servlets.  Most hosts that allow Java seem to be either expensive or have very little support.

In the end I decided to learn php and use that.  A lot of web hosts support MySQL and php and provide a service for quite cheap.  I am with these: [http://www.jomongee.co.uk/web_hosting.html](http://www.jomongee.co.uk/web_hosting.html).  GoDaddy seem cheap aswell.

I don't know exactly what you want to do, but this is working for me.

Paul

---

### Post by F.G. on 2012-05-14
hi PaulM1985,
thanks for your reply, i think personally i probably want to steer clear of mysql though. i made a mysql db a while ago and it seemed quite limited (although it may be better now). regarding php my accomplice is a php hater, so i guess it is probably off the menu too, i have never used it, so don't really have an opinion.  unfortunately where i work all their tools are proprietary and most are 'in house',  which is why i want to learn something new and gain some experience with a open framework. regarding our server, it will have to have fairly complete access and allow us to install stuff like java.

the plan is to build a niche interest user generated website for a specific user group (hence the need for scalability, in case it becomes popular, as well as purely aesthetic reasons). but the question is, having the time to learn a new skill, what to learn?

---

### Post by PaulM1985 on 2012-05-14
I would recommend reading about Model-View-Controller.  Here is a quick link to wikipedia's entry on it: [http://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller](http://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller)

If you want to use Java, you are going to want to learn about Servlets, JSP and Enterprise Javabeans (and in particular the Persistence API).

Paul

---

