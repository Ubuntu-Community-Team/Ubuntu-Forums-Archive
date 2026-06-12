---
title: "Lamp"
date: 2015-08-11
forum: Programming Talk
---

### Post by NaneK on 2015-08-11
Hi all,

I want to start learning PHP. I know that for testing PHP scripts I can't just open them in browser like with HTML, I need some localhost server, right?
I know about XAMPP, WAMP and LAMP, and I have some (basic) experience with wamp.

So I need something that will allow me to test my PHP scipts (later and MySQL - for Wordpress) on my laptop. It is my private laptop where I keep all my stuff, so it will not be live server for hosting or stuff like that xD

And the question is: is LAMP the "program" that I need, or I can use something else? If LAMP is the program I am looking for, can you provide my with the correct links or info on how to configure it, so my laptop isn't opening its ports to everybody. Security is important :)

I am runing stock (updated) Ubuntu 14.04.03 LTS, with no special configurations done by myself. So if I need to setup firewall or something like that, you will have to expain that too..

And please do not tell me to buy a hosting or a server! I have that, but I want to be able to work when not online (on trip, etc).

Thanks in advance.

---

### Post by tgalati4 on 2015-08-11
I find that installing *tasksel* works well for installing the LAMP stack.  LAMP (Linux--Apache--MySQL--PHP)  is a collection of several pieces that work together as a "stack" of software.  They are needed to run PHP.

```
sudo apt-get install tasksel
sudo tasksel
```

Select LAMP and let it run.  When finished open a browser:

[http://localhost](http://localhost)

---

### Post by Lars Noodén on 2015-08-11
Or it can be done without tasksel.

```

sudo apt-get update
sudo apt-get install  lamp-server^

```

Mind the caret, it is part of the name.  

Then you'll be able to work anywhere you've got your computer with you.

---

### Post by NaneK on 2015-08-12
Thank you both :D

---

