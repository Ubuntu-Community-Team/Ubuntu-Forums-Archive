---
title: "[SOLVED] connect two laptops across lan"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Bill magee on 2008-05-27
I have two offices at work with a laptop in each. One is running Hardy and the other is running Gutsy. Sometimes I want to grab a file from Hardy when I am am working on Gutsy and vice-versa. 

Can someone point me in the right direction please?

Cheers,
Bill

---

### Post by sayakb on 2008-05-27
Connect the two laptops and wait until the nm-applet shows "connected". You would be assigned with a temporary IP address. Check you IP using:
```
ifconfig
```Now install ssh on both laptops:
```
sudo apt-get install ssh
```After installing ssh, you can access the other laptop by typing the following at nautilus:
```
sftp://ip.add.re.ss/
```
Followed by providing Username and Password of the other laptop.

---

### Post by Monicker on 2008-05-27
One option is to install the openssh-server package on each, and use scp to copy files.

---

### Post by Bill magee on 2008-05-27
Thanks to you both. I am installing ssh and openssh-server now.

---

### Post by sayakb on 2008-05-27
> **Bill magee said:**
> Thanks to you both. I am installing ssh and openssh-server now.

Both are dependent. Installing ssh would automatically install openssh-server package.

---

### Post by Bill magee on 2008-05-27
I see that now LinuxIsInnovation. The connection is working perfectly now.

Ubuntu is the greatest! My colleagues are astonished at what I can do with it (and me a newbie since Dec 07). Maybe they will see the light one day.

Cheers,
Bill

---

