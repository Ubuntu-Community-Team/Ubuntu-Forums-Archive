---
title: "Windows Vista &amp; Ubuntu 8.04 Dual Boot - Problems please help !"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by new on 2008-09-16
Ok...i have gotten the dual boot done...and i am now working on the BCD setup thing...so that would be soon covered...i have a Dell Inspiron Laptop 1420 ! It has 4gb ram and 160 GB hard drive. I have given the OS each about 70 GB....so they have space. Well now this laptop comes with integrated webcam and bluetooth and i would really like to get them working in both OS...but now my driver from dell won't install the damn bluetooth software for the module 355...and now i can't get my wireless to work in ubuntu or my webcam or my bluetooth...could someone please help me...and how to get my ubuntu to be as good as it possibly can...with all the perks...thank you in advance...

---

### Post by jbrown96 on 2008-09-17
find out what hardware you have and start searching based on that. Sorry, but this thread probably won't get much attention since the title does not say exactly what your problem is. Therefore, you should try to find people with the same problems. 
1) Figure out what hardware you have. In a terminal, ```
lspci
```. The output will give you very specific information on the your hardware. Simple things like copying the line from your bluetooth device + Ubuntu and searching will probably find you an answer. 
2) I don't have any knowledge about bluetooth or webcams, but maybe others will be able to help you if you can't find an answer.
3) If you do find an answer somewhere else, it's always nice to post it here or at least a link. Then mark the post solved.

---

### Post by bobnutfield on 2008-09-17
As jbrown96 has said, all of these things have been covered pretty extenisively on this forum and others, but your hardware has to be identified to offer any real help.  For your bluetooth, however, you might check in System>Aministration>Services and make sure that the bluetooth service is checked.

---

