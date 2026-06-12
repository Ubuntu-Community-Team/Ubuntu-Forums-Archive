---
title: "How to enter root password in Live CD install?"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by d.kusummmanth@gmail.com on 2008-05-25
i wanna know How to enter root password in Live CD install?

---

### Post by Joeb454 on 2008-05-25
Why?

You don't need to, just use sudo

---

### Post by sayakb on 2008-05-25
For liveCD, it won't ask you for root password :)

---

### Post by mbaker824 on 2008-05-25
> **d.kusummmanth@gmail.com said:**
> i wanna know How to enter root password in Live CD install?

If you really want a root password, you'll have to change it after installing using sudo.  I usually do that myself, just in case I inadvertently lock myself out of my main admin account (which I did just a couple of weeks ago :()

Other than that, it really isn't necessary.  You can get persistent root access using 'sudo -i'.

Mark

---

### Post by Joeb454 on 2008-05-25
> **mbaker824 said:**
> If you really want a root password, you'll have to change it after installing using sudo.  I usually do that myself, just in case I inadvertently lock myself out of my main admin account (which I did just a couple of weeks ago :()

Other than that, it really isn't necessary.  You can get persistent root access using 'sudo -i'.

Mark

I still don't change the root password, just boot into recovery mode :)

---

### Post by bodhi.zazen on 2008-05-25
First, Ubuntu uses sudo for root access :

                                       [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
   
  
Second, on the live CD, or HD install, to access a root shell :

```
sudo -i
```

Third, you may set a root password in either the live CD or HD install with :

```
sudo passwd
```

This is not supported on these forums, but there are RARE times when setting a root password is required. You should lock the root account again :

```
sudo passwd root -l
```

---

### Post by sayakb on 2008-05-25
Even if we add a password to the root. Shouldn't that password get reset after rebooting to the LiveCD again? So ofcourse, no point in setting up a password.

---

### Post by mbaker824 on 2008-05-25
> **LinuxIsInnovation said:**
> Even if we add a password to the root. Shouldn't that password get reset after rebooting to the LiveCD again? So ofcourse, no point in setting up a password.

You said 'Live CD install', which would imply you're installing to the hard drive and would not be booting from the Live CD again.  If you are just running the Live CD, then you are correct, there would be no reason to set up a root password.

Mark

---

### Post by sayakb on 2008-05-25
I see, LiveCD **install**.. how one word makes the difference :KS

---

### Post by niteshifter on 2008-05-25
Hi,

>  Even if we add a password to the root. Shouldn't that password get reset after rebooting to the LiveCD again? So ofcourse, no point in setting up a password.


If just running off of a Live CD, then correct - there is no point in setting a root password, except to save some typing during a session.

If running off a Live CD *with persistence* - that's a different story. For whatever reason, the user may need a passworded root account.

---

