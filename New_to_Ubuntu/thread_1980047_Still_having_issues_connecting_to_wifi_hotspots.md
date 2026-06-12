---
title: "Still having issues connecting to wifi hotspots"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by Marcus Zion on 2012-05-14
Back when I had Windows I could easily pull up to any given place that has wifi and connect without issue with Ubuntu 11.10 this isn't happening. Most public networks that aren't secured like at lower end hotels, cafes and fast food restaurants have this little redirect that sends you to this user agreement page. 

My browser which is Firefox on occasion will redirect to it but 75% of the time it won't and I can't get on the internet without agreeing to the user agreement. I have to reset my connection several times before it actually starts working properly. So what is the issue here because this problem is more and more on my nerves.

Edit: The connection doesn't last more than a few minutes before it's completely lost. "Look for..." or "Unable to connect" sound familiar?

What is Iced Tea and how do I replace it with Java?

---

### Post by choppyfireballs on 2012-05-14
> **Marcus Zion said:**
> Back when I had Windows I could easily pull up to any given place that has wifi and connect without issue with Ubuntu 11.10 this isn't happening. Most public networks that aren't secured like at lower end hotels, cafes and fast food restaurants have this little redirect that sends you to this user agreement page. 
 
My browser on occasion will redirect to it but 75% of the time it won't and I can't get on the internet without agreeing to the user agreement. I have to reset my connection several times before it actually starts working properly. So what is the issue here because this problem is more and more on my nerves.
 
 
What i would try is go to your home network or get internet access however you can and install the java runtime plugins i.e java jre, java applet and java sdk a lot of the agreement pages are made using the java applet so I would try that and see if that will redirect you properly also what browser are you using.

---

### Post by Marcus Zion on 2012-05-14
> **choppyfireballs said:**
> What i would try is go to your home network or get internet access however you can and install the java runtime plugins i.e java jre, java applet and java sdk a lot of the agreement pages are made using the java applet so I would try that and see if that will redirect you properly also what browser are you using.
Firefox.

---

### Post by HiImTye on 2012-05-14
sometimes it's just a case of loading a webpage that doesn't use https:// in favor of one that uses http://

but give that java option a try, just to be sure

---

### Post by Marcus Zion on 2012-05-14
Updated the status on my problem. How do I get a Java plugin for Firefox on Ubuntu 11.10?

---

### Post by numand on 2012-05-14
@Marcus Zion, you can use Java which is provided from Ubuntu by giving ```
sudo apt-get install openjdk-7-jre
``` command or you can use java which is provided by Sun by giving ```
sudo add-apt-repository ppa:ferramroberto/java
sudo apt-get update
sudo apt-get install sun-java6-jdk sun java6-plugin
``` command. You can choose whichever java you want to use by giving ```
sudo update-alternatives --java
``` command

---

