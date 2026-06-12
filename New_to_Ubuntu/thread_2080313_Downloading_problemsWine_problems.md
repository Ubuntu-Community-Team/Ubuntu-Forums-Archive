---
title: "Downloading problems/Wine problems"
date: 2012-11-03
forum: New to Ubuntu
---

### Post by traces09 on 2012-11-03
I just downloaded Ubuntu 9.10 into my computer. (It was the only disk I had.)

I have previously downloaded 9.10 from this same disk, and though it was a long time ago, I could have sworn it downloaded Wine too.

Either way, now I don't seem to have Wine. There are some windows programs that I need to install. I went to the Wine website and tried to install it, but only got an error message that it couldn't be found. 

I am stumped. I really, desperately need to download these Windows programs and Ubuntu 9.10 is all I have now. I would appreciate any help you could give me.

If you have suggestions, please note that I am no way techie inclined and only barely familiar with Ubuntu. I will need things explained to me in detail. (In other words, talk to me like I'm a 6 year old.)

Thanks in advance!

Tracy:confused:

---

### Post by ron999 on 2012-11-03
> **traces09 said:**
> I just downloaded Ubuntu 9.10 into my computer...
I would appreciate any help you could give me...

If you have suggestions...
Hi
Install Ubuntu 12.10

---

### Post by newb85 on 2012-11-03
9.10 hit end-of-life April 2010.  It's not really a good idea to continue to use a EOL release.  EOL releases no longer receive new updates, including security updates.  ron999 suggested upgrading to 12.10.  I suggest 12.04, as it's a little more mature and won't hit EOL until April 2017 (whereas 12.10 is less than a month old and will hit EOL April 2014).

If you *must* continue using 9.10, do the following:
[list=1]
[*]Open a terminal (Ctrl+Alt+T).
[*]Run this command:
```
sudo gedit /etc/apt/sources.list
```
(It will ask for your user password.  As you type it in, it won't give you any visual feedback.  That's normal and for security reasons.)
[*]Change all the addresses in this file that contain "archive.ubuntu.com" so the lines read 
> deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) karmic...
[*]Save the file.
[*]Close the gedit window.
[*]In the terminal window,
```
sudo apt-get update
sudo apt-get upgrade
```
[*]Close the terminal window.
[/list]
That should give you all the updates for 9.10 that were released before it hit EOL.  It *might* also enable you to install WINE.

---

### Post by traces09 on 2012-11-03
I was going to work my way up to 12.04 by upgrading in steps, as was suggested somewhere. I was able to upgrade to 10.04, but the next upgrade aborted and left Ubuntu unusable until I reinstalled 9.10. 

Has this been a common problem?

---

### Post by critin on 2012-11-03
> **traces09 said:**
> I was going to work my way up to 12.04 by upgrading in steps, as was suggested somewhere. I was able to upgrade to 10.04, but the next upgrade aborted and left Ubuntu unusable until I reinstalled 9.10. 

Has this been a common problem?

Upgrading that far up is a bad idea.  You can upgrade one version, but I wouldn't do any more than that during one session.  Too bad you can't download 12.04.   Fresh installs are more stable.   Again, you'll need to run all the 9.10 updates.  ugg....

A fully updated 10.04 LTS upgrades directly to 12.04 LTS so that's not too bad.  Don't upgrade today though, let it rest.  lol

Wine isn't installed in any 'buntu version by default.  It isn't easy to set up wine, have you done it before?  Do you know how?  I never could figure it out but I don't use windows programs anyway.  Open sources have everything I need.

Good luck.

---

### Post by traces09 on 2012-11-03
Okay...I made it to the the 10.04 LTS and the upgrade manager says I can now upgrade to 12.04. Whew.

I will let the system rest overnight and go for it. Wish me luck!

I actually like what I've seen so far of Ubuntu. I'm hoping to find that I can really work with it.

Thank you for your suggestions :)

---

