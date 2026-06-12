---
title: "Changing Login Screen with 8.04"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by noiseordinance on 2008-04-29
When I click login window (System > Administration > Login Window), it asks me for my password and then the hard drive proceeds to click away and do nothing. It continues to do this until the computer completely shuts down. It does this after two different installs of 8.04. Any pointers?

---

### Post by Michael.Godawski on 2008-04-29
Such things come to my mind:
Are your CDs burned properly? Checked for defects and md5?
Do you have tried the alternate text installation?
Any error messages?

---

### Post by noiseordinance on 2008-04-29
How do I know if the CD is burned correctly? I did the data verify when I installed. I didn't encounter any issues during install. I have not, however, tried the text install...

---

### Post by Michael.Godawski on 2008-04-29
When you boot with your CD there is an option to check the CD for defects. 

The text installation might help but has not to. According to your description of your problem it can be pretty much everything and nothing causing the problem. 

It is not easy to suggest something useful without some input but I also see you cannot provide us with more info.

---

### Post by asgard_command on 2008-04-29
I recently tried to change my login window settings and had trouble. The settings box didn't open and like you the hard drive was just clicking away. I gave up and then about 2 minutes later 3 settings windows opened ( I must have clicked it multiple times)
I didn't investigate further I assumed the pc had just been extra busy doing something else, but maybe there is some kind of small bug causing this.

---

### Post by noiseordinance on 2008-04-29
I agree with the small bug possibility. It didn't do this in 7.04 for me. Yet, it did this when I initially installed 8.04, as well as after my second install (botched wireless adapter installation).

---

### Post by Michael.Godawski on 2008-04-29
What happens if your launch the login window via the terminal?

```
sudo dbus-launch gdmsetup
```

---

### Post by noiseordinance on 2008-04-29
> **Michael.Godawski said:**
> What happens if your launch the login window via the terminal?

```
sudo dbus-launch gdmsetup
```

Same exact problem. The hard drive starts clicking, and the CPU churns at about 10-15%. I meant to add, I did do the check for defects.

Weird. As I was typing this, the window popped up, but after about 30 seconds...

---

### Post by encompass on 2008-04-29
Sounds like a fat memory bug... please search and report it to launchpad.net.  You can link to this thread too.
Congrats on finding the bug.

---

