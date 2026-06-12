---
title: "Install Firefox 2 into 8.10 intrepid Gnome"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by model citizen on 2008-11-20
Hi all,

Apologies if this is a stupid question, I searched the forums and couldn't find what I want (though I bet it's there!). Anyway, I'm running Ubuntu 8.10 Gnome on my eee pc and everything's great but I don't like firefox 3. Can anyone help me to install the old firefox 2 whch I find faster? 

Cheers!

---

### Post by shifty_powers on 2008-11-20
nad also vulnerable to several security issues that won't be patched.

they are ceasing support for ff2. i would recommend trying another browser, there are plenty out there.

seamonkey, opera, flock....

---

### Post by ibuclaw on 2008-11-20
Create a copy of your sources.list file and edit it so all instances of "intrepid" are renamed to "hardy".

Easiest way to do this:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.d/hardy.list
sudo sed -i 's/intrepid/hardy/g' /etc/apt/sources.list.d/hardy.list
sudo apt-get update

```
Then open up synaptic and install the package **firefox-2**

Though, I agree with shifty_powers... it is no longer supported, so may be liable to security issues.

There are nice lightweight browsers out there, such as **Swiftfox**, **Epiphany** or Debian's **Iceweasel**

Regards
Iain

---

### Post by model citizen on 2008-11-20
Thanks for such a quick response guys. Ahh gutted, I really wanted the old firefox but not if it's going to be dodgy for security. Think I'll take a look at the alternatives you posted, 

Cheers

---

### Post by shifty_powers on 2008-11-20
well seamonkey is based on mozilla, as is flock. opera rocks too.

dude, there are LOADS of borwsers. i'm sure you'll find one that'll suit you :D

---

