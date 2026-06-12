---
title: "Add &amp; Remove"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by Oliver.BS on 2008-12-01
I keep getting this error when I try to tick the box to add 

The list of applications is not available

Click on 'Reload' to load it. To reload the list you need a working Internet connection.

---

### Post by hyper_ch on 2008-12-01
so you do what it says?

---

### Post by Oliver.BS on 2008-12-01
> **hyper_ch said:**
> so you do what it says?

What does it mean by Reload though I exit and retry Add & Remove to the same problem I have even restarted.

---

### Post by SunnyRabbiera on 2008-12-01
Add/ Remove is a very limited package manager anyhow, go to system then to administration and then to synaptic package manager.
Synaptic is sort of like a more advanced version of add/remove, make sure to hit its refresh button to keep you library fresh.
you can also use it to add extra repositories too, go up to settings and then to repositories, then in there check off the boxes except the ones marked source code in the first and second tab.
again hit refresh and the repositories will be more open :D

---

### Post by hyper_ch on 2008-12-01
> Click on 'Reload' to load it. To reload the list you need a working Internet connection.
you do that?

---

### Post by Oliver.BS on 2008-12-01
> **hyper_ch said:**
> you do that?

I do have a working connection thats the thing.

---

### Post by SunnyRabbiera on 2008-12-01
> **Oliver.BS said:**
> I do have a working connection thats the thing.

just hop into synaptic, it might actually help with add/ remove not being able to see the packages.
Like i said synpatic is more advanced, but its also quite simple at the same time

---

### Post by Idefix82 on 2008-12-01
Can you open a terminal, type in
```
sudo apt-get update
```
and post the output here?

---

### Post by SunnyRabbiera on 2008-12-01
> **Idefix82 said:**
> Can you open a terminal, type in
```
sudo apt-get update
```
and post the output here?

that works too, though hitting refresh in synaptic is basically the same thing

---

### Post by Oliver.BS on 2008-12-01
> **SunnyRabbiera said:**
> that works too, though hitting refresh in synaptic is basically the same thing

```
Hit http://ftp.ntua.gr intrepid Release.gpg
Hit http://ftp.ntua.gr intrepid/main Translation-en_GB
Hit http://ftp.ntua.gr intrepid/universe Translation-en_GB
Hit http://ftp.ntua.gr intrepid/restricted Translation-en_GB
Hit http://security.ubuntu.com intrepid-security Release.gpg
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_GB
Hit http://ftp.ntua.gr intrepid/multiverse Translation-en_GB
Hit http://ftp.ntua.gr intrepid-updates Release.gpg
Ign http://ftp.ntua.gr intrepid-updates/universe Translation-en_GB
Ign http://ftp.ntua.gr intrepid-updates/main Translation-en_GB
Ign http://ftp.ntua.gr intrepid-updates/multiverse Translation-en_GB
Ign http://ftp.ntua.gr intrepid-updates/restricted Translation-en_GB
Hit http://ftp.ntua.gr intrepid-proposed Release.gpg
Hit http://ftp.ntua.gr intrepid-proposed/universe Translation-en_GB
Ign http://security.ubuntu.com intrepid-security/main Translation-en_GB
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_GB
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_GB
Hit http://security.ubuntu.com intrepid-security Release
Hit http://ftp.ntua.gr intrepid-proposed/main Translation-en_GB
Hit http://ftp.ntua.gr intrepid-proposed/multiverse Translation-en_GB
Hit http://ftp.ntua.gr intrepid-proposed/restricted Translation-en_GB
Hit http://ftp.ntua.gr intrepid Release        
Hit http://ftp.ntua.gr intrepid-updates Release
Hit http://ftp.ntua.gr intrepid-proposed Release                    
Hit http://security.ubuntu.com intrepid-security/universe Packages  
Hit http://ftp.ntua.gr intrepid/main Packages  
Hit http://ftp.ntua.gr intrepid/universe Packages
Hit http://ftp.ntua.gr intrepid/restricted Packages
Hit http://ftp.ntua.gr intrepid/multiverse Packages
Hit http://ftp.ntua.gr intrepid/main Sources
Hit http://ftp.ntua.gr intrepid/universe Sources
Hit http://ftp.ntua.gr intrepid/restricted Sources
Hit http://security.ubuntu.com intrepid-security/main Packages
Hit http://security.ubuntu.com intrepid-security/multiverse Packages
Hit http://security.ubuntu.com intrepid-security/restricted Packages
Hit http://ftp.ntua.gr intrepid/multiverse Sources
Hit http://ftp.ntua.gr intrepid-updates/universe Packages
Hit http://ftp.ntua.gr intrepid-updates/main Packages
Hit http://ftp.ntua.gr intrepid-updates/multiverse Packages
Hit http://ftp.ntua.gr intrepid-updates/restricted Packages
Hit http://ftp.ntua.gr intrepid-updates/universe Sources
Hit http://ftp.ntua.gr intrepid-updates/main Sources
Hit http://ftp.ntua.gr intrepid-updates/multiverse Sources
Hit http://ftp.ntua.gr intrepid-updates/restricted Sources
Hit http://ftp.ntua.gr intrepid-proposed/universe Packages
Hit http://security.ubuntu.com intrepid-security/universe Sources
Hit http://security.ubuntu.com intrepid-security/main Sources
Hit http://security.ubuntu.com intrepid-security/multiverse Sources
Hit http://security.ubuntu.com intrepid-security/restricted Sources
Hit http://ftp.ntua.gr intrepid-proposed/main Packages
Hit http://ftp.ntua.gr intrepid-proposed/multiverse Packages
Hit http://ftp.ntua.gr intrepid-proposed/restricted Packages
Hit http://ftp.ntua.gr intrepid-proposed/universe Sources
Hit http://ftp.ntua.gr intrepid-proposed/main Sources
Hit http://ftp.ntua.gr intrepid-proposed/multiverse Sources
Hit http://ftp.ntua.gr intrepid-proposed/restricted Sources
Reading package lists... Done
oli@Olis-laptop:~$ 

```

---

### Post by SunnyRabbiera on 2008-12-01
your repositories should be updated then, add remove should work fine again.
But please do eventually ween yourself from add/remove.
Granted its a great tool for beginners and can give you the basics, but synaptic and apt in command line mode are way more diverse.
eventually you may not even need synaptic, apt in its command line mode is very easy to use on its own.

---

### Post by Oliver.BS on 2008-12-01
> **SunnyRabbiera said:**
> your repositories should be updated then, add remove should work fine again.
But please do eventually ween yourself from add/remove.
Granted its a great tool for beginners and can give you the basics, but synaptic and apt in command line mode are way more diverse.
eventually you may not even need synaptic, apt in its command line mode is very easy to use on its own.

Thanks Dude.

---

### Post by SunnyRabbiera on 2008-12-01
> **Oliver.BS said:**
> Thanks Dude.

thats mam to you :D
My avvie is deceiving though

---

