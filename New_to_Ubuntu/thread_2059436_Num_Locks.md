---
title: "Num Locks"
date: 2012-09-18
forum: New to Ubuntu
---

### Post by khangtruong on 2012-09-18
This is rather low priority, but I have a numeric password on my computer, and was wondering if there was a way to make it so that I don't have to remember to press Num Locks *every single time*? I just installed Ubuntu less than four days ago, so please don't tell me to open up any command line or edit any system files or whatnot please, because that confuses me :confused: .

---

### Post by androssofer on 2012-09-18
> **khangtruong said:**
> This is rather low priority, but I have a numeric password on my computer, and was wondering if there was a way to make it so that I don't have to remember to press Num Locks *every single time*? I just installed Ubuntu less than four days ago, so please don't tell me to open up any command line or edit any system files or whatnot please, because that confuses me :confused: .

it can be done.. however it requires the command line and conf files... 

its only confusing until you get comfortable doing it.. I felt the same at the start.. 

so i'll tell you anyway! :-)

first open a terminal window, either by clicking the ubuntu logo top left and searching for terminal. or pressing:

ctrl + alt + T

once you have it open type:

```
sudo apt-get install numlockx
```

this will install numlockx, a small program that allows control of num lock. it will ask you for your password, enter the password you use to log in. **note:** it wont show any characters as you type the password. this is normal.

once that has finished type:

```
sudo gedit /etc/rc.local
```

this will open a text editor. scroll to the bottom and just before the line that says exit 0, add:

```
numlockx on
```

once you've done that the bottom of the file should look like:

```


numlockx on
exit 0

```

then save and close the text editor. then type:

```
sudo chmod +x /etc/rc.local
```

then restart. This will turn numlock on at boot for you. 

wasn't so bad was it? :-)

---

### Post by mips on 2012-09-18
Check you BIOS, some systems allow you to turn it on in the BIOS at startup.

---

