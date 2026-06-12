---
title: "Not FULL Resolution with my Samsung Monitor!"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by Tachions on 2008-06-09
Hey everyone,

I have a Samsung SyncMaster 245BW monitor for my desktop dual booting Ubuntu and M$ XP, I love Linux but have not been using it that much because it is not fully using my screen resolution and causes things to lag or look like it is lagging, for instance, when I scroll down a page in firefox it lags... 

my full monitor resolution I am pretty sure is 1900 x 1280, and all I am currently able to support is 1600 x 1200...?!?

any ideas or fixes, please let me know, thanks a million!

---

### Post by quelx on 2008-06-09
Post */etc/xorg.conf* and your exact video card type, from the terminal```
lspci |grep VGA
```

---

### Post by Tachions on 2008-06-09
01:00.0 VGA compatible controller: ATI Technologies Inc RV530LE [Radeon X1600/X1650 PRO]


Is this what you need quelex?!?

---

### Post by Tachions on 2008-06-22
bump

---

### Post by unutbu on 2008-06-22
Try
```

cd /etc/X11
sudo cp xorg.conf xorg.conf-20080622
sudo aticonfig --resolution=0,1900x1280
```

Log out, then log back in.

If that does not work, post
```

cat /etc/X11/xorg.conf
```

If you get a white screen when you log back in, press Ctrl-Alt-F2. Log in, then type
```

cd /etc/X11
sudo cp xorg.conf xorg.conf-broken
sudo cp xorg.conf-20080622 xorg.conf
sudo /etc/init.d/gdm restart
``` That should restore your setup to what you have now. Then post 
```

cat /etc/X11/xorg.conf
cat /etc/X11/xorg.conf-broken

```

---

### Post by Tachions on 2008-06-23
hey unutbu, thanks for the post, everything was looking fine with the code until the last piece came up something like bad command with "resolution=0,1900x1280"
and something about parsing, sorry I dont have it in front of me because i decided to log out just in case it would work, but nothing, still 1600x1200... let me know if you still want me to post up the cat info... thanks for your help again!

---

### Post by markbuntu on 2008-06-23
Look in your /var/log/Xorg.0.log and you will see a line like:

Total of 27 modes found for primary display 

followed by a long list of modes that are all the possible resolutions for your display.


If it does not say 1900x1280 then you are out of luck. It could be 1920x1200 which is the common maximum resolution for a 24 inch display and which is closer to 1920x 1080 which is HD TV.

---

### Post by avtolle on 2008-06-23
Try, from a terminal```
gksudo displaycofig-gtk
```and see if your monitor is listed under the first tab. If it is, select it. I think that should do it.

---

### Post by Tachions on 2008-06-23
hey avtolle, thanks for the input but my monitor is not there, does that mean I sh*t out of luck, let me know....
thanks again

---

### Post by Tachions on 2008-06-23
hey markbuntu,

where do I go to check out that log?!?

thanks for your input and anxious to get rolling!

---

### Post by avtolle on 2008-06-23
> **Tachions said:**
> hey avtolle, thanks for the input but my monitor is not there, does that mean I sh*t out of luck, let me know....
thanks again
Since it is not listed, is your monitor a newer version of a prior version of the "same" monitor from Sansung? If it is, perhaps you can select the prior version and it will work. Otherwise, manually editing the /etc/X11/xorg.conf file might be the solution. 

BTW, did you check the graphics card on the second tab and did it detect correctly?

---

### Post by unutbu on 2008-06-23
According to [http://www.samsung.com/us/consumer/detail/spec.do?group=computersperipherals&type=monitors&subtype=lcd&model_cd=LS24HUBCFV/XAA](http://www.samsung.com/us/consumer/detail/spec.do?group=computersperipherals&type=monitors&subtype=lcd&model_cd=LS24HUBCFV/XAA),
your Samsung 245BW has resolution 1920x1200. 
Perhaps try 

```
sudo aticonfig --resolution=0,1920x1200
```

or, as avtolle suggested,
```
gksudo displayconfig-gtk

```

There are also the commands 
```

sudo dpkg-reconfigure -phigh xserver-xorg

```
or
```

gnome-display-properties
```
which you can try as well. (They all allow you to select from a list of resolutions.)

---

### Post by Tachions on 2008-06-24
hey guys so I tried all your input and it seem to not work right away, but then I updated my machine with the new updates and rebooted and wholah, don't know if it had to do with the your guys input, which I am grateful for, or from the updates, but wanted to say thanks again!

---

