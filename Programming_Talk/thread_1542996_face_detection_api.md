---
title: "face detection api"
date: 2010-07-31
forum: Programming Talk
---

### Post by mess110 on 2010-07-31
Hello

First of all if this is not the correct place to post this please tell me. I looked in the forum topics and I consider this a development 'thingy' and I am asking for improvement ideas, opinions and feedback.

I made a frontal face detection api and it would be nice if I could get some feedback. I consider it in early development, but I am sure a lot of people could find this useful.

(would have helped me in the past)

Don't want to give a lot of details because I want people to form their own opinion and criticize me.

So if you have a few minutes to spare maybe you can drop a line or two :)

**[http://detection.myvhost.de/]("http://detection.myvhost.de/")**

Cheers!

(I can not stress this enough: delete this topic if you think it is inappropriate)

---

### Post by Åtta on 2010-07-31
It seems like a nice thing to have, but it's definitely not something that I would want as a web service. Wouldn't it be better to release it as a library?

---

### Post by mess110 on 2010-07-31
Thank you very much for your reply :) I was thinking it could be an alternative when a library with dependencies is not an option.

cheers

---

### Post by WitchCraft on 2010-07-31
It doesn't work for:
[IMG]http://www.russianbrides180.com/uploaded_images/hot-Russian-bride-780222.jpg[/IMG]

[http://www.russianbrides180.com/uploaded_images/hot-Russian-bride-780222.jpg](http://www.russianbrides180.com/uploaded_images/hot-Russian-bride-780222.jpg)

It says invalid url.

It doesn't work when one has sunglasses on, or when the face is not frontal.

But how do you do it anyway ?

---

### Post by mess110 on 2010-08-01
I just tested it with that URL and it detected her face.

you need to type in the full URL of the image. http:// included.

thank you for your reply :D

the idea is that the interface is just for orientation purposes anyway. To show visual data. The idea is to enabled face detection through http requests :)

---

### Post by hakermania on 2010-08-01
> **mess110 said:**
> I just tested it with that URL and it detected her face.

you need to type in the full URL of the image. http:// included.

thank you for your reply :D

the idea is that the interface is just for orientation purposes anyway. To show visual data. The idea is to enabled face detection through http requests :)

You could have made your api to add the http:// if it doesn't exist..!
That's an improvement!
Anyway nice app!

---

### Post by mess110 on 2010-08-01
already working on that :)

thank you. and keep them coming =)

---

### Post by Sub101 on 2010-08-01
What algorithms are you using?

---

### Post by mess110 on 2010-08-01
its adaboost frontal face detector using a tree instead of a cascade

---

