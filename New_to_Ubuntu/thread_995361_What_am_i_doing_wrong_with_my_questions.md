---
title: "What am i doing wrong with my questions"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by gizmo_the_greater on 2008-11-27
i've asked in 3 threads 10 questions within lets say 48 hours, not even a answer ...

[http://ubuntuforums.org/showthread.php?t=993947&highlight=gpspipe](http://ubuntuforums.org/showthread.php?t=993947&highlight=gpspipe)
[http://ubuntuforums.org/showthread.php?t=994846&highlight=gpspipe](http://ubuntuforums.org/showthread.php?t=994846&highlight=gpspipe)
[http://ubuntuforums.org/showthread.php?t=995312&highlight=gpspipe](http://ubuntuforums.org/showthread.php?t=995312&highlight=gpspipe)

whats that community about - i see other posts with 143 views within a quarter of an hour but mine is not even watched? 

how can i post any result if none helps me getting one ...

i've made 3 posts for same topic, so less views that i'm asking myself what am i doing wrong?

yes, i'm not a genius ... but dont making questions keeps stupid!

by the way, im from austria, excuse my english ...

greetz, bedding for a response

---

### Post by laurielegit on 2008-11-27
Either you are asking realy hard questions or you are not asking them in the right way. Have a look at this: [http://www.catb.org/~esr/faqs/smart-questions.html](http://www.catb.org/~esr/faqs/smart-questions.html). It helped me a lot.

Good luck,

Laurie

---

### Post by Joeb454 on 2008-11-27
First off - duplicate threads on the same subject isn't really something we approve of here.

That said, I can understand your frustration, but you could bump your post once every 24 hours or so if it's still not been answered.

I hope that helps a little :)

---

### Post by Vadi on 2008-11-27
Sorry, don't have experience with GPS software =(

---

### Post by gizmo_the_greater on 2008-11-27
> **Vadi said:**
> Sorry, don't have experience with GPS software =(

thanks for the first replies i've ever got in here

whats really wrong with the following post.

[http://ubuntuforums.org/showthread.php?t=994846&highlight=gpspipe](http://ubuntuforums.org/showthread.php?t=994846&highlight=gpspipe)

i dont understand, i've tried to make my problem as clear as possible (is there any problem in the way i'm asking??????)

maybe i just need a kick in my f.... *** for what and why???????

---

### Post by gizmo_the_greater on 2008-11-27
im not sure if the problem is related to gpssoftware ... it seems gpspipe cant read device-settings for serialport from my 'virtual device'

i'm not sure if thats only realted to gpsdrive (maybe i'm using wrong mknod commands?)

---

### Post by philinux on 2008-11-27
I think your problem is not one thats been seen by many. Hence the lack of replies/views etc.

---

### Post by Paqman on 2008-11-27
> **gizmo_the_greater said:**
> 
i dont understand, i've tried to make my problem as clear as possible (is there any problem in the way i'm asking??????)

I don't think there's anything wrong with the way you've asked your questions, really. It's just quite a techy problem.

However, some tips for asking questions:
[LIST=1]
[*]Don't create multiple threads for the same problem. It makes it harder for people to help.
[*]Don't bump your own threads if they have no replies. The forum has a team who search for unanswered questions, bumping your thread means they probably won't ever find it.
[/LIST]

---

### Post by gizmo_the_greater on 2008-11-27
i'm not sure if it is such a "major" problem ... (no compares)

i've also looked ad gpspipe-sourcecode and and seems a "general" problem (ea system dont reports any serial settings to [any???] program) when it is not able to determine any "serial parameters"

so mayby anyone could help me how to determine howto check, if a device is configured properly as a fake gps ... 

maybe because of udev??? (i also spended some time finding aut usbdevfs is not working anymore)

give me a hint where to resume this discussion, and by the way, some more moments and i fall asleep ... answers may follow tomorrow

---

### Post by drs305 on 2008-11-27
gizmo the greater,

You might also try some of the forums which deal with specific topics (Networking, etc). Although they don't get nearly as many reads, the people reading the forum are often better equipped to answer specific questions. 

I thought the post you made regarding 'mknod /dev/gps_fake c 4 64; gpspipe -r -s /dev/gps_fake' was pretty well laid out but highly technical. Take a look at all the available forums when you have a detailed question.

I'd like to be able to handle questions like your's but don't have the knowledge to do so, which is why I mostly frequent the General and Beginners forums.

---

### Post by gizmo_the_greater on 2008-11-27
> **Paqman said:**
> I don't think there's anything wrong with the way you've asked your questions, really. It's just quite a techy problem.

However, some tips for asking questions:
[LIST=1]
[*]Don't create multiple threads for the same problem. It makes it harder for people to help.
[*]Don't bump your own threads if they have no replies. The forum has a team who search for unanswered questions, bumping your thread means they probably won't ever find it.
[/LIST]

thanks to all for the hints with the team, the bump-possability and so on ... i dont knew that ...

(noone ever can stop learning)

---

### Post by gizmo_the_greater on 2008-11-27
a simple (geek-like) question and idea to that prob:

whats about a "i REALLY dont know" flag an ony post?

Related to your level (how many posts, thanks, ... you got it would be an interesting possibility to enhance [the relativity] of ANY FORUM POST [allowing any user {which user level ever} giving feedback without leaving an reply - depending on experience-level it could help "real freaks" where it is worth to help on ...

---

### Post by overdrank on 2008-11-27
Hi and a proper title for the thread and the best information you can give on the issue. You must remember that most users here must have had the same issue or are willing to install and test what you are having issues with.

 Another issue is the user that knows the answer may not be online so just be patient and keep searching and bumping and adding info as to what you have tried. :)

---

### Post by gizmo_the_greater on 2008-11-27
> **drs305 said:**
> I thought the post you made regarding 'mknod /dev/gps_fake c 4 64; gpspipe -r -s /dev/gps_fake' was pretty well laid out but highly technical.

so where should i put this????

should'nt i give facts? (disregarding some private msg)

---

### Post by kansasnoob on 2008-11-27
How many people would understand your problem?

I'm clueless! It's like you're speaking a foreign language to me!

This is the most helpful and friendly forum I've ever found, but it's totally volunteers!

We share what we know!

---

### Post by drs305 on 2008-11-27
> **gizmo_the_greater said:**
> so where should i put this????

should'nt i give facts? (disregarding some private msg)

As t where it should go - I always search the forums before posting a question in hopes of finding an answer. When I do this and can't find a solution, I will note which forum has the most closely-related topics. In your case I did a search and no one forum stood out.

When I said it was 'well laid out but highly technical' I wasn't trying criticize it. I thought it was a good question. Yes you should include details. An explanation of what you are trying to do is sometimes helpful as there may be other ways to do what you want.

---

