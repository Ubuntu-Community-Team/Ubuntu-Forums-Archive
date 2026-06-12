---
title: "Problem with IOstream reference in C++ in Ubuntu"
date: 2012-05-18
forum: Programming Talk
---

### Post by siavashm31 on 2012-05-18
Hey,

I recently Installed Turbo C++ according to this instruction [http://maitnoobsatwork.blogspot.com/2011/08/how-to-install-turbo-c-on-ubuntu-linux.html](http://maitnoobsatwork.blogspot.com/2011/08/how-to-install-turbo-c-on-ubuntu-linux.html)
Now the problem that I have it's IOstream reference is missing and I don't know how to fix it :(

Does anyone have any suggestion for this issue?

Cheers
Sia

---

### Post by kingtaurus on 2012-05-18
> **siavashm31 said:**
> Hey,

I recently Installed Turbo C++ according to this instruction [http://maitnoobsatwork.blogspot.com/2011/08/how-to-install-turbo-c-on-ubuntu-linux.html](http://maitnoobsatwork.blogspot.com/2011/08/how-to-install-turbo-c-on-ubuntu-linux.html)
Now the problem that I have it's IOstream reference is missing and I don't know how to fix it :(

Does anyone have any suggestion for this issue?

Cheers
Sia

Do you mean the header file for iostream? 
Are you including the iostream header before you make calls to std::cout?
Please remember to include std:: (the header iostream is contained within the namespace std)

Cheers,

---

### Post by siavashm31 on 2012-05-18
Hey, 

I do include the <iostream> header and then I use namespace std; and cout. but after I compile the code, there is an Error which says that it couldn't find <iostream> and std is an unknown code.

---

### Post by Zugzwang on 2012-05-19
> **siavashm31 said:**
> Hey, 

I do include the <iostream> header and then I use namespace std; and cout. but after I compile the code, there is an Error which says that it couldn't find <iostream> and std is an unknown code.

Try to include <iostream.h> instead (and copy&paste the error message next time), and just leave out the "std::". Note that Turbo C++ for DOS is really old and does not adhere to many C++ common practices established in the last ~15 years or so.

---

