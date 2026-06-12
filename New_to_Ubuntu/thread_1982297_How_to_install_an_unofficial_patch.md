---
title: "How to install an unofficial patch?"
date: 2012-05-18
forum: New to Ubuntu
---

### Post by Houmie on 2012-05-18
Hi,

lxkeymap can't be started in LUBUNTU due a bug, that is confirmed and fixed here:

[https://bugs.launchpad.net/ubuntu/+source/lxkeymap/+bug/945603]("https://bugs.launchpad.net/ubuntu/+source/lxkeymap/+bug/945603")

Apparently the fix for it is here:

[https://launchpad.net/~lubuntu-dev/+archive/staging?field.series_filter=precise]("https://launchpad.net/~lubuntu-dev/+archive/staging?field.series_filter=precise")


I have accordingly added the PPA to my system:

```
sudo add-apt-repository ppa:gwibber-daily/ppame
```

and did a ```
sudo apt-get update
```

What is the next step to install the patch?

Thanks,

---

### Post by nothingspecial on 2012-05-18
> **Houmie said:**
> 


I have accordingly added the PPA to my system:

```
sudo add-apt-repository ppa:gwibber-daily/ppame
```



That's the wrong PPA it should be ppa:lubuntu-dev/staging

anyway, once you have the right one and have updated ```
sudo apt-get upgrade 
``` should upgrade lxkeymap for you.

---

### Post by Houmie on 2012-05-18
Thanks. I'll try that.  Do you know how to uninstall the wrong PPA?

---

### Post by nothingspecial on 2012-05-18
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:gwibber-daily/ppame
```

---

### Post by Houmie on 2012-05-18
Thank you :)

---

### Post by Houmie on 2012-05-18
Sorry, it seems even adding ppa:lubuntu-dev/staging and doing an update thereafter, won't update/fix the lxkeymap

Could it be that I had to sudo apt-get install ??? something?

 lxkeymap	 0.7.99+dfsg-0ubuntu2~ppa1

?

I tried either and it cant find it.

Many Thanks for your help, I need to get this fixed today before i fly back,

Thanks,

---

### Post by nothingspecial on 2012-05-18
Try removing and reinstalling it after updating.

---

### Post by Houmie on 2012-05-18
> **nothingspecial said:**
> Try removing and reinstalling it after updating.

I have some great news. 

After applying the correct ppa as described above;

It is not enough to do a ```
sudo apt-get update
```

You have to click on System Tools -> Update manager and apply the updates to replace the lxkeymap.

Works like a charm, no other steps required.

Thanks for pointing me to the right direction. :)

---

