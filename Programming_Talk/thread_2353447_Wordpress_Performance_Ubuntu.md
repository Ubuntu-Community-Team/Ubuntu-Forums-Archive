---
title: "Wordpress Performance Ubuntu"
date: 2017-02-21
forum: Programming Talk
---

### Post by Nathan_Veysey on 2017-02-21
Hello, 

Ive recently been having issues with performance with a booking system using a comet connection on Windows so have setup a Development environment on Ubuntu (Same as live servers for the system) the system is running and is faster than the windows counterpart however the WordPress (Multisite) performance is still quite slow (significantly slower than the live server). The machine is new 8GB DDR3s i7 4790 (non SSD) and is running the GUI version. PHP 7, MySQL 5.7 (default install config)

The whole site is slow, so not just the booking system (only loosely bound to WordPress, i.e. Plugins won't be an issue). The original version which has only had some minor architectural changes which was constructed on PHP 5.6 ran fine, the issues Ive had appear to have come from an update to PHP 7 on windows. But the code is relatively simple on the server side (Insert, Update, Delete, Push), most the complexity is on the client scripts. 

How would I best go about locating the reason for the bad performance, Ill get around to installing some less complex sites and see how they fair. Have previously installed a number of commercial servers and not had such bad performance? My bet would be on PHP being the culprit? 

It is workable, so can install some updates in the meantime, but would be nice to workout the issue and will be essential if its affecting other installs (to be confirmed)

UPDATE: 
phpmyadmin (local network) works well, and the site is being served across the local network.


Hope this is the correct area for this post, please let me know if not

Thank you

---

### Post by SeijiSensei on 2017-02-22
Can you explain a bit what "WordPress (Multisite) performance" means, in particular "Multisite?"  Is everything consolidated on this server, or does it need to interact with other servers as well?  

I use CentOS on servers rather than Ubuntu, with WordPress sites that only require the resources of the machine on which they are running.  They always have fine performance.  I've never had issues with my own sites coded in PHP either, though I'm still using PHP 5.  

Have you tried creating a simple test site in WordPress on this machine with a few posts and maybe a couple of graphics?  Is it slow?

---

