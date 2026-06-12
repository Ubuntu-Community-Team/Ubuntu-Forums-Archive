---
title: "Internet trouble"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by austinnormancore on 2008-07-30
I'm a very new Ubuntu user. 
I just installed ubuntu on my gateway laptop and I'm having some internet trouble. It picks up a network just fine, and it also says that it has a pretty good signal (generally 75-100%), however it acts like it has almost no signal. My service comes in waves. If I'm downloading something, it'll load for five seconds, then stall for five minutes. I keep refreshing the wireless selection, but it doesn't really fix anything.
Another problem is that occasionally it will decide not to find any wireless networks at all, and then the network manager will disappear from the top-right on the screen. I've gone back to the Network manager from the menu at the top left, but it isn't the same thing and doesn't help.
I then decided to simply plug in my computer and use a wired connection, only to find that it still does the exact same thing (I double checked and made sure it was connected to the Wired Connection). 
I know for a fct that it's not my internet, because I'm typing this on my mom's computer, which is picking up a signal just fine. I wasn't having this problem until I put ubuntu on it, so I'm pretty sure it has something to do with it.

Any pointers? I'm very much a noob when it comes to this stuff.
Thank you in advance.

---

### Post by JoneYee on 2008-07-30
> **austinnormancore said:**
> I'm a very new Ubuntu user. 
I just installed ubuntu on my gateway laptop and I'm having some internet trouble. It picks up a network just fine, and it also says that it has a pretty good signal (generally 75-100%), however it acts like it has almost no signal. My service comes in waves. If I'm downloading something, it'll load for five seconds, then stall for five minutes. I keep refreshing the wireless selection, but it doesn't really fix anything.
Another problem is that occasionally it will decide not to find any wireless networks at all, and then the network manager will disappear from the top-right on the screen. I've gone back to the Network manager from the menu at the top left, but it isn't the same thing and doesn't help.
I then decided to simply plug in my computer and use a wired connection, only to find that it still does the exact same thing (I double checked and made sure it was connected to the Wired Connection). 
I know for a fct that it's not my internet, because I'm typing this on my mom's computer, which is picking up a signal just fine. I wasn't having this problem until I put ubuntu on it, so I'm pretty sure it has something to do with it.

Any pointers? I'm very much a noob when it comes to this stuff.
Thank you in advance.

First off, the fact that two different network adapters have the same problem screams hardware to me.  Either the PCI pus on the machine or the router/switch you are connecting to.  

Could you give the output of *ifconfig* from Terminal.

Have you reset the router (power off, click the little pen sized reset button) then done the same on the cable/dsl modem?

The fact that network manager isn't coming up from time to time, I can't directly speak to that, but I would assume that its because it doesn't detect any networks.

EDIT: What exact type machine are you running?

---

### Post by northern lights on 2008-07-30
Can you please post the output of ```
sudo lshw -C network
```
Thank you.

---

