---
title: "Unity in 12.04 - Graphics Driver Issue"
date: 2012-07-24
forum: New to Ubuntu
---

### Post by AustenG on 2012-07-24
So I had my system working just fine, and I stupidly did something to mess up the current driver I was using. I think I must have accidentally saved something in system preferences.

Anyway, my screen resolution is all messed up and I am without gui access to my system preferences to change back the driver. Does anyone have any idea how to change the setting in system preferences? I'm using Ubuntu 12.04 with Unity. 

Please, any advice is welcomed!

Thank you.

---

### Post by cariboo on 2012-07-25
It would help if you told us what graphics adapter and driver you are using.

---

### Post by AustenG on 2012-07-25
I'm using an AMD Radeon 7970 HD video card, and I think the driver I had was one from their site. Would I just be able to open up firefox from the terminal, navigate to the website and reinstall the driver?

---

### Post by anewguy on 2012-07-25
> **AustenG said:**
> I'm using an AMD Radeon 7970 HD video card, and I think the driver I had was one from their site. Would I just be able to open up firefox from the browser, navigate to the website and reinstall the driver?

Huh?  Firefox IS the browser!

---

### Post by AustenG on 2012-07-25
Sorry, I meant terminal. 

I fixed it by opening ff, and reinstalling the latest ati driver.

Then, I just purged fglrx with:
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*

And followed the steps outlined here:
[http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers)

---

