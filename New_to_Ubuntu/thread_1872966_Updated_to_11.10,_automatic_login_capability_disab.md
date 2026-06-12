---
title: "Updated to 11.10, automatic login capability disabled?"
date: 2011-10-31
forum: New to Ubuntu
---

### Post by brallan on 2011-10-31
I updated from 11.04 to 11.10, and now i get a login screen. I want my computer to automatically log on, or if logged out, to login automatically after 10 seconds...

In versions previous to 11.04, (if I remember correctly) I would go into System> Login Screen, and set it to automatic login, but this no longer even seems to exist in 11.10.

anyone know how to get this capability back?  

I thought to boot into the old desktop with the main menu, but even if I COULD, that may not work, since opening up Main Menu does not even show the Login Screen anymore....

---

### Post by raja.genupula on 2011-10-31
> **brallan said:**
> I updated from 11.04 to 11.10, and now i get a login screen. I want my computer to automatically log on, or if logged out, to login automatically after 10 seconds...

In versions previous to 11.04, (if I remember correctly) I would go into System> Login Screen, and set it to automatic login, but this no longer even seems to exist in 11.10.

anyone know how to get this capability back?  

I thought to boot into the old desktop with the main menu, but even if I COULD, that may not work, since opening up Main Menu does not even show the Login Screen anymore....

Hi man 

open your terminal 
then do this

```
sudo nano /etc/gdm/custom.conf
```

then give there

```

[daemon]
TimedLoginEnable=false
AutomaticLoginEnable=true
TimedLogin=brallan
AutomaticLogin=brallan
TimedLoginDelay=30
DefaultSession=gnome
```

all the best

---

### Post by brallan on 2011-10-31
Found the solution to ONE part of the problem:

[http://www.liberiangeek.net/2011/09/enable-automatic-login-in-ubuntu-11-10-with-lightdm/](http://www.liberiangeek.net/2011/09/enable-automatic-login-in-ubuntu-11-10-with-lightdm/)

See below for details if the link doesn't work.

However, after the screensaver comes on, it STILL asks me for a login, something I do not want.

 [URL="http://www.liberiangeek.net/"]+++++++++++++++++++++++++++++++++++++++++++++++++
[/URL]
 Enable Automatic Login in Ubuntu 11.10 with LightDM

    
[IMG]http://www.liberiangeek.net/wp-content/uploads/2011/05/1bf95906d9de_837F/ubuntu_natty.png[/IMG]Since  Ubuntu 11.10 (Oneiric Ocelot) is defaulting to LightDM as its default  display manager, this tutorial shows you how to enable auto login in  Ubuntu with LightDM as the display manager. If you have upgraded to  Ubuntu 11.10 or will upgrade in the future, this tutorial will come in  handy when you need to setup automatic login.
 

**[SIZE=4]Getting started:[/SIZE]**
 
To get started, click on your username and select ***&#8216;User Account&#8217;*** or go to ***System &#8211;> Settings*** and select ***&#8216;User Accounts&#8217;. ***
 
[[IMG]http://3-www-accel-pss.googleusercontent.com/gadgets/proxy?container=accel&gadget=www.liberiangeek.net&debug=0&nocache=0&v=29o984j2gsoipbos4ojg34skm4&resize_h=201&resize_w=370&no_expand=1&rooe=1&html_tag_context=img&url=http%3A%2F%2Fwww.liberiangeek.net%2Fwp-content%2Fuploads%2F2011%2F06%2FEnable-Automatic-Login-in-Ubuntu-11.10_B2DD%2Fauto_oneiric_thumb.png[/IMG]]("http://www.liberiangeek.net/wp-content/uploads/2011/06/Enable-Automatic-Login-in-Ubuntu-11.10_B2DD/auto_oneiric.png")
 
Next, click the*** &#8216;Unlock&#8217;*** button at the top right to unlock.
 
[[IMG]http://www.liberiangeek.net/wp-content/uploads/2011/06/Enable-Automatic-Login-in-Ubuntu-11.10_B2DD/auto_oneiric_1_thumb.png[/IMG]]("http://www.liberiangeek.net/wp-content/uploads/2011/06/Enable-Automatic-Login-in-Ubuntu-11.10_B2DD/auto_oneiric_1.png")
 
Finally, change to &#8216;**ON&#8217;** for Automatic Login
 
[[IMG]http://2-www-accel-pss.googleusercontent.com/gadgets/proxy?container=accel&gadget=www.liberiangeek.net&debug=0&nocache=0&v=so2ici0ct40eqfin5vdicsec0k&resize_h=216&resize_w=464&no_expand=1&rooe=1&html_tag_context=img&url=http%3A%2F%2Fwww.liberiangeek.net%2Fwp-content%2Fuploads%2F2011%2F06%2FEnable-Automatic-Login-in-Ubuntu-11.10_B2DD%2Fauto_oneiric_2_thumb.png[/IMG]]("http://www.liberiangeek.net/wp-content/uploads/2011/06/Enable-Automatic-Login-in-Ubuntu-11.10_B2DD/auto_oneiric_2.png")
 
Restart to try.
 
Enjoy!
 [URL="http://allpremiumthemes.com/"]
[/URL]

---

### Post by Royalist on 2012-09-13
Glad you solved your problem Brallan.

I have the opposite problem i.e. at the login screen after boot-up, I am not required to give my password and I am Admin.  I have tried your technique but in reverse, many times.

I realise that I will have to use terminal [CODE]login[/Code, but I want the opposite to the '-f' option. Did you come across any hints that you might pass on please? :)

---

### Post by newb85 on 2012-09-13
> **brallan said:**
> However, after the screensaver comes on, it STILL asks me for a login, something I do not want.

It has been a couple years since I had a screensaver installed, but I seem to recall having an option in the screensaver settings dialog to require a password.

---

### Post by brallan on 2012-09-15
I find post-gnome ubuntu very annoying, I have since moved on to Kubuntu since I was so frustrated with things like this.... 

i installed ubuntu-desktop to see if i could answer your question, and found, to my dismay, that there are at least TWO different places that you have options to tweak for almost identical things. In hindsight, I see that not having these together is why i needed to ask this quesion in the first place.

System Settings> Brightness and Lock
System Settings> User Accounts

There may also be a way to change the screensaver settings, but I couldn't even find it!

best of luck!

---

### Post by newb85 on 2012-09-15
> **brallan said:**
> There may also be a way to change the screensaver settings, but I couldn't even find it!

If a screensaver is coming on, you must have installed screensavers and chosen a screensaver in a screensaver settings dialog.  The last few releases of Ubuntu haven't had screensavers installed by default.

---

### Post by brallan on 2012-09-20
thanks for that, newb85!

---

