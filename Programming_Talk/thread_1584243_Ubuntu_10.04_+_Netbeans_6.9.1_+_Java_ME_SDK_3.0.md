---
title: "Ubuntu 10.04 + Netbeans 6.9.1 + Java ME SDK 3.0?"
date: 2010-09-28
forum: Programming Talk
---

### Post by moinster on 2010-09-28
I was wondering if there is anyway to get Java ME SDK 3.0 on Linux to be used with Netbeans 6.9.1?

Anyone know if there is a workaround...? Or should I just run Netbeans on my Windows partition? :/

---

### Post by psycho5 on 2010-09-29
I suppose you could download Java ME SDK 3.0 from the website, install it at your home directory 

Then when running netbeans install, just specify --javahome ?

I am running netbeans 6.9.1 but with JDK version 6 release 21

---

### Post by lykeion on 2010-09-29
A linux version of JavaME 3.0 SDK isn't available. When 3.0 was released a year and a half ago I thought the linux version would soon follow. Now I have given up any hopes on this. 
IMO J2ME development as a whole is very shaky. Many mobile developers are leaving JavaME to develop for the Android or iPhone platform.
To get back to your question, some people claim that they used the windows version of the JavaME 3.0 SDK, and just copied the relevant libraries to be able to do development in linux, see:
[http://stackoverflow.com/questions/2291060/java-me-3-0-sdk-on-linux](http://stackoverflow.com/questions/2291060/java-me-3-0-sdk-on-linux)
I've tried this myself but didn't succeed, so for now I use the 2.5.2 SDK in linux and when I need 3.0 SDK I have to boot into windows. But mostly I concentrate on Android nowadays.

---

