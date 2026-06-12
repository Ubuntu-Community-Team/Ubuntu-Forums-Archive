---
title: "ubuntu program setup"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by hyperhopper on 2008-09-18
how can i get compixconfig setting manager from one comp with internet that is running windows to one that is not on internet but running ubuntu?

---

### Post by hyperhopper on 2008-09-18
also , i have a ubuntu boot disc to livecd on the windows comp...

---

### Post by howefield on 2008-09-18
> **hyperhopper said:**
> how can i get compixconfig setting manager from one comp with internet that is running windows to one that is not on internet but running ubuntu?

Boot from the live cd on the computer that has internet.

Use synaptic package manager, and search for compizconfig-settings-manager then click mark for installation, apply, and check the box that says download packages only.

You can then transfer the package to the other computer via usb stick or whatever.

Think this will work.

---

### Post by jemate18 on 2008-09-18
> **hyperhopper said:**
> how can i get compixconfig setting manager from one comp with internet that is running windows to one that is not on internet but running ubuntu?

Use the LiveCD...

---

### Post by mc4100 on 2008-09-18
If you don't have a live CD, there is another way, but you need to make sure you already have the correct dependencies installed, or that you get download them as well:
Grab the files manually from [here]("http://packages.ubuntu.com/hardy/compizconfig-settings-manager") using Firefox on Windows (or Internet Explorer) and save them to USB drive.
Then on Ubuntu, press Alt+F2 and type:
```
gksudo nautilus /var/cache/apt/archives
```
then drag the files from the USB drive into the nautilus window.
And then, in a terminal, type:
```
sudo apt-get install compizconfig-settings-manager
```

Edit: Of course, upon re-reading, I see that you do, in fact, have a LiveCD ...

---

### Post by hyperhopper on 2008-09-18
where are the files downloaded to

---

### Post by mc4100 on 2008-09-18
> **hyperhopper said:**
> where are the files downloaded to

```
/var/cache/apt/archives
```

---

### Post by Tutigan on 2008-09-18
Or download the .deb files from [http://ftp.iinet.net.au/linux/ubuntu/pool/main/c/compiz/](http://ftp.iinet.net.au/linux/ubuntu/pool/main/c/compiz/)
and install using the package manager...

---

