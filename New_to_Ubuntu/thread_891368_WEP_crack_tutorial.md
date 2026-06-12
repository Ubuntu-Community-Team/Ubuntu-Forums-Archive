---
title: "WEP crack tutorial"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by hellodoggie on 2008-08-16
What is a good one?

I've used [http://www.askstudent.com/hacking/how-to-crack-a-wep-key-using-ubuntu/](http://www.askstudent.com/hacking/how-to-crack-a-wep-key-using-ubuntu/) but have encountered some problems.

---

### Post by nicedude on 2008-08-16
First you must have a proper setup. As in an injection patched driver for your wifi card then you need aircrack-ng then you need to read the following link.

Heres a link on how to wifi hack
[http://docs.lucidinteractive.ca/index.php/Cracking_WEP_and_WPA_Wireless_Networks#WPA_Flavours](http://docs.lucidinteractive.ca/index.php/Cracking_WEP_and_WPA_Wireless_Networks#WPA_Flavours)

If you get more advanced than this then you should also be compiling aircrack from source as there are 2 more attacks in the source than in the latest Ubuntu version from the repositories

If you list the problems you are having I will try to help with them

Hope this helps everyone

---

### Post by lisati on 2008-08-16
I hope you're not using it in order to use someone else's network without permission!

---

### Post by hotrod6657 on 2008-08-16
> **lisati said:**
> I hope you're not using it in order to use someone else's network without permission!

yes, that could cause some problems.

---

### Post by sub7even on 2008-08-16
for my case, i do it for testing, but will do it some other time :D hope this thread will still exist by that time :D

---

### Post by WastePotato on 2008-09-01
I recommend that you listen to nicedude as he knows what he's talking about. His driver and instructions worked great on my AG7005EG.

Oh and: [http://www.aircrack-ng.org/doku.php?id=simple_wep_crack](http://www.aircrack-ng.org/doku.php?id=simple_wep_crack)

---

### Post by Swenghk on 2008-12-23
Seriously? Your name is Sub7Seven! Sub7 is one of, if not the most infamous easy-bake-oven type hacking programs. Testing? PSH! I think you're in for a little more than testing!

---

### Post by Chayak on 2008-12-23
Just a note that cracking someone's wireless even for 'testing' without written permission of the owner is a crime under US and most state codes.  I don't think this really belongs on this forum.

---

### Post by dmizer on 2008-12-23
This thread will remain open for the time being, but please remember that the following points will earn infractions, warnings, and/or thread closure:

1) advocating WEP cracking without permission.
2) being unclear about the purpose for cracking WEP
3) posting/linking any howtos which advocate/suggest cracking WEP without permission.

Please note: this is not a comprehensive list. It is meant as a guideline and a reminder of where the line is.

---

### Post by 73ckn797 on 2008-12-23
I am traveling around my town daily and access many unsecured connections. Being unsecured, IHO, is free invitation to connect, though I will typically connect to the connection offered from the location I am at. I use WICD and can designate "always connect" to whichever connection a particular place has available for public use. These places are new car dealerships and independent auto repair shops that make an internet connection available. The stray connections being recognized are many times weak signals anyway.

If you live in the US there are many places that have open connections for public use. Many times I park outside of places like office supply or restaurants and connect to those public services when a shop does not have a connection.

---

### Post by echotone on 2009-10-25
Ok. I live with my grandparents and they lost our wep key. I tried to follow some other forums and tutorials but to no avail. any simple new-ubuntu-user ways of achieving access to my network?

---

### Post by Trebaruna on 2009-10-25
Pug your laptop into the router. Log in. Get/set the key.
Cracking WEP for that is overkill. If you do decide to crack their encryption, however, make sure to point out to your grandparents anyone else could've done that too and that they ought to change their security.

---

### Post by MrWES on 2009-10-25
> **echotone said:**
> Ok. I live with my grandparents and they lost our wep key. I tried to follow some other forums and tutorials but to no avail. any simple new-ubuntu-user ways of achieving access to my network?


My parents did the same thing; I reset the router (via the router reset button, might be located on the backside and recessed) then plug into the router and point your browser to 192.168.1.1 and reset up the WiFi.

Also, I wrote the router login, passwd and passkey phrase on a post-it note and taped it to the bottom of the router :)

Bill

---

### Post by echotone on 2009-10-25
will do. I figured there is an easy way to do it. but hacking my router seems like more fun.

---

### Post by JoshuaRL on 2009-10-25
> **MrWES said:**
> My parents did the same thing; I reset the router (via the router reset button, might be located on the backside and recessed) then plug into the router and point your browser to 192.168.1.1 and reset up the WiFi.

Also, I wrote the router login, passwd and passkey phrase on a post-it note and taped it to the bottom of the router :)

Bill

Mine is different, and so may be lots of others.  The best idea if you're looking to reset and change details on a router is to look up the make and model online.  For instance, one model different than mine has a different default login password.  So look on the bottom, be specific, and exercise your Google-fu.

---

### Post by elkanji on 2010-06-13
> **hellodoggie said:**
> What is a good one?

I've used [http://www.askstudent.com/hacking/how-to-crack-a-wep-key-using-ubuntu/](http://www.askstudent.com/hacking/how-to-crack-a-wep-key-using-ubuntu/) but have encountered some problems.

Me too, I can't use Kismet and some Aircrack commands don't work.

My wireless card is a Broadcom b43 type, the compatibility list says it works ... 

I'm trying to figure out what exactly I need 2 do to get everything working, as in is there a problem with my drivers, or I'm missing configuration stuff ... 

I got to the point where I'm looking at b43fwcutter but I'm really very inexperienced with linux. I know how to navigate an OS but this all new to me.

However, I'd like to learn more of linux that's why i'm here :popcorn:

---

### Post by anewguy on 2010-06-13
> **elkanji said:**
> Me too, I can't use Kismet and some Aircrack commands don't work.

My wireless card is a Broadcom b43 type, the compatibility list says it works ... 

I'm trying to figure out what exactly I need 2 do to get everything working, as in is there a problem with my drivers, or I'm missing configuration stuff ... 

I got to the point where I'm looking at b43fwcutter but I'm really very inexperienced with linux. I know how to navigate an OS but this all new to me.

However, I'd like to learn more of linux that's why i'm here :popcorn:

If you need help getting your wireless adapter to work, please open another thread.

As for this thread, +1 on resetting the router.  If you are unable to do so, it suggests to us that you want this information for something other than looking at your router.  In that case, as noted earlier, it is considered illegal, and it is an infraction of forum rules to ask for, and for someone to post info or links to, information to be used for such a purpose.

Dave ;)

---

### Post by cariboo on 2010-06-13
> **dmizer said:**
> This thread will remain open for the time being, but please remember that the following points will earn infractions, warnings, and/or thread closure:

1) advocating WEP cracking without permission.
2) being unclear about the purpose for cracking WEP
3) posting/linking any howtos which advocate/suggest cracking WEP without permission.

Please note: this is not a comprehensive list. It is meant as a guideline and a reminder of where the line is.

Take note of dmizer's post before going any further.

---

### Post by migs73 on 2010-06-14
I in no way endorse the cracking of peoples wireless, and agree it should against forum rules to advocate it.
What worries me is why is Aircrack in the Ubuntu repositories in the first place??
Surely if somebody wanted to utilise it for some sort of development, they should be well enough versed in IT/Linux to compile it from source code, and leave it out of the repositories where some ne'er do well can have easy access to it and others wireless.

---

### Post by aeiah on 2010-06-14
> **migs73 said:**
> I in no way endorse the cracking of peoples wireless, and agree it should against forum rules to advocate it.
What worries me is why is Aircrack in the Ubuntu repositories in the first place??
Surely if somebody wanted to utilise it for some sort of development, they should be well enough versed in IT/Linux to compile it from source code, and leave it out of the repositories where some ne'er do well can have easy access to it and others wireless.

compiling aircrack from source is the easiest and least time consuming part of cracking wep, so leaving it out of the repos would serve no purpose.

the tutorials on the aircrack-ng website are probably the most useful guides for wep cracking etc, incidentally

---

### Post by migs73 on 2010-06-14
I am just wondering why it is in the repositories in the first place? It surely has limited legitimate uses, and its appearance in the repositories gives it an air of legitimacy (which it obviously is {lawyers take note):P}, but I think you get my meaning). This coupled with the nervousness of the moderators when people start to ask how to use it, gets me thinking? :confused:
NB I have no problems with this software (in fact I stumbled on this thread as my parents wireless has refused to let anybody except my dads laptop access it for the last 6 months and thought aircrack might be a solution. Looks like a reset and hope for the best as even wired connection with system password refuses access!) I am just kind of being a devils advocate.

---

### Post by new_tolinux on 2010-06-14
> **migs73 said:**
> This coupled with the nervousness of the moderators when people start to ask how to use it, gets me thinking? :confused:

That's not really different from the root login-part. There's a manual to it on the ubuntu site, but it's just not allowed to copy the steps from that manual onto this forum.
Therefore it's not strange that since something like hacking isn't allowed,  they should be nervous about threads which easily can become a "manual to hack your way into the world" even if the software to do it is all in the repositories.

For what it's worth, do a hard reset on the router and read the manual that came with it. That should give you the default admin login/password details you'll need to setup the router. The default wep-key is sometimes on a label at the bottom of the router, so you should look there either.
Besides all, wep is almost as insecure as having no security measures on your router therefore you should reconsider using wep at all. WPA/WPA2 is much more secure if a secure passphrase is used.

---

### Post by migs73 on 2010-06-14
From Wikipedia;
'In common parlance, a devil's advocate is someone who takes a position he or she does not necessarily agree with for the sake of argument.'
I believe knowledge is power, and if you know these things are out there, you can take steps to protect yourself (WPA for example, which my dads wireless is, definitely need to hit the reset now!).

NB I have tried the default password from a wired connection (from my dads laptop so I know it is not a mac id problem) to try and change the config etc. Didn't really want to muck around with it too much as it worked for him,just couldn't get my own connection when there, but have had to reinstall his OS (Vista) due to a virus (and it was due to be done after 3 years of bloating!) and thought now would be a good time.

---

### Post by new_tolinux on 2010-06-14
> **migs73 said:**
> NB I have tried the default password from a wired connection (from my dads laptop so I know it is not a mac id problem) to try and change the config etc. Didn't really want to muck around with it too much as it worked for him,just couldn't get my own connection when there, but have had to reinstall his OS (Vista) due to a virus (and it was due to be done after 3 years of bloating!) and thought now would be a good time.
Some routers require you to push a button on the back of it when a new laptop needs to connect. Other routers require that you do enable the mac-address of your machine in the router.

---

### Post by migs73 on 2010-06-14
I should still be able to connect via a cable/wireless using the default password to change the config? Especially when that machine can connect through it!
ie Laptop--> wireless--> internet = no problem
Same Laptop --> wireless --> router (to reconfig) with password (default or WPA/WPA2) = No

Same with LAN connection.

As I said reset button and hope for the best.

Anyway this is off topic, if I hit any problems when I do do it expect a new thread. 
Thanks for the advice

---

