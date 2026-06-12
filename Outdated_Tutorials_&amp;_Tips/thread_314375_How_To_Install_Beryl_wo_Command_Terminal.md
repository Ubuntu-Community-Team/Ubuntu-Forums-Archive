---
title: "How To Install Beryl w/o Command Terminal"
date: 2006-12-07
forum: Outdated Tutorials &amp; Tips
---

### Post by Tenchi on 2006-12-07
Hello Everyone,

I found this wonderful how to online of how you can install Beryl without using the command terminal and I wish to share it with everyone.

My specs are:
Edgy on a HP laptop ze2315, ATI Radeon Xpress 200M.

[Link to How To]("http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html")

And you’ll have to change the third party source to 

```
deb http://beryl-mirror.lupine.me.uk edgy all
```

The only issue I have is on my 2nd boot I lost my shutdown button, but you can log out and shutdown.

ENJOY :D

---

### Post by bugz0r on 2006-12-12
I can't download the gpg key for some reason. Can I get it somewhere else?

---

### Post by djlyx on 2006-12-12
ditto

---

### Post by PriceChild on 2006-12-12
The gpg key has changed.

It is now [EMAIL="root@lupine.me.uk"]root@lupine.me.uk[/EMAIL]

Please also make ALL downloads from lupine.me.uk instead from the ubuntu.beryl-project.org server. This will distribute the load.

For example,

```
wget ubuntu.beryl-project.org/root@lupine.me.uk.gpg
```Points to both:```
wget beryl-mirror.pricechild.co.uk/root@lupine.me.uk.gpg
wget beryl.lupine.me.uk/root@lupine.me.uk.gpg
```Your sources list should be```
deb http://ubuntu.beryl-project.org edgy main
```And nothing else (unless running 64bit)

---

### Post by hikaricore on 2006-12-12
> [hikaricore@devistate:~]$ wget ubuntu.beryl-project.org/root@lupine.me.uk
--21:44:36--  [http://ubuntu.beryl-project.org/root@lupine.me.uk](http://ubuntu.beryl-project.org/root@lupine.me.uk)
           => `root@lupine.me.uk'
Resolving ubuntu.beryl-project.org... 89.200.136.91, 82.140.42.54
Connecting to ubuntu.beryl-project.org|89.200.136.91|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
21:44:37 ERROR 404: Not Found.

[hikaricore@devistate:~]$ wget beryl-mirror.pricechild.co.uk/root@lupine.me.uk
--21:44:53--  [http://beryl-mirror.pricechild.co.uk/root@lupine.me.uk](http://beryl-mirror.pricechild.co.uk/root@lupine.me.uk)
           => `root@lupine.me.uk'
Resolving beryl-mirror.pricechild.co.uk... 82.140.42.54
Connecting to beryl-mirror.pricechild.co.uk|82.140.42.54|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
21:44:53 ERROR 404: Not Found.

Looks like I'll have to wait for it to exist.

:P

---

### Post by PriceChild on 2006-12-13
Whoops sorry... editied post accordingly.

---

### Post by hikaricore on 2006-12-13
Hehehe, it happens.

---

### Post by lenswipe on 2007-12-11
hi all im trying to install beryl on ubuntu 7.1 gutsy. Thing is i got told that it can be done via command line by downloading beryl from [here]("http://www.beryl-project.org/releases.php") and then pointing the terminal at the folder with the scource code in and typing ./make and then typing ./configure


when i do this though it just returns bash command not found.

can anyone shed any light on this please..

---

### Post by PriceChild on 2007-12-11
Compiz Fusion (new name for project that was beryl) is now in Gutsy by default. Use that instead.

system > preferences > desktop effects

---

### Post by lenswipe on 2007-12-11
> **PriceChild said:**
> Compiz Fusion (new name for project that was beryl) is now in Gutsy by default. Use that instead.

system > preferences > desktop effects


yea i got that working thanks but i wana know how to get beryl working becuase it does a whole lote more stuff....


like it can do the wipe down with fire when you minimise it etc...

thanks

---

### Post by mcduck on 2007-12-11
> **lenswipe said:**
> yea i got that working thanks but i wana know how to get beryl working becuase it does a whole lote more stuff....


like it can do the wipe down with fire when you minimise it etc...

thanks

No, they do all the same stuff. you just need to install compizconfig-settings-manager to be able to control every detail and select what plugins and effects you want to use. :)

---

### Post by Webdragun on 2008-03-22
> **mcduck said:**
> No, they do all the same stuff. you just need to install compizconfig-settings-manager to be able to control every detail and select what plugins and effects you want to use. :)

And how would one go about doing this? :)

I'm using gutsy 7.1, have not got my internet connection working with it yet.. so if there is a way to do it that doesn't involve connecting.. that would be awesome.

Thanks,
Webdragun

---

