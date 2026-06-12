---
title: "Web page hits-Counter?"
date: 2006-02-27
forum: Programming Talk
---

### Post by Begatelles on 2006-02-27
Guys, i want to write a hits-counter code and use it for a web page. 

There's tons of free products out there, but i want to try and reinvent the wheel somehow. :)

Can anyone help please? :)

Thanks in advance.:cool:

---

### Post by andrewsawyer on 2006-02-27
Are you wanting to do this just for your own site, or are you planning on setting it up as a business?

statcounter.com has loads of functionality.  You might want to look at what they do, and extend on it perhaps?

---

### Post by Begatelles on 2006-02-27
Thanks for your response!

Basically it's just some web-page i'm trying to set up with some articles, and i want a counter on it. I don't know if that can be done with plain HTML or whether i have to embed some Java application on it. The reason i want to experiment is cause i'm doing some java programming, and i thought something like that would be a good practice. Perhaps i'm wrong and it's all html?

---

### Post by andrewsawyer on 2006-02-28
I'm not sure that you'd need Java for it.  You can do it with javascript, and I know you can also do it with php.  I assume you can do it with asp too, but I'm not 100%.

Just be aware that if you do it with Java, it may not pick up anyone viewing the site that doesn't have java installed/setup/running.  Not 100%, but I'd think it would work like that.

---

### Post by gord on 2006-02-28
all you need is some way of storing a number on the server (database, just a file, whatever) and something that increases that number by 1 everytime a new session to the website is created (by session i meen a person navigating the site, you don't want the counter being increased on each page click because thats just silly). 

im not sure you can do it with js or java without some kind of database or server-side code, unless you use one of those external sites that count for you.

---

### Post by catnappist on 2007-08-10
I know this is old, but I just wanted to thank andrewsawyer for that advice about statcounter.com.  Much appreciated!

---

