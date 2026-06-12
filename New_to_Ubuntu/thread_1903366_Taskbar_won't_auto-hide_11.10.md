---
title: "Taskbar won't auto-hide 11.10"
date: 2012-01-02
forum: New to Ubuntu
---

### Post by Letty89 on 2012-01-02
My taskbar isn't auto-hiding anymore. I don't know what happened to it but it collapsed all day yesterday up until like 8pm. I know practically nothing about my OS. I'm on a netbook so screen space is of the up most importance. The bar stays out and takes up room so I can't even see everything on a browser page and I don't have the horizontal scroll bar on the bottom either. Help!

---

### Post by xc3RnbFO8P on 2012-01-02
Try in Terminal:
> unity --replace

---

### Post by Letty89 on 2012-01-02
> **Ringi said:**
> Try in Terminal:

Didn't work. :(

---

### Post by Nuno Machado on 2012-01-02
> **Letty89 said:**
> My taskbar isn't auto-hiding anymore. I don't know what happened to it but it collapsed all day yesterday up until like 8pm. I know practically nothing about my OS. I'm on a netbook so screen space is of the up most importance. The bar stays out and takes up room so I can't even see everything on a browser page and I don't have the horizontal scroll bar on the bottom either. Help!
Hi go to your terminal and run:

sudo apt-get install myunity

And then in that app you can control your Unity taskbar better

Thanks 

Nuno

---

### Post by audiomick on 2012-01-02
Thanks for that, Nuno. I have been waiting for something like that. Only thing is, myunity is not in the repos for 11.10. You have to install the ppa for it yourself. 

Here is the launchpad site:
[https://launchpad.net/myunity](https://launchpad.net/myunity)
[https://launchpad.net/~myunity/+archive/ppa]("https://launchpad.net/%7Emyunity/+archive/ppa")

Code to install the ppa and myunity, from this German language site:
[http://www.pc-magazin.de/news/ubuntu-linux-12-04-mit-neuem-unity-konfigurator-myunity-1222428.html](http://www.pc-magazin.de/news/ubuntu-linux-12-04-mit-neuem-unity-konfigurator-myunity-1222428.html)

```

sudo add-apt-repository ppa:myunity/ppa
sudo apt-get update && sudo apt-get install myunity

```I've installed it, and it seems to work. Don't know if it will solve the OP's problems, though. I would suggest switching the prefernces for the taskbar back and forwards a couple of times.

---

### Post by Nuno Machado on 2012-01-02
> **audiomick said:**
> Thanks for that, Nuno. I have been waiting for something like that. Only thing is, myunity is not in the repos for 11.10. You have to install the ppa for it yourself. 

Here is the launchpad site:
[https://launchpad.net/myunity](https://launchpad.net/myunity)
[https://launchpad.net/~myunity/+archive/ppa]("https://launchpad.net/%7Emyunity/+archive/ppa")

Code to install the ppa and myunity, from this German language site:
[http://www.pc-magazin.de/news/ubuntu-linux-12-04-mit-neuem-unity-konfigurator-myunity-1222428.html](http://www.pc-magazin.de/news/ubuntu-linux-12-04-mit-neuem-unity-konfigurator-myunity-1222428.html)

```

sudo add-apt-repository ppa:myunity/ppa sudo apt-get update && sudo apt-get install myunity

```

I've installed it, and it seems to work. Don't know if it will solve the OP's problems, though. I would suggest switching the prefernces for the taskbar back and forwards a couple of times.
Yes i forgot to post the repo as i had to do something here at work

Thanks for the edit

Nuno

---

### Post by Letty89 on 2012-01-02
> **audiomick said:**
> Thanks for that, Nuno. I have been waiting for something like that. Only thing is, myunity is not in the repos for 11.10. You have to install the ppa for it yourself. 

Here is the launchpad site:
[https://launchpad.net/myunity](https://launchpad.net/myunity)
[https://launchpad.net/~myunity/+archive/ppa]("https://launchpad.net/%7Emyunity/+archive/ppa")

Code to install the ppa and myunity, from this German language site:
[http://www.pc-magazin.de/news/ubuntu-linux-12-04-mit-neuem-unity-konfigurator-myunity-1222428.html](http://www.pc-magazin.de/news/ubuntu-linux-12-04-mit-neuem-unity-konfigurator-myunity-1222428.html)

```

sudo add-apt-repository ppa:myunity/ppa
sudo apt-get update && sudo apt-get install myunity

```I've installed it, and it seems to work. Don't know if it will solve the OP's problems, though. I would suggest switching the prefernces for the taskbar back and forwards a couple of times.

" I would suggest switching the prefernces for the taskbar back and forwards a couple of times."
Where do I find the preferences for it??

---

### Post by Nuno Machado on 2012-01-02
> **Letty89 said:**
> " I would suggest switching the prefernces for the taskbar back and forwards a couple of times."
Where do I find the preferences for it??
Inside the MyUnity app itself you can find many options to customize your Unity environment.

It works at first time you try, at least, mine did.

Hope it helped

Thanks

Nuno

---

### Post by audiomick on 2012-01-02
You would have to install that myunity application first. That is what I am referring to.
Do the code that I posted, one line at a time. 
Once it is installed, search for "myunity" in the dash and start it. I think the first tab is the one you need. Play around with the settings is the only advice I can offer. I only just installed the thing myself. 

The theory is, if you are lucky, one of the settings available in the application may be the one that has got stuck on your install, and changing it in the application may get it set back to where you want it. Hope it works... ;)

Perhaps I should add that I don't think you are risking trouble with this application. It appears that Canonical is in the process of including it in Ubuntu, so I am assuming it works ok.

---

### Post by Nuno Machado on 2012-01-02
> **Letty89 said:**
> " I would suggest switching the prefernces for the taskbar back and forwards a couple of times."
Where do I find the preferences for it??
And please if it is solved, please, mark the question as [SOLVED] on the topic

Thank you

Nuno

---

### Post by cmcanulty on 2012-01-02
on my laptop myunity settings don't stick even after logout and login

---

### Post by audiomick on 2012-01-02
Are you talking about 10.10 like it says under you Avatar? I don't think myunity claims to work before 11.04

---

### Post by audiomick on 2012-01-02
I just restarted mine to check. Seems like the settings are being retained.

---

### Post by cmcanulty on 2012-01-02
No I never noticed that I am running 11.10 usually classic but keep trying to configure Unity to test but the myunity doesn't keep any setting I put into it. I corrected the avatar

---

### Post by audiomick on 2012-01-02
Hmm. As I said, my settings stick on my 11.04 desktop. But we are hi-jacking this thread here. That is not nice... ;)

---

