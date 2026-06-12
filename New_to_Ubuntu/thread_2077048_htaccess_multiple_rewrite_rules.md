---
title: "htaccess multiple rewrite rules"
date: 2012-10-27
forum: New to Ubuntu
---

### Post by robolist on 2012-10-27
I have been developing a new website and custom CMS recently and it is my first time building my own CMS. I have used htaccess in the past for basic stuff and of course when developing WordPress sites i hardly need to touch the htaccess because WordPress/Plugins handles most of it for me. 

This time however I must do it all myself, so its a lot of fun but also very frustrating when it doesn't work the way i want it to. 

I am currently using the htaccess file to write my URLs from /index.php?subj=home to /home and so on for other pages. 

But the way the site is set up if the user lands on either the root / or the /index.php page they will see nothing. I would like to redirect these to /home but i cant seem to figure it out. 

Can anybody help me out with this please? The following is what i am using already, so i guess i just need to add one more rule, but im not sure exactly what. 

```
RewriteEngine on 
RewriteCond %{SCRIPT_FILENAME} !-d
RewriteCond %{SCRIPT_FILENAME} !-f
RewriteRule ^(.+)$ index.php?subj=$1
```

---

