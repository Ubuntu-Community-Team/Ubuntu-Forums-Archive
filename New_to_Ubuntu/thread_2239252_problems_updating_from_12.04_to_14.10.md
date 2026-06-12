---
title: "problems updating from 12.04 to 14.10"
date: 2014-08-12
forum: New to Ubuntu
---

### Post by kaare-l on 2014-08-12
Errormessage:
error under update control your net connection (it works perfectly!)

W:not able to get  [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources)  404  Not Found [IP: 91.189.91.14 80]
, W:not able to get  [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

? I'm concerned that I might have a bug that blocks this "security" update. Anybody got some idea what is wrong?

---

### Post by whitesmith on 2014-08-12
To help you we need data, data, data. What is your hardware? A laptop? A tower? Who made it? What's inside? 32 or 64-bit? Pure Ubuntu or dual boot? We can't help unless we know these things. The more specific you are the more help we can offer, and sooner. Regards.

---

### Post by QIII on 2014-08-12
A more important question might be why you are upgrading from an LTS to a development version that has not been released.

Those 404s are coming from urls for Hardy Heron.  You need to remove all Hardy repos from your sources.

---

### Post by Jonathan Precise on 2014-08-12
```
gksu gedit /etc/apt/sources.list
```

Find [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources) and [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources) . Remove those lines from the file. Save.

I'm assuming you meant 14.04 LTS. Make sure that the upgrade is set to "Another LTS version" After the edits have been done, run the following:

```
sudo -i apt-get update
sudo -i apt-get upgrade
sudo -i do-release-upgrade
```

---

### Post by whitesmith on 2014-08-12
I also took for granted that 14.10 was a typo.

@Jonathan Precise: A single sudo -i creates a nonterminating # session until the emulated terminal is closed by the user, unless I'm mistaken.

---

### Post by Jonathan Precise on 2014-08-12
@whitesmith: only if run alone:

```
owner@ubuntu-hp-2000-notebook:~$ sudo -i hello
[sudo] password for owner: 
Hello, world!
owner@ubuntu-hp-2000-notebook:~$ 
```

---

### Post by whitesmith on 2014-08-12
@Jonathan Precise: Curious. Mine stays open indefinitely. Probably our .profile or .login files are different.```
david@London:~$ sudo -i
[sudo] password for david: 
root@London:~# man sudo
root@London:~# 

```Linux is the mother of mysteries -- always fun to solve unless deadlines loom. Cheers!

---

### Post by Jonathan Precise on 2014-08-13
@whitesmith: exactly. You just ran sudo -i, and then run a command under the existing simulated root login shell. If you run sudo -i **XYZ**, it shouldn't stick around, though.

---

### Post by whitesmith on 2014-08-13
Now we're on the same frequency. I kept my simulated shell open for about 8 hours, so I'm reasonably sure it never closes, but persistence with a command is unrealized, as you pointed out. Regards.

---

### Post by JosephBeck on 2014-08-13
I also often see people who try to jump that many releases have problems. If there are still issues after the upgrade methods suggested above, probably be less of a headache to just install 14.04.1 fresh if you have /home on its own partition.

---

### Post by deadflowr on 2014-08-14
Beyond sudo -i and what not I would like to see the full output of 
```
cat /etc/apt/sources.list
```

But an upgrade from 12.04 **WILL** need to go to 14.04 first, before upgrading to the development release 14.10.
There is no channel open for precise to go to anything but trusty.

And double hops are fraught with potential problems, typically more so than a normal jump from only one release to another.

If the intent, though, is to run 14.10, and not simply upgrade to 14.04, which I would like to assume is what is the real intention (assumptions can quite often be very wrong, so I'll also say I hope...) then perhaps get the [daily-build iso]("http://cdimage.ubuntu.com/daily-live/current/") and install it.

My two cents anyway...

---

