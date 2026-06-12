---
title: "Epson multi-fuction CX5500 scanner in Ubuntu Hardy 64bit."
date: 2008-07-30
forum: New to Ubuntu
---

### Post by powerpleb on 2008-07-30
I have an Epson CX5500 printer/scanner multi-function thing which I am trying to get working on 64bit Hardy.

I got the printer working by installing the Stylus D68 drivers but I cannot get the scanner to work.
I've installed sane, libsane-extras and run ```
sane-find-scanner
```
and I get this```
found USB scanner (vendor=0x04b8 [Language Error], product=0x083f [Language Error]) at libusb:006:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

```
So I ran ```
scanimage -L
```
and I got this```
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```

So am I right in assuming that sane doesn't have the relevant drivers installed to run my scanner?

I've had a look around and apparently I need to install 'iscan' which isn't in the repos. So I tried to compile it and it failed to make.

Does anyone have any advice?

---

### Post by philinux on 2008-07-30
[http://ubuntufs.wordpress.com/2006/05/26/epson-perfection-2480-scanner/](http://ubuntufs.wordpress.com/2006/05/26/epson-perfection-2480-scanner/)

This is what i followed for my scanner.

All you need to substitute is the driver for your scanner.

---

### Post by powerpleb on 2008-07-31
> **philinux said:**
> 
All you need to substitute is the driver for your scanner.

I went looking on the driver CD and could only find 'ade001.bin'. I tried it, but I don't think it's what I'm looking for.

I've looked through the .cab files on the installation cd, and had a look at the Es7e.inf file which seems to be the windows driver and can't find an alternative.

---

### Post by rue1341 on 2008-07-31
Have you  installed "sane-utils" as well as "libsane-extras"? It worked for me straight away. (I removed i-sane just in case it interfered with xsane). 

The same problem I had was with an epson RX520 running 32 bit hardy

---

### Post by powerpleb on 2008-07-31
> **rue1341 said:**
> Have you  installed "sane-utils" as well as "libsane-extras"? It worked for me straight away. (I removed i-sane just in case it interfered with xsane). 


Yep, they're installed.

---

