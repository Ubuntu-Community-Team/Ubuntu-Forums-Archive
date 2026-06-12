---
title: "Problem - Software updates crashes"
date: 2013-10-23
forum: New to Ubuntu
---

### Post by jaffar-sb on 2013-10-23
I am unable to open the Ubuntu Software Centre, it crashes and disappear. 
And the error message is as follows:

**[An unresolvable problem occurred while initializing the package information.**
**Please report this bug against the 'update-manager' package and include the following error message:**
[B]'E:Encountered a section with no Package: header, E: problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.']

[/B]Please help me out.

[B]System Details:
Processor: [/B]Intel® Core™ i3-3210 CPU @ 3.20GHz × 4
**OS type:** 32 bit , **Ubuntu 12.04 LTS**

---

### Post by danielbauwens on 2013-10-23
Open up a Terminal and type "sudo apt-get install --reinstall software-center" (without quotation marks). Then try running it again.
[FONT=Ubuntu Mono]

[/FONT]

---

### Post by Bucky Ball on 2013-10-23
Welcome. You would have a better chance of getting help if you used a thread title that actually described your problem. This one says nothing. You can change it by editing your first post, 'Go Advanced' and edit the thread title.

Please use titles that actually describe the problem in future rather than generic titles like, 'Problem' or '12.04' or 'Issues with laptop'. You will greatly improve your chances of getting support.

Good luck. ;)

---

### Post by jaffar-sb on 2013-10-23
thanks a lot for guiding me.

@ daniel: i tried using the option which you provided, yet the error message appears as follows

**Reading package lists... Error!****E: Encountered a section with no Package: header**
**E: Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-i386_Packages**
**E: The package lists or status file could not be parsed or opened.**

Does the update manager update itself, or something needs to be done to correct it.?

thanks in advance.

---

### Post by fantab on 2013-10-23
Try this from terminal:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

If no errors are reported then run the update-manager again. If errors are reported then post them here.

---

### Post by danielbauwens on 2013-10-23
Alright. After looking around a bit, here are some other, possible solutions:
Try "sudo pip install --upgrade oauthlib" in the Terminal. If that doesn't work, try "sudo dpkg-reconfigure software center --force" (these are some solutions I found through other websites, so I'm not 100% sure it'll work, but it's worth a shot.

Daniel

---

### Post by jaffar-sb on 2013-10-23
thank you fantab. it worked. :)

---

