---
title: "System crashes"
date: 2023-08-14
forum: New to Ubuntu
---

### Post by yuridze on 2023-08-14
"Hi! I have 2 issues with SSD:
Sometimes OS crashes after that I have to restart computer. SSD is fine (SMART in windows disk utilite say that), but I can't see SMART information it in Ubuntu and that's the second issue. How can I fix it?
I have dual-boot with windows, pop os and ubuntu. In pop os issues are the same.
I did fsck at pop, ubuntu and usb flash dirve (zorin), because I can't unmounte /home.
then I did dmesg at zorin and ubuntu. here is the result: [https://paste.ubuntu.com/p/hq3zNJf6CP/](https://paste.ubuntu.com/p/hq3zNJf6CP/)
Do I have a corrupt filesystem or drive? What should I do next?

why can't I see SMART parameters for my SSD? [https://telegra.ph/file/3f462c7ff1478ba80eb3c.png](https://telegra.ph/file/3f462c7ff1478ba80eb3c.png)
Previously I could see it and I could do it on windows [https://paste.ubuntu.com/p/dQp57xM5SK/](https://paste.ubuntu.com/p/dQp57xM5SK/)

---

### Post by Holger_Gehrke on 2023-08-14
gnome-disks has a SMART-viewer built-in. It can be reached from the button with three dots in the title bar, just to the left of the minimize/maximize/close buttons; only appears after a drive is selected.

Holger

---

### Post by yuridze on 2023-08-17
It isn't working because SMART button is grey and unclickable

And I can't send message with image of it here I don't know why. In pop os it looks like this [https://telegra.ph/file/3f462c7ff1478ba80eb3c.png](https://telegra.ph/file/3f462c7ff1478ba80eb3c.png), in ubuntu situation absolutely the same!

---

### Post by Rubi1200 on 2023-08-17
Do you have good backups of ALL your important data?

---

### Post by deadflowr on 2023-08-17
It's an nvme drive.
So you probably need the nvme-cli package installed,
and then you can run the nvme smart-log command.
```
sudo nvme smart-log /dev/nvme0n1
```

---

