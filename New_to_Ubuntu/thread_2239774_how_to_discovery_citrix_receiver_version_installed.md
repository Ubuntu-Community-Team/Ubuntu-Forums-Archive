---
title: "how to discovery citrix receiver version installed"
date: 2014-08-15
forum: New to Ubuntu
---

### Post by deme2 on 2014-08-15
I am very new in Ubuntu and I am coming from Windows. Basically in Windows when you want to know the version just open the application and look for About or you can go to program files and it my answer in some cases. Well I was asked what is the version of Citrix Receiver I am using and I didn't discovery it yet. I open the citrix by open the url ([https://vendor.apps.some_company.com/Citrix/XenApp/site/preferences.aspx](https://vendor.apps.some_company.com/Citrix/XenApp/site/preferences.aspx)) in my Firefox (opened as sudo). I try find out some About but I couldn't then I try to look in the folder and I see it under /opt/Citrix/ICAClient but I don't understand how to discovery the version from there. I searched in the internet and the samples below didin't help:

deme@PC:~$ apt-show-versions Citrix
Citrix not installed (not available)

deme@PC:~$ apt-show-versions Citrix-receiver
Citrix-receiver not installed (not available)

deme@PC:~$ dpkg -l citrix
dpkg-query: no packages found matching citrix

---

### Post by Rob Sayer on 2014-08-16
You wouldn't have to open firefox as root to install software.  Don't open a browser as root ever again.  It's not secure.

That link looks extremely flaky.  it's not from the actual citrix site, which has multiple .deb files for dl'ing.

---

### Post by deme2 on 2014-08-16
well the only way I found to make citrix works in Ubuntu is starting firefox as root otherwise definitely it does not work. But coming back to my question, how can I figure out what is the current version installed in?

---

### Post by Rob Sayer on 2014-08-16
That was related to your question.  You apparently used a very, very flaky looking site to install something in a very flaky looking way.  You can't find it now.  Did you look in  /opt/Citrix/ICAClient?

ANYTHING that would require you to run in firefox started as root I would consider malware.  I'd try the *actual* citrix site if I were you.

---

### Post by deme2 on 2014-08-17
Which file from [COLOR=#000000]/opt/Citrix/ICAClient as showed in the image can tell me my version? I have to discovery this.[/COLOR]

[IMG]/home/deme/temp/ICAClient.png[/IMG]

---

### Post by deme2 on 2014-08-20
I am still looking for how to figure out which version I am using. My question can be approached as more generic question: how can I find a version from applications installed and stored in [COLOR=#000000]/opt/Citrix/ICAClient?[/COLOR]

---

### Post by Jonathan Precise on 2014-08-21
> **deme2 said:**
> I am still looking for how to figure out which version I am using. My question can be approached as more generic question...

It all depends on your app. Can you upload a screenshot of your app by going to attachments? (Don't use the [IMG]inline image[/IMG] tool for files in your PC. Use it for online images.)

P.S.: The link doesn't work for me.

---

### Post by Jonathan Precise on 2014-08-21
> **Rob Sayer said:**
> ANYTHING that would require you to run in firefox started as root I would consider malware.

Not necessarily. Maybe the OP downloaded something that needs to be run as root once downloaded, but since he/she is accustomed to click on the download instead of running [FONT=Courier New]sudo /home/**USER**/Downloads/_file-to.run_[/FONT], then running firefox as root fixes that as the downloaded file will be run as root.

Personally though, I like running the program from the cmd, so [FONT=Courier New]sudo -i /home/jonathan/Downloads/file-to.run[/FONT] isn't a problem for me.

---

### Post by deme2 on 2014-08-21
Jonathan, thank for your help. I am very begginer in linux and citrix as well. To express myself please let me tell what I would do to discovery any application version in Windows. I would open the application and look for About window or some similiar thing or I would go to programming files folder, find the exe file and then accordinly to the file name I might figure out the version. 
**What is the equivalent exe file from the attachement folder in Ubuntu?**
Let me describe the steps I do to log in my virtual machine from Linux or Windows every: I have to open a browser as administrator and then access the url [http://vendor.apps.some_company.com/](http://vendor.apps.some_company.com/) and that is it. From this point everything is the same no matter if it is Linux or Windows: I will type my citrix password and later my windows password. I am completed lost how to figure out the Citrix version in Ubuntu.

---

### Post by Jonathan Precise on 2014-08-21
The url doesn't seem to be working:

[ATTACH=CONFIG]255695[/ATTACH][ATTACH=CONFIG]255696[/ATTACH]

---

### Post by Jonathan Precise on 2014-08-21
> **deme2 said:**
> ...
**What is the equivalent exe file from the attachement folder in Ubuntu?**
...

Those files that have an icon that looks like gears, those are the equivalents to .exe files. Scripts (very common in ubuntu/linux) normally end in .sh (and always the icon looks like a text file) and are equivalent to .bat files. When running a program in Ubuntu, it can be a script or the one that has an icon that looks like gears.

Yes, it does look suspicious where you got it from. Try uninstalling citrix by running:

```
rm -rf /opt/Citrix
```

and downloading the [32-bit]("http://downloads.citrix.com/akdlm/8618/icaclient_13.0.0.256735_i386.deb?__gda__=1408641944_123079f8b7d9663904ca19fe3c9a085d&__dlmgda__=1408724860_5a7a7c7404b314983de022c9720ab3ef&fileExt=.deb") version or the [64-bit]("http://downloads.citrix.com/akdlm/8618/icaclient_13.0.0.256735_amd64.deb?__gda__=1408641944_e05fa988bd0f3016c10aaada8544a8b0&__dlmgda__=1408725024_5bb552137ff20c86546ef0ebf7ff0cc3&fileExt=.deb") version (and the [32-bit]("http://downloads.citrix.com/akdlm/8618/ctxusb_2.4.256735_i386.deb?__gda__=1408641944_d845411c82eee360b916296dcb7eccf2&__dlmgda__=1408724980_6d0648e487ead657536e596d1a9f5530&fileExt=.deb")/[64-bit]("http://downloads.citrix.com/akdlm/8618/icaclient_13.0.0.256735_amd64.deb?__gda__=1408641944_e05fa988bd0f3016c10aaada8544a8b0&__dlmgda__=1408725024_5bb552137ff20c86546ef0ebf7ff0cc3&fileExt=.deb") USB support package) from [http://www.citrix.com/downloads/citrix-receiver/linux/receiver-for-linux-130.html](http://www.citrix.com/downloads/citrix-receiver/linux/receiver-for-linux-130.html)

---

