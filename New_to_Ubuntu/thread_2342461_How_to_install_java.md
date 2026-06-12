---
title: "How to install java???"
date: 2016-11-07
forum: New to Ubuntu
---

### Post by guinea2 on 2016-11-07
Hi, I am new to ubuntu and I am trying to install java, I have the extracted folder in /usr/java/, but I can't open jar files or anything.. Is there a installer that i need or something I need to do?

---

### Post by Bucky Ball on 2016-11-07
Welcome. Install ubuntu-restricted-extras. That should do it. No need to do what you're doing and that may cause other issues.

Ubuntu not like Windows. You don't need to install everything from third-party sites, drivers and what not. It's reasonably rare you need to go to far away from the package manag, actually. 

Have a look at the first instructions for open-jdk (not java oracle) on [this page]("https://www.atlantic.net/community/howto/install-java-jre-jdk-on-ubuntu-16-04/"). And [this looks even simpler]("https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-get-on-ubuntu-16-04").

Hope that helps and good luck.

---

### Post by guinea2 on 2016-11-07
> **Bucky Ball said:**
> Welcome. Install ubuntu-restricted-extras. That should do it. No need to do what you're doing and that may cause other issues.

Ubuntu not like Windows. You don't need to install everything from third-party sites, drivers and what not. It's reasonably rare you need to go to far away from the package manag, actually. 

Have a look at the first instructions for open-jdk (not java oracle) on [this page]("https://www.atlantic.net/community/howto/install-java-jre-jdk-on-ubuntu-16-04/"). And [this looks even simpler]("https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-get-on-ubuntu-16-04").

Hope that helps and good luck.


Thanks, it worked for me!

---

### Post by Bucky Ball on 2016-11-07
Excellent news and thanks for marking as solved. :)

Best to check in the package manager for the app you're after and if it's not there ask here to start before grabbing stuff from a third-party. This applies mostly to apps. We sometimes get people that have used open-source, cross-platform apps in Win who get into trouble thinking they need to download and install the app from a third-party and things go pear-shaped when the app they're after is in Software Centre already. 

Some notables are VLC, Firefox, Thundbird, Skype. They're in the repos (Skype if you have 'Canonical Partners' repo enabled in 'Software and Updates> Other Software' tab).

PPAs are also used for things not in the official repos. It's like adding a private repository. Plenty are stable and supported but be careful with them. They are not officially supported and if they break, they break. Use at your own risk.

Enjoy. :)

---

