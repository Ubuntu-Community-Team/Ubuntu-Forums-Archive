---
title: "Least traffic way of comparing website"
date: 2009-07-02
forum: Programming Talk
---

### Post by WitchCraft on 2009-07-02
How do I best check an arbitrary webpage for updating?

For example someone posts an answer to "http://ubuntuforums.org/showthread.php?p=7546841"


Then, in a regular interval, I simply download the page and check the size, variations < 5 i let go through as unchanged, variations with more than 5 additional letters will be considered as a new page.

Is there a way to do that causing less traffic?

PS: Please note: I'm not using E-Mail notification because I don't want to run the email program all the time, and because some sites don't have e-mail notification integrated.

---

### Post by smartbei on 2009-07-02
Assuming the site you want to use this on also doesn't support RSS feeds, then I guess what I would do is check the Last-modified header of HTTP. It isn't always there, but if it is it can save you downloading the entire file. wget can do this, simply specify --timestamping and it will not download the file if it is not newer than the local file.

---

### Post by WitchCraft on 2009-07-03
> **smartbei said:**
> Assuming the site you want to use this on also doesn't support RSS feeds, then I guess what I would do is check the Last-modified header of HTTP. It isn't always there, but if it is it can save you downloading the entire file. wget can do this, simply specify --timestamping and it will not download the file if it is not newer than the local file.

Thanks ! 
New plan: I will investigate the HTTP header using the timestamp method which I can get from wget, check if RSS feeds are supported, if neither I will download the page.

---

