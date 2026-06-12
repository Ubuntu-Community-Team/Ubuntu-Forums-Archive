---
title: "How To: Setting up numlock on start up"
date: 2005-02-10
forum: Outdated Tutorials &amp; Tips
---

### Post by Pawel on 2005-02-10
Welcome everybody

For X-Window:

=> You have to install numlockx

For console:

=> Go to /etc/console-tools/ end edit the **config** file:

Find sth. like this:

**#LEDS=+num** (on the end of the config file)

and change it to:

**LEDS=+num**

If You can't find /etc/console-tools - you can install package called **console-tools** and then change the Your configuration.

Best regards
Pawel W.

---

### Post by Mr_Smiley on 2005-02-11
Thanks for this, very useful :).

---

### Post by nocturn on 2005-02-11
Thanks for the howto.

Numlockx has never worked for me though (strangly enough many people do have success with it).

---

### Post by Datchew on 2005-02-12
Still doesn't work after reboot. 

Oh well.

---

### Post by Pawel on 2005-02-13
[QUOTE=Datchew]Still doesn't work after reboot. 

Oh well.[/QUOTE]

But what's doesn't work ?  :???: Say sth else  ;-)

---

### Post by Datchew on 2005-02-15
the number lock of course. 
that's the only thing this thread tried to fix was to get the number lock to stay on. 
I'm not trying to sound mean, just trying to clarify. 

I followed the steps and my number lock does not come on by itself. 

Any other ideas?

---

### Post by nocturn on 2005-02-16
[QUOTE=Datchew]the number lock of course. 
that's the only thing this thread tried to fix was to get the number lock to stay on. 
I'm not trying to sound mean, just trying to clarify. 

I followed the steps and my number lock does not come on by itself. 

Any other ideas?[/QUOTE]

I have the same problem (also did the dpkg-reconfigure several times).

I don't know what causes it to fail, as it works for a lot of people.

---

### Post by Buffalo Soldier on 2005-03-19
[QUOTE=Datchew]the number lock of course. 
that's the only thing this thread tried to fix was to get the number lock to stay on. 
I'm not trying to sound mean, just trying to clarify. 

I followed the steps and my number lock does not come on by itself. 

Any other ideas?[/QUOTE]

Have you tried [How to turn on Num Lock when login into GNOME](http://ubuntuguide.org/#onnumlockgnome) at [UbuntuGuide.org](http://ubuntuguide.org/)?

---

### Post by Cuber on 2005-04-09
I have the same problem, I un-# the option and after reboot there is no numlock on.

Probably somthing wrong in  the config file.

---

### Post by kuleali on 2005-04-12
Nice, it worked

---

### Post by globalspace on 2005-04-20
[QUOTE=Buffalo Soldier]Have you tried [How to turn on Num Lock when login into GNOME](http://ubuntuguide.org/#onnumlockgnome) at [UbuntuGuide.org](http://ubuntuguide.org/)?[/QUOTE]



thanks with it it worked  :grin:

---

### Post by digilogman on 2009-07-31
Hey I'm new to Ubuntu. I have this problem, anytime I want to change something, like the num lock feature on startup I get this message telling me I dont' have enough privileges to change the file (console tools). How do I change these privilege settings?Thanx

---

### Post by MC707 on 2009-09-16
> **digilogman said:**
> Hey I'm new to Ubuntu. I have this problem, anytime I want to change something, like the num lock feature on startup I get this message telling me I dont' have enough privileges to change the file (console tools). How do I change these privilege settings?Thanx

If the OS says you don't have privileges while you configure using the GUI, then you SHOULD be prompted with for the root password (remember, the password you first entered when you installed ubuntu?). Maybe you didn't install the system, and you are not the administrator. In that case you should talk with the system admin (the guy who installed ubuntu.) If you are asked for privileges while using Terminal, then you have to issue the [sudo] command (without brackets) at the beginning, which will prompt you for your root password (again read above for root password.) Hope that helps.

---

