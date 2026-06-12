---
title: "Firefox 29.0.1 is out.  How to install on Ubuntu 14.04?"
date: 2014-05-14
forum: New to Ubuntu
---

### Post by cwmoser on 2014-05-14
How do you install a new version of Firefox?

Carl

---

### Post by slickymaster on 2014-05-14
On 32 bit Ubuntu:
```
wget ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/29.0.1/linux-i686/en-US/firefox-29.0.1.tar.bz2
tar -xjvf firefox-29.0.1.tar.bz2
sudo rm -rf /opt/firefox*
sudo mv firefox /opt/firefox29.0.1
sudo ln -sf /opt/firefox29.0.1/firefox /usr/bin/firefox
```
On 64 bit Ubuntu:```
wget ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/29.0.1/linux-x86_64/en-US/firefox-29.0.1.tar.bz2
tar -xjvf firefox-29.0.1.tar.bz2
sudo rm -rf /opt/firefox*
sudo mv firefox /opt/firefox29.0.1
sudo ln -sf /opt/firefox29.0.1/firefox /usr/bin/firefox
```

---

### Post by cwmoser on 2014-05-14
Thanks for the help.  Firefox upgraded perfectly with your commands.

---

### Post by Impavidus on 2014-05-14
Usually you can just let the automatic updater do its job.

---

### Post by vasa1 on 2014-05-14
I'm a bit puzzled as well.

---

### Post by jdeca57 on 2014-05-14
Isn't it so that for sake of stability only one better waits until the update is inserted in the standard repositories? Surely installing software manually might give problems...

---

### Post by The Spectre on 2014-05-15
I’m wondering why we haven’t received the Firefox 29.0.1 Update through automatic updates yet???

It has been out for almost a week and there are quite a few changes...
[http://www.mozilla.org/en-US/firefox/29.0.1/releasenotes/](http://www.mozilla.org/en-US/firefox/29.0.1/releasenotes/)

I think someone has dropped the ball and forgot about us.:(

---

### Post by caver12 on 2014-05-15
That is a little strange. My FF updated a while back through the update manager. Didn't have to do an ything. Using 14.04. :confused:

---

### Post by cwmoser on 2014-05-15
Before I issued the commands to do a manual install of Firefox 29.0.1, I tried 
the following over several days:
[B]sudo apt-get update
sudo apt-get upgrade[/B]

---

### Post by The Spectre on 2014-05-15
> **caver12 said:**
> That is a little strange. My FF updated a while back through the update manager. Didn't have to do an ything. Using 14.04. :confused:
Is your Firefox updated 29.0.1?

---

### Post by monkeybrain20122 on 2014-05-15
Not sure if they upgrade all the minor releases (is this the word? I mean something like 29.0 -> 29.0.1), these releases may not have anything relevant to our platform, say it may fix a bug for OSX. I have 29.0 and when I went to Mozilla's download page it says "congrats! you are using the latest Firefox."

---

### Post by pqwoerituytrueiwoq on 2014-05-24
now available via ppa
[https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa)
```
sudo apt-add-repository ppa:ubuntu-mozilla-security/ppa -y && sudo apt-get update && sudo apt-get upgrade
```

---

