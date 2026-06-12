---
title: "How to install AWN dock in ubuntu 8.4?"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by Pagh on 2008-07-11
Hello everyone.

Is there anyone who can post a tutorial on how to install AWN dock under Ubuntu 8.4???
I would be very grateful.

Thanks.


- Kasper Roland Pagh

Ps. I'm not scared of using the shell if that's the fastest way to install AWN.

---

### Post by kk0sse54 on 2008-07-11
Open up the terminal and type ```
sudo apt-get install avant-window-navigator
```, type in your password and presto you got awn being installed on your computer :)
Or...if you want the GUI version just open up Add/Remove Programs and search for avant-window-navigator and install it from there.

---

### Post by Pagh on 2008-07-11
OH MY GOD. This is embarrassing!!! it's in the repository i didn't know that!

I remember to check properly next time.

I'm so stupid

anyway thanks for the quick reply.

all the best.

---

### Post by kk0sse54 on 2008-07-11
:lolflag: No prob mate we all make mistakes every now and then :-D

---

### Post by jacobroecker on 2008-09-27
Sorry--total newbie here:  What's the next step after this?

Where do I go to find it and configure how it looks?

-Jacob
[Trailbrain]("http://trailbrain.com/wiki")

---

### Post by bumanie on 2008-09-27
System --> Preferences --> AWN Manager

---

### Post by vishzilla on 2008-09-27
The applets are missing in the repos. Add these to the sources; reload and install ```
sudo apt-get install avant-window-navigator-trunk awn-manager-trunk awn-extras-applets-trunk
```

there you will have the latest version

---

### Post by twrock on 2008-09-30
> **vishzilla said:**
> The applets are missing in the repos. Add these to the sources; reload and install ```
sudo apt-get install avant-window-navigator-trunk awn-manager-trunk awn-extras-applets-trunk
```

there you will have the latest version

Can you tell us what the repo is for those?
Thanks.

---

### Post by Martje_001 on 2008-09-30
I think he uses:
```
deb http://ppa.launchpad.net/awn-testing/ubuntu intrepid main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu intrepid main
```

---

