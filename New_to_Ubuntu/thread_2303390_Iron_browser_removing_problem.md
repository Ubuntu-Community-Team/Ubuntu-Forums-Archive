---
title: "Iron browser removing problem"
date: 2015-11-18
forum: New to Ubuntu
---

### Post by rdb3 on 2015-11-18
I have been checking out a few browsers since I recently installed Ubuntu (15.10) on my desktop.
One of them is Iron.

When I go to the Dash and enter Iron, I see that all these Iron files are there:  iron-linux, product logo, locales, resources, chrome pak, etc., etc., (lots of files)
When I enter:  sudo apt-get purge iron-linux
The reply coming back is 'unable to locate package iron-linux.'
So it looks like Iron has not been installed.

What is the best way for me to get rid of these files?  

Thanks in advance!!

---

### Post by Vladlenin5000 on 2015-11-18
How have you installed it?

---

### Post by Frogs Hair on 2015-11-18
If installed from a .deb package the package names for 32 and 64 bit are as follows.
```
iron32
``` ```
iron64
```

---

### Post by rdb3 on 2015-11-18
Vladlenin, 

I had to go back and re-think and search out how I started the whole thing late one night.
I downloaded the deb package from the SRWare site.  And apparently that is as far as I got that night.
Those files that I mentioned in my opening post were actually from the download.  Sorry for not being a little 
more aware on that one.

I just saw these installation instructions and finished out the installation via command-line.

[http://linuxg.net/install-srware-iron-on-ubuntu-debian-and-derivatives/](http://linuxg.net/install-srware-iron-on-ubuntu-debian-and-derivatives/)

Since it's installed now, I am going to check it out for awhile and see if I want to keep it.

Thank you!!

Frogs Hair,

On the link above, they say that to remove the browser enter:

[COLOR=#555555][FONT=consolas]$ sudo apt-get remove iron

[/FONT][/COLOR]Where can I go to check if it is iron or iron32?

Will a remove get rid of everything or would a purge be better?

Thanks!

---

### Post by Frogs Hair on 2015-11-19
Try both package names and if you get a not found error with one know it's the other. All dependencies should be removed and the user profile can be found home/ hidden folders/.config if I remember correctly. Iron should appear in the software as well.

---

### Post by rdb3 on 2015-11-19
Iron32 was not found.  Iron uninstalled.

To recap, I did not complete the install as I stated above.  After it was completed, it uninstalled.

---

