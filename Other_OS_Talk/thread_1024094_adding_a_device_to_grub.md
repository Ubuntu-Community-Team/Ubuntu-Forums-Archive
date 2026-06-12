---
title: "adding a device to grub"
date: 2008-12-28
forum: Other OS Talk
---

### Post by ajkiwi88 on 2008-12-28
ok so i have installed windows xp on an external usb hard drive and got it booting i now want to add this to grub so when its plugged in it can be selected how will i go about this?

---

### Post by caljohnsmith on 2008-12-28
In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and what it might take to boot Windows from Grub.

---

