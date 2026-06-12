---
title: "eclipse not finding C++ library"
date: 2008-10-26
forum: Programming Talk
---

### Post by dpj23 on 2008-10-26
I upgraded to 8.04...  I use eclipse to do some c++ programming...  However, when I try and create a managed c++ project... eclipse can't find the library...  

I know that they are in the /usr/include directory... so I can change the pathways...

But I would like to just configure eclipse to do so and not have to worry about putting this in...

---

### Post by dribeas on 2008-10-26
> **dpj23 said:**
> I upgraded to 8.04...  I use eclipse to do some c++ programming...  However, when I try and create a managed c++ project... eclipse can't find the library...  

I know that they are in the /usr/include directory... so I can change the pathways...

But I would like to just configure eclipse to do so and not have to worry about putting this in...

Your description of the problem is quite vague. It is hard to provide advice without knowing what the problem is, so I will go ahead with the basics: read the stickies, install build-essential, install eclipse-cdt.

And then, ask again with some more info on what the problem really is, the error messages you get, what is the library that eclipse can't find...

---

### Post by dpj23 on 2008-10-26
O.K., here is the problem...

When for example I want to create a managed c++ project...  none of the headers files are found... thus nothing will compile...

---

### Post by dpj23 on 2008-10-26
So, I guess I should ask how I can create a library folder and direct eclipse to use it... I sure it is in the preferences somewhere... however, I have yet to find a configuration...

---

### Post by jespdj on 2008-10-27
Did you install the package **build-essential**?
```
sudo apt-get install build-essential
```

---

### Post by dpj23 on 2008-10-27
You know I forgot to do this... once I read your post...  I knew what was wrong... 

Thank you for your post...

---

