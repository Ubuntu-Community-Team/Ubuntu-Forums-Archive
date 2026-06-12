---
title: "A few noob questions"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by chris000001 on 2008-06-10
so im pretty much a noob to linux.

here is what im trying to accomplish, i want my ubuntu box to be my router, web server and file server.

should i get the server version or will the desktop version work.

secondly ive been playing with the desktop varriant trying to get a raid set up and ive failed everytime ive done it. i do not want to boot from a raid i just want to use the raid as a storage array, i will be booting from a 36gb raptor.

i used this as a guide for my raid [http://mywheel.net/blog/index.php/software-raid-in-ubuntu/](http://mywheel.net/blog/index.php/software-raid-in-ubuntu/) and it seemed to work the best till i got to 

"Add the new virtual disk entry to /etc/fstab (explaining how /etc/fstab works is out of the scope of this article) and do issue"

from there i found a bunch of info on what i should do but nothing worked.
i would appreciate it if someone could point me in the right direction on these 2 questions.

---

### Post by hyper_ch on 2008-06-10
Use a descriptive topic title and not a generic "noob here" or "need help". You know, most people posting here want to get some help and you should support those, that provide help by indicating what the problem is about in the title.

---

### Post by rockerphil on 2008-06-10
well as far as setting up a raid i'm sure if you do enough reading you'll find what you need (sorry, i've never set one up myself) but in answer to the 1st question a server install should be fine since you won't be using it to browse the web. so a server install will save on a lot of system resources. and personally i would install it with just the Ubuntu minimal CD that you can download here


[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)


then just install a command line interface. that should suffice for the purposes you intend to use the machine for, but if some application isn't installed that you need it's always an apt-get away. hope this information helps. much luck to you




Phil

---

### Post by wolfen69 on 2008-06-10
> **hyper_ch said:**
> Use a descriptive topic title and not a generic "noob here" or "need help". You know, most people posting here want to get some help and you should support those, that provide help by indicating what the problem is about in the title.

it was pretty clear what he was asking.

---

### Post by Xiong Chiamiov on 2008-06-10
> **wolfen69 said:**
> it was pretty clear what he was asking.
But only once you clicked on the thread.  Considering that most of us have experience in only certain areas, that can waste time on our part and resources for the server.

@chris000001:
While you most certainly can do those things, I'm not sure if I'd recommend them.  Running a server that's open to the web can be a dangerous thing unless you know what you're doing.  Ubuntu server will better suit your needs, but comes without a GUI preinstalled.  If you've accepted the fact that you will be doing quite a bit of learning, though, they we'd be glad to help you.  Just make sure you know what you're getting into.

A very easy way to install a webserver is by using [XAMPP]("http://ubuntuforums.org/showthread.php?t=223410&highlight=xampp").  If you do so, however, make sure that you fix the security flaws (listed at the end of that post) that are present by default, since XAMPP is designed for local web development purposes.  Of course, you could also just install Apache and its associated packages [the proper way]("https://help.ubuntu.com/community/ApacheMySQLPHP") too.

---

### Post by chris000001 on 2008-06-10
> **rockerphil said:**
> well as far as setting up a raid i'm sure if you do enough reading you'll find what you need (sorry, i've never set one up myself) but in answer to the 1st question a server install should be fine since you won't be using it to browse the web. so a server install will save on a lot of system resources. and personally i would install it with just the Ubuntu minimal CD that you can download here

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

then just install a command line interface. that should suffice for the purposes you intend to use the machine for, but if some application isn't installed that you need it's always an apt-get away. hope this information helps. much luck to you

Phil

Thanks for the advise about the server install.

about the raid i have searched soooo incredibly much about the raid thing, its seriously a project that ive been working on for a month, the site that i listed earlier seems to be the easiest to follow except for the point where it leave me hanging.

> **Xiong Chiamiov said:**
> But only once you clicked on the thread.  Considering that most of us have experience in only certain areas, that can waste time on our part and resources for the server.

@chris000001:
While you most certainly can do those things, I'm not sure if I'd recommend them.  Running a server that's open to the web can be a dangerous thing unless you know what you're doing.  Ubuntu server will better suit your needs, but comes without a GUI preinstalled.  If you've accepted the fact that you will be doing quite a bit of learning, though, they we'd be glad to help you.  Just make sure you know what you're getting into.

A very easy way to install a webserver is by using [XAMPP]("http://ubuntuforums.org/showthread.php?t=223410&highlight=xampp").  If you do so, however, make sure that you fix the security flaws (listed at the end of that post) that are present by default, since XAMPP is designed for local web development purposes.  Of course, you could also just install Apache and its associated packages [the proper way]("https://help.ubuntu.com/community/ApacheMySQLPHP") too.

Also thanks for the advise, i had no idea ubuntu server didnt come with a gui, altho most of the time ive spent in ubuntu has been in the terminal or terminal through ssh on my laptop, i feel very comfortable with it, i dont completely feel comfortable about going completely command line.

as for it being a server open to the web and not being secure is not really a huge concern, im not going to keep anything private have it as my only copy. when i say webserver, i dont really want to host a webpage, but just so i can access certain files.


> **hyper_ch said:**
> Use a descriptive topic title and not a generic "noob here" or "need help". You know, most people posting here want to get some help and you should support those, that provide help by indicating what the problem is about in the title.

As for your post, ive noticed around the forum that you post similar things in threads that have a similar title, while i understand what you are saying, you provided me, or the others with similar titles absolutly no imformation to their question which makes your post entirely pointless, i was exceited to see 4 replys in so little time, just to be disappointed by your post. thanks for the advise on the titles, i will definatly consider it next time i post, but the least you could have done was provided some insight to my own and others questions.

---

### Post by hyper_ch on 2008-06-10
> **chris000001 said:**
> As for your post, ive noticed around the forum that you post similar things in threads that have a similar title, while i understand what you are saying, you provided me, or the others with similar titles absolutly no imformation to their question which makes your post entirely pointless, i was exceited to see 4 replys in so little time, just to be disappointed by your post. thanks for the advise on the titles, i will definatly consider it next time i post, but the least you could have done was provided some insight to my own and others questions.
Have you considered that I have no answer to your questions and hence you just tricked me into reading your thread and wasting my time instead of using my time to help others? I guess not.

---

### Post by chris000001 on 2008-06-10
> **hyper_ch said:**
> Have you considered that I have no answer to your questions and hence you just tricked me into reading your thread and wasting my time instead of using my time to help others? I guess not.

I did consider this, and from personal experence, as i dont mind reading other ppls issues, but if i dont have any advise for them or if i dont have anything constructive to say, i dont reply and move on with my life.

obviously since you think that the title of my thread is a trick you would avoid it and others seeing as how you post the same comment in every one.

---

### Post by hyper_ch on 2008-06-10
> **chris000001 said:**
> I did consider this, and from personal experence, as i dont mind reading other ppls issues
Neither do I ;)

> **chris000001 said:**
> but if i dont have any advise for them or if i dont have anything constructive to say, i dont reply and move on with my life.
but I did have somethign constructive to say ;)

> **chris000001 said:**
> obviously since you think that the title of my thread is a trick you would avoid it and others seeing as how you post the same comment in every one.
You see, all people here are volunteers, right? And we spend time helping. So if there is e.g. a "noob here - need help" topic and I read it only to to find out that he is asking about something I have no clue e.g. iPhone then my time was wasted. If this person had written "iPhone" in the thread title I could just have skipped it and helped someone else.

Not using an descriptive thread title is IMHO just pure laziness and it wastes time of those that do want to help.

---

### Post by teddyearp on 2008-06-10
Hmmm. . . interesting, I posted a question with a very descriptive title and only got one reply, maybe next time I'll waste more time to get more responses . . . .  hehehe
:lolflag:

---

