---
title: "Error 404 when trying to instal video driver"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by xcvcx on 2008-08-03
I just reformmated to Linux and I'm trying to install my video driver except that I get this error



> W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-18.41_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-18.41_i386.deb)
  404 Not Found

The video card is a "GEFORCE' GO 7600" on a HP Pavilion dv8000

---

### Post by GreenN00b on 2008-08-03
Seems like the file you try to download is not on the server anymore.
Try and click the link and see for yourself ...

---

### Post by Elfy on 2008-08-03
Inded it's not - you can see the page here

[http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/)

and there is no 2.6.24.13-18 deb file there is a 13-19_i386.deb which might work ok for the card. You can click it on the page and it will download and be available on your desktop probably - dbl clk will start gdebi to install it.

Alternatively you could install envy and it should get the right driver for the card. Assuming that you run hardy, this command will install it for you

```
sudo apt-get install envyng-gtk
``` it will be in your System Tools menu

---

### Post by xcvcx on 2008-08-03
I'm not sure which one of those files I should be downloading.

---

### Post by Elfy on 2008-08-03
Neither am I tbh, I don't know the meaning of the 13-18 although it could be as simple as relating to the kernel version, in which case the 13-19 download would then match with the newly released kernel. 

Install envy as shown above - it will make the right choice for your card (usually)

---

### Post by xcvcx on 2008-08-03
When I put in the command I get tihs

E: Couldn't find package envyng-gtk

---

### Post by Elfy on 2008-08-03
Are you running hardy - if you are make sure you have sources set up right. Software sources in system - admin menu.

Enable main, universe, restricted and multiverse. 3rd party tab - enable partners.

If you don't have hardy - go to  alberto milone's site and get it there

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

you will need the legacy version and not envyng.

---

### Post by chunchengch on 2008-08-03
> **xcvcx said:**
> I just reformmated to Linux and I'm trying to install my video driver except that I get this error





The video card is a "GEFORCE' GO 7600" on a HP Pavilion dv8000


just run [COLOR="Red"]$ sudo apt-get update[/COLOR] to update the repository, then the download and installation will proceed.

---

