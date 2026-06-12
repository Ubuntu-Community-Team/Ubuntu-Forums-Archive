---
title: "PHP Best Practices resource request (for the moderately proficient)"
date: 2009-08-13
forum: Programming Talk
---

### Post by bkann on 2009-08-13
Hi -

Here's some possibly useless background information.  I was introduced to PHP about eight years ago.  I did little with it for several years, but about three years ago I began to learn more about it and started working on some Web applications for fun in my spare time.  I was miserable for the first half of that time, but in the past 18 months or so I've started to really get the hang of it and I think my skills have advanced nicely.

My question is concerning how to hone in on some of the finer points of PHP (or writing code in general) and better conform to standards / best practices.  Does anyone know of a good resource that outlines some best practices for PHP code and demonstrates them simply?

For example, I've read that one should not echo/print from inside a function.  I've tried to avoid doing this, but nonetheless the advice seems vague.  What about printing from __Construct?  Or a fucntion that prints the results of another function?... things like this.

I look forward to seeing your input, and thanks in advance for anything you might be able to provide.

---

### Post by credobyte on 2009-08-13
Not sure about resources, however, why would you avoid echo/print in functions ? As an example, MySQL class and Error function - the easiest way is to add styling and text right into the function, not to make a function and check for it from another function/script.

---

### Post by s.fox on 2009-08-14
Hi,

You could look into using frameworks for your web development projects.  Of late I have been getting into [Cake]("http://en.wikipedia.org/wiki/CakePHP"),  but there are other frameworks :)

-Silver Fox

---

### Post by hessiess on 2009-08-14
Stick very closely to the MVC model, never mix display code with logic and use templating instead of the messy string concatenations that litter a lot of PHP code. Use a framework, eather write a custom one, or a readily available one like cakephp.

---

### Post by bkann on 2009-08-14
Thank you all.  I'll take a look into Cake.

As for the echoing from a function, the author argued that it's easier to debug if you echo the return from a function and not from inside the function itself.  While I didn't necessarily intend this post to be specifically about that, I thought the author's argument made a lot of sense, but again, there were some vague aspects of it.

Again, thanks, and any other feedback is welcome.

---

