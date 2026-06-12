---
title: "I can't burn a simple DVD on Lubuntu"
date: 2017-06-02
forum: New to Ubuntu
---

### Post by sed_faster on 2017-06-02
I relly angry with linux!

I have this setup:

1-https://www.asus.com/Motherboards/PRIME-B250-PRO/
2-I5 7500
3-8Gb Ram
4-SSD 120GB

and this SO
```

user@user:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty
user@user:~$ uname -a
Linux user 4.10.0-21-generic #23-Ubuntu SMP Fri Apr 28 16:14:22 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```

and I don't get burn a simple DVD with brasero! :/
After check integrate all data and path and when I click on the button "burn disk" the system lies down out DVD and informed "can't burn this disk".

How can I fix this problem? Maybe miss some driver to my drive DVD? Or miss some update to brasero?
This is the result of my update system:
```

user@user:~$ sudo apt-get update
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://archive.canonical.com zesty InRelease                             
Hit:3 http://security.ubuntu.com/ubuntu zesty-security InRelease               
Hit:4 http://ppa.launchpad.net/webupd8team/java/ubuntu zesty InRelease         
Hit:5 http://dl.google.com/linux/chrome/deb stable Release                     
Hit:6 http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu zesty InRelease
Hit:7 http://pt.archive.ubuntu.com/ubuntu zesty InRelease                
Hit:8 http://pt.archive.ubuntu.com/ubuntu zesty-updates InRelease
Hit:9 http://pt.archive.ubuntu.com/ubuntu zesty-backports InRelease
Reading package lists... Done                      


```

Thanks

---

### Post by poorguy on 2017-06-02
I would download and use Xfburn as it seems to work better than Brasero or has for me.

---

### Post by Rex Bouwense on 2017-06-02
Use xfburn.  It is far superior.

Ninja-ed again.

---

### Post by Bucky Ball on 2017-06-02
Erm, how about enquiring about some other more obvious possible causes prior to writing off Brasero. Will the DVD hold the amount of data you are trying to burn to it??? Check. There should be a bar or something down the bottom of Xfburn that tells you before you try burning. 

Is it a new disk, never used, clean, no fingerprints? There is no data already on the disk? Maybe obvious questions, but doesn't hurt to ask.

If you do try Brasero and it still doesn't work, I'd suggest you recheck the things I've pointed out again.

You don't need a driver for you DVD burner.

---

### Post by leunam12 on 2017-06-03
Try other burning applications such as xfburn or k3b, but it sounds like you have a bad disc(s). Also, is the DVD drive old? It could be a hardware issue.

---

### Post by RobGoss on 2017-06-03
If all else fail try using a **USB** drive they seem to  work the best these days. One thing that was pointed out to you is the size of the disk you're using make sure it can hold the ISO you're trying to burn and check for damages on that disk

---

### Post by leunam12 on 2017-06-03
I usually burn ISO files like this  ```
cdrecord -v -dao speed=4 dev=/dev/dvd /path/file.iso
```

---

