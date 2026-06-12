---
title: "Installing Firefox 3?"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by Xm3buX on 2008-08-13
I've downloaded firefox 3, and the thing went on my desktop, but how do I install it?

Thanks!

---

### Post by Crafty Kisses on 2008-08-13
> **Xm3buX said:**
> I've downloaded firefox 3, and the thing went on my desktop, but how do I install it?

Thanks!

What version of Ubuntu are you using? If your using Ubuntu 8.04, it's already pre-installed.

---

### Post by null byte on 2008-08-13
Try [http://www.youtube.com/watch?v=pIpne4cc3Hk](http://www.youtube.com/watch?v=pIpne4cc3Hk)

---

### Post by peakshysteria on 2008-08-13
if you're using Ubuntu: **Aplications --> Internet --> Firefox**

---

### Post by Xm3buX on 2008-08-13
> **Codename said:**
> What version of Ubuntu are you using? If your using Ubuntu 8.04, it's already pre-installed.
I'm using the latest one, but it's got firefox 2.

> **null byte said:**
> Try [http://www.youtube.com/watch?v=pIpne4cc3Hk](http://www.youtube.com/watch?v=pIpne4cc3Hk)
Can't watch it, I need flash, and I downloaded flash, but it's just a box on my desktop.

OK,hows this? How do I install things once they've downloaded?
Because right now they're just a box on my desktop :(

---

### Post by Crafty Kisses on 2008-08-13
> **Xm3buX said:**
> I'm using the latest one, but it's got firefox 2.


Can't watch it, I need flash, and I downloaded flash, but it's just a box on my desktop.

OK,hows this? How do I install things once they've downloaded?
Because right now they're just a box on my desktop :(

Open Terminal and run:
```
sudo apt-get update
sudo apt-get install firefox-3.0
```

---

### Post by kostkon on 2008-08-13
> **Xm3buX said:**
> I'm using the latest one, but it's got firefox 2.
The latest version of Ubuntu, 8.04, uses Firefox 3. So I assume you are using 7.10 Gutsy Gibbon?

Go to *System -> About Ubuntu* or *System -> Administration -> System Monitor* to see what version of Ubuntu you have.

---

### Post by nothingspecial on 2008-08-13
```
sudo apt-get install flashplugin-nonfree
```

Will install flash.

In most cases you shouldn`t have to download stuff from the internet. Use add/remove or synaptic package manager (system > administration > synaptic package manager.)
If you do need an app that isn`t availble that way look for a .deb as these install automatically.

---

### Post by peakshysteria on 2008-08-13
Could you please post the output of:
```
cat /etc/lsb-release
```

---

### Post by nothingspecial on 2008-08-13
Oh yeah and read this. It will explain a lot.

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Xm3buX on 2008-08-13
> **kostkon said:**
> The latest version of Ubuntu, 8.04, uses Firefox 3. So I assume you are using 7.10 Gutsy Gibbon?

Go to *System -> About Ubuntu* or *System -> Administration -> System Monitor* to see what version of Ubuntu you have.
Nope, it says I've got hardy.

---

### Post by nothingspecial on 2008-08-13
You should have firefox 3 then.

---

### Post by Crafty Kisses on 2008-08-13
I've already suggested this, but I'll suggest it again:
```
sudo apt-get update
sudo apt-get install firefox-3.0
```
If he has Ubuntu 8.04, then Firefox 3 is in the repos, and he can easily get it from the repos, it's not a problem.

---

### Post by Dill on 2008-08-13
First, open firefox in a Terminal

```
firefox &
```

or from the Applications menu...

**Applications** -> **Internet** -> **Firefox Web Browser**

and, in Firefox, go to 

**Help** -> **About Mozilla Firefox**

If this says you have version 2.0.x.nn, then you should go back to the Terminal and do this:

```
cd ~/Desktop
rm name_of_firefox_package.tar.gz
sudo apt-get install firefox-3.0 
```

where name_of_firefox_package is the name of the "box" you downloaded. As people have mentioned before, it's much easier to use Synaptic to install applications in Ubuntu.

If you'd like to install the package from source, you can check this link out:

[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

I've actually never installed anything from source myself, but I believe this should work. Perhaps others can comment on such an installation process.

[I]Also, I read through the thread again-- thanks to nothingspecial for providing this link, which is much more extensive than the one I posted:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Cheers for that.[/I]

Cheers, 
Dylan

---

