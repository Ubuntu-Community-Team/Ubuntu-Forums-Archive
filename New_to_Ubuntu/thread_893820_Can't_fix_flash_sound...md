---
title: "Can't fix flash sound.."
date: 2008-08-18
forum: New to Ubuntu
---

### Post by kramer65 on 2008-08-18
Hello,

The sound on youtube video's is not working anymore for a while now. I tried to fix it using tips in [this tread]("http://ubuntuforums.org/showthread.php?t=505632");
```
sudo apt-get install alsa-oss
gksudo gedit /etc/firefox/firefoxrc
```
Change:
FIREFOX_DSP=""
To:
FIREFOX_DSP="aoss"

Restart Mozilla Firefox. Now sound should work in Flash Player.


The file that opens however, is completely empty. And when I just insert the text ("FIREFOX_DSP="aoss") and hit save, it says something like "can't save file, file not found" (translated from Dutch).

Can anybody help with this?


ps. Opening several youtube tabs in firefox makes firefox very slow which didn't happen before. I just got a new pc (quadcore @2.66GH with 4GB memory), which should be able to run that easily I thought. It worked fine on my last computer as well which was a lot slower..

---

### Post by kostkon on 2008-08-19
> **kramer65 said:**
> Hello,

The sound on youtube video's is not working anymore for a while now. I tried to fix it using tips in [this tread]("http://ubuntuforums.org/showthread.php?t=505632");
```
sudo apt-get install alsa-oss
gksudo gedit /etc/firefox/firefoxrc
```
Change:
FIREFOX_DSP=""
To:
FIREFOX_DSP="aoss"

Restart Mozilla Firefox. Now sound should work in Flash Player.


The file that opens however, is completely empty. And when I just insert the text ("FIREFOX_DSP="aoss") and hit save, it says something like "can't save file, file not found" (translated from Dutch).

Can anybody help with this?


ps. Opening several youtube tabs in firefox makes firefox very slow which didn't happen before. I just got a new pc (quadcore @2.66GH with 4GB memory), which should be able to run that easily I thought. It worked fine on my last computer as well which was a lot slower..
If you are using 8.04, do you have the *libflashsupport* package installed?

---

### Post by kramer65 on 2008-08-20
I don't know. How can I check that?

---

### Post by t0p on 2008-08-20
You can find out if you have libflashsupport by opening Synaptic (**System > Administration > Synaptic Package Manager**) and doing a search for libflashsupport.

Are you running Flash 9 or 10?  If you don't know, it's probably 9.  [This fix]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472") may fix your problem.  It did for me.

---

### Post by kramer65 on 2008-08-20
Great! I installed libflash support through synaptic and it works now. It did work before though so I hope it will continue to work. I will post later in this form when it has worked for a while.. :-)

---

### Post by t0p on 2008-08-20
> **kramer65 said:**
> Great! I installed libflash support through synaptic and it works now. It did work before though so I hope it will continue to work. I will post later in this form when it has worked for a while.. :-)

*Hmmm*... I don't know if that's what Koston meant, but I certainly wasn't advising you to install libflashsupport.  There are many instability issues with Flash 9 and libflashsupport.  I pointed you toward the fix at [this link]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472") because it enables you to use Flash 10, which is far more stable and doesn't rely on libflashsupport.

If your vid playing continues fine, then that's great!  If it does become unstable, check out the link above.

---

