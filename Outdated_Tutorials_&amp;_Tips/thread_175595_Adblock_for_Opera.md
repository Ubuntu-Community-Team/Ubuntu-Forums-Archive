---
title: "Adblock for Opera"
date: 2006-05-13
forum: Outdated Tutorials &amp; Tips
---

### Post by Pjotor on 2006-05-13
This is how to block ads in Opera 8.5.

Open file  /home/username/.opera/opera6.ini (you should NOT edit this file while Opera is running so please close your Opera-browser before you do this):

```
gedit ~/.opera/opera6.ini
```

and add there just after

```
[Adv User Prefs]
```

the following line:

```
URL Filter File=/home/username/.opera/block.ini
```

(remember to replace username with your username;) )

Save and exit.

Create file block.ini in directory /home/username/.opera

```
gedit ~/.opera/block.ini
```

and paste there the contents of the following link:

[http://linux1.no/forum/viewtopic.php?t=306](http://linux1.no/forum/viewtopic.php?t=306)

(yes, the long one)

Save and exit.

Start Opera and thank the Norwegians!

---

### Post by shamrock_uk on 2006-05-19
Also you can download the beta of Opera 9 from [http://labs.opera.com](http://labs.opera.com) which has a built in content blocker accessible with a right-click.

---

### Post by magnusbb on 2006-05-20
Thanks for a great tip.

---

### Post by Rikostan on 2006-05-20
Thanks for the tip. The lack of a decent adblock is what is stopping me from using Opera. I tired Beta 9, but the adblock is not near as full featured as Firefox's is.

---

### Post by lazyd2 on 2006-05-20
Thanks for the great tip!

---

### Post by aaarg on 2006-05-21
worked perfectly....thanks!

---

### Post by ice60 on 2006-05-22
i use Privoxy. it's an HTTP proxy, so everything from the internet is filtered through Privoxy's filters before it gets to Opera. it's similar to Proxomitron (perhaps the greatest program of all-time)

---

### Post by Pjotor on 2006-05-23
[QUOTE=ice60]i use Privoxy. it's an HTTP proxy, so everything from the internet is filtered through Privoxy's filters before it gets to Opera. it's similar to Proxomitron (perhaps the greatest program of all-time)[/QUOTE]

Actually, when I started using Opera I remembered reading your 'Opera Improved' -how-to some time earlier, but even though I tried searching the forums, couldn't find it so I 'borrowed' this how-to from the Norwegian forum.

But thank you!

P

---

### Post by Juippisi on 2006-05-26
[http://ubuntuforums.org/showthread.php?t=33945](http://ubuntuforums.org/showthread.php?t=33945)

And there's a nice example file. 

Yes, Opera 9 has a wonderful adblocking technique. I'm waiting to see the "stable-release" of the new Opera. I'm now using Firefox. I do not have adblock-extension installed, but that doesn't bother me.

---

