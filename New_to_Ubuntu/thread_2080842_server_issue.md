---
title: "server issue"
date: 2012-11-05
forum: New to Ubuntu
---

### Post by nicksimpson32 on 2012-11-05
Hi  everyone,
I have ubuntu 12 04 lts desktop installed, apache2, nothing else.
I can see my webpage externally if I enter my sitename.com followed by port number.
Could anyone tell me please what file/files need to be configured so that I am able to reach my web page with only the site name - no ip.
Thank you in advance.

---

### Post by lisati on 2012-11-05
The way it usually works is that you set your domain name with your DNS provider to point to your public IP address, and have port fowrarding (usually port 80 for web sites) set within your router to point to the machine which is hosting your web site.

---

### Post by The Cog on 2012-11-05
If it's port 80 then you don't need to specify the port number. If it's any other port number then there is no option but to specify the port number in the browser.

---

### Post by nicksimpson32 on 2012-11-05
Thank you guys

---

