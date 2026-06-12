---
title: "Ubuntu won't display RHTML files"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by mcbgun on 2008-06-28
Hey guys.

Does anyone know how to get Mozilla to display .rhtml files?

I know its nothing to do with mozilla but I cannot for the life of me get rhtml files to work!
 
I'm a total noob with ruby so forgive me if i'm being stupid. Obviously when I change the extension to .html instead of .rhtml it comes up fine. What does this mean!?! Have I not installed a certain packkage?

Tearing my hair out trying to follow a book on ecommerce with ruby on rails, so many problems!

Cheers guys

---

### Post by defrex on 2008-06-28
rhtml is a template markup for Ruby on Rails, if I'm not mistaken.

If so, you need to run the rails dev server and go to (i think) localhost:8080 in firefox. You don't ever open rhtml files except to edit them. They are simply template files rails uses to render the final html.

---

### Post by mcbgun on 2008-06-28
Thanks for your reply.

It seems like the rhtml file i'm supposed to create doesnt do anything! I put what was meant to go in my index.rhtml file into an index.html.erb file and it worked.

Doesn't bode well for the rest of the book if what I've done there impacts on everything else but hey.

Cheers anyway

---

### Post by benson2788 on 2009-02-17
rhtml is the old version of the rails html markup files.  Since rails 2.0 or 2.1, I forget which, they switched to .html.erb, instead.  What book is is that you are complaining about being out of date, out of curiousity?

---

