---
title: "Hard cpu lockup after few seconds of boot"
date: 2015-08-20
forum: New to Ubuntu
---

### Post by Justin_Kyle_Ramos on 2015-08-20
I'm a complete novice when it comes to linux so please attempt to simplify what you recommend me to do
After installing 15.04, i get hard lockups after 10 or so seconds of boot. I have a 2013 Alienware 17 (aka the first generation),intel i7 4700mq,nvidia gtx770m.
Any suggestions to what i should do?
ill add a picture next reply

---

### Post by tgalati4 on 2015-08-20
Welcome to the forums.  Is your CPU fan spinning?  Have you cleaned out the machine and reseated the connections?  It could be a power supply problem.

---

### Post by Justin_Kyle_Ramos on 2015-08-21
the fan still spins. i use a laptop so i cant reset any connections or clean the machine. it just says on the console something about a hard lockup and a lot more things i don't understand

---

### Post by Justin_Kyle_Ramos on 2015-08-21
so i waited a few minutes on the lockscreen of Ubuntu, nothing happens. it only happens when i log in to my account

---

### Post by tgalati4 on 2015-08-21
It would be helpful to get a screen shot with some of those messages.  Try using a camera or phone.  Hit the Pause key just before the point it freezes.  Then take a picture.  It could be a graphics card issue.  Does your machine boot into a Live Session using a bootable USB stick?

---

### Post by tristan16 on 2015-08-21
Definitely sounds like a problem with the graphics. At the lockscreen, hit Ctrl + Alt + F1 to get to a text terminal, log in with your username and password, then run the following command:
```

sudo apt-get install nvidia-346

```

Once that's been installed,
```

reboot

```

See if you still have an issue with the Nvidia drivers installed.

---

