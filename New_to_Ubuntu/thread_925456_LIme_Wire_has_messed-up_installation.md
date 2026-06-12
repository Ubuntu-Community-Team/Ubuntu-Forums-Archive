---
title: "LIme Wire has messed-up installation"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by Big Chris on 2008-09-20
Can anyone help a still very new person to Linux?

I tried to install Lime wire and half way through the installation with GDebi package installer it froze - so I tried again and this message came-up: 'Only one software management tool is allowed to run at the same time close updates or Synaptic'. So I went to check Synaptic to see if that was running and the following message came-up. 'dpkg was interrupted you must manually run dpkg. E: dpkg-- configure-a'. E:-cash-70pen failed, please repeat.

Can anyone help?

---

### Post by howefield on 2008-09-20
Close synaptic or any package managers you have running and open a terminal and type

```
sudo dpkg. E: dpkg-- configure-a
```

It will ask for your password, type it in and press enter, hopefully it will correct the error.

---

### Post by mevets on 2008-09-20
did you try running 'dpkg-- configure-a'?

---

### Post by mc4100 on 2008-09-20
Easy to fix, just copy & paste into a terminal ( in Applications -> Accessories ):
```
sudo dpkg --configure -a
```

---

### Post by Big Chris on 2008-09-20
Hi, I put it in the above command. Then I went over to Synaptic, but when I went to close Synaptic this came up:
E: /var/cache/apt/archives/sun-java6-jre_6-06-0ubuntu1_all.deb: subprocess pre-installation script returned error exit status 1
E: /var/cache/apt/archives/sun-java6-bin_6-06-0ubuntu1_i386.deb: subprocess pre-installation script returned error exit status 1

Also a crash alert came-up saying: 'sorry, the package 'sun-java6-bin 6-06-Dobuntol' failed to install upgrade.

Can anyone say where I am going wrong?

---

