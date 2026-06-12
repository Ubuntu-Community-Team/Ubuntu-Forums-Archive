---
title: "ubuntu 12.04 resolution stuck"
date: 2012-08-13
forum: New to Ubuntu
---

### Post by hnf a on 2012-08-13
hi all i'm new on ubuntu and i want to ask why my screen resolution stuck at 1024x768 but in windows i can apply 1366x768 resolution how to do that on ubuntu i have use x server to change resolution to 1366x768 but on the screen it's just show 1280x768 and i use "xrandr --output default --mode 1366x768" but the result is cannot find mode 1366x768.

and i have another problem why my splash screen looks like barcode like this: [http://img35.imageshack.us/img35/898/hsa0251.jpg](http://img35.imageshack.us/img35/898/hsa0251.jpg)

---

### Post by cortman on 2012-08-13
I've not yet done it myself (no need to) but there are instructions on adding a mode to xrandr [here]("http://ubuntuforums.org/showthread.php?t=1112186"). Resolution doc page [here]("https://wiki.ubuntu.com/X/Config/Resolution").

---

### Post by hnf a on 2012-08-13
i'm very appreciate your reply. yes there are more option in x server but it's still show 1280x768px when i choose 1366x768,can it caused by nvidia driver?

---

### Post by cortman on 2012-08-13
It could be the driver, I suppose, but have you tried setting it with the Displays settings in System Settings? Does it give an option for 1366x768 there?

---

### Post by hnf a on 2012-08-13
yes there an option to choose 1366x768 res but still didn't match the resolution in the screen.it's just show 1280x768 rather than 1366x768 and now i boot into virtual terminal and i can't read anything just like tihs
 [http://img35.imageshack.us/img35/898/hsa0251.jpg](http://img35.imageshack.us/img35/898/hsa0251.jpg)

---

### Post by hnf a on 2012-09-15
thanks for the support, my problem fix by changing graphic card to amd now i can feel 1366x768 in linux

---

