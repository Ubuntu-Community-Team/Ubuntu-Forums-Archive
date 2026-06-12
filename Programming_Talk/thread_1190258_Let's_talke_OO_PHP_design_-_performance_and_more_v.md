---
title: "Let's talke OO PHP design - performance and more vs. procedural call"
date: 2009-06-17
forum: Programming Talk
---

### Post by akvino on 2009-06-17
I am in dilemma, what is the OO PHP way?

I am trying to understand if design should compliment the rules of:

case One:
1 USER/ 1 SESSION/ 1 OBJECT on need to use basis instantiated on user call / new objects per a user.. To expand on this thought - 100 users = 100 objects 

case Two: 
MANY USERS use 1 OBJECT for it's functionality needs / the object is instantiated upon application start and is life independent on user session - usually these objects are functional objects providing application functions (example quick_forms, PDO)/ other half of the objects are on need to use basis and are instantiated upon the user call and go by the 1 user = 1 object instantiation rule

case Three:
Many USERS use only 1 object of each kind, even if the object is instantiated on user need and not when application starts up.

case Four:
Maybe we need to keep procedural calls in some occasions, such as one user per one object instantiation, vs. many users one object instantiation.

My questions - what is correct way to program keeping in mind performance aspects of the application? What is the impact of 1 user per 1 object methodology on memory allocation, cpu, etc.. ?

Please keep in mind I am new to PHP so I haven't had a chance to visit Zend Framework in more detail, maybe in the future...:popcorn:

---

### Post by Reiger on 2009-06-17
Think about what your application does. What steps does it take. What steps depend on context.

For instance if I have a script that, say, outputs a list of items in a directory I am not going to make that an object. What's the point after all? A function will do just fine.

If I am implementing `something that queries something else' I am going to conjure some Object to hold for instance template queries that are closer to what `something else' can work with combined with a compile method that fills in a given template, combined with a query method that interfaces with `something else'.

OOP overhead is incurred from having OOP provisions built into the language itself, more so than from deciding to use an Object instead of functions. Although if your design leads you to a singleton pattern or any of that global-in-disguise mess then you may very well want to be honest about it and go for functions there.

---

### Post by akvino on 2009-06-18
My main concern is how efficient is PHP when multiple users are using single object instances vs. each user having it's own designated object instance. More objects have to make system less responsive, but by how much?

---

### Post by simeon87 on 2009-06-18
Do you have many users? Readable and maintainable code is preferable over fast but less-than-ideal code. I doubt object creation will turn out to be the bottleneck of your website; just choose the clearest option, see if it works and only rewrite it if it turns out to be too slow.

---

### Post by akvino on 2009-06-18
> **simeon87 said:**
> Do you have many users? Readable and maintainable code is preferable over fast but less-than-ideal code. I doubt object creation will turn out to be the bottleneck of your website; just choose the clearest option, see if it works and only rewrite it if it turns out to be too slow.

That is exactly what I am trying to get down to, there has to be guidelines for writing or implementing OOPHP the proper way, standardization in other words. I am not familiar enough with Zend to dive into it more, but I would assume some of the OO principles would translate to PHP OOP best practices.

---

