---
title: "Gmail &amp; Network Firewall"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by Me! on 2008-05-13
Hi all,
 
 I can not receive pop3 of gmail because my network firewall do not allowing else of port 80 !
 
 How can I receiving the gmail pop3 with port(995).
 
 thank you!

---

### Post by brettg on 2008-05-13
Short of creating a tunnel through port 80 to another machine on the net and accessing pop3 via that vpn I would suggest that there is nothing you can do. 

Having said that I'm pretty sure your firewall will allow https (PORT 433) as well as 80 (unless it is severely restrictive ) in which case you can just access your emails via a browser and download them via pop3 later

---

### Post by nicedude on 2008-05-13
Hey man sorry to here you have g-mail problems. But you need to giive everyone more info to help you. 

1. By network firewall, Do you mean a router or another PC that you gain internet access through or a firewall installed on your PC ?

2. Do you have admin authorization on the device or software that is blocking your comunications ? 

3. What operating system are you using ? if Ubuntu then what version ?

4. What program are you trying to use to retreive your Email from Gmail.


Also when getting mail from Gmail I think I had to go to Gmail and enter my account settings there to change a setting allowing me to get it with pop3 via Thunderbird email.

Please post more and I or someone can help you resolve this.

---

### Post by Me! on 2008-05-13
> **brettg said:**
> Short of creating a tunnel through port 80 to another machine on the net and accessing pop3 via that vpn I would suggest that there is nothing you can do. 

Having said that I'm pretty sure your firewall will allow https (PORT 433) as well as 80 (unless it is severely restrictive ) in which case you can just access your emails via a browser and download them via pop3 later

Yes I can access to https (almost time) , I'm using normal browser to viewing my emails too.

but I want to know is Ubuntu can do that.

I think yes, but how ?

---

### Post by Me! on 2008-05-13
> **nicedude said:**
> Hey man sorry to here you have g-mail problems. But you need to giive everyone more info to help you. 

1. By network firewall, Do you mean a router or another PC that you gain internet access through or a firewall installed on your PC ?

2. Do you have admin authorization on the device or software that is blocking your comunications ? 

3. What operating system are you using ? if Ubuntu then what version ?

4. What program are you trying to use to retreive your Email from Gmail.


Also when getting mail from Gmail I think I had to go to Gmail and enter my account settings there to change a setting allowing me to get it with pop3 via Thunderbird email.

Please post more and I or someone can help you resolve this.

OK man,

1. another PC that you gain internet access through
 2. No I don't have admin authorization :(
3. Ubuntu 8.04 the new release with updates + Kubunut desktop settings .
4. Kmail , pop3 is enabled in gmail.com , it is work out side this network.

I hope that some one resolve this

thanks

---

### Post by nicedude on 2008-05-13
Don't know if you can solve this easily without admin status and if all ports are blocked except 80. Since you said pop3 port 110 is blocked did you check imap port 143 as google also has that as a option to retrieve mail. Beyond that you will probably have to investigate tunneling out through port 80 in order to try and get your mail, Otherwise you will just have to log on to google to get it while in this location ( If this location is blocking web access to gmail then say so as there are multiple urls for it and they probably don't block them all ) Hope you find a solution :-)

You might have a look at this.
[http://internetducttape.com/2006/10/04/how-to-access-gmail-when-its-blocked-at-work-or-school/](http://internetducttape.com/2006/10/04/how-to-access-gmail-when-its-blocked-at-work-or-school/)

---

### Post by niceguy123 on 2008-06-08
> **nicedude said:**
> Don't know if you can solve this easily without admin status and if all ports are blocked except 80. Since you said pop3 port 110 is blocked did you check imap port 143 as google also has that as a option to retrieve mail. Beyond that you will probably have to investigate tunneling out through port 80 in order to try and get your mail, Otherwise you will just have to log on to google to get it while in this location ( If this location is blocking web access to gmail then say so as there are multiple urls for it and they probably don't block them all ) Hope you find a solution :-)

You might have a look at this.
[http://internetducttape.com/2006/10/04/how-to-access-gmail-when-its-blocked-at-work-or-school/](http://internetducttape.com/2006/10/04/how-to-access-gmail-when-its-blocked-at-work-or-school/)

Can't access gmail from this computer.
1. I'm on my own computer, that I have upgraded to Hardy 8.04 previously 7.04 and had no problem.
2. Its networked to the internet via a router (an xp on the same router can access gmail).
3. I can view other pages on the internet, even other google sites. 
4. I tried alturative ulrs listed at [http://internetducttape.com/2006/10/04/how-to-access-gmail-when-its-blocked-at-work-or-school/](http://internetducttape.com/2006/10/04/how-to-access-gmail-when-its-blocked-at-work-or-school/)
:confused:

---

