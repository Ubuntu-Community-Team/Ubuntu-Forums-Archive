---
title: "Update drivers"
date: 2014-03-05
forum: New to Ubuntu
---

### Post by sdvf on 2014-03-05
Hi guys. I've install Lubuntu recently and i think some drivers may not been installed/update. I think youtube sound is delayed. And the sound it's much lower then in windows. I must up close to max to listen music like i want to ear it.

Is there any program or something to see if all my components are working good?

Tks

---

### Post by mörgæs on 2014-03-06
```
sudo apt-get update
sudo apt-get dist-upgrade
```

will update if needed.

---

### Post by nunecas123 on 2014-03-06
Check this ppa out:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

It should have all of the updates you have. This is official.

If you need any help "installing" a PPA on your system, be sure to say it.

---

### Post by 3rdalbum on 2014-03-06
On Linux we don't really "update drivers", at least not on their own.

Not sure about the video/audio sync issue, I haven't heard of that happening for years. I take it this doesn't happen on anything but Flash videos?

The volume may be able to be turned up more. Go to a terminal and type "alsamixer" and press Enter. Go to the right until you reach the PCM channel and make sure that's around 90%, but not higher.

Ultimately, the maximum volume of an audio device is governed by its driver, not by the hardware itself. Linux drivers are usually written by people who have not seen the source code for the Windows driver, so things may be a bit different. Sometimes Linux sounds louder or clearer, sometimes Windows does. It all depends on the driver for your particular audio device.

---

