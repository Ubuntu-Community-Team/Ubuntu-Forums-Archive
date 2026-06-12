---
title: "Parsing POST results in PSP"
date: 2008-03-05
forum: Programming Talk
---

### Post by Majorix on 2008-03-05
Imagine someone uses my website coded in Python Server Pages and he submits, say his age, with the POST method.

In the next page, how do I tell him "You are XX years old"? ie. how do I parse the results of a POST in PSP?

In PHP there is an array of the variables sent, and you can subscript it with the name of the form variable.

I have looked around, but I couldn't yet find how to do this in PSP. I have found a way to do it with the cgi, but I don't even know what a cgi is, or how I can use it on the web.

Please help me in any way you can. Thanks a lot!
Maj-

---

### Post by pmasiar on 2008-03-05
Why you want to use PSP? It is such unclean way - almost as bad as PHP. If you are beginner Python web app developer, follow Guido's pronouncement and use Django instead.

---

### Post by Majorix on 2008-03-05
You see, I actually don't know anything about web development. I needed this for a project for a game I play, and I thought PSP was the most commonly used framework.

After doing a little research, I have come to the conclusion that Django is much wider used. So I guess I will be switching to Django. I hadn't started the project yet anyways, so I don't have anything to lose.

I am installing it in the background. Thanks for the recommendation :)

---

### Post by Smygis on 2008-03-05
Setting up Python CGI in lighttpd is super easy. And using it is awsome. My problem with Django is that you have to do a weeks worth of configuring and lerning of the different things in it before you start doing stuff that slightly resembles something that might end up on a website.

I gave up on Django after i started reading the tutorial. Turbogears just worked in comparison.

---

### Post by pmasiar on 2008-03-05
I also prefer TurboGears :-) 

You can write very simple web app using plain cgi module and plain python web server: [http://learnpython.pbwiki.com/WebApplication](http://learnpython.pbwiki.com/WebApplication)

---

