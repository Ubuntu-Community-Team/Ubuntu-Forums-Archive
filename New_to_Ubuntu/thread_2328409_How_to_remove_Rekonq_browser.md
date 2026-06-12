---
title: "How to remove Rekonq browser"
date: 2016-06-20
forum: New to Ubuntu
---

### Post by rdb3 on 2016-06-20
I installed the Rekong browser via terminal and would like to uninstall.

I entered:  sudo apt-get --purge remove rekong

Did not remove it.  It's in home > .kde

Any suggestions on how to remove it all?  Thanks.

---

### Post by vasa1 on 2016-06-20
Try rekonq instead of rekong.

---

### Post by Impavidus on 2016-06-21
+1

Furthermore, the stuff in your HOME/.kde must be the user configuration files, cache, cookies etc. Those are not automatically removed when the software is uninstalled. You can remove it manually after you have uninstalled rekonq.

---

### Post by rdb3 on 2016-06-21
> **vasa1 said:**
> Try rekonq instead of rekong.

I kept looking at your post over and over again and could not see the difference between a 'q' and a 'g'  until finally ...  :D

Thank you.

---

### Post by vasa1 on 2016-06-21
> **rdb3 said:**
> I kept looking at your post over and over again and could not see the difference between a 'q' and a 'g'  until finally ...  :D

Thank you.Not to worry. We've all been there before ;)

---

### Post by rdb3 on 2016-06-21
> **Impavidus said:**
> +1

Furthermore, the stuff in your HOME/.kde must be the user configuration files, cache, cookies etc. Those are not automatically removed when the software is uninstalled. You can remove it manually after you have uninstalled rekonq.

Going to HOME and .kde and doing right click, Move to trash, will do it?  Just want to make sure I don't leave any residual stuff behind.

---

### Post by vasa1 on 2016-06-21
> **rdb3 said:**
> Going to HOME and .kde and doing right click, Move to trash, will do it?  Just want to make sure I don't leave any residual stuff behind.
Do you have any other kde apps?
Better provide the output of **ls -R ~/.kde** before proceeding.

---

### Post by rdb3 on 2016-06-21
> /home/maxie/.kde/share/apps/kssl/userCaCertificates:

/home/maxie/.kde/share/apps/kwallet:


/home/maxie/.kde/share/apps/rekonq:
adblockrc  history  session


/home/maxie/.kde/share/config:
drkonqirc       kdebugrc    kioslaverc              kwalletrc
katerc          kdedrc      ksslcertificatemanager  phonondevicesrc
kconf_updaterc  kdeglobals  ktimezonedrc            rekonqrc
kcookiejarrc    kio_httprc  kuriikwsfilterrc


/home/maxie/.kde/share/kde4:
services


/home/maxie/.kde/share/kde4/services:
searchproviders


/home/maxie/.kde/share/kde4/services/searchproviders:


No other kde apps.  Does removal of kde affect libreoffice or any other packages that installed with Ubuntu 16.04?

---

### Post by vasa1 on 2016-06-21
No, libreoffice isn't kde-related.

Just to be safe, run **sudo apt-get purge -s rekonq** first and see what is proposed to be removed. The **-s** provides a simulation = dry run.

(No need for  sudo apt-get --purge remove ...; sudo apt-get purge is enough.)

---

### Post by rdb3 on 2016-06-21
[B]sudo apt-get purge -s rekonq
[/B]
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Package 'rekonq' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
```

---

### Post by vasa1 on 2016-06-21
> **rdb3 said:**
> [B]sudo apt-get purge -s rekonq
[/B]
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Package 'rekonq' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
```So you've already removed the program? And now you're only concerned with ~/.kde? In that case, just delete the folder!

BTW, why the **10 not upgraded**?

---

### Post by rdb3 on 2016-06-21
> **vasa1 said:**
> So you've already removed the program? And now you're only concerned with ~/.kde? In that case, just delete the folder!

BTW, why the **10 not upgraded**?

Yes, I removed rekonq around post #4.

Sorry, not sure what **10 not upgraded**&#8203; means.   :confused:

If it's in reference to KDE applications releases, this is what I did to install rekonq originally:

[http://ubuntuhandbook.org/index.php/2014/01/install-rekonq-browser-2-4-2-ubuntu/](http://ubuntuhandbook.org/index.php/2014/01/install-rekonq-browser-2-4-2-ubuntu/)

---

### Post by vasa1 on 2016-06-21
> **rdb3 said:**
> ...
Sorry, not sure what **10 not upgraded**&#8203; means.   :confused:
...
If you run ```
sudo apt-get update
```followed by```
sudo apt-get upgrade
``` you'll know. You can always refuse to proceed by pressing "n" instead of "Y" at the prompt.

You'll get a more complete picture by **next** running```
sudo apt-get dist-upgrade
```. Again, you can abort the process as described above.

If you wish, you can post the complete output of each command here using [code] tags to enclose the terminal output.

---

### Post by Impavidus on 2016-06-21
> **rdb3 said:**
> Going to HOME and .kde and doing right click, Move to trash, will do it?  Just want to make sure I don't leave any residual stuff behind.

Not the entire .kde directory, just the directory belonging to rekonq. From your following post that would be ~/.kde/share/apps/rekonq.

---

### Post by rdb3 on 2016-06-21
> **vasa1 said:**
> If you run ```
sudo apt-get update
```followed by```
sudo apt-get upgrade
``` you'll know. You can always refuse to proceed by pressing "n" instead of "Y" at the prompt.

You'll get a more complete picture by **next** running```
sudo apt-get dist-upgrade
```. Again, you can abort the process as described above.

If you wish, you can post the complete output of each command here using [code] tags to enclose the terminal output.

Thanks.  Good to know and made a note of it.

At this point, I just want to delete the kde folder.

Since rekonq has been removed, I think I will mark this thread Solved.

---

### Post by rdb3 on 2016-06-21
> **Impavidus said:**
> Not the entire .kde directory, just the directory belonging to rekonq. From your following post that would be ~/.kde/share/apps/rekonq.

Yes, my next attempt will be to remove kde.  Thanks.

---

