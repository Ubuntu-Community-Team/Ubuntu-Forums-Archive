---
title: "Google Chrome"
date: 2012-10-25
forum: New to Ubuntu
---

### Post by ex-para on 2012-10-25
I am using 12.4. Is Google Chrome included in the depositories/ packages, if so I cant find it, if not would it be best to use Terminal and please how to do this.

---

### Post by PaulW2U on 2012-10-25
No, Google Chrome is not in the repositories.

You can install Chromium which is in the repositories or Google Chrome by following the instructions at [http://www.ubuntuupdates.org/ppa/google_chrome](http://www.ubuntuupdates.org/ppa/google_chrome).

---

### Post by ex-para on 2012-10-25
Thanks for the reply do I need to use all these commands.

wget -q -O - [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | sudo apt-key add - 

Setup repository with:

sudo sh -c 'echo "deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main" >> /etc/apt/sources.list.d/google.list'

Setup package with:

sudo apt-get update 
sudo apt-get install <package name>

---

### Post by PaulW2U on 2012-10-25
> **ex-para said:**
> Thanks for the reply do I need to use all these commands.

Yes you do.

Once installed you may see an error when you run an update as a duplicate Google repository is sometimes added. Just delete one of the entries.

---

### Post by vasa1 on 2012-10-25
I find it easier to use another browser to navigate to dl.google.com and then just follow the instructions on screen. Just point and click.

---

### Post by ex-para on 2012-10-26
Could not get those instructions to work after several attempts but I did find out Chromium is in the packages so I did download that and I see no difference. Thanks again for the replies.

---

### Post by monkeybrain2012 on 2012-10-26
You can just download and install the .deb from Chrome's website. Once installed it will automatically create its own repository entry in your sources list (so it will be updated like other software you installed from Ubuntu's repositories)

Well one common reason to install Chrome is because of flash, since Chromium doesn't have it I see no point in installing Chromium, I would prefer Firefox any day for other purposes, just my two cents.

---

### Post by ex-para on 2012-10-28
I just did not know that but thanks for the information as I now do.

---

