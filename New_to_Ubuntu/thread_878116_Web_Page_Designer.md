---
title: "Web Page Designer"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by Polish Rifle on 2008-08-02
When I was a Windows XP user I used a combination of Frontpage and Nvu, but I'm looking for a powerful Linux Web Page creator.  Any suggestions?

---

### Post by perlluver on 2008-08-02
> **Polish Rifle said:**
> When I was a Windows XP user I used a combination of Frontpage and Nvu, but I'm looking for a powerful Linux Web Page creator.  Any suggestions?

Well nvu works in Linux, but there is also Quanta.

---

### Post by MattBD on 2008-08-02
I recommend Kompozer. It's actually a more developed version of Nvu. Bluefish is also very good.

---

### Post by Polish Rifle on 2008-08-02
I guess I don't consider Nvu powerful, haha.

---

### Post by Polish Rifle on 2008-08-02
> **MattBD said:**
> I recommend Kompozer. It's actually a more developed version of Nvu. Bluefish is also very good.

Do I download the Linux package or the Debian package for Ubuntu 8.04?

---

### Post by MattBD on 2008-08-02
> **Polish Rifle said:**
> Do I download the Linux package or the Debian package for Ubuntu 8.04?

Neither. Just open a terminal and enter the following to get the version from the repositories:
```
sudo apt-get install kompozer
```
If you want to try Bluefish (which I would say is probably more powerful than Kompozer), then enter the following:
```
sudo apt-get install bluefish
```
It's always best to skip the version on the website and go for the version in the repositories if possible.

---

### Post by Paqman on 2008-08-02
Dreamweaver 8 also works very well if you install it through [Wine Doors](http://www.getdeb.net/app/Wine-Doors). You'll need  a valid license key for it, though.

Kompozer is probably the next best thing to Dreamweaver that's available for Linux. It's undergone a lot of development recently and could end up as a really good product.

Anything would be better than Frontpage though. That thing writes the ugliest code i've ever seen in my life.

---

### Post by Polish Rifle on 2008-08-02
I mostly hardcode (I'm not very good), but I want to start implementing more css and java in my websites, so I think bluefish might be my program.  I don't Kompozer has the java editor in it.

---

### Post by Paqman on 2008-08-02
> **Polish Rifle said:**
> I want to start implementing more css and java in my websites

My advice: go hard with css, go very light with javascript.

Not everybody even has javascript switched on, and lot of people block scripts. Don't use js for any vital function of your site, and make sure that it degrades gracefully and usably for any browser without it.

Css is unbelievably awesome though. Firefox 3 even passes the Acid2 test, so a huge chunk of users have just got a lot closer to the W3C standards.

---

### Post by Cotopaxi on 2009-04-17
From the different web page designers, which you mentioned: which one is the easiest to start for an absolute beginner and which one has the best tutorial or any tutorial at all?

Thanks! ;)

---

