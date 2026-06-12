---
title: "Javascript to view Gmail"
date: 2010-10-13
forum: Programming Talk
---

### Post by aktiwers on 2010-10-13
I want to create a javascript that shows either my unreaden mails or a list of them.

I simply want to use the RSS feed on Gmail and get the info this way.

I somehow can't grasp how to do this. I wan't it to autologin so i use this url

[https://USERNAME:PASSWORD@gmail.google.com/gmail/feed/atom](https://USERNAME:PASSWORD@gmail.google.com/gmail/feed/atom)

But it gives me an: "Unauthorized Error 401"..

Any ideas why this happends or any other way to do this(using only javascript).

---

### Post by DanielWaterworth on 2010-10-13
is this javascript on an external domain or javascript run in the browser (ie like greasemonkey). If it's the former, what you're essentially trying to do is a csrf attack and hence you're not going to be able to.

I also wouldn't have thought you'd be able to access gmail via http auth either.

---

### Post by aktiwers on 2010-10-13
Thanks for the reply DanielWaterwoth.

I'm basically trying to create a small "start page" like iGoogle, where I have all my favorite stuff. I see that Google provides RSS feeds and wanted to use that.

So yes I'm trying to run my javascript in the browser. 
On iGoogle there is a widget that does exactly what I want:
[http://www.google.dk/ig/directory?url=www.google.com/ig/modules/builtin_gmail.xml](http://www.google.dk/ig/directory?url=www.google.com/ig/modules/builtin_gmail.xml)

It would be okay if I needed to create a login field first. 

But I already get stuck at the point described in #1 post.

Maybe I am trying to achieve this in a wrong way?

---

### Post by aktiwers on 2010-10-14
Bumb

---

### Post by DanielWaterworth on 2010-10-14
Can you not just create an iframe with the iGoogle widget in it?

---

