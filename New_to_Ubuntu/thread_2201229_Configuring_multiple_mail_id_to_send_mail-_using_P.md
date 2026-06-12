---
title: "Configuring multiple mail id to send mail- using Postfix server"
date: 2014-01-23
forum: New to Ubuntu
---

### Post by praveen_kumar2 on 2014-01-23
Hai,
1. I configured Postfix in ubuntu server 12.04. 
2. I Use gmail id and password to send mail.

[B]The problem:

[/B]I have more than one website in my server, so when i send activation or other email, the mail was delivered to the user with the same gmail id i added in postfix. 

[B]Solution expected:

[/B]I would like to add few more Mail Id and password, so i can use those mail id to send mail for different websites. so user will only get the appropriate mail id.
for ex: [EMAIL="no-reply@one.com"]no-reply@one.com[/EMAIL], [EMAIL="no-reply@two.com"]no-reply@two.com[/EMAIL], [EMAIL="no-reply@three.com"]no-reply@three.com[/EMAIL]. 

I'm quite new to ubuntu, so expect your valuable inputs.

Thanks,
Praveen.

---

### Post by TheFu on 2014-01-23
Hosting your own email server is fun, challenging, and always a learning experience. I've been doing email servers for  ... over 15 yrs.
[http://blog.jdpfu.com/2011/08/16/readers-ask-about-hosting-email](http://blog.jdpfu.com/2011/08/16/readers-ask-about-hosting-email) explains the parts you need to make it work.  A single server can host thousands of domains from 1 IP and there are many other considerations with your hosting provider if you plan to send emails outbound ... in bulk.

---

### Post by praveen_kumar2 on 2014-01-23
Thanks friend. I will check...

---

