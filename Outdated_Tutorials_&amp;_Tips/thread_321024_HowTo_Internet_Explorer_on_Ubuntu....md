---
title: "HowTo Internet Explorer on Ubuntu..."
date: 2006-12-18
forum: Outdated Tutorials &amp; Tips
---

### Post by jbaloul on 2006-12-18
[http://howtoforums.net/viewtopic.php?t=172](http://howtoforums.net/viewtopic.php?t=172)

Are you stuck on Windows because of a few web sites that require Internet Explorer?
Don't you really wish Internet Explorer would just run on your Linux PC instead of buying an expensive PC to run VMware on Linux?
Are you stuck with these...
[i]"hmmm...dual boot, should I ?"
"If Mac could do it, why can't Linux?"
"I heard of emulators like Wine, but just couldn't get it to work?"[/i]

Is this what you are looking for?
[http://howtoforums.net/downloads/screenshots/ies4linux/ies4linux.png](http://howtoforums.net/downloads/screenshots/ies4linux/ies4linux.png)

So, after venturing in the world of migration...
We found this:
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

A very cool, easy to follow instructions which automates the installation and configuration of Linux, Wine, & IE

It simply works...
It will create everything for you...just follow the instructions based on your Linux distribution here:
[http://www.tatanka.com.br/ies4linux/page/Installation](http://www.tatanka.com.br/ies4linux/page/Installation)

Once installed, you should have a directory like this...
```

/home/jacob/.ies4linux/bin

```
...with all the versions of IE you chose during install.
You can either click on the shortcuts created for you on the desktop or, run them in a console, such as:
```

~/.ies4linux/bin/ie6 &

```

------------------
If you are looking for other stuff in this realm this mite interest you as well:
[ HowTo install rdesktop 1.5 including SeamLess Windows ](http://howtoforums.net/viewtopic.php?t=52)
[HowTo auto-install VMware-Server on Ubuntu 6.06 Dapper ](http://howtoforums.net/viewtopic.php?t=55)

--
Enjoy!
Jacob
[http://howtoforums.net](http://howtoforums.net)
"every man dies, but not every man really lives"

---

### Post by aysiu on 2006-12-18
For Ubuntu users, you'll have to install *wine* and *cabextract* before you can use the IEs4Linux installer.

Full Ubuntu-specific instructions with screenshots here:
[http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux)

---

### Post by BLTicklemonster on 2006-12-18
I stupided out and, on a fresh install of edgy, I went to install ies4linux, and just after pressing enter from the command line, I freaked because I knew I hadn't installed wine or cabextract, yet ies4linux installed perfectly.

---

### Post by aysiu on 2006-12-18
> **BLTicklemonster said:**
> I stupided out and, on a fresh install of edgy, I went to install ies4linux, and just after pressing enter from the command line, I freaked because I knew I hadn't installed wine or cabextract, yet ies4linux installed perfectly.
Really? I wonder how that worked. Does the new version of the script install Wine and Cabextract for you?

---

### Post by BLTicklemonster on 2006-12-18
No idea, but that was on either edgy or feisty. I just redid my edgy back to dapper, clean install, so I'm about to try it again and see. I'll let you know as soon as beryl finishes downloading and downloading and downloading and downloading lol.

---

### Post by BLTicklemonster on 2006-12-18
Huh. Had to install wine and cabextract in Dapper, but I know I didn't have either of them in Edgy, and I don't have them in Feisty. I'll boot to Feisty in a little while and see if I have it in there. Otherwise, I reckon I been trippin'.

---

### Post by aysiu on 2006-12-18
> **BLTicklemonster said:**
> Huh. Had to install wine and cabextract in Dapper, but I know I didn't have either of them in Edgy, and I don't have them in Feisty. I'll boot to Feisty in a little while and see if I have it in there. Otherwise, I reckon I been trippin'.
I'm wondering which one of these it is:

1 ) The IEs4Linux script has been modified to install Wine and Cabextract for you
2 ) The IEs4Linux script has been modified to somehow no longer need Wine and Cabextract
3 ) You somehow installed Wine and Cabextract without knowing it? Or installed them in Dapper and they were still around after you upgraded to Edgy?

Because it's definitely not this:
4 ) Cabextract and Wine are now included as part of the default Ubuntu installation, as of Edgy and Feisty.

Don't believe me--go here:
[http://packages.ubuntu.com/edgy/metapackages/ubuntu-desktop](http://packages.ubuntu.com/edgy/metapackages/ubuntu-desktop)

---

### Post by BLTicklemonster on 2006-12-18
I believe you. Hence the "I been tripping" statement. I just don't remember ever putting wine or cabextract on either of them. Having some problems right now, though. I can't get fluxbox to come up when I log out. It's installed, and there's a .fluxbox directory in /home/me, but I can't get it! ](*,) 

Anyway, I stand corrected. Gotta start paying attention to which cigarettes I buy and smoke, I reckon. Sorry for the misunderstanding.

---

### Post by Incompetnce on 2007-02-23
> **aysiu said:**
> For Ubuntu users, you'll have to install *wine* and *cabextract* before you can use the IEs4Linux installer.

Full Ubuntu-specific instructions with screenshots here:
[http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux)

Those screenshots and instructions are for dapper, edgy looks slightly different... I cant work out whether I have the universe thing or not. im scared of running the script on that page, in case edgy is different... any clues?

---

### Post by aysiu on 2007-02-23
I think in Edgy it's called Software Sources instead of Software Properties.

---

