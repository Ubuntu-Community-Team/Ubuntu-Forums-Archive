---
title: "Having to restart to open wireless connecitons"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by brodiesel on 2008-09-10
Alright, so I've got Hardy working and I'm pretty happy, but...

There are many times that when I try to open a wireless connection after making the computer go into hibernation and click on the wireless icon it doesn't show any available networks. To show some available networks, I have to restart the computer. Not only that, but the last time I did that it erase all of my bookmarks. ???? Of course, for whatever reason when I restart my pc, it takes forever and a day.

I may not be a big fan of XP, but at least I was able to just close my machine when I was done, and then when I reopened it it started right back up and connected to the network.

Suggestions?

as a ps, this ?:
I'm also trying to port over all of my firefox stuff, and i've found the file on the windows side, but i cant figure out where on the ubuntu side to drop it. Where are my mozilla files? The ubuntu search function doesn't seem that great...

---

### Post by bobnutfield on 2008-09-10
> 
as a ps, this ?:
I'm also trying to port over all of my firefox stuff, and i've found the file on the windows side, but i cant figure out where on the ubuntu side to drop it. Where are my mozilla files? The ubuntu search function doesn't seem that great...

Your mozilla files are in /home/<your user name>.  They are hidden files that you have to select "show hidden files" from the view tab, so it will show up as ./mozilla.  That is where all your profile files are.


I will tell you that many, many people have trouble with suspend and hibernate in Linux.  I have used many distros and none seem to work well with suspend.  I have eventually given up on it and just shut down when I am not using my laptops.

---

### Post by brodiesel on 2008-09-10
thanks, that was helpful. now, can you help me figure out what this means?

> you can copy the entire profile over.
its at C:/Documents & Settings/<WindowsUser>/Application Data/Mozilla/Firefox/Profiles/ its a wierd folder name with .default
copy this to /home/<UbuntuUser>/.mozilla/firefox/
and then change profiles.ini (in that folder) to have the different profile name as the one you just copied. That copies bookmarks, addons etc, even keeps the right order

I've copied the .default file to the folder, but i'm not quite sure how to change the profile to have the different profile name. How do I get firefox to adopt my other profile?

---

### Post by bobnutfield on 2008-09-10
Unfortunately, I have never had occassion to need to move or transfer my profile information in Firefox, so I have never tried it.  But, I did find the information on doing it:

> [http://support.mozilla.com/en-US/kb/Profiles](http://support.mozilla.com/en-US/kb/Profiles)

Hopefully this is what you are looking for.

---

### Post by brodiesel on 2008-09-11
Thanks, that page solved the issue of importing my firefox profile. I have come closer to understanding the wireless issue, so I'll probably start a new thread to try and get to the root of the issue.

---

### Post by cariboo on 2008-09-12
You are doing things the windows way, remember Linux is not windows. Usually you don't have to restart your computer because a service is not working, next time if you need to restart your network connection in a terminal type:

```
sudo /etc/init.d/networking restart
```

Jim

---

