---
title: "HTTPS page does not load"
date: 2015-08-10
forum: New to Ubuntu
---

### Post by niall2 on 2015-08-10
Hi. I am new to Forums and Support however i am attempting to get some answers Setting up a Self-signed SSL Certificate. 
I am also new to Linux and Ubuntu. 

My problem is that i have a web application set up which runs perfect on the the Apache2 HTTP protocol however when i am setting up the HTTPS the application does not load. 
I have read Ubuntu's Official documentation on Setting up self signed Certificates numerous times and have redone the Certificate twice as Many times. 

I am using Ubuntu 14.04
My problem is that my HTTPs page jsut does not serve up. 
i have checked the error logs and all it says is [core:notice] [pid 9583] AH00094: Command line: '/usr/sbin/apache2'

I have been reading on this for a week now without any solution.

Can someone please help me with this issue?

---

### Post by dino99 on 2015-08-10
a user cas example: [https://yoast.com/move-website-https-ssl/](https://yoast.com/move-website-https-ssl/)  that could help you

and a general list about the subject: [https://duckduckgo.com/?q=setting+https+ssl+page](https://duckduckgo.com/?q=setting+https+ssl+page)

---

### Post by niall2 on 2015-08-10
Thank you dino99.... I will begin my reading. Hope it helps to solve my problem.

---

### Post by haplorrhine on 2015-08-10
I only know that https is 443 and SSH is 22.

cat /etc/services | grep xxxx

---

### Post by MartyBuntu on 2015-08-10
Make sure your computer and server are both set to the correct current date and time. **https** will freak out, otherwise.

---

### Post by SeijiSensei on 2015-08-10
As Marty says, servers should be running the ntpd daemon, and clients should be configured to use an NTP server.  That's true whether you are using SSL or not.  There's no reason not to synchronize your clocks these days.

---

