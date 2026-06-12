---
title: "[C++] parsing HTML forms"
date: 2009-05-18
forum: Programming Talk
---

### Post by Pyro.699 on 2009-05-18
Hello All,

I am kind of new to the C++ language although i do understand the basics. So please bare with me if something i say is a little off.

Anyways, I've been programming in Python and realized its limitations for secure distribution. One of the methods that i have been using for Python is called ClientForm ([link here](http://wwwsearch.sourceforge.net/ClientForm/)). Its basic function is to open web pages (using urllib2) and phrase the forms allowing you to fill out those forms and submit the data to the webserver.

Thanks
~Cody Woolaver

---

### Post by slavik on 2009-05-18
umm, is there a question?

---

### Post by Pyro.699 on 2009-05-18
Is there an equivalent in C++ for parsing HTML forms?

Thanks
~Cody Woolaver

---

### Post by Reiger on 2009-05-18
There is libxml which is GNOME XML library that can be used to supply a 'backend' to deliver a DOM API. (PHP uses it for its DOM API for instance.) I imagine that you could use that one?

Link: [http://xmlsoft.org/html/index.html](http://xmlsoft.org/html/index.html)

---

### Post by Pyro.699 on 2009-05-18
I remember a while back hearing something about being able to include python modules in C++ programs, is this true? Because if it is, it would be much simpler if i could just import the python file.

---

