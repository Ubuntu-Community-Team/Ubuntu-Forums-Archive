---
title: "Can't Save Manual Network Settings"
date: 2012-02-21
forum: New to Ubuntu
---

### Post by RyujiOtogi on 2012-02-21
'Ello. I'm running Ubuntu 11.10 x32 bit desktop edition within VirtualBox(latest version: 4.1.as of writing) on my Mac OS X Lion. I'm trying to setup a Static IP. I Google'd this and found a fairly simple and easy-to-understand walk -through. You simply go to System Settings on the side panel, and go to Network which is listed under Hardware. Then you click on Configure to edit your connection settings, and change the Automatic (DHCP) method to Manual under iPv4 settings. I did just that, and proceeded to add my Address, Netmask, Gateway, and DNS servers. After that I was ready to save, happy for once to quickly find a plain-and-simple solution. 

But, I CAN'T save these settings. The Save Button is grayed out, making my efforts to save these changes utterly useless. I searched the forum for an answer and found a couple threads where users had a similar problem, but they seemed to figure it out themselves and I didn't see their solutions. Of course, further Google inquiries also returned unsatisfactory results. If anyone could be help, your services would be greatly appreciated!

---

### Post by RyujiOtogi on 2012-02-21
Ok, nevermind. I tried it again and my computer likes me now. I'm not sure what fixed the problem. I looked at the settings under the other categories like 'Wired', '802.1x Security', and 'IPv6 Settings' and checked & unchecked a few boxes after exiting out the window a few times to mess around with it. Something I did put it back in shape apparently. Perhaps one of the settings I had prevented it from saving.

---

### Post by JASONATRON on 2012-03-17
So you have no idea how you solved this problem?  I have the same problem and I can't seem to figure it out.  In fact, I'm running Ubuntu on two different computers and in both cases the save button is "greyed out."

---

### Post by don equis on 2012-03-23
This is the first result on google when searching the problem. I could solve it deleting the old configuration and then making a new one.

---

### Post by molton on 2012-06-06
I also had this problem, I solved it by deleting extra blank entries above and below the entry I added to the manual IP list.  For some reason the list looked empty, but it had blank entries that were causing problems.  I hope this helps.

---

