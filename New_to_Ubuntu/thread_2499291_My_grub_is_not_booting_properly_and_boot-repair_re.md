---
title: "My grub is not booting properly and boot-repair reccomendation not working"
date: 2024-07-22
forum: New to Ubuntu
---

### Post by kancharlameghana30 on 2024-07-22
Hello, 
So recently I installed my ubuntu 24.04 again after deleting the windows and ubuntu  I had in dual boot  . I had booting problems even before I removed winows but after that also my grub didn't load properly and I used reboot it 3,4 times to make it boot. I want repair the grub so I tried doing it myself following a blog in terminal but coudn't do it  . So I decide to install boot-repair in live usb and asked it to recommend . It gave me few commnands which are not working . I have a url with the info I got from boot-repair. The url is [https://paste.ubuntu.com/p/Xz9fdZHzjt/](https://paste.ubuntu.com/p/Xz9fdZHzjt/). So please help me if u understand the info in tne url.

---

### Post by tea for one on 2024-07-22
Disable secure boot (line 52)
Remove nvme0n1 disk KIOXIA 256GB
Ensure that dev/sda is priority boot disk in your PC boot menu.

Any improvement?

---

