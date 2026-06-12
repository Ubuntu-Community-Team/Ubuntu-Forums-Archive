---
title: "Google Earth and very small fonts."
date: 2012-05-03
forum: New to Ubuntu
---

### Post by quirino77 on 2012-05-03
Hello.

My Google Earth has very small fonts.
I had tried to install ms fonts, qt, even the "native look" fonts, but none has worked.
On a fresh install, it looks ok, but once i install the NVIDIA driver the fonts got too small that can't be read. It happens on the menu, upper and left. The labels on  the maps looks ok once a change the font size on Google Earth options.

I had try the nvidia .run and the install from "additional drivers".

What esle could i try?


I'm using Ubuntu 12.04, a GTX 560TI and a 42" full HD.

Thanks.

---

### Post by Curtis6767 on 2012-05-03
Scroll down in this linked thread until you find the discussion about fonts.

[http://ubuntuforums.org/showthread.php?t=1917614&highlight=Google+Earth+ia32-libs](http://ubuntuforums.org/showthread.php?t=1917614&highlight=Google+Earth+ia32-libs)

Apparently a couple of ways to deal with them.

Have not tried these solutions but looking over details now.

---

### Post by quirino77 on 2012-05-03
Thank's for your help.

The only one i hadn't tried was the google-fix. I had tried some similar, but not with this pack name.
By the way, google earth do not open. Even after checked all the files permition.

My problem is someway different. The problem is not a "ugly" font. But unreadable.

Here is how it looks. The problem is the buttons and menus.
[http://imageshack.us/photo/my-images/88/screenshotfrom201205032.png/](http://imageshack.us/photo/my-images/88/screenshotfrom201205032.png/)

---

### Post by nemonever on 2012-05-05
Hi. Same issue here. Not ugly but unreadable, just like the picture quirino77 posted.
I've tried on my 3 desktop pc: on a 32bit ubuntu 12.04, on a 64bit kubuntu 12.04 and on a 32bit ubuntu 10.10. In each one the problem is the same. Only thing in common is the nvidia video cards.
I've tried the google-fix too, but the small fonts are very persistent...
There is one thing: in my notebook with an ubuntu 12.04 64bit it works after first install. I've got to investigate a little more...

---

### Post by quirino77 on 2012-05-05
Do your notebook have an NVIDIA GPU and driver installed?

After installing 12.04, i had no problem. But once i install gforce driver the fonts change.

---

### Post by quirino77 on 2012-05-05
Got a solution (at least i can read). Don't know why hadn't worked on previous Unity, only on Gnome.

sudo apt-get install qt4-qtconfig
sudo qtconfig-qt4
go to Fonts> Point Size> 36 (for me is ok).

I don't know if it will change others programs. Let me know if you have problem. I had none untill now.

---

