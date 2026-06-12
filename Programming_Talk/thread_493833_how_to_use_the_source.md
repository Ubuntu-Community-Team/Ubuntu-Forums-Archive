---
title: "how to use the source?"
date: 2007-07-06
forum: Programming Talk
---

### Post by invictus on 2007-07-06
Hi

If I want to use the source code of the ubuntu components (gnome etc...), how should I get started if I want to get, modify (...this part I know), and compile/replace the existing components on my system? I know I could just download the source from the projects websites (gnome.org etc...) but then I may get another version than ubuntu is using. Its important for me to know that if somethings fail after I have compiled it is because of my code and not because some other events like that I have incorrect version that doesnt work.

I know C and C++ and just want to see if I can contribute...but first I need to know how I shall get started...

---

### Post by Tomosaur on 2007-07-06
> **invictus said:**
> Hi

If I want to use the source code of the ubuntu components (gnome etc...), how should I get started if I want to get, modify (...this part I know), and compile/replace the existing components on my system? I know I could just download the source from the projects websites (gnome.org etc...) but then I may get another version than ubuntu is using. Its important for me to know that if somethings fail after I have compiled it is because of my code and not because some other events like that I have incorrect version that doesnt work.

I know C and C++ and just want to see if I can contribute...but first I need to know how I shall get started...

You can download the source code for packages in the Ubuntu repositories (meaning you will get all of the modifications to that source which the Ubuntu developers have used):

```

sudo apt-get source <package name>

```

---

