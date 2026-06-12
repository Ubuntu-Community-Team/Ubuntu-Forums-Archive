---
title: "Driver troubles?"
date: 2013-06-06
forum: New to Ubuntu
---

### Post by Sqverl on 2013-06-06
Hello, I'm a newbie with ubuntu(or any other linux based OS for that matter.). I bought a new Laptop with preinstalled ubuntu and decided to give it a go, like I've always wanted to. First thing first, I went to check system specs, just to be sure I had the right laptop and I was not sure if pre-installed OS version was 64x or 32x. But here comes trouble. I heard all drivers were preinstalled into the kernel, and since this particular laptop is considered "ubuntu ready", I assumed every driver possible were preinstalled as well. I assumed wrong. On first page of specs it said Graphics: Unknown. So I went and installed all the updates from updater and restarted PC as it promted to, just in case it was some outdated version of OS or something. Anyway, did not help. So I was wondering if there is something else I'm missing, that has to be done with fresh ubuntu. Help?

Short version for pros:
* Problem:   Probably missing graphics driver. At least according to system details.
* PC:           Dell Inspiron 15r 5521
* Certificate: Ubuntu certified - says so [HERE]("http://www.ubuntu.com/certification/hardware/201208-11540/")
* Graphics:   Presumably graphics card is Intel 4000
* OS version: 12.04 LTS. All updates from updater are installed.
* Might be related: sudo lshw command output to html generates a page which shows SMBus as red?

---

### Post by deadflowr on 2013-06-06
Install the mesa-utils package.
The intel drivers are open-source and included out of the box.

Open a terminal and run
```
sudo apt-get update
```
and then
```
sudo apt-get install mesa-utils
```

Note, you'll need to enter your password.
The password field will be blank, DON'T fret, the password will enter invisibly.
Type it as you remember it.

---

### Post by Sqverl on 2013-06-06
Oh, how nice, that was quick AND helpfull. Thanks, I think that solved it. At least system details are showing something other than unknown. Now I'll go read some manuals as to what that command actually does. ))) Thanks, again.

---

### Post by deadflowr on 2013-06-06
Which command would you like more help to understand?
Or are you meaning the mesa-utils package?

---

