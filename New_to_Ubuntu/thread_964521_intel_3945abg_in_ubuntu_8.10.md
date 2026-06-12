---
title: "intel 3945abg in ubuntu 8.10"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by jrecortel on 2008-10-31
hello.seems like many have already upgrade to ubuntu 8.10.i would like to ask if intel 3945abg works OOTB in ibex.thanks.

---

### Post by trekrem on 2008-10-31
I can confirm it is working for me in 8.10 (using a non-proprietary driver).

---

### Post by akuhon on 2008-10-31
> **jrecortel said:**
> hello.seems like many have already upgrade to ubuntu 8.10.i would like to ask if intel 3945abg works OOTB in ibex.thanks.

I don't think it's distro specific, but rather it's kernel specific.
Have a look at this :

[http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/)

Hope it helps ..

Rgds,

---

### Post by Muflon on 2008-10-31
Yes the Intel Pro Wireless 3945 802.11a/b/g works out of the box in Hardy and Intrepid.  It is the one that I use and I have never had any issues with it in Ubuntu.

Muflon

---

### Post by rocketsbay on 2008-10-31
Not working for me. Was working with ndiswrapper under 8.04. Now I can't even turn the radio ON. I tried the hardware switch as stated in the release notes and fn+f2 but nothing seems to turn on the radio.

The LED for the wireless is on up until the login screen then mysteriously turns itself off.

Any help is appreciated.

---

### Post by davethebald on 2008-11-01
Not working for me either on a Dell XPS M1330, never has.  I got this computer in May with the 7.10 preloaded.  Never got the wireless to work.  I did see the comment in the notes about the killswitch, did it but still not working.

If I had any, I'd be pulling my hair out.

---

### Post by austin512 on 2008-11-01
My 3945abg worked fine out of the box in 8.04, but when I upgraded to 8.10, it started causing kernel panics. The [release notes]("http://www.ubuntu.com/getubuntu/releasenotes/810#System%20lock-ups%20with%20Intel%204965%20wireless") for 8.10 say this is only supposed to happen with the 4965abgn. I did the fix of installing the linux-backports-modules-intrepid package and now it appears to work fine.

---

### Post by davethebald on 2008-11-01
Austin512 - thanks for the info.  I installed that package.  Not working yet, so I am still working on it.

Now the bad news.  I am one of those dreaded newbies who doesn't really know what he is doing.  I assume that installing this package will not hurt anything if it does not help.

At least I am having fun.  Sort of.

---

### Post by flyboy917 on 2008-11-02
> **austin512 said:**
> My 3945abg worked fine out of the box in 8.04, but when I upgraded to 8.10, it started causing kernel panics. The [release notes]("http://www.ubuntu.com/getubuntu/releasenotes/810#System%20lock-ups%20with%20Intel%204965%20wireless") for 8.10 say this is only supposed to happen with the 4965abgn. I did the fix of installing the linux-backports-modules-intrepid package and now it appears to work fine.

Ditto here. I don't know if it's causing kernel panics, it just quits working intermittently. I can disconnect from my WPA network and reconnect and it will work for a little bit...only to have to do it again...and again. Will try the backport fix.

---

