---
title: "apt-get not working properly"
date: 2006-07-10
forum: Repositories &amp; Backports
---

### Post by sincereheart on 2006-07-10
Background / Current Environment:
I have 64 bit EMT Dell Machines. I installed AMD64 version of Ubuntu few days ago. 
I can connect to the outside world via command line. (Do not have Firefox installed as yet.. The installation failed...through apt-get.... Although I can do nslookup..)

Symptoms:
1.  Nevertheless my pings are not working properly. It goes in an uneding loop for all ping requests.. even for localhost... it has the same issues...
2.  apt-get is constantly causing problems. It seems to work partially. But then I do see problems with main and restricted repositories... and even in universe ...

Actions Taken
1.      I backed up and then modified the original /etc/apt/sources.list file. Enabled the entries for Universe. Did not un-comment any thing from Multiverse. So only going to use Universe (apart from main and restricted).

2.       Things seemed better. Tried doing an apt-get update. Was Able to get "lgn" probably login for some packages for the first time ever. However majority of these failed. Lot of failures came from main and restricted...
I wonder why... both of these are un-commented.

3.         Also tried removing the word "us" from the url links from sources.list.. (Since I am located in USA)
Still no luck......
(I wonder why can't DNS names be used for the lookup of repositories.. ).

4.        I was unable to do:
sudo apt-get install firefox

It seemed to work partially... as if going through the dependencies and installing them.. but then it also errored out..

Questions:
What am I missing. What are my options.
With command prompt, I am unable to use mouse. So difficult for me to do a copy paste of any file e.g.  sources.list. Since I do not have firefox so I am compelled to use a different machine to send messages or browse through any of the web sites... So I am pretty restricted in what I am able to do...

What log file do I look at for 'apt-get' errors...

I do not have gnome. I tried installing GNOME but same issues...

======================================================

---

### Post by sincereheart on 2006-07-10
FYI:
I have Ubuntu Server version (Drape) installed. 

=================================================

---

### Post by lordlollo on 2006-07-12
Sorry, why did you install the server edition if you did plan to use gnome and graphical stuff like firefox? :-k

---

