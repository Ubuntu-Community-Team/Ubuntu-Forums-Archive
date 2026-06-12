---
title: "Not Found error"
date: 2022-10-12
forum: New to Ubuntu
---

### Post by laimutislaz on 2022-10-12
Hello all,

maybe some have dame issue and can help me with information how to sort it out please?
I’m getting error 404:
Not found
The requested URL was not found on this server
Apache/2.4.52 (Ubuntu) Server at up-address Port 80

i have google for it, found one and the same solution, but unfortunately it’s not working.

anyone could help me please,

---

### Post by MAFoElffen on 2022-10-12
That is the screen your are going to see in a browser, if you pressed a link that pointed to, or you typed in a web address to a page that did not exist (anymore)... So either the URL of the object either was wrong, or the resource isn't there. And that the host of that page is running Apache Web Server (as a service).

EDIT: Or the network connection was not there. If you see other webpages, then the rule that out...

---

### Post by mIk3_08 on 2022-10-13
> **laimutislaz said:**
> Hello all,

maybe some have dame issue and can help me with information how to sort it out please?
I’m getting error 404:
Not found
The requested URL was not found on this server
Apache/2.4.52 (Ubuntu) Server at up-address Port 80
i have google for it, found one and the same solution, but unfortunately it’s not working.
anyone could help me please,
This is not working url address anymore. Noting to worry about. Regards and cheers.

---

### Post by laimutislaz on 2022-10-13
Hello all,
So I have managed to fix an error, but now I have other issue.
I have created registration.php and tried to connect to MySQL, but when you click registration button it&#8217;s brings you an error, looks like my server not connecting to MySQL.
Any ideas why and how to fix the problem?

I&#8217;m using local host and run server Ubuntu 22.04 do I need extra permission to connect to server? Or I need to use IP 127.0.0.1?

---

### Post by yancek on 2022-10-13
>  but when you click registration button it’s brings you an error,

And what would that error be?  Did you try to connect as a user or as root or both.  Did you try localhost as well as 127.0.0.1?

---

### Post by mIk3_08 on 2022-10-13
> **laimutislaz said:**
> Hello all,
So I have managed to fix an error, but now I have other issue.
I have created registration.php and tried to connect to MySQL, but when you click registration button it&#8217;s brings you an error, looks like my server not connecting to MySQL.
Any ideas why and how to fix the problem?

I&#8217;m using local host and run server Ubuntu 22.04 do I need extra permission to connect to server? Or I need to use IP 127.0.0.1?
You're building/configuring a website for this? You haven't mentioned anything in your first post about your website that you are trying to fix. I think next time you should be able to clarify and elaborate more about your concern so that the community wont be confuse about you're thread. Regards and cheers.

---

### Post by MAFoElffen on 2022-10-14
MySQL connection string includes info about dB user and authentications to complete the connection. Then the query...

As posted, please provide more information on what you have, what you are trying to do as a goal, and what you did that is not working.

---

