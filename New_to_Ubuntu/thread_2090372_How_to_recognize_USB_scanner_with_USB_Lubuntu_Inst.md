---
title: "How to recognize USB scanner with USB Lubuntu Install"
date: 2012-12-02
forum: New to Ubuntu
---

### Post by philpense on 2012-12-02
Running Lubuntu on a windows notebook through a USB drive.  Just connected a document scanner through a USB connection.  How do I get Lubuntu to recognize the scanner just connected.  How can the driver driver be seen by Lubuntu?  Guidance sought

---

### Post by Cheesemill on 2012-12-02
If the scanner is supported properly it should just work.

What is the make and model of the scanner?

---

### Post by philpense on 2012-12-02
> **Cheesemill said:**
> If the scanner is supported properly it should just work.

What is the make and model of the scanner?
This is the Canon CanoScan 3000ex and requires a downloaded driver even when connected to a windows computer.  This driver is downloaded and installed to my other windows computers.

---

### Post by Cheesemill on 2012-12-02
I'm afraid you're out of luck. This scanner is unsupported on Linux as Canon don't provide drivers for it:

[http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON)

---

### Post by 3rdalbum on 2012-12-02
> **philpense said:**
> This is the Canon CanoScan 3000ex and requires a downloaded driver even when connected to a windows computer.  This driver is downloaded and installed to my other windows computers.

Yes, Windows always requires additional drivers to use devices.

But this isn't Windows.

Try plugging the scanner in and then opening Easyscan or whatever scanning software you want to use. If it's detected, then you have the driver.

I know the SANE website says that scanner is not supported, but it looks like it was last updated in 2010 - things may have changed.

---

