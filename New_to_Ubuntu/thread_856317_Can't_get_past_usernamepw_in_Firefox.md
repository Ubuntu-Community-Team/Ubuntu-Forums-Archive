---
title: "Can't get past username/pw in Firefox"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by donnyb on 2008-07-11
I have just created a Ubuntu 8.04 boot CD.  The CD boots just fine.  The problem I have is that when I try to use Firefox, it asks for a username and password.  How can I remove the need for this information?

---

### Post by quantumstitch on 2008-07-11
Is this after installation or from the live-cd?

---

### Post by phantomjoker on 2008-07-11
That sounds like your internet connection - unless it is asking for your ubuntu username etc. If it is asking for your ubuntu usrename etc then maybe go into settings and ask it to remember passwords for sites - which may stop it, but Im not sure... if its your internet username asked for then you need to configure your network connection...

---

### Post by MasterXandrex on 2008-07-11
Firefox doesn't ask for a username for the remember password function. Submit a screenshot so we might have further knowledge.


Xan

---

### Post by donnyb on 2008-07-11
This is on the live CD.  I used it one other time, but did not use Firefox that time.
I will submit a screen shot.

---

### Post by donnyb on 2008-07-11
I had a problem with the screen capture, but instead, wrote down what I saw.  First, I tried several other programs, but only Firefox would give a small pop-up menu that required a username and password.  FF is Version 3 Beta 5.

The small pop-up screen says: "Authentication Required.  Enter username and password for http://svctag-3kkxgb1:9017"  If I hit "OK" a few times I get a slightly bigger screen that says, "The site says - SmartFilter-NTLM"
I hope this means something, as I am a total beginner.

---

### Post by aysiu on 2008-07-11
Please submit a screenshot. That will tell us a lot.

To do a screenshot, press Alt-Print Scrn... or press Alt-F2 and type ```
gnome-screenshot
```

Once you've done that, [this](http://ubuntuforums.org/showpost.php?p=4527031&postcount=4) will help you upload the screenshot to the forums.

---

### Post by dracayr on 2008-07-11
It means that the site you want to visit requests a login, not firefox. Can't change anyting about that :popcorn:

dracayr

---

### Post by donnyb on 2008-07-11
Here is the screenshot.  Could this problem be from our server/network?  This computer is a work computer.

---

### Post by aysiu on 2008-07-11
That's weird. It looks as if it's trying to reach the Ubuntu start page but is, for some reason, requesting information from [http://svctag-3kkxgb1:9017](http://svctag-3kkxgb1:9017)

Do you have some kind of web filtering software active in your network?

---

### Post by aktiwers on 2008-07-11
Do you usually have to type in a username and password to login to the Internet?
It seams like the browser gets redirected to a page your ISP has setup, where you need to login?

---

### Post by dracayr on 2008-07-11
That's strange. does this happen with all pages you visit? My guess is that you have a proxy server that requires authentification. Is this possible?

dracayr

---

### Post by donnyb on 2008-07-11
I will take my computer home and try this again.  I suspect it may be some type of web filter, as you suggest.  BTW, I get the same message no matter what site I try (ie - Google.com, yahoo.com, MSN.COM, etc).

I will report my findings in a day or two.

---

### Post by mcduck on 2008-07-11
It might be thathte network connection requires logging in before you can access the web, and it automatically redirects you to the login page until you give it the username & password. Perhaps you should ask the admins about it?

When I lived in Denmark my internet connection required logging in after every boot, so whatever page I tried to open it just redirected me to the login page until I gave the username & password. Exactly in the same way that seems to be happening to you..

---

### Post by unutbu on 2008-07-11
Edit: Oops.

---

### Post by donnyb on 2008-07-11
I took my work computer home and when I tried to connect, it worked just fine.  When I login at work (Win XP) I do need a username/password, so assume it is setup not at the OS level, but at the network level - hence the username/password when using Ubuntu.

---

### Post by Frak on 2008-07-11
It really sounds as if there is a filter on your network, or the ISP requires login. $30 says that's already been mentioned.

EDIT
Yep, it has.

---

