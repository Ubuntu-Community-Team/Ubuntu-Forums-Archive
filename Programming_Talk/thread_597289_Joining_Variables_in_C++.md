---
title: "Joining Variables in C++"
date: 2007-10-30
forum: Programming Talk
---

### Post by startherepodcast on 2007-10-30
Hey,

I'm am just starting out in c++ and I have come across a problem  to which I have not been able to find an answer. I need to join to variables together so that I can have part of a string in quotes and then add to it a variable.

Thanks..

---

### Post by aks44 on 2007-10-30
Care to elaborate?

What exactly are you trying to do? Please give examples, as I find your question pretty confusing/confused.

---

### Post by startherepodcast on 2007-10-30
What I am trying to do is pass a command to curl via system() to post to a php script.

```
string curl = "curl -F var1=";
string var1 = "Hello World";

system(Joint_Variable_Goes_Here)
```

How Could I Join these two strings together so that I could execute the command.

Thanks

---

### Post by aks44 on 2007-10-30
If I understood correctly the "*so that I can have part of a string in quotes*" part, here it is:

```
std::string curl = "curl -F var1=";
std::string var1 = "Hello world";

std::string result = curl + "\"" + var1 + "\"";

system(result.c_str());
```

The above code assumes that you don't have any double-quotes in var1. If you may have some, you'll have to escape them beforehand.

---

### Post by startherepodcast on 2007-10-30
Thanks that seems to work great.  Could you also Please tell me where I can find some more tutorials on c++ ,and some example code, if you know any.

Thanks...

---

### Post by aks44 on 2007-10-30
> **startherepodcast said:**
> Twhere I can find some more tutorials on c++ ,and some example code, if you know any.

You could try Bruce Eckel's free [Thinking in C++]("http://mindview.net/Books/TICPP/ThinkingInCPP2e.html") book. It's not for complete newbie programmers, but it teaches correct C++ AFAIK.

I never read it though, those kind of books tend to bore me to death. :oops:

---

### Post by LaRoza on 2007-10-30
My wiki has many references on C++. You might find what you want in the string header.

---

### Post by startherepodcast on 2007-10-30
Thanks for those suggestions. I'll check them out and hopefully improve my skills a bit in the way of C++.

Thanks Again For All Your Help

---

