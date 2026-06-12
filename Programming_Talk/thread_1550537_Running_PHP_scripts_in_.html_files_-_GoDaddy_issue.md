---
title: "Running PHP scripts in .html files - GoDaddy issues"
date: 2010-08-11
forum: Programming Talk
---

### Post by Lootbox on 2010-08-11
Hi everyone.

I've been grappling with this problem for a few hours now and at this point I should probably just bite the bullet and do it the long way, but I still want to figure this out.

Basically, I want my .html files to run PHP scripts without having to change the extensions (and thereby all internal links as well). I looked it up, and immediately found that I just need to modify/create .htaccess with:

```
AddType application/x-httpd-php .html
```

I'm running Apache on my computer through XAMPP. I test a .html with PHP code and it works beautifully.

However, when I upload them to the actual website (hosted through GoDaddy), I get problems. First, the browser attempts to download my .html files instead of displaying them. After a few hours' search, I find [http://forums.digitalpoint.com/showthread.php?t=7584#post7483543](http://forums.digitalpoint.com/showthread.php?t=7584#post7483543).

When I try that instead, the problem changes - I get a 403: Forbidden error every time I try to visit a .html file. Just to see what happens, I make a simple test.php file, and that displays correctly. So it seems to be just the .html files. There's nothing else in .htaccess denying me access. Once again, this same setup works fine locally.

At this point, I call GoDaddy's customer support number. As expected, the actual conversation lasts less than 2 minutes - I describe my problem, he immediately says he doesn't know how to fix it but he's heard it's "hard." Yay GoDaddy (not my choice, I'm working with a group).

So... if anyone has experienced these kind of issues, any help would be very much appreciated. Now, excuse me while I exercise my CTRL + F skills.

---

### Post by donsy on 2010-08-11
> **Lootbox said:**
> 
```
AddType application/x-httpd-php .html
```
  Try including ".php" in your AddType directive:
```
AddType application/x-httpd-php .html .php
```Is ".htaccess" in the same directory as your script?

---

### Post by Lootbox on 2010-08-12
> **donsy said:**
> Try including ".php" in your AddType directive:
I tried adding that as well, but ran into the same issues.

> **donsy said:**
> Is ".htaccess" in the same directory as your script?
It is.

At the point I think the best solution is to convince the group's president to switch hosts when the contract expires. I guess you get what you pay for.

---

### Post by donsy on 2010-08-12
> **Lootbox said:**
> At the point I think the best solution is to convince the group's president to switch hosts when the contract expires. I guess you get what you pay for.
I use [http://www.inmotionhosting.com/](http://www.inmotionhosting.com/) and highly recommend them. Their support is great, and so far no downtime.

---

### Post by kennygichuhi on 2013-01-09
i was experiencing the same problem .just go to the root of your website and create .htaccess file and add the code below.this will work perfect  :p

Options +ExecCGI
 AddType application/x-httpd-php .php .html
 AddHandler x-httpd-php5 .php .html

---

