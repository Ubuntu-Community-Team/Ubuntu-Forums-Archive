---
title: "copy hidden files for beginners"
date: 2011-09-14
forum: New to Ubuntu
---

### Post by lloydhood on 2011-09-14
How do I copy multiple hidden files from one directory to another in Ubuntu?
 
Just to clarify, I am an Absolute Beginner!
 
I have used forums and lists to great benefit and thought I would post this hoping it helps some.
 
I have been searching google to find how I copy hidden files from a skel folder to a user folder. I found a lot of questions and a lot answers and none seemed to work for me. I also found this forum and joined, hoping to end my beginner status asap.
 
So what I found made me think that maybe the question was not posed properly. The directories in question already exist, so I thought:
"cp -r /etc/skel /home/destination";
"cp ./.* /home/destination";
"cp -a * /home/destination" ...
 
the last of a long list incorrect commands!!!
 
It turns out that "cp -a * /home/destination" is absolutely correct except my permissions weren't in line. So:
 
"sudo cp -a * /home/destination"
 
got the job done easy peasy.
 
From one Absolute Beginner to another, I hopes this helps!
 
lloyd

---

### Post by sarwiz on 2011-09-14
Doesn't it feel great to get to the solution of a problem like this.

---

