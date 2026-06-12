---
title: "what is the PHP???"
date: 2011-06-19
forum: Programming Talk
---

### Post by hockey97 on 2011-06-19
Hi, I just am curious to know exactly what PHP is. 
I know it's  a server sided programming lango. I would like to know what programming language was it programmed with??

Also would PHP be defined as a CGI program? I know it's a programming language but I would think it's a CGI since it's a server sided programming language so am I totally off basis with this thought. If so would CGI be a server sided programming lango? I know CGI stands for common gateway interface and mainly refereed to websites or servers in general. 

I notice to have php running on your server mainly apache you need to install a module and have php installed on your computer/server system itself.

Just would like to know if I were to make my own server sided programming language would I be making a cgi program??

I don't plan to make my own stuff... just would like to learn more about the subject and topic to better understand How PHP works inside... or under the hood.

---

### Post by simeon87 on 2011-06-19
> **hockey97 said:**
> Hi, I just am curious to know exactly what PHP is. 
I know it's  a server sided programming lango. I would like to know what programming language was it programmed with??

Not sure, I think it has been implemented in C as a module for Apache.

> **hockey97 said:**
> Also would PHP be defined as a CGI program? I know it's a programming language but I would think it's a CGI since it's a server sided programming language so am I totally off basis with this thought. If so would CGI be a server sided programming lango? I know CGI stands for common gateway interface and mainly refereed to websites or servers in general.

It is possible to run PHP as CGI but that's not common. 

> **hockey97 said:**
> I notice to have php running on your server mainly apache you need to install a module and have php installed on your computer/server system itself.

Just would like to know if I were to make my own server sided programming language would I be making a cgi program??

No, although technically you could make a CGI program that parses and executes your own server-side programming language.

---

### Post by hockey97 on 2011-06-19
So php is coded in C and  so is the module  for apache?

So lets say I plan to make my own server sided programming language. Would I just write it all in C or C++ and then write a module for apache and many other web servers? 

So I won't be using cgi at all?? In order to get my language to work with many servers? 

I am just curious on how one would make a server sided programming language. Understanding this will also help me understand how php works under the hood.

---

### Post by simeon87 on 2011-06-19
> **hockey97 said:**
> So php is coded in C and  so is the module  for apache?

So lets say I plan to make my own server sided programming language. Would I just write it all in C or C++ and then write a module for apache and many other web servers? 

So I won't be using cgi at all?? In order to get my language to work with many servers? 

I am just curious on how one would make a server sided programming language. Understanding this will also help me understand how php works under the hood.

In that case you should study mod_php, I think it's written in C and utilized in Apache as a shared object library (.so). So yes, you'd write your server-side language module in C which can read code written in your language. The module then does whatever it needs to do to create the webpage output.

You can do it as CGI but that'll be slower.

I must say I haven't looked into this but copying the way PHP did it seems to be the way to go.

---

### Post by hockey97 on 2011-06-19
ok thanks, I just looked at a wiki : [http://en.wikipedia.org/wiki/PHP](http://en.wikipedia.org/wiki/PHP)

It says that they created a cgi program. The cgi program was programmed by Rasmus Lerdorf.

so, I am kinda still confused as to why they said they made a cgi program for php. Maybe it was in the past.. not sure.

But thanks anyways. I will look more into the subject. Just would like to know exactly how one makes a server sided programming language.

---

### Post by simeon87 on 2011-06-19
> **hockey97 said:**
> ok thanks, I just looked at a wiki : [http://en.wikipedia.org/wiki/PHP](http://en.wikipedia.org/wiki/PHP)

It says that they created a cgi program. The cgi program was programmed by Rasmus Lerdorf.

so, I am kinda still confused as to why they said they made a cgi program for php. Maybe it was in the past.. not sure.

But thanks anyways. I will look more into the subject. Just would like to know exactly how one makes a server sided programming language.

You can write PHP in CGI but it's just slow. That's why many websites now run Apache with mod_php which is faster than going through the whole CGI thing upon each request.

---

