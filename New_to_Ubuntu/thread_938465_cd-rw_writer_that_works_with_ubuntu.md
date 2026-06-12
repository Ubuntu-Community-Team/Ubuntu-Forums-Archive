---
title: "cd-rw writer that works with ubuntu"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by orwellus on 2008-10-04
Just wondering what what is a good cd-rw writer that works with Ubuntu. I don't need something too elaborate, just a simple external cd writer. I was looking at maybe something from Sony or Dell. I have Ubuntu 7.10 installed on my computer, which is about 3 years old and has 700mhz, 17GB harddrive, and 256 RAM. 

Thanks.

---

### Post by expatCM on 2008-10-04
They should all work.  Have you experienced any problems?

---

### Post by halitech on 2008-10-04
any external should work, just make sure that if you go with a usb version that you have at least 1 usb port (if its only 3 years old it should have at least 2) and if you don't have any usb ports (highly unlikely) pick up an add on pci usb card as well

---

### Post by handydan918 on 2008-10-04
> **orwellus said:**
> Just wondering what what is a good cd-rw writer that works with Ubuntu. I don't need something too elaborate, just a simple external cd writer. I was looking at maybe something from Sony or Dell. I have Ubuntu 7.10 installed on my computer, which is about 3 years old and has 700mhz, 17GB harddrive, and 256 RAM. 

Thanks.

I regret to inform you that your message has been caught in an eddy in the space-time continuum. The chances of you having a 3 year old anythiong with a 700 mhz cpu are approximately..................







0/100

---

### Post by Pro-reason on 2008-10-04
Most drives will just work out-of-the-box, especially if you upgrade to a recent kernel.  (It may or may not be necessary to upgrade to a more recent version of Ubuntu for that.)

With a bit of Googling, I'm sure you could find out whether there are any manufacturers making drives that require weird drivers.  You can then avoid those ones.

If you avoid external drives (connected via USB), and instead use an internal drive, you will definitely have no trouble.  Presumably you have some reason for wanting an external one, though.  If you do go for an internal one, check your motherboard to see whether you have enough free ports.  The very wide ports are IDE, and the smaller ones are SATA.  My fiancée's computer has two IDE ports and two SATA ports, whereas mine has one IDE port and four SATA ports.  You can get CD/DVD drives that use either IDE or SATA.  Make sure you get the right type.

---

### Post by Pro-reason on 2008-10-04
> **orwellus said:**
> which is about 3 years old and has 700mhz

What is it that's 700mHz exactly?  Perhaps you could do this on the command line:

```

sudo lshw > lshw.txt
gedit lshw.txt

```

Copy the paste the output here.  Make sure you use the **#** button to put [noparse]```
...
```[/noparse] tags around it, otherwise it will be illegible and fill the page.

That's just if you want to show us the full info for your system.

---

### Post by orwellus on 2008-10-05
Thanks for the replies. I guess I just I wanted some reassurance before I bought anything.

---

