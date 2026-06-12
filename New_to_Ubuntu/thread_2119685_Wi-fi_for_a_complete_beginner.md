---
title: "Wi-fi for a complete beginner"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by lrhee on 2013-02-24
Hi, I just installed ubuntu last night and I've been enjoying it so far; until I had to use wi-fi. My laptop does not have a hardware switch, it is activated by fn+f2 in windows but from what I gathered this won't work in ubuntu. 

I tried "rfkill list all" and "rfkill unblock all" in the terminal and wi-fi had neither hard block nor soft block. Is it a driver issue?

Thanks

---

### Post by westie457 on 2013-02-24
Welcome to the Forum.

The Fn+F2 key-combination should work in Linux/Ubuntu as well.

Hi, lets get this started.

Firstly go to here and follow the suggestion. [http://ubuntuforums.org/showpost.php?p=12520783&postcount=2](http://ubuntuforums.org/showpost.php?p=12520783&postcount=2)

Further help will come after the 'netinfo.txt' file has been looked at.

Thank you.

---

### Post by tartalo on 2013-02-24
In a terminal type
```
lshw -c network
```
That will tell you the model of your Wifi card, with that information it will be easier to find a solution.

---

### Post by lrhee on 2013-02-24
> **tartalo said:**
> In a terminal type
```
lshw -c network
```That will tell you the model of your Wifi card, with that information it will be easier to find a solution.

The model is: "netlink bcm57780 gigabit ethernet PCIe" by Broadcom coroporation.

Thanks for your replies

---

### Post by westie457 on 2013-02-24
Unfortunately the info you posted is for the ethernet port.

Could you try again please using the suggestion in my previous post. The link there has been fixed.

The netinfo.txt file will provide a lot more information for us to help you.

Thank you.

---

