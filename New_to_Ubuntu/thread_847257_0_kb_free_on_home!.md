---
title: "0 kb free on home??!"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by strongboww on 2008-07-02
hey guys,
my home says that there are 0kb free actually there should be around 2GB

in order to that, i cant run mail service or any other programs because they all fail and tell me that "no space is free"

could this have something to do with my try to compile pidgin today? or todays repo updates?

tia
b.

---

### Post by hyper_ch on 2008-07-02
output

```

df -l

```

---

### Post by strongboww on 2008-07-02
```

/dev/sda1             73939452  70243264         0 100% /
varrun                  517684       236    517448   1% /var/run
varlock                 517684         0    517684   0% /var/lock
udev                    517684        52    517632   1% /dev
devshm                  517684        12    517672   1% /dev/shm
lrm                     517684     38176    479508   8% /lib/modules/2.6.24-18-generic/volatile
overflow                  1024        52       972   6% /tmp
gvfs-fuse-daemon      73939452  70243264         0 100% /home/longbow/.gvfs

```

---

### Post by milosz.galazka on 2008-07-02
Also some space is reserved (depending on chosen filesystem)...

---

### Post by benfindlay on 2008-07-02
Type ```
df -h
``` and then try an ```
sudo apt-get clean
``` and see whether you're any better off!

Hope this helps!

---

### Post by strongboww on 2008-07-02
nice, clean worked

at least i have 600mb left which is far more less than actually should be,

---

### Post by benfindlay on 2008-07-02
You want to keep doing that every now and again then. When ubuntu downloads updates, it doesn't delete the temp install files once the updates are applied. The clean command purges them for you!

---

### Post by strongboww on 2008-07-02
> **benfindlay said:**
> You want to keep doing that every now and again then. When ubuntu downloads updates, it doesn't delete the temp install files once the updates are applied. The clean command purges them for you!
purge the unclean! :D

---

### Post by Elfy on 2008-07-02
and ring a bell

You might also want to check if you have anything else that is taking up space - it isn't actually your /home which is full it's your /

The file in /home (gvfs) is not actually taking up the room it says it is.

---

### Post by tipiglen on 2008-07-02
Thanks for that.  It got me some space back.  

I got here trying to find out why my home directory has a directory called .gvfs which shows unusual attributes - ? ?????. It cannot be entered or deleted, and apparently is for the gvfs-fuse-daemon which appears on your df listings, but not on mine.

Any ideas?

The other problem I'm chasing is that on a rather old and slow computer I keep getting freezes with larger file transfers, and I'm trying to get at the usb speed control to see if limiting the speed might solve the problem.  At present |I can't back up to an external HDD which works quite well with a newer faster computer.  Both running Hardy.

If I can back up the data, I'll try a new, clean re-install.

Thanks again for the extra bit of room.

Salaam/Shalom/Shanthi/Dorood/Peace
   Namaste  -ed

---

### Post by bhadotia on 2008-07-02
> [COLOR=Blue]You installed everything that was in synaptic:shock:[/COLOR]
yes.. lol ... i didn't know what i was doing
[COLOR=#0000ff]just out of interest how long did it take ?[/COLOR]
Euh about 10 hours 			 		 		  		  		 		 			 				


HaHA HA HA Ahhh   Hooo HEEEE HHHHAAAA AAAHHH HEEEE HOOO.
What a signature!

---

### Post by Elfy on 2008-07-02
I thought it amusing as well, I was a bit lost for words at the time :)

---

