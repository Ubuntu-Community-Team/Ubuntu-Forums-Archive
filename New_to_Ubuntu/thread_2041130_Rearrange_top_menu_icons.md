---
title: "Rearrange top menu icons?"
date: 2012-08-11
forum: New to Ubuntu
---

### Post by d4m1r on 2012-08-11
Hey guys, just wondering if anyone knew how to rearrange the top menu icons or even if it possible at all? Specifically, I have a set of specific things that start at boot (including weather, sysmon, etc) and I want everything I launch after logging in, to be to the left of all the at launch icons.

Right now, they seem to be starting randomly in terms of placement....Specifically, I'd like the KMess icon (green bird) to be to the left of the Skype (green checkmark) icon. Is it possible to rearrange the order of these icons? :confused:

[IMG]http://i48.tinypic.com/294m0dt.png[/IMG]

---

### Post by Darkhaund on 2012-08-11
I would like to know this as well..


BTW, what is that "green bird"  you got there? it looks nice.. what app is it or what does it do?

---

### Post by d4m1r on 2012-08-11
It's KMess, a linux MSN Messenger client.

---

### Post by Frogs Hair on 2012-08-11
The indicators can be moved in Gnome Classic with Alt + Right Click or Super Key + Alt + Right Click. In Unity, indicators other than the defaults normally appear in the order the applications were installed and can't be moved.

---

### Post by d4m1r on 2012-08-12
> **Frogs Hair said:**
> In Unity, indicators other than the defaults normally appear in the order the applications were installed and can't be moved.

That doesn't seem to be the case....Not only did I install KMess last, but I also launched it last but it still places the icon in in between others and NOT at the end (to the left). Could this be an issue with the KMess icon specifically? I don't believe it is choosing where to place itself however so I think it is a bug with the default top menu bar package in Ubuntu 12.04...

It **should** be organizing icons not by install order or anything else, but simply in what order were they started....That way, all the default at boot icons would be first and each application you launch after, will place their icon to the left of ones already there. If that were the case, I wouldn't have this issue :(

---

### Post by d4m1r on 2012-08-12
Does anyone else have any suggestions? :confused: Seems like this is a common problem but nobody has idea's on how to move the icons around....

---

### Post by d4m1r on 2012-08-12
For those of you who are also looking for a solution, read [THIS]("http://www.tuxgarage.com/2011/06/re-arrange-appindicators-in-ubuntu.html"). I found it while doing some serious research into this issue and while it does not work for me (Ubuntu 12.04 x64) it may work for you....

The article was written in June of last year so I am guessing the author was using 11.04 (or even older?) and modifying that file for me did change things, but for the worse.....

---

### Post by 25tom on 2012-08-13
If those icons are in the indicator section of the menu bar, then I'm not sure if they can be moved; however, see what right-clicking on the icons will do - it's possible that there is a 'move' option in the popup menu...

---

### Post by d4m1r on 2012-08-13
> **25tom said:**
> If those icons are in the indicator section of the menu bar, then I'm not sure if they can be moved; however, see what right-clicking on the icons will do - it's possible that there is a 'move' option in the popup menu...

No, there is not. I've read similar stories online (ctrl + right click, middle click, super key +alt + right click) but none of that stuff works as it is gnome panel shortcuts....The only thing that looks like it might work, is middle clicking on the icon (makes it flash) but then it does nothing.....

---

### Post by marlow59 on 2012-08-13
Maybe it's just impossible with Unity... :(

---

### Post by Frogs Hair on 2012-08-13
I have no experience with Kmess , but, applications have appeared in the order installed on the last three unity releases. There are currently no options to move the indicators in Unity. The dconf editor has limited indicator settings right now.

---

### Post by Darkhaund on 2012-08-14
How did you make is so that you speaker icon on the tray has a "blue" sound wave? mine is jsut plain white

---

### Post by d4m1r on 2012-08-14
> **marlow59 said:**
> Maybe it's just impossible with Unity... :(

Yes, looks like it is currently impossible to do this is Ubuntu 12.04 Unity.....:(

---

### Post by Darkhaund on 2012-08-15
any info tip on the speaker icon that appears blue?

---

### Post by d4m1r on 2012-08-15
> **Darkhaund said:**
> any info tip on the speaker icon that appears blue?

That's offtopic but its the default icon for the gnome 3 theme I'm using....

---

### Post by moteprime on 2013-01-10
@d4m1r
Hi did you find anything. I also would really like to get my panel indicators organized.

---

### Post by d4m1r on 2013-01-10
> **moteprime said:**
> @d4m1r
Hi did you find anything. I also would really like to get my panel indicators organized.

Myself as well but unfortunately, this does currently not seem possible in Ubuntu 12.04 LTS as I've researched it quite a bit and found no way to do it :(

---

### Post by moteprime on 2013-01-10
Isn't it a bit strange really. Linux people are not the kind to just sit on their hands when it comes to a thing like this.
I did find a couple of places that described two config files that controls it in 12.04, but it seems it changed in 12.10 so it only covers the default indicators.

---

### Post by d4m1r on 2013-01-10
Indeed it is strange and I have found similar things after my research but my original problem remains with 12.04...How to specify/lock/whitelist my top menu bar so I can control where 3rd party icons are located.

Or any similar function, regardless of the method.

---

### Post by moteprime on 2013-01-11
And i really can't imagine that it can be very difficult to change the order of the icons.

---

### Post by Shuey on 2013-05-27
I realize the info from this link is old (relatively speaking), but it appears to work:
[http://www.webupd8.org/2011/06/how-to-change-application-indicators.html](http://www.webupd8.org/2011/06/how-to-change-application-indicators.html)

---

### Post by moteprime on 2013-05-27
Thanks for sharing the link!

---

