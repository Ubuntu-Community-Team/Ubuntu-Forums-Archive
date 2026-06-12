---
title: "Looking for video editing/authoring software"
date: 2013-12-09
forum: New to Ubuntu
---

### Post by StevenN218 on 2013-12-09
Hello Everyone!
     I recently watched Revolution OS and have become a huge fan of the Linux movement. I am running Ubuntu 13.10 (Saucy Salamnder).
I tried installing Cinelerra and have read the past thread for installing it and still can't figure it out. When I type the command "sudo apt-get install cinelerra" this comes up:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package cinelerra is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'cinelerra' has no installation candidate

I have past video editing experience using Adobe CS4 Premier Pro. I installed kdenlive but I am looking for a video editor that will enable me to edit clips from an external drive without ever loading them on to internal drives in my cpu. To edit clips in kdenlive they have to be on my main internal drive. I am hoping like Adobe CS4 Premier Pro Cinelerra will let me do this.

 Any advice or suggestions?

With Peace and Thanks,
Newzzini

---

### Post by tgalati4 on 2013-12-09
[http://openshot.org/](http://openshot.org/)

---

### Post by StevenN218 on 2013-12-09
Thanks! this openshot does let me work from an external drive. But out of curioisity do you know how I can install Cinelerra or another program that is more professional?

---

### Post by asus-user on 2013-12-10
> **StevenN218 said:**
> But out of curioisity do you know how I can install Cinelerra or another program that is more professional?

you can find all the information needed for installing Cinelerra here: 
[URL="https://launchpad.net/~cinelerra-ppa/+archive/ppa"]https://launchpad.net/~cinelerra-ppa/+archive/ppa
[/URL]
Hope it works for you well.

---

### Post by philinux on 2013-12-10
See this [http://www.techdrivein.com/2013/09/top-5-video-editors-for-ubuntu-linux.html](http://www.techdrivein.com/2013/09/top-5-video-editors-for-ubuntu-linux.html)

And pitivi is in the repos.

---

### Post by StevenN218 on 2013-12-10
How do I make sure I  have both the Universe and Multiverse repositories enabled?

---

### Post by newb85 on 2013-12-10
Open "Software & Upddates" from the Dash.  It should be obvious from there.

If GUI differences complicate that approach, you could also do this:
```
cat /etc/apt/sources.list | grep universe
cat /etc/apt/sources.list | grep multiverse
```

If the repos are enabled, their deb lines won't be commented out with "#" at the beginning of the line.

---

