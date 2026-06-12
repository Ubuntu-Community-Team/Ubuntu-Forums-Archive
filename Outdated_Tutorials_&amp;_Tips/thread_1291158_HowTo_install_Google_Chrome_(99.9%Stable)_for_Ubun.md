---
title: "HowTo: install Google Chrome (99.9%Stable) for Ubuntu"
date: 2009-10-14
forum: Outdated Tutorials &amp; Tips
---

### Post by baskar007 on 2009-10-14
Google Chrome for Linux released not yet. But we can use the developer edition of Google-Chrome, especially Google Chrome developer edition version 4.0.221.8 have more stable than other before releases. I think this version is a stable version for Linux, because i used Google chrome for 48hours yes two day, i did not find any major bug and other issues in this version.

[IMG]http://3.bp.blogspot.com/_bRIGrsC_jRk/StNx8EO5XeI/AAAAAAAAALY/Fz1KiPQGRiM/s320/snapshot100.png[/IMG]
May be this is a release version of google chrome? Who knows huh?


ok i'll write how do i get this latest version and installed on my ubuntu here.
this also work on Kubuntu as well

[IMG]http://1.bp.blogspot.com/_bRIGrsC_jRk/StNytb-iEXI/AAAAAAAAALg/zoPWHchloQM/s400/snapshot2.png[/IMG]

Add the Google software repository:
> $ sudo gedit /etc/apt/sources.list.d/google-chrome.list


wait a bit for open gedit, then add this line:
> deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable main
save the file.

Add signing key by run this command on terminal:
> $ wget -q -O - [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | sudo apt-key add -


Update sources list:
> $ sudo apt-get update


Install Google Chrome Dev Build:
> sudo aptitude install google-chrome-unstable


press alt F2 and type "google-chrome" to run the app or you can find the link in Internet folder of your application list.

Same detail on my BlogPAge: [softwareroxer]("http://softwareroxer.blogspot.com/2009/10/google-chrome402218-dev-for-ubuntulinux.html")

If you have a time, just give a visit to my blog. 
Thankyou!
[CENTER]Google Chrome and Google-Team Rocks !
[/CENTER]

---

### Post by ptcbus on 2009-12-06
People who do not want to use the command line could use the synaptic package manager to install chrome. See step by step instructions here: [Link]("http://ptcbus.blogspot.com/2009/11/installing-chromium-google-chrome-for.html")

---

### Post by Sciamano on 2009-12-18
Anyone knows how to make links (in an email message or in an RSS feed) open in a new tab in Chrome?
Thanks!

---

### Post by Henrikx on 2009-12-18
**SRWare Iron: The browser of the future - based on the free                    Sourcecode "Chromium" - without any problems   at privacy and security**

[Chrome vs Iron]("http://www.srware.net/en/software_srware_iron_chrome_vs_iron.php")
 [Chrome]("http://www.srware.net/en/software_srware_iron.php")

---

