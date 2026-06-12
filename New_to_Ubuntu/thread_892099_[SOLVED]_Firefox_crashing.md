---
title: "[SOLVED] Firefox crashing"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by jualin on 2008-08-16
My Hardy installation is running great, can't be any better. However today I found a problem which I don't know if is related with something wrong with weather.com or something wrong with flash. Every time I try opening [The Weather Channel]("www.weather.com") website Firefox crashes and I have to restart it. This is the output when I run Firefox using the terminal > jualin@owner-desktop:~$ firefox [www.weather.com](www.weather.com)

(firefox:6168): Gtk-WARNING **: Error parsing gtk-icon-sizes string:
	'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Segmentation fault

The "Segmentation fault" error occurs after the Weather channel website finishes loading. The first line "Error parsing GTK" I get every time with many applications but it has never cause a crash. Every other website works great except this one. Any ideas?

---

### Post by dje on 2008-08-16
do you use flash 10? i got this error whenever i started firefox when i tried flash 10 (could be the bbc homepage which is my homepage). [http://weather.com]("http://weather.com") works fine for me with flash 9 from the repos

dje

---

### Post by jualin on 2008-08-16
Yes, I am using flash player 10. You think is a problem with Flash 10?

---

### Post by dje on 2008-08-16
well i got this error when i used flash 10 but didnt when i used flash 9 so i would say yes :)

dje

---

### Post by jualin on 2008-08-16
Thank you for the suggestion, I will uninstall Flash 10 and try Flash 9 and tell you if you were right.

---

### Post by jualin on 2008-08-16
You were right, it was a problem with Flash 10. Flash 9 doesn't appear to crash firefox when accessing the website.

---

### Post by dje on 2008-08-16
glad its fixed although i want to start using flash 10 but i cant cos i keep getting that error :(

---

### Post by jualin on 2008-08-16
I wanted to use Flash 10 too since it improves my Flash/Nvidia issue, which makes flash videos lag on Full Screen. I hope they fix that problem soon. Thank you again.

---

