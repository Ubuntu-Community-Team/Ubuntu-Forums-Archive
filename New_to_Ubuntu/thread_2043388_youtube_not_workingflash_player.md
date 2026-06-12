---
title: "youtube not working/flash player"
date: 2012-08-16
forum: New to Ubuntu
---

### Post by evansj on 2012-08-16
hi,
I have recently installed flash player in ubuntu from the software store and tryed to play a video on you tube however Firefox does not load the video it just loads a black box and everything else on the page.

any ideas
james

---

### Post by NikTh on 2012-08-16
Hi Evansj and welcome to UbuntuForums.org

Please open a terminal (ctrl+alt+t) and copy-paste from here these 3 commands , one at time
```
cat /etc/lsb-release && uname -r 
apt-cache policy adobe-flashplugin
apt-cache policy flashplugin-installer
```post back the results but..
..put the results inside [CODE] tags , by highlighting the text and click the** #** symbol on top of message pane.
Thanks

---

### Post by evansj on 2012-08-16
sorry didn't quite understand how to put the results in  code tag so have just posted the results in without the tags i have separated each command result with a line

  	 	 	 	 	 	   DISTRIB_ID=Ubuntu 
 DISTRIB_RELEASE=12.04 
 DISTRIB_CODENAME=precise 
 DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS" 
  3.2.0-29-generic-pae 
 

 

 adobe-flashplugin: 
   Installed: (none) 
   Candidate: (none) 
    Version table: 
 

 flashplugin-installer: 
   Installed: 11.2.202.238ubuntu0.12.04.1 
   Candidate: 11.2.202.238ubuntu0.12.04.1 
   Version table: 
  *** 11.2.202.238ubuntu0.12.04.1 0 
         500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/multiverse i386 Packages 
         500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/multiverse i386 Packages 
         100 /var/lib/dpkg/status 
      11.2.202.233ubuntu2 0 
          500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/multiverse i386 Packages 
 

 hope this is OK

James

---

### Post by NikTh on 2012-08-16
Deleted .

---

### Post by NikTh on 2012-08-16
Hi , 
ok try this 
```
sudo apt-get purge flasplugin-installer 
sudo apt-get install adobe-flashplugin
```you can also try to install all restricted extras (including adobe-flash) , with this command
```
sudo apt-get install ubuntu-restricted-extras
```but first run purge command (1st).


> **evansj said:**
> sorry didn't quite understand how to put the results in  code tag 

When you click on "New Reply" you can highlighting the output and then click on the  [IMG]http://ubuntuforums.org/images/editor/code.gif[/IMG] button in the message toolbar.

---

### Post by SeijiSensei on 2012-08-16
You'll need to [activate]("https://help.ubuntu.com/community/Repositories/Ubuntu/") the "partner" repository to install adobe-flashplugin.

---

