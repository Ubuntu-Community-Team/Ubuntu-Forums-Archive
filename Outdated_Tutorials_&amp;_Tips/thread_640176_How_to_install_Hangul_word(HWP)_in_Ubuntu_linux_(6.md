---
title: "How to install Hangul word(HWP) in Ubuntu linux (60 day trial version)"
date: 2007-12-13
forum: Outdated Tutorials &amp; Tips
---

### Post by mikwig on 2007-12-13
Ever been emailed a .hpw file from someone and not been able
to use it? Wanting to try out a powerful fully featured word
alternative?  Try Hangul word. This is how to install the trial 
version. (NB. it is possible to get around the trial vesion, but if
you like purchasing is better)

Note, this has been tested on Fiesty and Gutsy, and works in the 386/686 versions, but not in the 64 bit versions.

**Step 1 - Get RPM**
```
 wget http://mikwig.webhop.org/files/haansoft-hwp-trial-6.4.0.1083-1hs.i386.rpm
```

**Step 2 - Convert it to a deb file and install**
```
sudo apt-get install alien
sudo alien -k --scripts haansoft-hwp-trial-6.4.0.1083-1hs.i386.rpm
sudo dpkg -i haansoft-hwp-trial_6.4.0.1083-1hs_i386.deb
```

**Step 3 - Link against libraries to confuse it into submission**
```
cd /usr/lib
sudo ln -sf libssl.so.0.9.8 libssl.so.5
sudo ln -sf libcrypto.so.0.9.8 libcrypto.so.5
```

**Step 4 - The other libraries...**
```
cd ~
wget http://mikwig.webhop.org/files/hwp2005.tar.gz
tar xfz hwp2005.tar.gz
cd hwp2005
sudo cp libXft.so.5 /usr/lib/hnc/lib
cd /usr/lib/hnc/lib
sudo ln -sf libXft.so.5 libXft.so
sudo ln -sf libXft.so.5 libXft.so.2
```
Don't forget to clean out the hwp stuff from your home directory. :)

*This tutorial was taken from the [linux in korea]("http://mikwig.webhop.org") website with permission*

---

### Post by mikwig on 2008-02-03
Note - Haven't figured it out yet, but HWP (hangul word) is seg faulting.

When I figure it out I shall update it on the wiki - 

[http://mikwig.webhop.org](http://mikwig.webhop.org)

as well as posting here.

---

### Post by pagadama on 2008-02-04
&#51060;&#44144; 7.10&#50640;&#49436; &#50504;&#46104;&#51648; &#50506;&#45208;&#50836;?
[&#50668;&#44592;]("http://skykebi.tistory.com/28")&#47484; &#52280;&#44256;&#54644; &#48372;&#49464;&#50836;

---

### Post by mikwig on 2008-04-29
> **pagadama said:**
> &#51060;&#44144; 7.10&#50640;&#49436; &#50504;&#46104;&#51648; &#50506;&#45208;&#50836;?
[&#50668;&#44592;]("http://skykebi.tistory.com/28")&#47484; &#52280;&#44256;&#54644; &#48372;&#49464;&#50836;

I got it working in 7.10 (gutsy) and 8.04 (hardy) using the above tutorial.

also note if you google search you can find a way around the trial period.
Though it is a good program and I do recommend paying for it.

---

### Post by cj1976 on 2008-04-30
I tried this method and it doesn't seem to have installed anything to the system. I can't find the program anywhere

---

