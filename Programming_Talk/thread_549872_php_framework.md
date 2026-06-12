---
title: "php framework"
date: 2007-09-13
forum: Programming Talk
---

### Post by md5hash on 2007-09-13
can you recommend easy to use php framework.

---

### Post by loell on 2007-09-13
the one that made the buzz on PHP, when RoR was really storming the webframework field.

was [http://www.symfony-project.com/]("http://www.symfony-project.com/")

but i've heard better things on cakephp too :)

---

### Post by md5hash on 2007-09-13
> **loell said:**
> the one that made the buzz on PHP, when RoR was really storming the webframework field.

was [http://www.symfony-project.com/]("http://www.symfony-project.com/")

i tried symfony before and it very cool lots of features but i havent used it yet in one of my projects.i think symfony is for a advanced php programmer.

---

### Post by loell on 2007-09-13
hehehe, i am pro django btw ;)

i've heard askeet being not so intuitive to learn, :-k

---

### Post by md5hash on 2007-09-13
youre right.. do you have a guide in creating simple MVC framework

---

### Post by loell on 2007-09-13
no, i don't have :( , creating a MVC framework requires a mystic knowledge of a programming language where your framework is base.   :mrgreen:

---

### Post by md5hash on 2007-09-13
wow mytic knowledge.. i think i should stick with symfony

---

### Post by loell on 2007-09-13
sorry, would you like to see a web app samples or would you like to know how to build a framework?
cause a web framework is entirely a different thing from a web application development. creating things like symfony and cakephp is quite difficult and often done not by a single person alone.

---

### Post by md5hash on 2007-09-13
if possible i need to create my own simple mvc

---

### Post by pmasiar on 2007-09-13
> **md5hash said:**
> if possible i need to create my own simple mvc

it depends on value of "simple" :-)

I know Python, not PHP. BTW Python more naturally leads you to MVC, because mixing code and presentation looks ugly (like native PHP code by beginner :-) ) so you naturally want to do it differently - and doing it differently and right in Python looks clear and neat.

- one of very "simple" frameworks (which does very little, but does not stand in your way doing it your way is Pylons. But you need to know what to do.
- Django guides you a lot, and there is one way to do it, and it works in 80% of cases OK enough, so it is "simple" to start and finish.
- Turbogears is framework (version 2.0) will be on top of Pylons) which makes it "simple" to use different components as you prefer: different templating engines, different ORM, etc.
- web.py is "simple" too: just one single module.
etc.

So it depends what kind of "simple" you want.

And not, it is not "simple" to create a framework. You can automate only something you understand very, very well. Both language and problem area. Most framework were extracted from code implementing couple of systems. Only after doing it five times you know how to do it right. :-)

---

