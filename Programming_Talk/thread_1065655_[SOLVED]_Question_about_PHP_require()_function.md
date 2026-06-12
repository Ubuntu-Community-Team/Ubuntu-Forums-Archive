---
title: "[SOLVED] Question about PHP require() function"
date: 2009-02-10
forum: Programming Talk
---

### Post by Sprax on 2009-02-10
I'm including a page using the require() function (an authentication script) and I need to return information to the page the require function was called from. How would I go about doing this? I don't want to use global variables because apparently they tend to be disabled on most web servers.

I'm thinking it could be done using the post method. But how do I know which page require was sent from? 

So something like this:
> <form method=post action=X>
Except X would depend on which page called the function

Thanks!

---

### Post by Sprax on 2009-02-10
And as usual I figure it out right when I make the post...

define a return value!

> return $X;

---

