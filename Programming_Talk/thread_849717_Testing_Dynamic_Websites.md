---
title: "Testing Dynamic Websites"
date: 2008-07-04
forum: Programming Talk
---

### Post by era86 on 2008-07-04
Greetings!

I was wondering how most of you locally test your websites.  For example, I am working on a website with some python cgis and I want to test drive them on my laptop.  Should I just install an apache server on my laptop and drive them from there?  Is there any other solution?

Let me know.  Thanks in advance!

---

### Post by soapytheclown on 2008-07-04
i just have a test server but testing on yr laptop is just as good i guess

---

### Post by LaRoza on 2008-07-04
> **era86 said:**
> Greetings!

I was wondering how most of you locally test your websites.  For example, I am working on a website with some python cgis and I want to test drive them on my laptop.  Should I just install an apache server on my laptop and drive them from there?  Is there any other solution?

Let me know.  Thanks in advance!

Python? See pmasiar's wiki. There is an easy solution for you :-)

---

### Post by pmasiar on 2008-07-05
There are simpler servers for local testing that apache. CherryPy is a good one. And you can write your own server in 7 lines of Python. :-)

But consider upgrading from CGI, if your application is not just a trivial training task. Both leading web app frameworks, Django and Turbogears, come with developer's server, and many other goodies. One of them, both will help you to write your code in Model-View-Controller pattern, much better for maintenance. I use TG: it will create for you empty project with working "hello world" page, which you can modify and enhance, and I bet that Django (recommended for Python/CGI newbies) is as simple (or more) as TG.

Or, did you asked for testing your websites programmatically, by a script? There are [many many interesting ways](http://www.softwareqatest.com/qatweb1.html#FUNC) to do it. [Selenium](http://selenium.openqa.org/) and [twill](http://www.onlamp.com/pub/a/python/2005/11/03/twill.html) are considered good ones (and popular in Python community), but there are more.

---

### Post by era86 on 2008-07-05
Thanks pmasiar!  I will look into the links you provided.  I basically wrote some websites in xhtml and was trying to test out a form that changes some information on the page.  Simple stuff.  Thanks again!

---

