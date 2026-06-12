---
title: "Lightdm issue and no graphical login - newbie"
date: 2017-10-03
forum: New to Ubuntu
---

### Post by bergenist on 2017-10-03
Hi,

I have a Ubuntu Xenial LTS on a VMware virtual machine. It contains pretty important stuff about my work, and since this morning I can't use it anymore. I have no idea why, I don't remember installing any updates or new app.. 

When I log in I have these error message : 
[ATTACH=CONFIG]276944[/ATTACH]

I tried, following troubleshooting forums to install GDM (it blinked my screen) and xdm (still text only).

here is my lightdm.log 
[ATTACH=CONFIG]276945[/ATTACH][ATTACH=CONFIG]276946[/ATTACH][ATTACH=CONFIG]276947[/ATTACH][ATTACH=CONFIG]276948[/ATTACH]
I made a log of my X session :
[http://termbin.com/ua66](http://termbin.com/ua66)


What should I do ? :( 

Thank you for your help !

---

### Post by bergenist on 2017-10-03
[ATTACH=CONFIG]276950[/ATTACH]Ok. 
After having a look to forums, I finally remembered that I apt upgrade 2 days ago. 
So i upgraded my Nvidia drivers.

But now I have the invite for my credentials, and when I put my password and I getting back to the same. 
By doing alt + ctrl + F2 I can enter my credentials and it works.. 

but I can get on the graphical desktop. How can this be possible? :(

---

