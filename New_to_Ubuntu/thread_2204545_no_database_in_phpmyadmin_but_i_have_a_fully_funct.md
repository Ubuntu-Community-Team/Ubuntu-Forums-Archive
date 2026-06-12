---
title: "no database in phpmyadmin but i have a fully functioning wordpress site"
date: 2014-02-09
forum: New to Ubuntu
---

### Post by adamjedgar on 2014-02-09
Im a little confused by this,
after following some very bad advice when trying to check if my mail function is working on my apache server, i went to the logon screen and selected the reset password option (the idea being that it will send me an email). Of course, as luck would have it, the email never arrived! Now im locked out of my Wordpress site!

Anyway, one way of getting around this issue is to go to the server directly and use phpmyadmin to change the password...trouble is, ive logged into phpmyadmin on my server...and there is no Wordpress database??? How do i have a wordpress site up and running with 22 plugins, about 50 images, 15 or so pages, a few posts, calender, countdown timer to next event etc all working and no Wordpress database???

---

### Post by adamjedgar on 2014-02-09
It turns out there was a solution...delete all of the wordfence files.
Once i did that i was able to log back in using my original username and password. 

Weird result...go figure???

---

### Post by Habitual on 2014-02-09
> **adamjedgar said:**
> It turns out there was a solution...delete all of the wordfence files.
Once i did that i was able to log back in using my original username and password. 

Weird result...go figure???
There's a lockout feature in Wordfence, an excellent product.

But since you removed it, I  suggest adding this to your .htaccess or apache|http conf file:
```
<Files wp-login.php>
order deny,allow
deny from all
allow from xx.yy.zz.aa       # Connecting from my computer at home
</Files>
```

This will keep the knuckleheads from banging away on your admin login page.
"xx.yy.zz.aa" could have multiple entries, if required, or necessary, eg:
```
allow from xx.yy.zz.aa             # Comment0
Allow from aaa.bbb.ccc.ddd        # Comment1
```

If you add it to your apache | httpd conf file don't forget to restart the service.
I hope that's helpful.

---

### Post by adamjedgar on 2014-02-10
Hi Doug,
I have reinstalled WP Better security and will probably reinstall wordfence too however i am just going to wait until i have the mail functionality working properly (will start another thread on this)
so do i substitute the letters for my static ip address...or the local one for the vm-Virtual Box (or both)?

---

