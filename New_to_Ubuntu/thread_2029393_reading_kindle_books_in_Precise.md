---
title: "reading kindle books in Precise"
date: 2012-07-19
forum: New to Ubuntu
---

### Post by mystmaiden on 2012-07-19
I tried to install Kindle for Pc under Wine, but it just crashes. Has anyone gotten it to work? I tried googling but only found bits of information, nothing complete enough to fix the problem. Or is there another application that will read kindle books in precise?

thanks,

mystmaiden

---

### Post by richpri on 2012-07-19
See [http://appdb.winehq.org/objectManager.php?sClass=application&iId=10597](http://appdb.winehq.org/objectManager.php?sClass=application&iId=10597)

You may need to use a back version of the Kindle app.

---

### Post by blueshead on 2012-07-19
Calibre works a treat.

```


        sudo add-apt-repository ppa:n-muench/calibre 
        sudo apt-get update
        sudo apt-get install calibre


```

[http://calibre-ebook.com/]("http://calibre-ebook.com/")

---

### Post by I2k4 on 2012-07-19
Do you know you can read Kindle books in your FireFox or Chrome browser in Linux rather than try to run the Windows Kindle app?  just google the "Kindle Cloud Reader" and log in to the Amazon site to set it up. The Cloud Reader becomes one of your five permitted Kindle "devices" and you can read your books on any device that will run a compatible browser.

Only problem is it only works for actual Amazon purchases and not for free downloads that are readable on kindle, e.g. Gutenberg public domain books.  But it works great for Kindle books you buy.

---

### Post by epikvision on 2012-07-19
I agree with I2k4 that reading Kindle books is easy with the browser.  Cloud reader is very convenient.  Whenever I want to read and annotate on kindle books, I use my trusty Chrome and run the cloud reader app. 

You can't use cloud reader for other files but the content that Amazon provides.

---

### Post by mystmaiden on 2012-07-19
Thanks to everyone for the replies.

richpri - Thanks for pointing that out, I had forgotten to check the version on the  wine website. First thing, i'll have to figure out how to uninstall the current Kindle for pc.

blueshead - I like to use open source whenever I can so I did try calibre but I ran into this 
```

Following your upgrade to Precise
------------------------------------------------------
YOU NEED TO DO A FORCE DOWNGRADE OF PYTHON-QT4, OTHERWISE CALIBRE WON'T WORK PROPERLY.
 More info: https://launchpad.net/~n-muench/+archive/calibre
Press [ENTER] to continue or ctrl-c to cancel adding it
```I wasn't sure if this meant hitting yes would do the force downgrade or if it was something I have to do separately. Did you run into this?
Also, I noticed on amazon when I tried to dl the book, it only gives an option for kindle on pc. Will it even download if you do not have it?

l2k4 and epikvision - Thanks for the heads up about the cloud service. I use my laptop quite a bit when I am away from  internet access so I need the books on my hd. Still handy to know though.

mystmaiden

---

### Post by blueshead on 2012-07-19
> **mystmaiden said:**
> Thanks to everyone for the replies.

richpri - Thanks for pointing that out, I had forgotten to check the version on the  wine website. First thing, i'll have to figure out how to uninstall the current Kindle for pc.

blueshead - I like to use open source whenever I can so I did try calibre but I ran into this 
```

Following your upgrade to Precise
------------------------------------------------------
YOU NEED TO DO A FORCE DOWNGRADE OF PYTHON-QT4, OTHERWISE CALIBRE WON'T WORK PROPERLY.
 More info: https://launchpad.net/~n-muench/+archive/calibre
Press [ENTER] to continue or ctrl-c to cancel adding it
```

I wasn't sure if this meant hitting yes would do the force downgrade or if it was something I have to do separately. Did you run into this?
Also, I noticed on amazon when I tried to dl the book, it only gives an option for kindle on pc. Will it even download if you do not have it?

l2k4 and epikvision - Thanks for the heads up about the cloud service. I use my laptop quite a bit when I am away for internet access so I need the books on my hd. Still handy to know though.

mystmaiden

Yes.. go ahead and press enter.. Then enjoy calibre.. :D

---

### Post by papibe on 2012-07-19
Hi mystmaiden.
> **mystmaiden said:**
> I use my laptop quite a bit when I am away from  internet access so I need the books on my hd. Still handy to know though.

You can read books **offline** using the Amazon Cloud Reader. Read about it here: [Using Kindle Cloud Reader]("http://www.amazon.com/gp/help/customer/display.html?ie=UTF8&nodeId=200732280").

All you need is a browser :D

Regards.

---

### Post by mastablasta on 2012-07-20
if calibre PPA si still giving you problems then this command will definally work: [http://calibre-ebook.com/download_linux](http://calibre-ebook.com/download_linux)
 
installed it immediatelly after fresh 12.04 installation.

---

### Post by I2k4 on 2012-07-20
> **papibe said:**
> Hi mystmaiden.


You can read books **offline** using the Amazon Cloud Reader. Read about it here: [Using Kindle Cloud Reader]("Using Kindle Cloud Reader").

All you need is a browser :D

Regards.

Thanks.  Your link didn't work for me, but Google found it here:

[http://www.amazon.com/gp/help/customer/display.html?ie=UTF8&nodeId=200732280](http://www.amazon.com/gp/help/customer/display.html?ie=UTF8&nodeId=200732280)

Handy to know in Linux.

---

### Post by papibe on 2012-07-20
> **I2k4 said:**
> Your link didn't work for me,...

Oops, fixed now.

Regards.

---

