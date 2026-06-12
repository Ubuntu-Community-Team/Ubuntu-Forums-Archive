---
title: "Keyboard and touchpad not working"
date: 2019-05-10
forum: New to Ubuntu
---

### Post by totomyl on 2019-05-10
Hi I am using Ubuntu 16.04.6 LTS. I have booted up my laptop and the keyboard and touchpad are not working at all. No external keyboards work either. Upon booting into recovery mode, the keyboard is working. Reading through some threads and forums online, I have yet to find a fix to my problem. Many suggest typing sudo apt-get install xserver-xorg-input-all, but when i tried to put that after dropping into the root shell, I get 

"failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-input-all_7.7+13ubuntu3.1_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-input-all_7.7+13ubuntu3.1_amd64.deb) Temporary failure resolvin 'ca.archive.ubuntu.com' "  

I have also tried sudo apt-get update but i get a bunch of failures like the above. any hope to fix this? 

I apologize if I am not posting in the right forum or something like that, Thanks in advance.

---

### Post by xyloid2 on 2019-05-12
```
 failed to fetch ... Temporary failure resolving ... 
```

These type of error indicate either a DNS error or a package management issue during update, here's a link that solves those issues [https://askubuntu.com/questions/91543/apt-get-update-fails-to-fetch-files-temporary-failure-resolving-error](https://askubuntu.com/questions/91543/apt-get-update-fails-to-fetch-files-temporary-failure-resolving-error)

Reply back once that is resolved.

---

### Post by Autodave on 2019-05-12
...and when you reply to that, if you are still having problems, please give us some info about your system.

---

