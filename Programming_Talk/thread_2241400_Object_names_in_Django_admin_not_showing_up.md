---
title: "Object names in Django admin not showing up"
date: 2014-08-25
forum: Programming Talk
---

### Post by sleepee on 2014-08-25
I'm new to Django, web development, and pretty much any kind of programming/development in general, so please take it easy on me if this is a dumb question.
I'm trying to get my feet wet and learn a little Django, but there's just one issue that is really bugging me.

In the Django admin site (1st attachment), I would like to see the name I've assigned to a Person object instead of "Person object."
The same thing happens when I pull up a Person object in the django shell (I could get a screenshot of that as well if needed.)
I thought the __unicode__ function I wrote in the models.py (2nd attachment) was supposed to solve this for me, but apparently it's not working.
I'm on Django 1.6.5, python 3.4.
This isn't really a big deal to me now since I don't have many objects, but I'm sure eventually this is going to be really important to solve since it would be easier to administer an app if i could give my objects actual names.  Any help with this would really be appreciated. Thanks.

---

### Post by bizhat on 2014-08-26
__unicode__ need to be changed to  __str__ when you use python 3.

Another django noob here :)

---

### Post by sleepee on 2014-08-26
> **bizhat said:**
> __unicode__ need to be changed to  __str__ when you use python 3.

Another django noob here :)

it worked!
and as soon as i saw that it worked i had to smile and chuckle at my noobness.  somehow i knew it had to be something that simple.  lol!
thanks  bizhat!

---

