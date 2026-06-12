---
title: "VLC and DVD"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by makada on 2008-05-04
Hi all. I am new to Ubuntu, so just bear with me.

I have installed Ubuntu 8.04 as dual boot with my win xp. After installing ubuntu , I have been following instructions at [http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_DVD_Support](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_DVD_Support) and then I installed vlc also.

The problem is that I cannot make vlc the default dvd player. I tried as the guide said at [http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_make_VLC_open_when_you_insert_a_DVD](http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_make_VLC_open_when_you_insert_a_DVD)

and typed

cp /usr/share/applications/vlc.desktop /home/hildenae/.local/share/applications/vlc-dvd.desktop

but I keep getting the message 

cp: cannot create regular file `/home/hildenae/.local/share/applications/vlc-dvd.desktop': No such file or directory

Also when I attempt to play any DVD with VLC it refuses and tells 

cannot find dev/scd0

But when I checked the properties of the DVD it showed it was at media/cdrom1, so when I manually typed this into the device name of vlc, it started playing. How can I make VLC recognize the correct device id and how to make it play automatically?

Also no matter what I use totem or VLC, the picture quality is pathetic. It is greyish with few colors and lot of green lines.

Thanks for the help in advance

---

### Post by chewearn on 2008-05-05
> **makada said:**
> The problem is that I cannot make vlc the default dvd player. I tried as the guide said at [http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_make_VLC_open_when_you_insert_a_DVD](http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_make_VLC_open_when_you_insert_a_DVD)

and typed

cp /usr/share/applications/vlc.desktop /home/hildenae/.local/share/applications/vlc-dvd.desktop

but I keep getting the message 

cp: cannot create regular file `/home/hildenae/.local/share/applications/vlc-dvd.desktop': No such file or directory


There is a problem with the home path in that command (it's assuming the user is "hildenae", which I'm sure you are not).  Use this instead:
```
cp /usr/share/applications/vlc.desktop ~/.local/share/applications/vlc-dvd.desktop
```


> 
Also when I attempt to play any DVD with VLC it refuses and tells 

cannot find dev/scd0

But when I checked the properties of the DVD it showed it was at media/cdrom1, so when I manually typed this into the device name of vlc, it started playing. How can I make VLC recognize the correct device id and how to make it play automatically?I'm not sure if it's your typo here, but there is an additional forward slash in front of the path, like this: /dev/scd0

If it's not a typo, correct this by opening VLC player, go to:
Settings menu > Preferences > Input / Codecs
Find the items under "Default devices"; change the path to /dev/scd0

You need to restart VLC for the change to take effect.



> 
Also no matter what I use totem or VLC, the picture quality is pathetic. It is greyish with few colors and lot of green lines.

Thanks for the help in advanceTake a photo and post it here.

---

### Post by makada on 2008-05-05
Thanks for the reply

At work now. Will go home and reply back

---

