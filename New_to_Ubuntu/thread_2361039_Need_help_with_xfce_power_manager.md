---
title: "Need help with xfce power manager"
date: 2017-05-11
forum: New to Ubuntu
---

### Post by login721 on 2017-05-11
I installed xubuntu in dell e4200 and i have some problems with xfce4 power manager .


1 .I can control screen brightness with hot key and terminal command(# tee /sys/class/backlight/acpi_video0/brightness <<< 5) , but slider in power manager do nothing .Screen dim setting is not working (xfce power manager > Display > "Put to sleep after" and "Switch off after" are works).
 What i tried :
[COLOR=#333333][FONT=sans-serif]     "Handle display brightness keys" is checked.
     Change [/FONT][/COLOR] kernel parameter acpi_backlight to vendor,native,video and update-grub , but none of them work.
    Added acpi_osi=linux . 




2.The e4200 have 15 levels of brightness but the onscreen notification only have 10 levels ,so the notification is not match the real brightness level .Is there any way to config the notification ?


Thanks in advance!
Sorry for my bad English!

---

### Post by oldrocker99 on 2017-05-11
Your English is fine! You might go to the Desktop Environments subforum and search that thread for "xfce power" with quotes. That'll filter the entire Forum database quickly. 

Welcome to the forums. You are obviously an experienced user, and I hope that you will enjoy Xubuntu and/or the other flavors of Ubuntu.

---

### Post by login721 on 2017-05-12
thank for reply ! I just bought the e4200 for 15bucks a weak ago , and i think its time to switch from Windows to something new .I did alot of google search to config the os and make the ide works .Everything is perfect except that brightness setting .

-------------------------------------
update :
I noticed that brightness setting only affect intel_backlight .Here is the brightness value each time i raise screen brightness :

0 : 0
1 : 3978
2 : 7956
3 : 11934 
4 : 15912
5 : 19890
6 : 23868
7 : 27846
8 : 31824
9 : 35802
10: 39780
11: 39780
12: 39780
13: 39780
14: 39780
15: 39780
16: 39780

I tried all the method i can find but none of them help .I end up with disable the onscreen notification (which is disable the audio level notification too) , and use turn off screen instead of dim screen .

update 2 : in debug mode fxce4-power-manager shows warning : no output have backlight property

---

