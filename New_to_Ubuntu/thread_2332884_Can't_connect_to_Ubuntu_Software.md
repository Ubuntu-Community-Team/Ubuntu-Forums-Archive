---
title: "Can't connect to Ubuntu Software"
date: 2016-08-05
forum: New to Ubuntu
---

### Post by mangoh on 2016-08-05
Hello,
after several minutes, Ubuntu Software has not finished searching. It won't load the results for the default screen (recommended software etc.) either. I'm using 16.04.

Thanks.

Dell Inspiron Laptop Intel® Core&#8482; i3 CPU M 330 @ 2.13GHz × 4 
Using WiFi
I can load websites on my browser. I'm posting this on the same machine while I wait for Ubuntu Software.

Update: the same thing happens when I try to run an installer package downloaded from the Internet, e.g. Dropbox.

---

### Post by mook765 on 2016-08-05
Please edit your post and add some more information.
What kind off hardware do you use ?
Are you using WLan or Lan ?
Is your computer a laptop ?
Just right now we can just guess, maybe your internet-connection is not estabished properly.
When you open your web-browser, can you load websites ?

---

### Post by mangoh on 2016-08-11
Have done so, thanks.

---

### Post by RobGoss on 2016-08-13
Try changing your server location it may not be the best choice for your area, **Software & Update **> **Download from >** you can choose a better location from the **drop-down menu **then just save your changes

---

### Post by Bucky Ball on 2016-08-13
This could be (and may not be) related to the problem I am having with another package manager, Synaptic. Every time I open it it needs to rebuild the app database. Everytime. Did your issue just start happening recently (last few weeks) or it has always happened for you with 16.04?

---

### Post by Geoffrey_Arndt on 2016-08-13
Can try a reinstall:   
sudo apt-get install --reinstall packagename

---

### Post by kibohusky on 2016-08-14
If you cannot find a resolve you can install gdebi and have that manage debs instead of the store:

sudo apt-get install gdebi

---

### Post by mangoh on 2016-08-29
> **Bucky Ball said:**
> This could be (and may not be) related to the problem I am having with another package manager, Synaptic. Every time I open it it needs to rebuild the app database. Everytime. Did your issue just start happening recently (last few weeks) or it has always happened for you with 16.04?

I only installed the OS recently, so I have only been using it for a few weeks anyway. I did install a couple of things early on.

> **RobGoss said:**
> Try changing your server location it may not be the best choice for your area, **Software & Update **> **Download from >** you can choose a better location from the **drop-down menu **then just save your changes

My system won't accept my password to do this!

> **kibohusky said:**
> If you cannot find a resolve you can install gdebi and have that manage debs instead of the store:

sudo apt-get install gdebi

I tried this but I didn't get any application, just an empty installer package.

> **Geoffrey_Arndt said:**
> Can try a reinstall:   
sudo apt-get install --reinstall packagename

Please excuse my absolute ignorance, but how do I know what the package is called?

---

### Post by howefield on 2016-08-29
Have you updated since installing the operating system ?

```
sudo apt update
```
```
sudo apt upgrade
```

---

