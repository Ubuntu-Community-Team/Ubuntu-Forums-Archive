---
title: "apt-get or aptitude ?"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by Sealbhach on 2008-07-07
I seem to see from looking at the forums that there is a difference between

```
sudo apt-get install package
```

and

```
sudo aptitude install package
```


or "remove package".

What's the difference?  Does it matter which one I use? 


.

---

### Post by hyper_ch on 2008-07-07
aptitude will install also the "recommended" packages and removal of meta-packages seems to be better handled...

however I prefer apt-get as it does install only the necessary packages.

---

### Post by Linux_Man on 2008-07-07
I think that apitude had some features that weren't supported in older versions of apt-get but I believe that now they are essentially the same. At least I always have used apt-get install rather then using aptitude install and my HD is still in one piece but your millage may be different.

---

### Post by Seisen on 2008-07-07
This link should explain everything in better detail.

[http://www.psychocats.net/ubuntu/aptitude]("http://www.psychocats.net/ubuntu/aptitude")

---

### Post by billgoldberg on 2008-07-07
> **Sealbhach said:**
> I seem to see from looking at the forums that there is a difference between

```
sudo apt-get install package
```

and

```
sudo aptitude install package
```


or "remove package".

What's the difference?  Does it matter which one I use? 


.


I would use apt-get

to remove use

apt-get autoremove package

---

### Post by ibuclaw on 2008-07-07
For a long time, aptitude was the better app because apt-get was awful at dependency handling.

Now it has kind of evened out a bit, so it doesn't really matter, but aptitude still kicks apt-get's behind when it comes to purging application residual config after they've been uninstalled. (Residual Config are orphaned config and man files that you don't need, because the app isn't install anymore).

```

# to view residual config installs
dpkg -l | awk '{if ($1 == "rc") print $2}'
# to store them in a variable
export PACKAGES=$(dpkg -l | awk '{if ($1 == "rc") print $2}')
# to remove all rc files afterwards.
sudo aptitude purge $PACKAGES

```
The above would not work if you tried it with apt-get.

Also, aptitude **does not install the recommended packages by default**, thank-you very much! :popcorn:

But, in recommendation.
Perhaps
```

sudo apt-get install package
sudo aptitude purge package

```
is perhaps the way to go in the future.

Regards
Iain

---

