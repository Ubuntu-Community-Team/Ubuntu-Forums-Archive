---
title: "PHP password protected apache site."
date: 2007-06-12
forum: Programming Talk
---

### Post by tipalm73 on 2007-06-12
Hello,

I am new to programming and have been messing around with linux for a few years now.

I have a little ubuntu server on my internal lan at home. Following a tutorial I set up a PHP login page that references the user table in mysql DB. What I want to do is password protect my website. I followed this example: [http://www.devnewz.com/devnewz-3-20050214PasswordProtectionwithPHPMySQLandSessionVariables.html](http://www.devnewz.com/devnewz-3-20050214PasswordProtectionwithPHPMySQLandSessionVariables.html)

here is my site tipalm.mine.nu.

When logged in it shows a link to phpmyadmin, a media database link(non-existent), and the option to logout..fantastic. My problem is you can just go to tipalm.mine.nu/music and get the index page. So though I have a login screen that indeed redirects to a secure page, my url is not secure and I dont know how to block the url if your not logged in and allow if you are.

I know this sounds vague, but I can provide any info needed to explain better.

Thanks in advance!

---

### Post by EndPerform on 2007-06-12
Instead of trying to code a PHP app, why not look at using Apache and an .htaccess file?  Check out this link:

[http://httpd.apache.org/docs/2.0/howto/auth.html](http://httpd.apache.org/docs/2.0/howto/auth.html)

which will give you a nice overview of how to set it up under Apache 2.

---

### Post by SDE on 2007-06-12
if you wanted an alternative to that tutorial, you could try mine here: [http://php.codenewbie.com/articles/php/1482/Login_With_Sessions-Page_1.html](http://php.codenewbie.com/articles/php/1482/Login_With_Sessions-Page_1.html)

basically all the source is there for a little mock-site which uses php and sessions to protect content.

---

### Post by tipalm73 on 2007-06-12
> **SDE said:**
> if you wanted an alternative to that tutorial, you could try mine here: [http://php.codenewbie.com/articles/php/1482/Login_With_Sessions-Page_1.html](http://php.codenewbie.com/articles/php/1482/Login_With_Sessions-Page_1.html)

basically all the source is there for a little mock-site which uses php and sessions to protect content.

Thanks I'll try it out.

---

### Post by barmazal on 2007-06-12
> **EndPerform said:**
> Instead of trying to code a PHP app, why not look at using Apache and an .htaccess file?  Check out this link:

[http://httpd.apache.org/docs/2.0/howto/auth.html](http://httpd.apache.org/docs/2.0/howto/auth.html)

which will give you a nice overview of how to set it up under Apache 2.

support the idea ...

---

### Post by tipalm73 on 2007-06-12
> **barmazal said:**
> support the idea ...


Well I could do that, but ultimately I'd like for people to be able to create an account. 

I just finished 2 semesters of c# and think this would be a challenge. Went out and bought an o'reily php and mysql book, so I am sure I can find some answers.

Any advice is appreciated though. I will do that for a temporary fix to my problem.

Thx.

---

