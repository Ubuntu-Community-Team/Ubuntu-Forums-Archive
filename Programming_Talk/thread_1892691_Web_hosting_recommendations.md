---
title: "Web hosting recommendations"
date: 2011-12-08
forum: Programming Talk
---

### Post by PaulM1985 on 2011-12-08
Hi

I am about to start on my final project in my third year studying a Computing degree.  As part of my project I want to create a Facebook application which will be hosted externally to Facebook, where Facebook will forward to my web address, as seen here:

[http://blogs.oracle.com/sduv/entry/write_facebook_applications_using_java](http://blogs.oracle.com/sduv/entry/write_facebook_applications_using_java)

I was wondering if anyone could recommend any sites that provide web hosting that support Java (ie servlets and JSP).

My site will contain an game in the form of an applet that the user will play and at the end of the game I want the applet to post it's state to the server, which will save the serialised Java object to file.  I am researching AI and so the game files will allow me to assess what has happened during the game and what decisions the artificial agent chose to take.

I know that I can probably do this in PHP, which lots of web hosts seem to support, but the rest of the project is quite a handful, so sticking with what I know is preferable.

Paul

PS - I have considered hosting this myself using tomcat and dynamic DNS, but my internet connection is too unreliable to make this an option, so I need a 3rd party to host it.

---

### Post by juancarlospaco on 2011-12-08
Gae ?

---

### Post by karlson on 2011-12-08
> **PaulM1985 said:**
> I need a 3rd party to host it.

Many sites can provide hosting with Java and JSP support the question is how much you want to pay for it.

---

### Post by PaulM1985 on 2011-12-08
I am not looking to pay too much, I am a student :-).  I know there are plenty out there and I could just google "Java web hosting" but I am asking for hosts that people use themselves and recommend.

I was assuming that people on here were quite likely to use web hosting services of some sort.

Paul

---

### Post by bluexrider on 2011-12-08
I have mine at GoDaddy for 12 bucks a year

---

### Post by karlson on 2011-12-08
> **PaulM1985 said:**
> I am not looking to pay too much, I am a student :-).  I know there are plenty out there and I could just google "Java web hosting" but I am asking for hosts that people use themselves and recommend.

I was assuming that people on here were quite likely to use web hosting services of some sort.

Paul

[http://www.fatcow.com](http://www.fatcow.com)
[http://www.godaddy.com](http://www.godaddy.com) I wouldn't use them but they are cheap.

My personal favorite would be to choose a Linux machine if you have one available at school.  Install a webserver on it and Tomcat and run it on port other then 80.

I actually had one running for awhile when I was at school.

---

### Post by 11jmb on 2011-12-08
I don't know the parameters of this project and how much time you have left, but hosting your own http server would be a great addition to the project.

This isn't going to be due at the end of your fall semester is it? (in a week or 2?)

---

### Post by PaulM1985 on 2011-12-08
Karlson, the two you listed don't seem to support java.

I can't use schools computer because the university course is self taught and there isn't exactly a campus. It's all remote working. [Www.open.ac.UK](Www.open.ac.UK) for more info.

My course is nine months long starting Feb 2012. I have hosted sites before and I know how to set them up, just my internet connection has recently gotten pretty bad and so anything I host is not going to be reliable.  The main focus of my project is genetic algorithms and distributed computing to speed evolution rates, so I would rather focus my efforts on those rather than hassle with hosting troubles. The website is only to host the game so that I can gather information on how well my artificial player competes against real people.

Paul

---

### Post by collisionystm on 2011-12-08
Maybe check bluehost or network solutions

---

### Post by GeneralZod on 2011-12-09
You can also hire a cheap VPS for a few months, and install whatever you want on it.  I pay £2.23 p/m for mine, and it has a static IP.

---

### Post by highspider on 2011-12-17
> **bluexrider said:**
> I have mine at GoDaddy for 12 bucks a year

That's what I would do. I would buy a cheap-o computer off craigslist, newspaper add garage sale, ebay, ask a computer store for a old free one or other.  Then use that use that cheap-o as your server with a Domain Name Registrar for around 15$ for the whole year!

Check my attached to see what slow cheap-o I is use for my Ubuntu server.
Rendering web pages and running javascript is not going to need a expen$ive computer.
also remember that you dont need a monitor, keyboard, mouse just the cat5 cable and power cord once it's up running. So you could barrow the ones off your main computer to install the server software.

---

### Post by rithika on 2011-12-20
To host your java based applications, you can check out **[B]Hioxindia**[/B]. You can host your Java server pages/servlet at $3.21. A reliable web host, good service, good technical assistance with 99.9% assured uptime.

---

### Post by ratcheer on 2011-12-20
**Just stay away from 1&1. **Their ads are enticing, but once you sign up, it is difficult to ever cancel.

Tim

---

### Post by Habitual on 2011-12-20
20.00 USD a month at [http://www.linode.com/](http://www.linode.com/)

---

