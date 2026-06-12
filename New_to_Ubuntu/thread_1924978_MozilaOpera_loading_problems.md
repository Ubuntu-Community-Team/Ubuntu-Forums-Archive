---
title: "Mozila/Opera loading problems"
date: 2012-02-13
forum: New to Ubuntu
---

### Post by nemark on 2012-02-13
Sometime when i try to load pages like youtube facebook 9gag etc. they don't load completely actually they hardly ever do. The only thing that ranges is how much of it isn't loaded from this being the minimum : 
[http://www.uploadup.com/di-Z8W7.png](http://www.uploadup.com/di-Z8W7.png) to it only missing some thumbnail pictures.

I am running  Ubuntu 11.10 32bit on the following platform:
RAM 3.0 GiB
CPU Intel® Pentium(R) 4 CPU 3.00GHz
Graphics  GeForce 210/PCI/SSE2 

I tried playing with MTU but that hardly did anything  so i decided  to keep it on the defolat value of 1500.
I have java and flash support installed i tried it at kb2.adobe.com/cps/155/tn_15507.html and [http://java.com/en/download/testjava.jsp](http://java.com/en/download/testjava.jsp). I don't have schokwawe player installed but it doesn't support ubuntu unless you are using wine. Thanks for the help !

---

### Post by lovinglinux on 2012-02-13
Have you tried to disable ipv6?

See [http://www.webgapps.org/tutorials/firefox/troubleshooting/connection-issues-and-solutions](http://www.webgapps.org/tutorials/firefox/troubleshooting/connection-issues-and-solutions)

---

### Post by HiImTye on 2012-02-13
is this while you have no network load? i.e. you aren't downloading any torrents or any large files at high data rates

---

### Post by nemark on 2012-02-14
> **lovinglinux said:**
> Have you tried to disable ipv6?

See [http://www.webgapps.org/tutorials/firefox/troubleshooting/connection-issues-and-solutions](http://www.webgapps.org/tutorials/firefox/troubleshooting/connection-issues-and-solutions)

Thank you, i tried that but it didn't seam to work. I found it strange to switch ipv6 from false to true to disable it but i went with it but still no improvement . I did some online test again and they say i have no ipv6 (whether i  leave the settings on true or false). [www.test-ipv6.com]("http://www.test-ipv6.com") and [www.ismyipv6working.com]("http://www.ismyipv6working.com") 

 I thought that maybe youtube has some restrictions towards my country but it loads normally on my sisters computer ( running Windows XP)

---

### Post by nemark on 2012-02-14
> **HiImTye said:**
> is this while you have no network load? i.e. you aren't downloading any torrents or any large files at high data rates

Yes without any network load, it sometimes loads almost totally fine that is the strange thing. It sometimes work fine and sometimes it just doesn't :P I am using youtube as an example because it happens on it the most.

---

### Post by nemark on 2012-02-14
I just wanted to add a picture of it when it actually loads something [http://www.uploadup.com/di-DCMF.jpg](http://www.uploadup.com/di-DCMF.jpg)
This is how it looks most of the times when it actually loads. And just  to add one more time this doesn't happen only on youtube, i just took it  as an example.

---

### Post by lovinglinux on 2012-02-14
Try a different browser like Chrome or Opera, to see if the problem also occur with them or is limited to Firefox.

---

### Post by lovinglinux on 2012-02-14
Duplicate

---

### Post by nemark on 2012-02-19
> **lovinglinux said:**
> Try a different browser like Chrome or Opera, to see if the problem also occur with them or is limited to Firefox.

I tried it on opera and Firefox before opening this topic and the problem was the same on both, maybe a little worse on opera. I installed Chrome 3-4 days ago, and it did improve things. It is much rarer  that i get a useless page. Thing i noticed that google chrome asks me for a key ring password (or something like that) witch i guess gives it the permission to temporary store  data on my pc. So it got me thinking that maybe there is a problem with permissions because the browser manly has problem loading picture/, videos (stuff that is temporally saved on my pc).So is there something that i have maybe accidenttaly   activated / deactivated ?

---

### Post by lovinglinux on 2012-02-20
> **nemark said:**
> I tried it on opera and Firefox before opening this topic and the problem was the same on both, maybe a little worse on opera. I installed Chrome 3-4 days ago, and it did improve things. It is much rarer  that i get a useless page. Thing i noticed that google chrome asks me for a key ring password (or something like that) witch i guess gives it the permission to temporary store  data on my pc. So it got me thinking that maybe there is a problem with permissions because the browser manly has problem loading picture/, videos (stuff that is temporally saved on my pc).So is there something that i have maybe accidenttaly   activated / deactivated ?

When using Opera, what happens if you use Turbo mode?

---

