---
title: "[SOLVED] Firefox startup problem"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by phil66 on 2008-05-30
Ubuntu 7.10 Gutsy
Firefox 2.0.0.14

When I start Gutsy Firefox immediately open

When it opens the url is "http://www.%u.com"

My home page is Yahoo.com

This all happens before I login to the internet

Where do I find this setting to correct.:confused:

TIA
Ray

---

### Post by rockerphil on 2008-05-30
you should be able to set your home page from the Edit menu and clicking on "Prefferences" then it's in the main tab, if that doesn't work then i'd just reinstall Firefox.

sudo apt-get remove --purge firefox

sudo apt-get install firefox

---

### Post by phil66 on 2008-05-30
> **rockerphil said:**
> you should be able to set your home page from the Edit menu and clicking on "Prefferences" then it's in the main tab, if that doesn't work then i'd just reinstall Firefox.

sudo apt-get remove --purge firefox

sudo apt-get install firefox

Thanks for the reply

I checked the home page setting before posting every thing correct

Uninstall and reinstall requires ubuntuzilla install to get the current program.

Would rather not go that way just yet

Maybe someone has experienced this problem and will offer help

Ray

---

### Post by sacback on 2008-05-31
> **phil66 said:**
> Ubuntu 7.10 Gutsy
Firefox 2.0.0.14

When I start Gutsy Firefox immediately open

When it opens the url is "http://www.%u.com"

My home page is Yahoo.com

This all happens before I login to the internet

Where do I find this setting to correct.:confused:

TIA
Ray

If you go under preferences you should be able to set up your homepage, Im sure. Sometimes it sets itself. But it shouldn't reall ybe a big problem; you changing it.

---

### Post by Bubba64 on 2008-05-31
If you can open the yahoo page then go to preferences-main-use current page, this should set it as your opening page

---

### Post by phil66 on 2008-05-31
> **Bubba64 said:**
> If you can open the yahoo page then go to preferences-main-use current page, this should set it as your opening page

I think my problem is being misunderstood

The problem is not in the home page setting but rather in the fact that Firefox opens by itself

When I boot up the computer Firefox open immediately after the desktop

I do not click on Firefox it just opens by itself and then the url [www.%u.com](www.%u.com) which is server not found shows in the address bar this is due to not being conected to the internet

Thanks for all the replies
Ray

---

### Post by phil66 on 2008-05-31
> **phil66 said:**
> I think my problem is being misunderstood

The problem is not in the home page setting but rather in the fact that Firefox opens by itself

When I boot up the computer Firefox open immediately after the desktop

I do not click on Firefox it just opens by itself and then the url [www.%u.com](www.%u.com) which is server not found shows in the address bar this is due to not being conected to the internet

Thanks for all the replies
Ray

Problem solved 
Ubuntu setting in system>preferences>startup programs the Firefox program was set to start up

Thanks for all the help

---

