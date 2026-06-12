---
title: "How can I safely install over 1000 packages including solving dependencies &amp; Updates?"
date: 2012-03-02
forum: New to Ubuntu
---

### Post by Lucypie on 2012-03-02
Okay, I will be reinstalling ubuntu from ubuntu 11.04. I have a backup of every package I've ever installed, 1472 in total. I wish to reinstall all of these. Some are updates to other packages. Its very confusing trying to install them via symnaptic. It always gives me broken package errors. If I reinstall ubuntu completely, I will have a fresh chance. So please help me :) Thank you!!

---

### Post by cortman on 2012-03-02
I would recommend you come up with a list of all the programs you use on a regular basis, ones that actually benefit you, and just re-download and install them from scratch. This will save you a lot of crud on your system. Any program you find you need and don't have you will always be able to download for free whenever you want.
If you prefer to use your existing debs and want to reinstall EVERYTHING, [this blog post ]("http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/")might help you out.

---

### Post by Lucypie on 2012-03-02
Cortman, the reason I don't redownload is because of my internet limit. I don't wish to go over. Plus, I could never list all the programs I always am using. Thanks for the link, I will check it out.

EDIT: About that... It is actually a collection of 3 or 4 different installations. I've had some, uhm, problems.... constantly :) But it was AptOnCd, so i have somewhat of a list, but it still causes problems seeing there are many updates in with it.

---

### Post by cortman on 2012-03-02
> **Lucypie said:**
> Cortman, the reason I don't redownload is because of my internet limit. I don't wish to go over.

I can understand this.

I'm NOT SURE if it'll work or not, but if you'd copy all your packages to /var/cache/apt/archives, you may be able to reinstall them simply using apt-get. Aptitude first looks for downloaded debs in that folder (and installs them) before downloading new.

---

### Post by Lucypie on 2012-03-03
Is apt-get all I would use, or would I use apt-get programname? I could probably handle that, but it would cause a pain for things like GIMP with all the extra plugins and packages, or some uncommon programs that I have no clue what the name are. Thank you again :)

PS. My computer hates this forum. Since I reinstalled this system, I haven't visited this forum. I also had no problems. Now I'm having my old problems again LOL. Such a mean system, but I love it :)

---

### Post by Paqman on 2012-03-03
You can pass multiple packages to apt-get for installtion. For example:
```
sudo apt-get install package1 package2 package3
```

I don't know if it would be happy doing all 1472 in one command though. If not you could write a short script that looped through the list and installed them individually. Might take a while, but wouldn't necessarily need to be babysat while it worked.

Just to be clear: if you dump the packages into APT's package cache (/var/cache/apt/archives) owned by root then any apt-get commands will install the cached copy if there's no newer one available.

---

### Post by Bucky Ball on 2012-03-03
Just make a bootable CD of your install with Remastersys: 

[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

Go to 'Ubuntu Version'. This will make a bootable and installable 'LiveCD' of your current computer configuration, including all currently installed and updated packages. You don't need all that stuff.

Here's some other ideas:

[http://au.search.yahoo.com/yhs/search?p=create+ubuntu+cd+of+current+configuration&fr=altavista&fr2=sfp&iscqry=](http://au.search.yahoo.com/yhs/search?p=create+ubuntu+cd+of+current+configuration&fr=altavista&fr2=sfp&iscqry=)

There's a few different softwares that can do this for you without you doing all that stuffing about ... extremely long-winded and unnecessary. Use a pre-existing tool to do this as so far people are trying to reinvent the wheel here (no offence intended and hopefully none taken). ;)

---

### Post by cortman on 2012-03-03
> **Bucky Ball said:**
> Just make a bootable CD of your install with Remastersys: 

[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

Go to 'Ubuntu Version'. This will make a bootable and installable 'LiveCD' of your current computer configuration, including all currently installed and updated packages. You don't need all that stuff.

Here's some other ideas:

[http://au.search.yahoo.com/yhs/search?p=create+ubuntu+cd+of+current+configuration&fr=altavista&fr2=sfp&iscqry=](http://au.search.yahoo.com/yhs/search?p=create+ubuntu+cd+of+current+configuration&fr=altavista&fr2=sfp&iscqry=)

There's a few different softwares that can do this for you without you doing all that stuffing about ... extremely long-winded and unnecessary. Use a pre-existing tool to do this as so far people are trying to reinvent the wheel here (no offence intended and hopefully none taken). ;)

If the OP is reinstalling due to a messed-up system, making a duplicate of the current configuration seems rather to defeat the purpose...?

---

### Post by Bucky Ball on 2012-03-03
> **cortman said:**
> if the op is reinstalling due to a messed-up system, making a duplicate of the current configuration seems rather to defeat the purpose...?

k. ;)

---

### Post by Lucypie on 2012-03-06
My apologies for the long wait of response... I might have forgotten that I posted this.

Yes, I am reinstalling due to a system screw-up. When my system was fine and dandy, I thought about using remastersys to back it up. But noooooo, This is good and I don't need any backup..... Hmmm. 

I'm considering waiting until I take my business trip to reinstall all updates, seeing I'll be spending two nights in a hotel... but what if the internet is useless? Who knows... I soon may try reinstalling my system. Thank you all again for your answers... I hope they help me when I reinstall!!

---

### Post by Bucky Ball on 2012-03-06
Just a note: many ISPs support certain servers and downloads and uploads to and from them don't effect your quota (for me it is aarnet in Australia which has  Ubuntu mirrors). You might want to look into that, find a supported server that has Ubuntu mirrors. You then change your server in Software Sources to the one your ISP supports and all good. Update/upgrade/download away! ;)

---

