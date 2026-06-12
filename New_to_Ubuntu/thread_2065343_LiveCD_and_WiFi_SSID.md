---
title: "LiveCD and WiFi SSID"
date: 2012-10-01
forum: New to Ubuntu
---

### Post by jsbulat on 2012-10-01
Hi,

I wonder if i can modify LiveCD to store SSID and password for wifi.
I am moving often form one home to another and have 2 WiFi setups.
Lets say SSID *HomeOne *with password *sweethome* and HomeTwo with password *homesweet*.

Can i modify LiveCD to automatically connect to wifi in both locations?
I do not want to use persistent image though.

Sincerely,
jsbulat.

---

### Post by newb85 on 2012-10-01
Retaining settings without a persistent image?  I believe that would be called having your cake and eating it, too.

---

### Post by androssofer on 2012-10-02
> **newb85 said:**
> Retaining settings without a persistent image?  I believe that would be called having your cake and eating it, too.

+1

a live usb with persistent space is the only way to achieve this.. 

is it perhaps for privacy issues you do not want a persistent image?

---

### Post by jsbulat on 2012-10-02
Not exactly a privacy - more like security and simplicity reasons:
1) I want simple setup that even my wife can use;
2) Simple upgrade from version to version.
3) I believe there is only one way to be 100% virus free - booting from cd (never heard of virus that can infect cd :D)

I realize that it is impossible to setup wifi and save settings after i have burned cd.
But is it possible to setup WiFi **before** burning cd by modifying image? And then use it with these settings permanently burnt in to cd.

I am planning to use it to work with bank accounts, so trojans and viruses are really concern me.

---

### Post by androssofer on 2012-10-02
> **jsbulat said:**
> Not exactly a privacy - more like security and simplicity reasons:
1) I want simple setup that even my wife can use;
2) Simple upgrade from version to version.
3) I believe there is only one way to be 100% virus free - booting from cd (never heard of virus that can infect cd :D)

I realize that it is impossible to setup wifi and save settings after i have burned cd.
But is it possible to setup WiFi **before** burning cd by modifying image? And then use it with these settings permanently burnt in to cd.

I am planning to use it to work with bank accounts, so trojans and viruses are really concern me.

its most likely less safe to boot from disk than installing it.. as while the virus won't persist from boot to boot. The system is still accessible whilst it's running.. and as there aren't many linux virus, there are a number of web browser and java exploits. I would worry more about the later.

so as you cannot install the latest updates to fill security holes. Those vulnerabilities will remain exploitable while the system is running. 

However if you install it, or boot from a usb system with a persistent file, you can install updates to patch the gaps.. 

Ubuntu is a lot more safe than windows.. So i'd say you are fine using it for online banking etc... 

if your really concerned here is more info on how to make your system super secure:

[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)

---

### Post by jsbulat on 2012-10-02
Thank you, androssofer.

The link to security improvement you gave me is beyond my understanding at this point. I am just starting to explore linux.

Probably i should start with persistent live usb and see where  it brings me.

Thank you for your help.

---

