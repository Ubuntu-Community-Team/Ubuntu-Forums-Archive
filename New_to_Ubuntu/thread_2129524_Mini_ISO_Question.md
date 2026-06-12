---
title: "Mini ISO Question"
date: 2013-03-26
forum: New to Ubuntu
---

### Post by mamamia88 on 2013-03-26
If Install the Ubuntu-Desktop package after installing a cli only install will it be the same result as downloading the entire cd and installing from that?

---

### Post by deadflowr on 2013-03-26
I don't know.

Would you get firefox, and thunderbird, and libreoffice with that?

Or is it just the base Unity/Gnome packages.

---

### Post by mamamia88 on 2013-03-26
[http://packages.ubuntu.com/quantal/ubuntu-desktop](http://packages.ubuntu.com/quantal/ubuntu-desktop). Can I use the no install reccomends option then install a couple of the reccomends separate?

---

### Post by deadflowr on 2013-03-26
> **mamamia88 said:**
> [http://packages.ubuntu.com/quantal/ubuntu-desktop](http://packages.ubuntu.com/quantal/ubuntu-desktop). Can I use the no install reccomends option then install a couple of the reccomends separate?

I can see no reason why not.

If let's say you want to install evolution instead of thunderbird.

---

### Post by mamamia88 on 2013-03-26
Cool worth a try using the no install reccomends option shaved a GB off the download

---

### Post by Cheesemill on 2013-03-26
> **mamamia88 said:**
> If Install the Ubuntu-Desktop package after installing a cli only install will it be the same result as downloading the entire cd and installing from that?
Yes, you'll end up with exactly the same system.

---

### Post by ibjsb4 on 2013-03-26
> **Cheesemill said:**
> Yes, you'll end up with exactly the same system.

Yep, tis the same as using the live CD.

If you want the desktop install without the recommends:

```
sudo apt-get install --no-install-recommends ubuntu-desktop
```

---

### Post by deadflowr on 2013-03-26
> **ibjsb4 said:**
> Yep, tis the same as using the live CD.

If you want the desktop install without the recommends:

```
sudo apt-get install --no-install-recommends ubuntu-desktop
```

I think that's the option the OP was looking at.

I believe the ubuntu-desktop package is one that needs a yes or no confirmation to install and will list the packages being installed, so if that's the case it'd be wise to review the packages getting installed to see if anything wanted is getting installed as well.

---

### Post by mamamia88 on 2013-03-26
Well I just got to say don't do that.  I tried it and not only did it take longer than a standard ubuntu install it didn't work properly ie the lens would't find any results.  Just gave up and installed arch.

---

### Post by Cheesemill on 2013-03-26
> **mamamia88 said:**
> ...not only did it take longer than a standard ubuntu install...
That's to be expected.

Even disregarding the time it will take to download all of the packages you still have to install over a thousand packages one at a time, whereas using the Live CD you are simply copying an already installed system onto your hard drive.

---

### Post by mamamia88 on 2013-03-26
True butnb why does it take so long even to get to the CLI install? I swear it took nearly as long to install a cli only system as a full desktop

---

