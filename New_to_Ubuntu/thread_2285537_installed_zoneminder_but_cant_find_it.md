---
title: "installed zoneminder but cant find it"
date: 2015-07-06
forum: New to Ubuntu
---

### Post by ty_james_tharp on 2015-07-06
hi, i installed zoneminder but can't find it . i've searched applications, files , computer . it shows up on software center as installed , so i uninstalled and reinstalled but cant find it, i don't know how to use terminal, but i tried anyway. got nothing. this is making me feel really stupid. can someone help me? please?

---

### Post by roger_1960 on 2015-07-06
Hi

Which ubuntu are you using? unity, xfce ? If its unity, put "zoneminder" into  the search box (icon at the top of the unity bar on the left)

---

### Post by oldos2er on 2015-07-06
Have you tried entering ```
zoneminder
``` into a terminal? I've never used the program so I don't know if it's a CLI app or not.

---

### Post by ty_james_tharp on 2015-07-07
i guess im not using unity i dont know what a unity bar is

---

### Post by ty_james_tharp on 2015-07-07
yes i tried that but command not valid

---

### Post by ty_james_tharp on 2015-07-07
i dont think im using unity

---

### Post by bab1 on 2015-07-07
> **ty_james_tharp said:**
> hi, i installed zoneminder but can't find it . i've searched applications, files , computer . it shows up on software center as installed , so i uninstalled and reinstalled but cant find it, i don't know how to use terminal, but i tried anyway. got nothing. this is making me feel really stupid. can someone help me? please?

Zoneminder is not the easiest application to install.  It should install a full LAMP stack.  You need to configure Apache2 etc..  Please explain the steps you used to install zoneminder.  If you have installed it correctly, you should be able to access the web based Interface  [http://127.0.0.1/zm](http://127.0.0.1/zm) in your favourite web browser.

---

### Post by ty_james_tharp on 2015-07-07
whats a lamp stack? whats apache? tried to access web interface got a 404 error

---

### Post by ty_james_tharp on 2015-07-07
i installed it from ubuntu software center

---

### Post by bab1 on 2015-07-07
> **ty_james_tharp said:**
> whats a lamp stack? whats apache? tried to access web interface got a 404 error
Zoneminder is a web cam server with no GUI access other than via a web page.  LAMP is a complete web server setup with a web server (Apache2) a database (Mysql) and a programing language for the web page (PHP).

You can't install Zoneminder without configuring all of these.

[COLOR="#0000FF"]Edit:  Betcha didn't configure it. [/COLOR]  ;-)

See: [http://www.zoneminder.com/wiki/index.php/Ubuntu_Server_14.04_64-bit_with_Zoneminder_1.28.0_the_easy_way]("http://www.zoneminder.com/wiki/index.php/Ubuntu_Server_14.04_64-bit_with_Zoneminder_1.28.0_the_easy_way")

---

### Post by ty_james_tharp on 2015-07-07
no i didnt configure it, i dont even know what a GUI is. lol

---

### Post by bab1 on 2015-07-07
> **ty_james_tharp said:**
> no i didnt configure it, i dont even know what a GUI is. lol
Graphical User Interface.

I think that you need to learn a little more about computing in general and Linux (Ubuntu) specifically.

---

### Post by ty_james_tharp on 2015-07-07
you think???? duh , you know every person who uses ubuntu is not a geek some of us are just normal people who dont spend our life on the computer. why does it have to be made so complicated ? its gotten so complicated , its not fun any more. when completing a simple task takes days. thank you for trying to help me . i so appreciate it .. people like you keep my faith in humanity . but im giving up on computers enjoy

---

### Post by bab1 on 2015-07-07
> **ty_james_tharp said:**
> you think???? duh , you know every person who uses ubuntu is not a geek some of us are just normal people who dont spend our life on the computer. why does it have to be made so complicated ? its gotten so complicated , its not fun any more. when completing a simple task takes days. thank you for trying to help me . i so appreciate it .. people like you keep my faith in humanity . but im giving up on computers enjoy
In fact Linux in general is a lot easier than before.  What is complicated is all the new things you can do these days.  Unfortunately it's either time of money with this kind of thing.  If you want to get it for free you have to invest some time (to learn).  On the other hand if you are willing to pay $$$ then I'm sure there is a simple, but costly solution.  Linux is still a little geeky in some aspects.
[COLOR="#0000FF"]
Edit:  It's kinda like fixing your car.  You don't have to know how to fix it if you are willing to pay.  Of course you are still allowed to drive it.[/COLOR]  :D

---

