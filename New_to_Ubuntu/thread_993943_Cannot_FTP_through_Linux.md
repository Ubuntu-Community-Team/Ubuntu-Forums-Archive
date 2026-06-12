---
title: "Cannot FTP through Linux"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by aabrego on 2008-11-26
Dear all:

I need to FTP some sites to download binary files but when FTP I get the following message: 

FTP: Connected: Connection Refused

How do I set my system to allow FTP?

Regards,

Antonio

---

### Post by taurus on 2008-11-26
To allow incoming, you first need to install a ftp server like vsftpd or proftpd.  Have you installed one?

---

### Post by silverglade00 on 2008-11-26
That seems more like the ftp site you are trying to access has refused your connection. It could be that the site is busy. To test it and make sure that it is not your computer, try to go to [ftp://ftp.aol.com/](ftp://ftp.aol.com/) with your ftp client. If it works, then it is the ftp server not letting you connect.

---

### Post by aabrego on 2008-12-23
Hi:

I tried the go to [ftp://ftp.aol.com](ftp://ftp.aol.com) but I got the proxy screen. Then I suppose it is the firewall not letting me in. Doesn't it? What should I try next? Or in other words, what should I say to my firewall people?

Regards,

Antonio

---

### Post by Kellemora on 2008-12-23
Hi AA

Do you need a screen name and password to get in?

If so, check that to make sure you didn't type it in wrong, like with the caps lock key on, things like that.

TTUL
Gary

---

### Post by desperado665 on 2008-12-23
It may be that the firewall has your FTP port blocked. Try running this in terminal:

sudo ufw allow 21/tcp


or exchange 21 for the connection port on the FTP server you are trying to access.

Hope that helps  :)

---

### Post by handydan918 on 2008-12-23
> **aabrego said:**
> Hi:

I tried the go to [ftp://ftp.aol.com](ftp://ftp.aol.com) but I got the proxy screen. Then I suppose it is the firewall not letting me in. Doesn't it? What should I try next? Or in other words, what should I say to my firewall people?

Regards,

Antonio
If you have "firewall people," I assume you are either doing this from work or the West Wing of the estate. 
Either way,if you have "people" who handle your firewall, yeah, I'd let'em have a looksee.

---

### Post by aabrego on 2009-01-07
Hello:

Here I go again. When I'm connected to Firefox and ftp different sites, I can access them. However, when I'm in terminal window and write, for instance, ftp garner.uscd.edu I got ftp: connect: Connection refused.

It doesn't seems to be the firewall, does it?

Antonio

---

### Post by Nepherte on 2009-01-07
It certainly isnt' a firewall isue on your computer. All outgoing connections are allowed.

---

### Post by aabrego on 2009-01-07
I have setup my password in the following locations:

1- System -> Preferences -> Network Proxy -> Proxy Configuration; and
2- My .baschrc file as: 

export http_proxy=http://username:password@proxy:port
export ftp_proxy=http://username:password@proxy:port

---

### Post by Doneer on 2009-01-07
Hello! welcome to website; [www.shoes-trader.com](www.shoes-trader.com)

We are a trade and manufacturing company of brand name sport productions in China,Our main productions are:Jordan,Nike shoes;Lv,Prada bags;Jeans(evisu jeans.rmc short.);Sunglasses hat etc 

Here I list some of our products. 
Brand shoes: Nike, Adidas, Bape, BBC, Prada, LV, Timberland, Puma 
Brand clothes: Gucci, Bape, BBC, Rock&republic Seven, Red Monkeys, Diesel, LEE, D&G 
Brand bag: LOUIS VUITTON, GUCCI, CHANEL, CHRISTIAN DIOR, COACH 
Brand Watch: ROLEX, RADO, Omega, Cartier. 
Brand glasses: Chanel, Dior, Gucci, Louis Vuitton, Burberry, Police, Fendy. 

We insists that " SAFETY+ QUALITY+FAST DELIVERY+ GOOD PRICE = PERMANENT CUSTOMER".With high-standard quality, fastest delivery and satisfied service and reasonable price for you. 

Welcome to visit our website [www.shoes-trader.comIf](www.shoes-trader.comIf) you are 
interested in our production pls don't hesitate to contact us. 
Thank you! 
Best regards!

---

### Post by The Cog on 2009-01-07
You are using a proxy in firefox? Then you probably need to use a proxy in the command-line client as well. Unfortunately, I don't know how to confgure the command-line ftp client to use a proxy. You might also have to use passive mode.

---

