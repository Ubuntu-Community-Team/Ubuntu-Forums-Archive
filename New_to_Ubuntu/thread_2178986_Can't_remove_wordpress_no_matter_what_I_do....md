---
title: "Can't remove wordpress no matter what I do..."
date: 2013-10-06
forum: New to Ubuntu
---

### Post by julia3 on 2013-10-06
I have been at this for three hours. Why I have been at this for three hours you ask? Because when I go to install a theme it says....
Could not create directory. /var/www/wordpress/wp-content/upgrade/terminally.tmp
Therefore I thought to myself. I will reinstall wordpress by terminal. I can not remove wordpress. 
When I do 
sudo apt-get purge wordpress 
After changing directories to the file wordpress it says...
Reading state information... Done
Package 'wordpress' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 263 not upgraded.
I even tried doing 
rm -R wordpress
I do not know what to do. Please help me remove wordpress.
Thanks,
Julia

---

### Post by lisati on 2013-10-06
> **julia3 said:**
> I have been at this for three hours. Why I have been at this for three hours you ask? Because when I go to install a theme it says....
Could not create directory. /var/www/wordpress/wp-content/upgrade/terminally.tmp
Therefore I thought to myself. I will reinstall wordpress by terminal. I can not remove wordpress. 
When I do 
sudo apt-get purge wordpress 
After changing directories to the file wordpress it says...
Reading state information... Done
Package 'wordpress' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 263 not upgraded.
I even tried doing 
rm -R wordpress
I do not know what to do. Please help me remove wordpress.
Thanks,
Julia

Did you install Wordpress manually? If so, **carefully** copy and paste the following EXACTLY to your command line:
```
sudo rm -rf /var/www/wordpress
```
This will remove your wordpress files, but not your database. Be extremely careful, as a typo can make a mess of things.

---

### Post by BlinkinCat on 2013-10-06
> **lisati said:**
> Did you install Wordpress manually? If so, **carefully** copy and paste the following EXACTLY to your command line:
```
sudo rm -rf /var/www/wordperss
```
This will remove your wordpress files, but not your database. Be extremely careful, as a typo can make a mess of things.

Hi lisati - is the spelling of your command accurate?

---

### Post by lisati on 2013-10-06
> **BlinkinCat said:**
> Hi lisati - is the spelling of your command accurate?

Well spotted, thank you. 
Corrected as follows:
```
sudo rm -rf /var/www/wordpress
```

---

### Post by julia3 on 2013-10-09
Thanks for your reply. This is solved. 
sudo rm -rf /var/www/wordpress worked. 
I was able to unistall wordpress and then reinstall it. Thanks.

---

