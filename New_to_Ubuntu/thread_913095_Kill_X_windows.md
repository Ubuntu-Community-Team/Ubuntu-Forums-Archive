---
title: "Kill X windows"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by ranger5664 on 2008-09-07
I am working on killing the x windows and dont know how to do it in xubuntu.If any1 could tell me a way to kill it (not restart it) then i would be very appreciative.

---

### Post by jordanmthomas on 2008-09-07
```
sudo /etc/rc.d/gdm stop
```
Obviously, make sure you've saved your work, etc.

---

### Post by ranger5664 on 2008-09-07
What happens when i kill it? will i still be able to install stuff? thats the only reason i wanna kill it. Thanks

---

### Post by ranger5664 on 2008-09-07
That command didnt work!

---

### Post by overdrank on 2008-09-07
> **ranger5664 said:**
> That command didnt work!

Hi and using the ctrl, alt, F2 keys this will bring you to command prompt and login. Then you can try this command ```
sudo /etc/init.d/gdm stop
``` and to start it again then you can replace stop with start.
Edit did not see the OP was using xfce,.

---

### Post by Shazaam on 2008-09-07
Since he is using Xubuntu shouldn't it be this?
```
sudo /etc/init.d/xdm stop
```

---

### Post by OutOfReach on 2008-09-07
> **Shazaam said:**
> Since he is using Xubuntu shouldn't it be this?
```
sudo /etc/init.d/xdm stop
```

That's what I would think. :s

---

### Post by jordanmthomas on 2008-09-07
> **ranger5664 said:**
> That command didnt work!

My bad, I use arch and have gotten used to using rc.d.  
It should be init.d instead of rc.d

As far as I know, Xubuntu uses gdm just like Ubuntu does.

---

