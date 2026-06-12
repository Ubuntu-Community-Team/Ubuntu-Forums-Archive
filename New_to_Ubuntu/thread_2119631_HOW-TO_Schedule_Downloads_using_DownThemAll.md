---
title: "HOW-TO: Schedule Downloads using DownThemAll"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by Mahdi D on 2013-02-24
Hey there,

There's a trick to schedule your downloads using [DownThemAll!]("https://addons.mozilla.org/en-US/firefox/addon/downthemall/"), if you ask me, DTA is the fastest download manager available for Ubuntu users, flareGet is great, but it doesn't integrate with Firefox unless you pay for it. ( Edit: It does, I was wrong, thanks to [[COLOR=#000000]adnan-kamili[/COLOR]]("http://ubuntuforums.org/member.php?u=1407121") we know that, we can integrate flareGet with Firefox by FlashGot, but we have to [download flareGet from it's site]("http://flareget.com/download"), not from Ubuntu Software Centre. You'd better use flareGet or Internet Download Manager 5.05 under wine, they work fine, this trick has some problems.  )

We know that, if we close DownThemAll without pausing downloads, the downloads will resume upon starting DownThemAll again, so, what happens if we make DownThemAll our homepage, and schedule Firefox to open on the right time? that's it! ( Thanks to [[COLOR=#DD4814]**lovinglinux**[/COLOR]]("http://ubuntuforums.org/member.php?u=649167"), we know [how to make DownThemAll our homepage]("http://ubuntuforums.org/showpost.php?p=7891010&postcount=5") )

So that's it, we make 

```
chrome://dta/content/dta/manager.xul
```our homepage, then, we need a script to start Firefox at the time we want it to, then, shut the system down at the specified time.


open gedit or any other text editor and write these : 

```
#!/bin/bash

sleep [Time you want this script to wait]

sudo shutdown -h [Shutdown's time]

firefox


```As an example, imagine it is 5:00 PM now, and we want our downloads to be started at 1:00 AM and we want our system to shutdown at 7:45 AM, we'll write our script like this:

```
#!/bin/bash

#sleep time equals to time between 5 PM and 1 AM, so 8. for more options of sleep command, see *sleep --help*
sleep 8h

#24 hours clock
sudo shutdown -h 7:45

firefox


```You're done with writing, save it as a .sh file, then, you can run it via Terminal like this:


```
sudo sh /path/to/file/scheduler.sh
```[COLOR=Red]
NOTE: YOU MUST RUN IT AS ROOT, ELSE, IT WILL ASK FOR PASSWORD WHEN IT COMES TO RUN SHUTDOWN COMMAND, SO THAT WON'T WORK.[/COLOR]

KNOWN ISSUE:

      Resets Firefox Add-Ons.



Enjoy!


[COLOR=Red](For Persian / Farsi users:
[/COLOR][&#1583;&#1608;&#1587;&#1578;&#1575;&#1606; &#1601;&#1575;&#1585;&#1587;&#1740; &#1586;&#1576;&#1575;&#1606; &#1607;&#1605; &#1605;&#1740;&#1578;&#1608;&#1606;&#1606;&#1583; &#1575;&#1586; &#1575;&#1740;&#1606; &#1604;&#1740;&#1606;&#1705; &#1575;&#1587;&#1578;&#1601;&#1575;&#1583;&#1607; &#1705;&#1606;&#1606;&#1583;)]("http://ubuntuforums.org/blog.clockwise.pro/%d8%b2%d9%85%d8%a7%d9%86%d8%a8%d9%86%d8%af%db%8c-%d8%a8%d8%b1%d8%a7%db%8c-downthemall/")

---

### Post by adnan-kamili on 2013-02-25
FlareGet integrates with firefox fully, without any cost. Just install flashgot addon and choose flareget from the list.

---

### Post by Mahdi D on 2013-02-25
> **adnan-kamili said:**
> FlareGet integrates with firefox fully, without any cost. Just install flashgot addon and choose flareget from the list.


I tried it, but that doesn't seem to work, at least for me, and that goes a little bit illegal, because flareGet itself gives integration with a cost, dunno. :D

I really like DownThemAll and I think it's better than flareGet, that's a personal choice anyway. xD

---

### Post by adnan-kamili on 2013-02-25
It seems you have installed flareget from Ubuntu Software Centre. It has some issues. Try using the version available on website: [http://flareget.com/download](http://flareget.com/download) . It works fine, and it is not illegal, flashgot support was added for flareGet on request by its developer only.

---

### Post by Mahdi D on 2013-02-26
> **adnan-kamili said:**
> It seems you have installed flareget from Ubuntu Software Centre. It has some issues. Try using the version available on website: [http://flareget.com/download](http://flareget.com/download) . It works fine, and it is not illegal, flashgot support was added for flareGet on request by its developer only.


Hey there, you were right! now, I don't think if anybody needs this trick, thank you very much! <3

---

