---
title: "Unable to instal printer drivers via software center."
date: 2013-10-29
forum: New to Ubuntu
---

### Post by coffeepenguin on 2013-10-29
Hello,  I have a brother dcp-7040 and I went to brother's site to get the drivers because they were not included in the list of drivers in system settings. [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-7040](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-7040)  I found the appropriate driver, however when I try to install it using the software center I receive the message "This package is of bad quality." After pressing ignore and install I kept getting the error "unable to complete installation." After trying a few times I don't get that message anyomore, however, It still isn't installing. This is happening for both the lpr driver and the cupswrapper driver.           I am running Ububntu 13.10 amd64          Edit: also brother does not provide a ppd file for that specific printer.  Edit: here areLintian check results for /the details for the first error:   home/han_solo/Downloads/cupswrapperDCP7040-2.0.2-1.i386.deb: E: cupswrapperDCP7040: bad-package-name E: cupswrapperDCP7040: package-not-lowercase E: cupswrapperDCP7040: maintainer-address-missing Brother Industries,Ltd

---

### Post by cariboo on 2013-10-29
Did you try the install method on [this]("http://welcome.solutions.brother.com/bsc/public/us/ca/en/dlf/dlf/000000/006800/dlf006893.html?reg=us&c=ca&lang=en&prod=dcp7040_us_as&type2=91&os=128&flang=4&dlid=dlf006893") page?

The only thing is that su doesn't work as expected any more, so instead of using:

```
sudo su
```

just use:

```
sudo
```

---

### Post by coffeepenguin on 2013-10-30
I can't believe I made such a silly mistake, thank you so very much for helping me. After 4 days I can finally print things :D

---

