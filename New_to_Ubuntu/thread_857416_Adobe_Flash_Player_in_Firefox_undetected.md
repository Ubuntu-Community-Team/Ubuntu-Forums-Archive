---
title: "Adobe Flash Player in Firefox undetected"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by SamerBerjawi on 2008-07-12
I have the adobe flash player installed on firefox and suddenly it is no more detected, I tried to install it again, but I got that it is installed!
I can't find it on the add-ons list, how can I fix that?

---

### Post by aysiu on 2008-07-12
By what method did you install it?

---

### Post by SamerBerjawi on 2008-07-13
By the usual method, when you open a page that requires flash player, you get below the Tabs Bar that a an add-on is missing, i clicked on it and etc..
It was working fine but now suddenly it is not!

---

### Post by ./. on 2008-07-13
Have you tried installing Flash from source?

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

---

### Post by aysiu on 2008-07-13
> **SamerBerjawi said:**
> By the usual method, when you open a page that requires flash player, you get below the Tabs Bar that a an add-on is missing, i clicked on it and etc..
It was working fine but now suddenly it is not!
Can you paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then post the output back here? ```
cat /etc/apt/sources.list
sudo apt-get update
sudo apt-get install flashplugin-nonfree
ls /usr/lib/mozilla/plugins
ls -l /usr/bin/firefox
```

---

### Post by Unotforme on 2008-07-15
> **aysiu said:**
> 
sudo apt-get install flashplugin-nonfree
[/code]

I've been struggling to get flash installed. The instructions on the adobe site don't list that command. I just ran the above command and it ran fine!

---

