---
title: "SOLVED Thanks user name &amp; password apt"
date: 2013-07-17
forum: New to Ubuntu
---

### Post by arranskye on 2013-07-17
In windows I have been using a free apt called roboform.  Everytime I use a web site its added to my roboform profile and includes my user name and password for each website. visited.

I use robo form as my home page where it displays all the websites i use frequently. I click on the required website and I m able to enter immediately as the username and password have already been input by roboform.
I can also enter particular pages on websites.  For example Absolute beginners section on the Ubuntu forums.

Has Ubuntu got anything similar to this please.  Having used Roboform for some time and never needed to think about user names or passwords, I have forgotten a lot of them now.  I have looked in the software centre, and im not very good at guessing the names they would show under, so the ones i have tried appear to just hold the passwords.

Thanks

---

### Post by dino99 on 2013-07-17
i does not know how that roboform deal with security; but im translating it like : "open door" welcome page for all that want to glance/rob your browsing settings and private data. Quite scary to me.

[http://aahank.com/2013/install-keepass-on-ubuntu/](http://aahank.com/2013/install-keepass-on-ubuntu/)

---

### Post by VMC on 2013-07-17
@arranskye,[COLOR=#DD4814][COLOR=#000000]
[/COLOR][/COLOR]
Have you seen [THIS]("http://www.roboform.com/platforms/overview") page ?

---

### Post by Dave_L on 2013-07-17
> **arranskye said:**
> Has Ubuntu got anything similar to this please.

Firefox has similar functionality. It can store web site usernames/passwords, and its history auto-completion and bookmarks are helpful in accessing sites that you visit frequently.

As noted above, storing usernames/passwords is a tradeoff of convenience vs. security.

---

### Post by slickymaster on 2013-07-17
> **arranskye said:**
> In windows I have been using a free apt called roboform.  Everytime I use a web site its added to my roboform profile and includes my user name and password for each website. visited.

I use robo form as my home page where it displays all the websites i use frequently. I click on the required website and I m able to enter immediately as the username and password have already been input by roboform...

For what is described, it really seems that that application is a fatal security flaw and very dangerous to have on one's system. Once a malicious online attacker has access to your personal information, your life is literally over.

> **dino99 said:**
> ... [http://aahank.com/2013/install-keepass-on-ubuntu/](http://aahank.com/2013/install-keepass-on-ubuntu/)
+1
If want/need an application in order to fill in forms on websites, I also recommend you [KeePass]("http://keepass.info/help/v2/setup.html#mono"). You can add the PPA to your system, that way every time you update your *buntu box it will also be updated:```
sudo apt-add-repository ppa:jtaylor/keepass
sudo apt-get update
sudo apt-get install keepass2
```

---

### Post by arranskye on 2013-07-17
hi, Thanks for all your replies.  I should have mentioned, in Roboform, a master password is required to open the profile and this can also be used to secure the username & password for any chosen website.

Thanks for the link VMC but I have taken your security issues on board and will install keepass using the terminal as this gives me some practice, so thanks for the instructions.

cheers

---

### Post by VMC on 2013-07-17
One final thought. If you instead use keepassx, then you can use the same "keepassx.kdb" db file on both Windows and Linux - keepass and keepassx use different db's. Look into both before you decide. Read the differences between them found [HERE]("http://www.keepassx.org/forum/viewtopic.php?f=1&t=1701").

---

