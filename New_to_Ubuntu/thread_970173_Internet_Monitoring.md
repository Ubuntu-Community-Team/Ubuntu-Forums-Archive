---
title: "Internet Monitoring"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by Nyankan on 2008-11-03
I'm new to the whole Linux game, having a Linux only system running for only a month, but recently I discovered on my phone bill an abnormally high amount of Internet Usage. Researching Further, I discovered that there is something that every two seconds is downloading a single package, which may look small, but it builds up, and when your on a capped internet, its no good when it does that. Since I'm unfamiliar with whats supposed to be running, and whats not, I don't know what could be eating up my Internet Usage.

Can anyone recommend a program to monitor which applications access the internet and keeps a record of them, so I can pinpoint the application that is causing this? Or is there an application that is vital to Linux which downloads a package every 2 seconds, and if so, how do I change this to a longer time?

I'm still running 8.04, if thats of any help

---

### Post by talsemgeest on 2008-11-04
I can't think of any of the default applications or services that would do that. My default install of Ubuntu hardly ever accesses the internet without me accessing the internet, except to download updates. 

Are there any non-default programs that you have installed that might need to access the net?

---

### Post by Nyankan on 2008-11-04
> **talsemgeest said:**
> I can't think of any of the default applications or services that would do that. My default install of Ubuntu hardly ever accesses the internet without me accessing the internet, except to download updates. 

Are there any non-default programs that you have installed that might need to access the net?

I cant recall anything like that. The only program which I think I have downloaded that might access the internet at common times is the Firestarter Firewall. 

This is why I'm looking for a program that'll tell me what is accessing the internet when and log it for me. That way, I can find out whats causing it, and how to curb it

---

### Post by funchords on 2008-11-04
If I was having this problem, I would probably turn to an application called Wireshark 

**sudo apt-get install wireshark**

experiment a little with it so that you understand how it works, and then turn it on when you walk away from the keyboard and see what happened when you get back.  

Using the logs, you can probably figure out what the traffic is -- and then knowing that, you can probably figure out what app sends or receives it.

---

### Post by talsemgeest on 2008-11-04
Yeah, sorry I can't think of anything like that for Ubuntu. You might be looking for some kind of packet sniffer, but where to find one I have no idea.

Sorry I can't be of more help :(

---

### Post by Nyankan on 2008-11-04
> **funchords said:**
> If I was having this problem, I would probably turn to an application called Wireshark 

**sudo apt-get install wireshark**

experiment a little with it so that you understand how it works, and then turn it on when you walk away from the keyboard and see what happened when you get back.  

Using the logs, you can probably figure out what the traffic is -- and then knowing that, you can probably figure out what app sends or receives it.

Wonderful. I'll download it now and get back to you if its solved my problem or not

---

### Post by Nyankan on 2008-11-06
Well I figured out the problem, it was a ping between my router and my computer itself, and did not involve the internet connection at all, since it persisted when the computer was taken off the internet, but stopped when it was disconnected from the router. 

Thanks for your help, both of you

---

### Post by talsemgeest on 2008-11-06
I'm glad you figured it out. :)

---

