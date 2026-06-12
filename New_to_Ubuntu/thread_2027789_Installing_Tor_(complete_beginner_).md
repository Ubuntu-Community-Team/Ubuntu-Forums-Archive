---
title: "Installing Tor (complete beginner )"
date: 2012-07-17
forum: New to Ubuntu
---

### Post by hazley on 2012-07-17
I'm using the latest version of ubuntu - Precise. I'm on the second latest update if that matters (?)

Anyway I'm completely new to this and I've yet to successfully download anything from the web. As of now I just want to focus on installing tor

I downloaded the bundle and I have no idea what to do with it so I then tried the way specified in this thread [[http://ubuntuforums.org/showthread.php?t=1547445&highlight=tor+fastest]](http://ubuntuforums.org/showthread.php?t=1547445&highlight=tor+fastest])
I copy pasted the text into the terminal and the next step was to install the torbutton add on for firefox, the only problem is that the link he gives is in german and seems to be broken anyway 

Any advice on this or something I can copy/past to simply extract from the bundle?

---

### Post by Paqman on 2012-07-17
If you just want Tor in a browser, the easiest thing to do is download the whole Tor browser bundle, extract it somewhere and click to run it. It contains all the components ready configured so it's no hassle. The only problem is that it won't update automatically (although it will tell you if it's out of date).

If you're wanting to run other stuff besides your browser through it you'll probably want to install the packages from the repos and configure it properly.

---

### Post by hazley on 2012-07-17
> **Paqman said:**
> If you just want Tor in a browser, the easiest thing to do is download the whole Tor browser bundle, extract it somewhere and click to run it. It contains all the components ready configured so it's no hassle. The only problem is that it won't update automatically (although it will tell you if it's out of date).

If you're wanting to run other stuff besides your browser through it you'll probably want to install the packages from the repos and configure it properly.
The thing is I have no idea how to extract

---

### Post by Paqman on 2012-07-17
> **hazley said:**
> The thing is I have no idea how to extract

Right click > extract here.

Or double click and choose a different location to extract into.

---

### Post by ub07 on 2012-07-17
If it's a *.tar.gz file you extract it by entering the following in a terminal window:



```
gunzip filname.tar.gz
``` 
That should give you a tar file. Then you need to do this:


```
tar -xvf filename.tar 
```

That should extract it.

---

### Post by Lars Noodén on 2012-07-17
@ub07, actually it can be extracted in one step

```

tar zxvf filename.tar.gz

```

However, to keep things tidy, I would strongly recommend working from the version in the repositories.  That makes it easier to uninstall, automates updates and upgrades, and manages dependencies (if any).

---

