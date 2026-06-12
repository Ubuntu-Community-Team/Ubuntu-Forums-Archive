---
title: "New Project: CrackWiFiMachine"
date: 2011-05-27
forum: Programming Talk
---

### Post by hakermania on 2011-05-27
Cool title for an application, isn't it? xD

Before starting spamming that these things are illegal and that it isn't nice to do things that you wouldn't like to do to yourself, i'd like to make it clear that **this is not a hacking tool, it is a tool for penetration testing, for _REAL_**
I don't approve hacking in other people's network in any way. Consider that it is illegal to do so in most of the countries.
So, I had a try on the past on hacking a WEP password, it was my first touch with Backtrack Linux, I didn't know it was an OS then, I thought it was a program for hacking or something like that...
What I realized through my experience with all the available hacking tools out there is that I found them very hard to use. For example, the command line tools like aircrack-ng, airodump-ng and airmon-ng aren't at all user friendly. Don't forget that these tools are actually referring to simple people who want to test the security of their own network. They aren't hackers and they don't have to learn how to use terminal in order to do a simple "hack".
So, mainly, some info about this program:

[LIST]
[*]A user-friendly application so that you don't need to be a hacker to test your security.
[*]Included Instructions on the Help menu on how to test the security of WEP and WPA/WPA2 networks so as not to search blindly on the internet and hearing one thousand different opinions.
[*]Improve my writing code by providing you with the source and reading your suggestions.
[*]The program is written in C++ with Qt Creator and it is still being prepared.
[/LIST]
The only drawback is that it has to be run with gksudo because commands of the aircrack-ng package require this (this is not dangerous for this specific program, you can see the source and compile it yourself to see that nothing dangerous or suspicious is happening). Also, mention that normally this is the sixth improved version of the program but, because the previous versions were quite a fail, this is my first post I think for this app...

So far I have created a working General and WEP modems tab (so till now you can test the application only in WEP modems):
[IMG]http://img835.imageshack.us/img835/7599/generalpv.png[/IMG]

[IMG]http://img839.imageshack.us/img839/5454/wephacking.png[/IMG]

[IMG]http://img849.imageshack.us/img849/1747/wep.png[/IMG]

WPA/WPA2 isn't ready yet.
So, as you can see from the screenshots, you can create a project for each modem you test, which I find user friendly, while you can access the project files and modify them as you wish (via terminal for example)

So, what I need is suggestions on improvements that can be made in the layout or in the code itself and, additionally, I'd like to know your opinions about the program :)
Finally, mention that the packages macchanger and aircrack-ng are required
So, here is the program already compiled for 32-bit (run the Make file as root and the application will be installed, run the Unmake (lol) as root again to unistall the app):

[http://dl.dropbox.com/u/11379868/CrackWiFiMachine6%20-%20program.tar.gz]("http://dl.dropbox.com/u/11379868/CrackWiFiMachine6%20-%20program.tar.gz")

And here is the source code if anyone wants to have a look:

[http://dl.dropbox.com/u/11379868/CrackWiFiMachine6-source.tar.gz](http://dl.dropbox.com/u/11379868/CrackWiFiMachine6-source.tar.gz)

---

### Post by jon zendatta on 2011-05-30
when I get that far:
```
~/Desktop$ tar xzvf CrackWiFiMachine6-program.tar.gz
tar (child): CrackWiFiMachine6-program.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now

```
Tarball is extractable. **My error**

---

