---
title: "Updating system using sudo apt-get"
date: 2012-04-21
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2012-04-21
Hi everyone

sorry for a dumb question, but how do I update the system using apt-get.
I know that if I type sudo apt-get update, it updates the list of packages available, but how do I then use that updated list to upgrade any packages that are out of date?

I know I could go to update manager and let that do the updating, but where is the fun in that?

Oops, almost forgot. I'm running Ubuntu 11.10 i386.
Glenn.

---

### Post by iponeverything on 2012-04-21
```
sudo apt-get upgrade
```

will then upgrade the packages.

---

### Post by Senior_Buckethead on 2012-04-21
That did it, thanks.

---

### Post by JKSully on 2012-04-22
i didnt think that this would be a normal post seeing as Linux users are used to binary code. :p Saying thanks for the others though.

---

### Post by Bucky Ball on 2012-04-22
```
sudo apt-get upgrade
```Before running this you should always:

```
sudo apt-get update
```

... first. ;)

---

### Post by jerrrys on 2012-04-22
+1 Bucky Ball

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

---

### Post by Baldrick_NZ on 2012-04-22
> **jerrrys said:**
> +1 Bucky Ball

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

Or to make it easier with one command:```
sudo apt-get update; sudo apt-get upgrade
```or```
sudo apt-get update && sudo apt-get upgrade
```
Either will work fine. ;-)

---

