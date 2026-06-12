---
title: "update upgrade"
date: 2012-09-25
forum: New to Ubuntu
---

### Post by Primus1 on 2012-09-25
Hi, just updated my computer, used the Terminal instead of the update manager :). Got these results and would like to check with you if there is a problem or not please:

W: Failed to fetch [http://ppa.launchpad.net/fabio-massaioli/lockbox-ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/fabio-massaioli/lockbox-ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


**After the update:**


No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.

Setting up ghostscript-cups (8.71.dfsg.1-0ubuntu5.5) ...

Setting up ghostscript-x (8.71.dfsg.1-0ubuntu5.5) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
dave@dave-storm:~$ 

Just concerned about the 'failed to find' and Index files not being found. Sorry if I have not formatted the code properly.
Thanks.

---

### Post by NikTh on 2012-09-25
Hi , 
the ppa you have does not exits. Either removed from laucnhpad or there is a mistake in name. 

If you remove the PPA , then you will be fine.

From terminal (Ctrl+Alt+T) run this command 
```
gksudo software-properties-gtk
``` at the opened window , go to "Other Software" and find the PPA named **fabio-masa** and remove it. 

Then run again ```
sudo apt-get update 
sudo apt-get upgrade
``` 

Thanks

---

### Post by newb85 on 2012-09-25
Looks like there's a problem with your sources list, specifically surrounding Fabio Massaioli's PPA for lockbox.

Go to /etc/apt/sources.list.d and find the file for that ppa.  It will be something like fabio-massioli-lockbox-precise.list

Copy the contents or simply attach the file to a new post.

---

### Post by newb85 on 2012-09-25
> **NikTh said:**
> Hi , 
the ppa you have does not exits. Either removed from laucnhpad or there is a mistake in name. 

It definitely still exists, and it's right [here]("https://launchpad.net/~fabio-massaioli/+archive/lockbox-ppa").

---

### Post by NikTh on 2012-09-25
> **newb85 said:**
> It definitely still exists, and it's right [here]("https://launchpad.net/~fabio-massaioli/+archive/lockbox-ppa").

So the quick fix for that is 

To remove the PPA as I said and add the correct one 
Removing
```
sudo rm /etc/apt/sources.list.d/fabio*
```

Adding
```
sudo add-apt-reposirotry **ppa:fabio-massaioli/lockbox-ppa**
sudo apt-get update
``` 

:)

---

### Post by newb85 on 2012-09-25
Agreed.  It would still be nice to see the contents of the file before you remove it.  But maybe that's just my curiosity getting the best of me.

---

### Post by Primus1 on 2012-09-25
Thanks for replies,

@ newb85
The file at sources.list.d only contains this:

deb [http://ppa.launchpad.net/fabio-massaioli/lockbox-ppa/ubuntu](http://ppa.launchpad.net/fabio-massaioli/lockbox-ppa/ubuntu) lucid main

I don't recall installing this Lockbox software. It's not in my menu of apps so I assume it's run from the Terminal. Looks very useful so I will apply the fixing code from NikTh (thanks) but first post this for your comments.

---

### Post by newb85 on 2012-09-25
You should be able to check Synaptic or the Software Center to see if it's installed.  If the ppa wasn't added correctly, it very likely isn't.

---

