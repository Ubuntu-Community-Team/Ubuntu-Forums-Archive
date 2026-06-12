---
title: "not found !!"
date: 2013-06-28
forum: New to Ubuntu
---

### Post by muhammad shaheen on 2013-06-28
Hello , I installed ubuntu 11.10 64bit alongside windows 7, and when I logged in and opened the update manager, it gave me a message to upgrade to the LTS version of 12.04 so I updated it and it is ok, the problem is , many software that I used to use in 11.10 are not available ... whenever I search for them in the software center it gives me a "Not Found" error , and if I use terminal with sudo command to install them it gives me an error that these software may be obsolete or something, for example , compiz configuration setting manager , SM player , VLC player ... so ... my question is divided into two:
1- what may cause this problem ??
2- is there another software like compiz manager , or a newer version with another name to enable the effects like wobbly windows and so on ??

thank you

---

### Post by Bashing-om on 2013-06-28
muhammad shaheen; Hi ! Welcome to the forum.

Do not know what can be said.
All the items you reference are available... Perhaps it is your search parameters; also keep in mind that files names in ubuntu are "space,letter,capital" exact.
As an example:
> 
sysop@1304mini:~$ apt-cache search smplayer
smplayer - complete front-end for MPlayer and MPlayer2
smplayer-themes - complete front-end for MPlayer - icon themes
smplayer-translations - complete front-end for MPlayer and MPlayer2 - translation files
sysop@1304mini:~$

What returns when you do terminal code:
```
apt-cache search compiz
```

[INDENT][INDENT][INDENT]just try'n to help[/INDENT][/INDENT][/INDENT]

---

### Post by deadflowr on 2013-06-28
Your repositories are probably disabled, or unavailable in your area.

To check open the update manger and click on the settings button.

Then make sure the repos listed are all checked.
Then close and hit the check button.

You can also run an update through the terminal, and post the output.
```
sudo apt-get update
```
And if that's not helping, post the output of
```
cat /etc/apt/sources.list
```

---

