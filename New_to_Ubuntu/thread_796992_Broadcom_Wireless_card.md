---
title: "Broadcom Wireless card"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by pikabuntu on 2008-05-16
I have a broadcom card and i got it working a few weeks ago and to make a long story short, i reinstalled hardy and now i cant remember what made it work...

---

### Post by dizee on 2008-05-16
These threads may be useful [http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

### Post by Raccoon1400 on 2008-05-16
[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)

worked for me.

---

### Post by pikabuntu on 2008-05-16
i'm sorry, but those meant nothing to me :(
could someone give me something more clear?

---

### Post by Exsecrabilus on 2008-05-16
```
sudo apt-get install b43-fwcutter
```

A window will pop up asking you if you would like to extract firmware from the Internet.

Click and proceed through the steps.

After, just turn it on; click a button or whatever.

Your wireless card should now be working!

---

### Post by pikabuntu on 2008-05-16
> **Exsecrabilus said:**
> ```
sudo apt-get install b43-fwcutter
```

A window will pop up asking you if you would like to extract firmware from the Internet.

Click and proceed through the steps.

After, just turn it on; click a button or whatever.

Your wireless card should now be working!


this is what i got from that:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package b43-fwcutter

---

### Post by Exsecrabilus on 2008-05-16
Try going **System** >> **Administration** >> **Software Sources**.

Under **Ubuntu Software** tab, check boxes enabling the main, universe, restricted, and multiverse respositories.

Now click **Close** and wait for the things to download.

Now try the command in my previous post and tell us the results.

---

### Post by sam_delta on 2008-05-16
you need to activate your repos, ,, open the synaptic package manager under system>administration>synaptic package manager, and then click on tools>repositories, and check every repository that is unchecked (ex, universe, multiuniverse, supported, i duno the exact names just check them all)

then try again "sudo apt-get install b43-fwcutter"

tell us how it goes

sam

---

### Post by sam_delta on 2008-05-16
just to point out that ive heard that b43-fwcutter wont work if you install it via synaptic, because it wont fetch/download any firmware

sam

---

### Post by Exsecrabilus on 2008-05-16
Thanks for that, I'll edit my post.

---

### Post by pikabuntu on 2008-05-16
thanks sooooooo much.
that's not what i did last time, but it worked!!

---

### Post by Raccoon1400 on 2008-05-16
I haven't been able to get the card working with anything other than ndiswrapper.
See my link farther up the page.

---

### Post by sam_delta on 2008-05-16
@raccoon, yeah, different broadcoms chipset tend to work with b43-fwcutter, some others wont work and will need ndiswrapper, as it is your case.

@pika, no problem pika we have a great community here, glad its working , enjoy ubuntu

sam

---

### Post by pikabuntu on 2008-05-16
yeah, it is a great community, every time i have had a problem people have been able to help right away. anyway, thanks for the help everyone!!!

---

