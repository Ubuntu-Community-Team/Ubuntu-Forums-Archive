---
title: "How to Add Chromium and Empathy to startup programs"
date: 2014-04-06
forum: New to Ubuntu
---

### Post by mckempt2 on 2014-04-06
I'm positive I got the wrong commands. I got thunderbird and pithos to startup on login, just can't do chromium or empathy the same way. Yelp? I just want to know the proper command or how to find the proper command. Thanks!

12.04 LTS

---

### Post by mckempt2 on 2014-04-06
figured it out. I capitalized the commands

---

### Post by Double.J on 2014-04-06
Hi there!

A very warm welcome to the forums!

Have you been using the 'Startup Applications' tool up until now? If not, it is the easiest way to manage your startup apps. just type startup into the search bar of the launcher and hit return.

So down to business, the commands. 90% of the time, it's just a case of using the packages name. in the case of empathy, this worked on my machine:
```
empathy
```
rebooted to test and boom, working.
now chromium didn't quite work. 
```
chromium
```
nudda, did nothing.

As a short cut, the code you want is:
```
chromium-browser
```

So how did I find out the package name? There's a couple of techniques - you could search in Synaptic Package Manager - if you have the package installed there will be a little green box to the left of the package. Or you could use the Ubuntu Software Centre - if installed there is a green tick. I prefer to search in the terminal. 

Now I can search all the installed packages on my system:
```
dpkg --get-selections | grep -v deinstall
```
(dpkg is the package manager behind the scenes that all these tools are using)

That's pretty useful if I'm going to be doing a reinstall, and want to know every package I have, but it's a lot of packages to wade through for an hour just to find the one I want. I can just search dpkg by pakage name. Now a heads up - dpkg search takes things very literally. if I search for chromium, it won't find any packages called 'chromium' and happily report back that it's 'not installed and no info is available' This is the same issue I had to start with - the package is not called 'chromium' What I can do it add an asterisk to the end of my search:
```
dpkg-query -l chromium*
```
This tells dpkg to search for any package that starts with 'chromium' no matter how it ends. My output was
```
jj@hostname:~$ dpkg-query -l chromium*Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                  Version               Description
+++-=====================-=====================-==========================================================
ii  chromium-browser      33.0.1750.152-0ubuntu Chromium browser
un  chromium-browser-insp <none>                (no description available)
ii  chromium-browser-l10n 33.0.1750.152-0ubuntu chromium-browser language packages
ii  chromium-codecs-ffmpe 33.0.1750.152-0ubuntu Free ffmpeg codecs for the Chromium Browser
un  chromium-codecs-ffmpe <none>                (no description available)
```
The ii means installed, So I have three packages installed starting chromium, the first one is the browser itself, so the package I want is 'chromium-browser'.
Finally I test this by calling the package name in a subshell:
```
(chromium-browser &)
```
This will launch the application. If it launches, then you can be pretty sure putting that package name in the code box of the startup applications will launch the app.** This is a good step to take even if you found out the package name from synaptic or the software centre**, and is why I search from the terminal to start with!

Finally if you are having no luck finding your package name you can try
```
apt-cache search chromium
```
This will search all packages known to the system and show you the hits with their description. This will be a much larger selection and can help you find obscurely named packages.

Hope it's all helped make things a bit clearer - I wanted to go into a bit of detail as understanding a bit of the packaging system will come in handy over and over again down the road!!

All the best, let us know how you got on!

Jj

PS note how none of the commands I gave used 'sudo'? we don't need admin privileges for any of these tasks, so it's best to get into the habit of only using it when needed early on!

Edit: Noticed now solved, Must have just missed it when I hit reply! hope this is useful info - don't forget to mark thread as solved!

---

