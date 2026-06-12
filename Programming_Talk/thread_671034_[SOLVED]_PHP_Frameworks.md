---
title: "[SOLVED] PHP Frameworks"
date: 2008-01-18
forum: Programming Talk
---

### Post by Circus-Killer on 2008-01-18
I am a web developer, about to start two new projects. Currently, I am looking for a PHP-based framework to use in these projects.

While there are so many, and I know everyone has their own opinions, I would like to hear your opinion. I've been looking at CakePHP and it really looks like a strong possibility.

But before I make my decision, I would like to hear your thoughts. If you have used a particular framework that you enjoyed using, please let me know the name of the framework and what you liked or didn't like in the framework.

Please try maybe give reason for you liking it, and also specify how big the learning curve is. Thanks in advance. Looking forward to hearing your thoughts on the subject.

---

### Post by Sam on 2008-01-18
You can try [CodeIgniter](http://codeigniter.com/). I'm working on it now and it is very promising. Have a look on their [user guide](http://codeigniter.com/user_guide/toc.html).

---

### Post by ThinkBuntu on 2008-01-18
CakePHP is really nice, but I haven't done anything significant with it. Actually, except for minor features in clients' websites, I really haven't done anything significant with PHP, so take my advice with a rock of salt. In any case, as I've begun stepping into PHP development lately, I've read a ton of opinions about the top PHP frameworks, so hopefully my reading can save you some time. It seems to come down to Symfony and CakePHP for most, and it seems like both are more than capable of getting the job done. It seems that CodeIgniter is worse than Cake based on most reviews, and that Zend is really a half-baked (ha-ha...) framework. There are numerous smaller projects out there like QCodo that also have been acclaimed.

I've followed the 15-minute blog tutorial for Cake, and even begun writing my own web app in it, which is so far coming along pretty well. I have yet to use Symfony, so I really can't help you with a comparison based on experience, but Cake is pretty easy to use. The documentation is a bit all over the place, but I've been able to find answers between tutorials, The Manual, and the API pretty well when needed.

---

### Post by Circus-Killer on 2008-01-25
well, i thank you both for your input, however i was hoping for a bigger response from the general forum communitee.

basically, there are well over 40 PHP frameworks, far too many to look into. so far "we've" had suggestions for CakePHP and CodeIgniter. Anyone have experience or thoughts on any others?

Has anyone tried Zend? Personally, it looks a handful, but i could be wrong, haven't looked into it properly. How about Symphany or Seagull?

Please, anyone using **any** PHP framework, just give the name of the framework and your thoughts on it. even if its just a couple of lines. just so i can get a rough idea on what people like and what there thoughts are.

I know everyone has there own preferences and tastes, and each framework has its strengths and weaknesses, thats why I'm just asking for opinions.

---

### Post by garak on 2008-09-09
My suggestion is Symfony 1.1 (or above).
It makes all the dirty job for you, so you can focus on your model and almost forget about the rest. But it's also a collection of highly decoupled classes, so you can even use it just like a collection of libraries.

---

### Post by cb951303 on 2008-09-09
I use CodeIgniter. I doubted between CakePHP and CI but I think I made the right choice because as everyone agrees CakePHP lacks documentation. Which is big disadvantage. CI has a huge userguide. You can practically start coding in minutes. But AFAIK CakePHP has a bigger library. CI is faster though :)

---

### Post by garak on 2008-09-09
> **cb951303 said:**
> I use CodeIgniter. I doubted between CakePHP and CI but I think I made the right choice because as everyone agrees CakePHP lacks documentation. Which is big disadvantage. CI has a huge userguide. You can practically start coding in minutes. But AFAIK CakePHP has a bigger library. CI is faster though :)
The main issue with CodeIgniter is that it's PHP4 compatible. It's fool, PHP4 is DEAD. Why to give up to real OOP? Symfony is a collection of most of programming best-practices and it's not really so hard to learn (you can do a simple site just in minutes)

---

### Post by cb951303 on 2008-09-09
> **garak said:**
> The main issue with CodeIgniter is that it's PHP4 compatible. It's fool, PHP4 is DEAD. Why to give up to real OOP? Symfony is a collection of most of programming best-practices and it's not really so hard to learn (you can do a simple site just in minutes)

I don't want start a flame war but symphony is bloated. Also PHP4 support is a must have for me since most of the hosts I work with still uses PHP4. 

Remember that in server biz having the latest software is not always the best thing. It's safe to say that PHP4 is more secure and stable then PHP5 but not in the meaning of "PHP5 is not stable or secure". Simply because it has been around longer. BTW PHP4 is still a supported software. I wouldn't call it "DEAD".

---

### Post by Circus-Killer on 2008-09-10
alright, i thought i had already made this post, but anways....
i chose to go with codeigniter. i needed something simple, quick and would be easy for me to get the hang of.
been using codeigniter since about february/march and i am very happy.

thanks to all those who made other suggestions too.

---

### Post by garak on 2008-09-10
> **cb951303 said:**
> I don't want start a flame war but symphony is bloated. Also PHP4 support is a must have for me since most of the hosts I work with still uses PHP4. 
Remember that in server biz having the latest software is not always the best thing. It's safe to say that PHP4 is more secure and stable then PHP5 but not in the meaning of "PHP5 is not stable or secure". Simply because it has been around longer. BTW PHP4 is still a supported software. I wouldn't call it "DEAD".
Don't want to flame, but I'd like to state some points.
Symfony (NOT Symphony) is not bloated: it's highly customizable and its collection of classes is mostly decoupled (e.g. you can pick what you need and give up the rest).
PHP5 is not "the latest", it's out since 2004 and stable since 2005.
PHP4 end of life (= death) was announced on july 2007 for the end of the same year: if your hosting service is still PHP4 only, maybe it's time to look for an alternate one.

---

