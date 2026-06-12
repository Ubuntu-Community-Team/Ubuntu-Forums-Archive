---
title: "Apache2 showing default page instead of forum"
date: 2019-06-12
forum: New to Ubuntu
---

### Post by sj11123 on 2019-06-12
I am new to this stuff and tried to open a website, and when I clicked the link it directed me to 'Apache 2 Ubuntu Default Page' instead of the myBB forum that I set up.

---

### Post by yancek on 2019-06-12
You need to post a lot more detail to get any help.  Is this server set up on a localhost machine?  Is it online?  How did you do this?  Do you try to access by domain name or by IP address?  How did you create the link?  Is the link pointing to a specific file in the appropriate location?

---

### Post by sj11123 on 2019-06-13
Yes, the site is on a localhost machine, but the Ubuntu default page isn't. I have to access my forum by IP address.

---

### Post by yancek on 2019-06-13
> Yes, the site is on a localhost machine, but the Ubuntu default page isn't. I have to access my forum by IP address. 		 	  	 		 		

A standard install of Apache on Ubuntu will put the 'default page' (index.html) in the /var/www/html directory.  Is the file you are trying to access when you click your link in that directory or a sub-directory and do you have the full path to it set up with your link.  Not sure where your default page is and why it isn't on the localhost.  Did you delete it?

What link are you referring to in your initial post?  You still are posting a very minimal amount of information and I don't know that anyone will be able to help without more details.

---

### Post by TheFu on 2019-06-13
Running a public forum is one of the hardest tasks to accomplish in the computer world. I've been a Unix/Linux admin since 1994-ish with hundreds of different servers.  Forum servers scare me.

Securing a forum is extremely difficult.  Keeping it free of spam posts is next to impossible.  There are 20+ forum admins here keeping these forums clean, but it is a never-ending task for those volunteers.

I've considered running forums, but decided against it. Heck, just running my blog the last 20 yrs has shown me more spam posts than you could imagine.  Almost all are automated and designed to get passed the filters we all use.

Of course, if this is a private forum, not on the internet, or only accessible through a VPN, it should be fine.  Go crazy.

I have zero expertise that would likely help. We don't use apache and avoid php-based webapps.  Sorry.

---

### Post by SeijiSensei on 2019-06-13
If the myBB directory resides in /var/www/html/myBB/, then it should be visible as [http://localhost/myBB/](http://localhost/myBB/).  If it resides anywhere else on the machine, it won't be visible without more configuration.

You need to be the root user, via sudo, to do anything in /var/www/html.

Have you read this yet? [https://help.ubuntu.com/lts/serverguide/httpd.html](https://help.ubuntu.com/lts/serverguide/httpd.html)

---

