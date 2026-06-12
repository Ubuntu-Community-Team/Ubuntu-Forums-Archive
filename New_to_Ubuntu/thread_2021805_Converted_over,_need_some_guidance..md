---
title: "Converted over, need some guidance."
date: 2012-07-09
forum: New to Ubuntu
---

### Post by gudcode on 2012-07-09
Hi all!

Up until a few months ago I never really thought about Linux, then I went to a work interview where they only used open-source software. He gave me an Ubuntu cd and I went ahead and made a dual-boot. After playing around with it I discovered you can do much more than you ever would in Windows. The funny thing is here in South-Africa even seasoned programmers know nothing about Linux. So after a few weeks of doing a dual-boot I decided my laptop will be a dedicated Linux box and my tower for all the silly windows stuff..... Now to my point

I have done a few .NET courses in C# and VB and I was very disappointed with the way colleges exploit these courses, it all feels like a big money making scheme to me. My views towards MS has changed for the worse. 

I would like to get involved in development and was wandering if anyone can point me in a direction where a noob developer can get his hands dirty, I would also like to learn to create a Linux system based on certain company's business needs and the like. Where would the best place be for me to start. I know C# quite well, I can use Mono for that, is there another language that would be better suited for this(python, ruby....)

I can't believe people are so in the dark about this os in S.A, I would like to open their eyes.

Thanx in advance.

PS. when hitting ctrl, alt and f1 through f6...is that basically a terminal that opens?

---

### Post by afixane on 2012-07-09
Hi, wellcome to freedom :D

If you want to start programming, try Python. Or, if you're familiar with VB, try Gambas. Both is easy for me.

---

### Post by ronnysingh on 2012-07-09
> **gudcode said:**
> 
I can't believe people are so in the dark about this os in S.A, I would like to open their eyes. 


Amen. I hope the same for people of India.I am not into programming or development as my profession belongs to finance but I still try to spread awareness among people.

---

### Post by gudcode on 2012-07-09
Thanx, for some reason I am attracted to python. Will get a reference book, shouldn't be hard to figure out. I am really impressed with this system, the only limit here is imagination! Feels like there is so much to learn but not enough time in a day...

---

### Post by directhex on 2012-07-10
> **gudcode said:**
> Hi all!

Up until a few months ago I never really thought about Linux, then I went to a work interview where they only used open-source software. He gave me an Ubuntu cd and I went ahead and made a dual-boot. After playing around with it I discovered you can do much more than you ever would in Windows. The funny thing is here in South-Africa even seasoned programmers know nothing about Linux. So after a few weeks of doing a dual-boot I decided my laptop will be a dedicated Linux box and my tower for all the silly windows stuff..... Now to my point

I have done a few .NET courses in C# and VB and I was very disappointed with the way colleges exploit these courses, it all feels like a big money making scheme to me. My views towards MS has changed for the worse. 

I would like to get involved in development and was wandering if anyone can point me in a direction where a noob developer can get his hands dirty, I would also like to learn to create a Linux system based on certain company's business needs and the like. Where would the best place be for me to start. I know C# quite well, I can use Mono for that, is there another language that would be better suited for this(python, ruby....)

Would you rather learn a new language from scratch, or leverage your existing language knowledge & learn only new toolkits & developer tools? You can develop perfectly reasonable apps for Ubuntu in C# if you want to, using only Open Source tools.

> PS. when hitting ctrl, alt and f1 through f6...is that basically a terminal that opens?

This goes back to UNIX. Each of the keys provides you with a "Virtual Terminal" in the "dumb UNIX terminal" sense. Each of them is named ttyX - for example, tty4 is on ctrl-alt-F4. There's an app called getty sitting there, providing you with an interactive session - if you look at tty9 you'll see what you get with no getty running.

You can look at /etc/init/ttyX.conf to see the configuration files which tell the system to spawn multiple getty instances. You can also spawn getty in other places, such as on a serial port (named ttySX for numbers 0 upwards) and even on a USB serial adapter (ttyUSBX)

---

### Post by Nytram on 2012-07-10
A good way to start developing is to identify some need or requirement you have that isn't currently filled by existing software. Maybe a new app, or an improvement to an existing one. I think this is the main motive for creating free/open source software - a developer writes something for herself and then shares it with the community.

If you want your software to be cross-platform then I'd suggest Java which is similar to what you already know with C#, otherwise I'd go with Python for Linux-only apps.

---

### Post by xedi on 2012-07-10
> **gudcode said:**
> 
I would also like to learn to create a Linux system based on certain company's business needs and the like. 


Do you mean a whole Linux distribution? To get yourself familiar with all the typical components of a desktop linux operating system, you could install arch, which is a minimal Linux distribution and requires you to install many components yourself. You could also go the more hardcore way and look at the linux from scratch ebook which teaches you how to build a Linux OS completely from source. 

[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

For more specific advice somebody more knowledgeable about this topic should be able to give help you better but I think just to get a very basic overview this might get you started.

---

### Post by gudcode on 2012-07-12
Thanx for all the help, I'll look into all of that

---

### Post by mastablasta on 2012-07-12
heh what do they think most internet runs on then? Windows 7 home edition?
 
Google uses Ubuntu (modified). Andrioid is built on modified linux kernel (they shaved soem unnecessary stuff of of it) most servers online are linux based (well some BSD and some MS, but mostly linux).
 
anyway  this e-book is good to start with python i was told: [http://www.diveintopython.net/](http://www.diveintopython.net/)
and it really is easy to read. and free.
 
I believe Arch Linux has good documentation and if you install it even in virtual mashcine you will sure learn a lot about Linux. 
LFS can be a bit difficult to start with.

---

### Post by ymra on 2012-07-12
It could be useful to learn c or c++ .

---

### Post by Sendo Eevpix on 2012-07-12
Nice to know you made a good switch. ^^

Yes, like you, After using Ubuntu, my likes and ideas of Windows started to go bad and dark, so I haven't used Windows for the most part of four years. Most of them reasons being that MS is lying, and exploiting people's lack of knowledge of Linux, just to make money off of Linux stuff, and discouraging people from Linux, like with their 2004 'Get the Facts' ad campaigns.

Though as of programming, I been with Ubuntu for so long, though I haven't tried to work out with programming. So I can't actually suggest something to you. :(

---

### Post by directhex on 2012-07-12
If it were me, I'd stick with C#... but that's because I like C# as a language, and hate Python

---

### Post by clive littlewood on 2012-07-12
Hi and welcome to the wonderful world of Linux.

Something different for learning Python is to check out the full circle magazine.

fullcirclemagazine.org/

They have been running a python for beginners series for many months now, and this would also be good reading for a Ubuntu newcomer.

Start downloading the back issues !!!!!!

Regards

Clive

---

### Post by gudcode on 2012-07-12
Thanks again for all the info, I will be reading late into the night with all those links.  

It seems to me that apple has made some type of Linux system their own by just sticking an apple onto it. 

I know every one has a personal preference to programming languages, but what would be the best option to work and program on Linux and then if need be it can be distributed to windows. Most of them are very similar in anyway. Mostly I would like to do some web development(LAMP, ah so this is where python comes in?) and maybe a few apps, but would like to get into cloud integration as well.

I have to say I Love Linux! Windows only comes on for VS...Every time I explore the terminal I discover something new, nothing I ever would have been able to do with windows.

Last thought.....Here in South-Africa any PC bought has windows installed, would it be possible to sell PC's without any OS or maybe Kubuntu or something. It feels like there could be a big market for this system if people only knew, and it's hard for them to even try it out too, wonder why. It was an easy change for me after throwing money towards Microsoft to receive nothing in return.

Thanks again for everyones input, it's appreciated!:guitar:

EDIT: I have a good idea for a gym trainer app or website but not sure how to go about it, where can I share what I have done already and maybe get some help? Also if there is a project going that a noob like me can try and participate in?

---

### Post by pe7er on 2012-07-13
> **gudcode said:**
> Here in South-Africa any PC bought has windows installed, would it be possible to sell PC's without any OS or maybe Kubuntu or something. It feels like there could be a big market for this system if people only knew, and it's hard for them to even try it out too, wonder why. It was an easy change for me after throwing money towards Microsoft to receive nothing in return.

Yeah, I saw the documentary "Revolution OS" where people protested against that sort of MS tax. 
Some companies now have a refund policy: [http://en.wikipedia.org/wiki/Windows_refund](http://en.wikipedia.org/wiki/Windows_refund)

> **gudcode said:**
> EDIT: I have a good idea for a gym trainer app or website but not sure how to go about it, where can I share what I have done already and maybe get some help? Also if there is a project going that a noob like me can try and participate in?

If you want to create a web application, you might look into Content Management Systems like Joomla or Drupal.
You can build your webapplication using those CMS as framework,
so you don't have to build everything from scratch (layout, database, user authentication etc). 
E.g. Joomla uses a framework with objects that you can extend. Or put stuff into the database by just creating a MySQL query and giving that to Joomla's database object.

---

### Post by gudcode on 2012-07-14
> **pe7er said:**
> 
If you want to create a web application, you might look into Content Management Systems like Joomla or Drupal.
You can build your webapplication using those CMS as framework,
so you don't have to build everything from scratch (layout, database, user authentication etc). 
E.g. Joomla uses a framework with objects that you can extend. Or put stuff into the database by just creating a MySQL query and giving that to Joomla's database object.

Thanx for the input. I have played around with Joomla a bit, it's nice for back end management. I am used to doing everything with ASPX.... but at the moment I am very anti-MS

---

