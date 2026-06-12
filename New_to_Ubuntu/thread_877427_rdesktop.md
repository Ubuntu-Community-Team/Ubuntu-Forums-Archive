---
title: "rdesktop"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by Bigbob22 on 2008-08-01
I am trying to connect from my Ubuntu computer to a Vista computer, but it is not working. What should I do to fix this?

---

### Post by Bigbob22 on 2008-08-01
Please help.

---

### Post by tommynz1975 on 2008-08-01
If you are wanting to share out a folder to vista?

here is a cool video I found on youtube.  helped me out a lot.

[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

Have Fun..

---

### Post by Bigbob22 on 2008-08-01
No I was wanting to connect to vista using rdesktop for remote desktop. My mom has problems with her vista comuter a lot and I don't live with her to her fix it, so I wanted to do a remote desktop. I don't know how to do it and i tried rdesktop but I don't understand the port tunnelling 3389 stuff.

---

### Post by Xerp on 2008-08-01
First your mum will need to enable remote desktop and then change her firewall and router to allow you through.

[http://www.microsoft.com/windowsXp/using/mobility/getstarted/Remoteintro.mspx](http://www.microsoft.com/windowsXp/using/mobility/getstarted/Remoteintro.mspx)
[http://portforward.com/](http://portforward.com/)

---

### Post by Bigbob22 on 2008-08-01
it was enabled, but I don't know how to change the firewall and router to allow me through. How do I change the firewall and router to allow me through?

---

### Post by briealeida on 2008-08-01
You might want to try logmein.com (if you're willing to pay). 

Otherwise, read this:

[http://www.neowin.net/forum/lofiversion/index.php/t486641.html](http://www.neowin.net/forum/lofiversion/index.php/t486641.html)

---

### Post by Bigbob22 on 2008-08-01
I'm looking for a way to access my Mom's vista computer using my ubuntu computer for free. the link you gave me showed a bunch of windows only remote access and you had to pay for them.

---

### Post by Bigbob22 on 2008-08-01
Please help

---

### Post by Bigbob22 on 2008-08-02
Bump

---

### Post by Bigbob22 on 2008-08-02
bump

---

### Post by jamesrfla on 2008-08-02
> **briealeida said:**
> You might want to try logmein.com (if you're willing to pay). 

Otherwise, read this:

[http://www.neowin.net/forum/lofiversion/index.php/t486641.html](http://www.neowin.net/forum/lofiversion/index.php/t486641.html)

You can get Log me in free to get to your moms windows computer. Log me in uses firefox and all you have to do is install a plug in.

---

### Post by Bigbob22 on 2008-08-02
It says it doesn't work for linux

---

### Post by jamesrfla on 2008-08-02
I can give you instuctiosn tommorow. Can't now sorry.

---

### Post by Bigbob22 on 2008-08-03
Alright, thanks.

---

### Post by cariboo on 2008-08-03
You will have to open the firewall and do the port forwarding for your mother's computer on her computer. To open the firewall just go to remote desktop help in windows and it will walk you through it. It's been a while since I did  this in Windows so you'll have to go with Microsoft's help. As far as port forwarding on the router, You will have  to be on your mother's computer to do that also. You will have to enter the router's management interface by entering something like [http://192.168.1.1](http://192.168.1.1), if that doesn't work try 192.168.0.1, or 192.168.2.1. The best way is to look at the documentation that is on the installation disk that came with the router. This will also tell you how to set up port forwarding.

Jim

---

### Post by jamesrfla on 2008-08-03
I am just posting what I did on a earlier post. All you need to do is have remote desktop enabled and have a VNC veiwer on the client computer and a IP address(ex.192.168.1.4). If you are doing remote desktop out side your network (on the internet) then you need to port forward port 5900. Then find your work ip address. If you have any other questions or are confused on something hear let us know.

---

### Post by Bigbob22 on 2008-08-03
Thanks I'm going to try it next week when I go to her place.

---

### Post by jamesrfla on 2008-08-03
If you have any problems just come back to this exact thread and I can help you.

---

### Post by tired of MS on 2008-08-03
LogMeIn has a FREE one, works great!  Been using it for 2 yrs with both XP and Ubuntu.  The only draw back is in 1st setup on remote cpu your Mom will have to log into your acct at LogMeIn to set that cpu up.
I have 6 cpu s on my account and no problems.

---

### Post by jamesrfla on 2008-08-03
He is trying to access his Ubuntu computer from a windows computer. I don't think log me in free works with Linux.

---

### Post by bodhi.zazen on 2008-08-03
There are 2 or three steps to using rdesktop.

First you must configure Windows (I assume this is already done).

Then you must configure your mom's router to froward the port. This varies by router, but you need to log into the router and use port forwarding. Sometimes this is called virtual servers, it varies by router. Look in your manual or search on line for your router.

[http://ezinearticles.com/?Remote-Desktop-Protocol-(RDP)-Port-Forwarding&id=115181](http://ezinearticles.com/?Remote-Desktop-Protocol-(RDP)-Port-Forwarding&id=115181)

Then you must know your mothers IP address, not the LAN address, but the public address. Use something like "show ip" (from your mothers house).

[http://showip.net/](http://showip.net/)

Note her IP address may change from time to time ...

---

