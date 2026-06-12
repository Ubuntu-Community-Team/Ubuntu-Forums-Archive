---
title: "php pear self-install"
date: 2010-12-06
forum: Programming Talk
---

### Post by aaronp on 2010-12-06
Hi everyone,
I've just moved a website from a server I was running on a computer at home to a free webhost. 
Unfortunately I use PEAR for smtp mail auth and even though their FAQ said it was available, I just found out (after starting to test the site) that it's only on their paid accounts.

I'm going to pay for the hosting at some point, but wanted to test it out before I lock myself into any particular provider.

Now, knowing that PEAR is just a bunch of php modules, I've copied Mail.php and PEAR.php onto the server (one level above the public html root) and referenced ../Mail.php from my script. It seems to be picking up Mail.php ok but it looks like Mail.php can't find PEAR.php. I'm not sure where to put it so it can find it, without having to modify the path. Is this even possible? (to install it without having it installed on the server overall)

Here's the error I started getting after I copied Mail.php and PEAR.php:

```
Fatal error: Call to undefined method PEAR_Error::send() in /home/a2383139/public_html/smail.php on line 79
```

thanks
Aaron

---

