---
title: "Wireless Issues"
date: 2012-08-28
forum: New to Ubuntu
---

### Post by allyveriah on 2012-08-28
Can't get webpages to load on firefox but I have signal on my works wireless. It worked fine until the school tech. by passed their system on it so I could use the net on campus. But the broswer loads half way and stops completely or it acts like it is still loading and will do this forever but never load the page. I have retyped the password many times with the same result. I am rather new to Linux and not really sure how to work it to be honest. Any help or advice to get this computer to pick up the internet would be lovely.
Right now it says I have 84% connection but it won't load any of my bookmarks D:
 
I was told to run a: 
echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf > /dev/null
 
But I have no idea what that means or how to even do it. -_- Yay for being new to linux and it messing up right off the bat lol.

---

### Post by PhantomTurtle on 2012-08-28
> **allyveriah said:**
> Can't get webpages to load on firefox but I have signal on my works wireless. It worked fine until the school tech. by passed their system on it so I could use the net on campus. But the broswer loads half way and stops completely or it acts like it is still loading and will do this forever but never load the page. I have retyped the password many times with the same result. I am rather new to Linux and not really sure how to work it to be honest. Any help or advice to get this computer to pick up the internet would be lovely.
Right now it says I have 84% connection but it won't load any of my bookmarks D:
 
I was told to run a: 
echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf > /dev/null
 
But I have no idea what that means or how to even do it. -_- Yay for being new to linux and it messing up right off the bat lol.

Basically what you want to do is (and I assume you are running Ubuntu with Unity) to open up terminal by searching it in the Dash. When Terminal opens just type in(or copy and paste, no ctrl-v for terminal just right click and press paste),

```
echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf > /dev/null
```

You will know when its finished because you will see something like,
```
phantom@phantom-deksktop: 
```
Try it after that, and I am not sure if a restart is required, but if it doesn't work do a restart as well.

---

