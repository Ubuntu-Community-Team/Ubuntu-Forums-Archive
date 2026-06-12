---
title: "Firefox 3 Java Help"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by forseti42 on 2008-04-26
I installed Java following the instructions, but when I try to play a game on Yahoo, it still says I am missing Java.  I've already tried a restart.

[http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting)
[http://www.java.com/en/download/help/5000010500.xml#enable](http://www.java.com/en/download/help/5000010500.xml#enable)

Thanks a bunch!
Ryan

---

### Post by NilsE on 2008-04-26
Look in about:config and see what plugin for Java is installed. 

If it is not the icedtea-gcjwebplugin plugin try to install it from Synaptic and see if that helps. You may need to remove whichever one is installed.

---

### Post by forseti42 on 2008-04-26
> **NilsE said:**
> Look in about:config and see what plugin for Java is installed. 

If it is not the icedtea-gcjwebplugin plugin try to install it from Synaptic and see if that helps. You may need to remove whichever one is installed.
How do I go about doing this?  The first part that is.

---

### Post by billgoldberg on 2008-04-26
> **forseti42 said:**
> How do I go about doing this?  The first part that is.

Just type about:config in firefox.

---

### Post by billgoldberg on 2008-04-26
You do know that the best way to install java is by just typing in a terminal

"sudo apt-get install ubuntu-restricted-extras"

That way java, flash and countless other much needed apps get installed.

ps: restarting the OS is never needed on ubuntu (well after installing software that is).

---

### Post by forseti42 on 2008-04-26
Did that.  Still no luck.

---

### Post by forseti42 on 2008-04-26
Ok, I just noticed this, but any sounds in Firefox don't work.  Whether it is embedded music on a webpage or youtube videos.  My sound is working though.

---

### Post by billgoldberg on 2008-04-26
> **forseti42 said:**
> Ok, I just noticed this, but any sounds in Firefox don't work.  Whether it is embedded music on a webpage or youtube videos.  My sound is working though.

You could always try another browser like epiphany (if you decide to use it also install it plugins packqge).

In the past I had more success running java in epiphany than I did in firefox.

About the firefox things, well, delete the flash player and java completely using synaptic and then install the restricted extras. Those should work fine.

---

### Post by SunnyRabbiera on 2008-04-26
> **forseti42 said:**
> Ok, I just noticed this, but any sounds in Firefox don't work.  Whether it is embedded music on a webpage or youtube videos.  My sound is working though.

well if you are using hardy I feel your pain as firefox 3 crashed out on me a few times.

---

### Post by gandaran on 2008-04-26
> **billgoldberg said:**
> You do know that the best way to install java is by just typing in a terminal

"sudo apt-get install ubuntu-restricted-extras"

That way java, flash and countless other much needed apps get installed.

ps: restarting the OS is never needed on ubuntu (well after installing software that is).

the ubuntu-restricted-extras is no longer the best way to install the restricted extras in ubuntu 8.04, this package will select open java for install.
it's best to go to synaptic and select sun-java6-plugin for install.

---

### Post by billgoldberg on 2008-04-26
> **gandaran said:**
> the ubuntu-restricted-extras is no longer the best way to install the restricted extras in ubuntu 8.04, this package will select open java for install.
it's best to go to synaptic and select sun-java6-plugin for install.

Oh, didn't now that.

---

