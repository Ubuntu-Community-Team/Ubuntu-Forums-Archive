---
title: "New Install 15.04 Zen Book Pro some &amp; scalling"
date: 2015-08-22
forum: New to Ubuntu
---

### Post by zongosaiba on 2015-08-22
Greetings to all, 

 I have installed Ubuntu 15.04 on my new asus zen book pro. I have completely removed Win 10 (could not stand it). 
Everything is working perfect. I have one small issue and it is linked to scaling. The scaling is not bad overall. The only part remaining that has not scaled is the inside of 'Files'. This opens up my home folder. Everything in there is so tiny :) The funny thing, this is the only part that has not scaled. That begs the question , if everything else has scaled, why not the inside of Files (home folder) ?
Also, if anyone has a fix for it that would be much appreciated. Otherwise, I am going to have to buy a magnifying glass :)

All the best

PS: I just installed Spotify and it is not scaling either. I thought if the system had the correct drivers the apps would scale. Is Ubuntu 15.04 able to scale on 4K display?

future on scaling looks bleak -> [https://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/](https://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/)

For those interested, here is one solution to have spotify scale properly. Remove any prior source list from Spotify.

# echo deb [http://repository.spotify.com](http://repository.spotify.com) testing non-free | sudo tee [/etc/apt/sources.list.d/spotify.list]("http://ubuntuforums.org/etc/apt/sources.list.d/spotify.list") 

# apt-get update
# apt-get upgrade

Exec=spotify --force-device-scale-factor=1.5 %U -> change the factor to whatever you want in spotify.desktop and voila.

Problem solved. My entire Ubuntu desktop is now scaling to my heart's content. Here is one solution to the issue. 
You need to calculate your real DPI.
#  xdpyinfo | grep dots - resolution -> this should give you your actual resolution. Mine was set at 90*96. That is why I was seeing so small.
# xrdb -query | grep dpi - Xft.dpi -> this should give you your actual DPI
Next calculate your real DPI
# xrandr | grep -w connected -> this command will give you all the details about your display regarding x and y axis including size. This is what I got on mine as an example: eDP1 connected primary 3840x2160+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
Next step, we do some math:
First we put everything in Inch. Divide x and y by 2.54: 34.4 cm / 2,54 = 13,54 In (x). For Y now 19,4 / 2,54 = 7.63 In
Next we take X DPI and Y DPI and divide by size of X and Y. 3840 / 13,54 = 283. Same for Y 2160 / 7,63 = 283 (real DPI)

Final step. We modify lightdm 
# vim [/etc/lightdm/lightdm.con]("http://ubuntuforums.org/etc/lightdm/lightdm.con")
Add this line xserver-command=X -dpi 283 
Restart X or reboot.

Please be very careful when you attempt those changes as you might end up rebooting to a black screen. Do this only if you feel Ok and you understand the risk. 
I am using Ubuntu 15.04 64 bit
Kernel 4.1.6-040106-generic
UNITY 
If you have a different configuration, this might not be suitable. Also I am guessing this is only one approach. You might be able to achieve the same result using a different method. 

I now remember why I gave up on Linux in 2011 :)

---

