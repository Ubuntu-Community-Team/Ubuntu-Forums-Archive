---
title: "[SOLVED] Invalid Menu Item -- addAsPodcast..."
date: 2008-06-08
forum: New to Ubuntu
---

### Post by stevezygote on 2008-06-08
I am on a Kubuntu 8.04 machine which includes a 2.2Ghz Celeron with 512MBs of RAM on a 60GIG HDD, with two partitions, one for Kubuntu and one for Windows XP SP3. 

Consistently I get an error message in Kubuntu which I neither understand nor know how to fix. The header reads:

[B]Error - Dolphin
The desktop entry file
/usr/share/apps/d3lphin/servicemenus/amorok_addaspodcast.desktop
has an invalid menu item
addasprodcast
then an ok button
[/B]
once I get this error message when trying to access a file in Dolphin I cannot do anything else. I have to close Dolphin and then reopen it and even THEN I'm not ensured that I won't get the error message again. 

Question: how do I fix this once and for all. 

Thanks.

---

### Post by aos101 on 2008-06-08
This is a known bug which still isn't fixed :(

[https://bugs.launchpad.net/ubuntu/+source/dolphin/+bug/199393/](https://bugs.launchpad.net/ubuntu/+source/dolphin/+bug/199393/)

To fix it go Kicker -> Run Command and type:
```
kdesu kate /usr/share/apps/d3lphin/servicemenus/amarok_addaspodcast.desktop
```
Then add this line to the end of the file:
```
Exec=dcop amarok playlistbrowser addPodcast %u
```
Save that, and you might need to restart Dolphin.  I *think* that should fix it (I more or less just copied the fix from the people posting in the bug report).

---

### Post by stevezygote on 2008-06-08
Thank you. We'll see if I've fixed it. I do it a slightly different way. I started with Unix based mainframes at University long before DOS came along and as soon as the GUI environment came along I went straight to it. I guess I have a very graphical mind. Anyway, I took the path in Dolphin to the file in question and right clicked it and loaded it as root (which is an option I have in Kubuntu). Find that much easier. I added the line you told me and saved it. No problem. So now we'll wait and see. Thanks again! I don't know what I would do without the good people in the community that supports the neophyte. Really appreciate it!

---

### Post by aos101 on 2008-06-08
Yeah doing it a more graphical way is fine.  There's many ways to do things, so just do what works for you :)

I'm attempting to build a package that fixes this problem, so we'll see how that goes.  It really should be fixed, so hopefully an update to dolphin can get released to fix this for everyone.

---

### Post by arcanus on 2008-07-14
Lovely asos!

Didn't even have to restart Dolphin. (Window$e problem that :P)

---

### Post by aos101 on 2008-07-14
A fix for this bug is currently in testing in hardy-proposed, so hopefully soon the fix will be released and pushed out as an update to all Kubuntu users (so people won't need to mess about like this to fix it themselves).

---

