---
title: "Bash wget help?"
date: 2010-07-22
forum: Programming Talk
---

### Post by programminglinguist on 2010-07-22
```
#!/bin/bash
wget -F -B -i -r -p -e robots=off -A .png,.jpg --no-directories http://en.wikipedia.org/wiki/Rome
```

My goal is to download all .png and .jpg files from the wikipedidia rome website (it's just an example website) w/o directories and asap. 

I am coming across A LOT of trouble and the code really isn't making sense to me. But somehow this combination of options worked for wget. I read up on the manual of wget and didn't even get close to a 50% understanding of what I'm doing but, it kinda works.

I ran this script inside a folder and a whole buncha png and jpg files started downloading. Sounds good right? I notice that a lot of them have a weird thumbnail, all of them similar and when i try to open the images I see this error message 

```
Error interpreting JPEG image file (Not a JPEG file: starts with 0x3c 0x21)
```

which is weird because it clearly says in the properties that the image IS in fact a JPEG. The fileszie isn't suspicious either. 40kb. That sounds like a jpeg to me.


Any help to get this to work?

---

### Post by ssam on 2010-07-22
0x3c 0x21 is "<!" in ascii. looks like you have actually received a an html page.

try viewing one of the files with less or cat (or a text editor).

it may be a page asking that you don't mass download content. if so it maybe possible to trick the web server into think you are a normal browser, by changing the user agent, and having a random delay.

the politest way to get data from wikipedia is to follow methods from 
[http://en.wikipedia.org/wiki/Wikipedia:Database_download](http://en.wikipedia.org/wiki/Wikipedia:Database_download)

---

### Post by programminglinguist on 2010-07-22
> **ssam said:**
> 0x3c 0x21 is "<!" in ascii. looks like you have actually received a an html page.

try viewing one of the files with less or cat (or a text editor).

it may be a page asking that you don't mass download content. if so it maybe possible to trick the web server into think you are a normal browser, by changing the user agent, and having a random delay.

the politest way to get data from wikipedia is to follow methods from 
[http://en.wikipedia.org/wiki/Wikipedia:Database_download](http://en.wikipedia.org/wiki/Wikipedia:Database_download)

haha I'm one step ahead of you on that one, I tried the useragent and random delay trick. Same results. 

So in the history of bash there hasn't been a script to do what I want? Really? I would think someone by now would have given me a smartass comment to check some site for my dumb question to be answered. Hmm well I'm disappointed.


Oh and here's an edit: AAAH! YOU'RE RIGHT. They ARE HTML files D:

Damn server tricked me.

---

