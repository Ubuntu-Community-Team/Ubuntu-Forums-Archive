---
title: "PHP, redifining an existing class"
date: 2009-05-12
forum: Programming Talk
---

### Post by orlox on 2009-05-12
Hi. I am in a situation where I find myself in the need to redefine an existing class, cause the one included in the libraries of one of my servers is buggy and crashes. Is there a way to do this??

I just want to rewrite the class (I only need some basic functionality so this wouldt be so hard), and then ask php to redifine the existing class with that one.

The reason why I want to do it this way instead of modifyng directly the calls to that class, is because the code that uses the library is part of a database abstraction layer wich I dont want to modify each time I download a new version of it...

---

### Post by slavik on 2009-05-12
yes, you can. download the code, fix it and submit a patch.

---

### Post by orlox on 2009-05-12
Thats an alternative when the people that run the servers care to correct problems and issues, but I guess thats not my case...

PHP was compiled on this servers with the library I need disabled (it has a specific flag for that on the ./configure), but the classes are available though they function unproperly (dont know precisely why the classes are available given this circumstances).

My hosting service wont change a thing under the excuse that "It might negatively affect other websites hold on the same server".

So its not actually a solution to rewrite the code, since it doesnt seem to have any errors (it was compiled with an specific flag to disable it so I guess thats the reason it doesnt work), and also because the server manager refuses to change anything related to the servers configuration...so having a fix in the code wouldnt make any difference...

What i really need is a way to redefine the classes at runtime (though im not sure if this is even possible...)

PD: The library im trying to use is PDO which is used for database access, and the server was compiled with --disable-pdo and produces a completely blanck page when trying to use the query() method of this class.

---

