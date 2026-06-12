---
title: "Firefox 3.0.1 temp files"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by richg on 2008-07-30
Does Ubuntu 8.04 clear all the temp files when the OS is shutdown? When running Ubuntu, I have looked at times and I see files that must be for the OS but I am never sure if a file could be put there by someone on the 'Net.
Just wondering as I am not very good at Linux software. I do not have any Windows or Gates on my Linux PCs.
Thanks.

Rich

---

### Post by Shazaam on 2008-07-30
Usually all unneeded OS temp files disappear on shutdown or a reboot.

Firefox is a different animal.....
A. Go to Places>Home folder>.mozilla (hidden folder- CTRL+H to unhide)>firefox>yourprofile>cache
Everything but the files _CACHE_001 through _003 and _CACHE_MAP can be deleted.
B. To set Firefox up so it will clear everything open Firefox, go to Edit>Preferences>Privacy>Always clear my private data>Settings and check all of the boxes. Then, when you are done you can go to Tools>Clear Private Data and cleanup. If you want it done automatically for you when you close Firefox make sure to check off "Always clear my private data when I close Firefox".
When you set Firefox up like this all saved passwords, forms and cache for websites will be cleared. Another thing to remember is sometimes things get put into your .thumbnails folder too. :)

---

### Post by freak42 on 2008-07-30
you are not very clear in what you want?

do you want to remove all temporary files, cookies and history data from firefox? then choose (in firefox Tools->Clear Private Data)

files downloaded by firefox temporarily (for opening them with other applications) should be cleared by ubuntu automatically after a while.

---

### Post by sandeepy on 2008-07-30
i have a question here ... is the .mozilla path true even for mp3/video files played using mplayer ? I sometimes find that some mp3s get buffered in /tmp but not always. where else cud they be ?

---

### Post by kansasnoob on 2008-07-30
In Firefox go to Edit > Preferences, then click on the privacy tab.

Look here:

[ATTACH]79548[/ATTACH]

You see where it says "Private data", well you can choose "Always clear my private data when I close Firefox" if that's what you want.

---

### Post by richg on 2008-07-30
> **freak42 said:**
> you are not very clear in what you want?

do you want to remove all temporary files, cookies and history data from firefox? then choose (in firefox Tools->Clear Private Data)

files downloaded by firefox temporarily (for opening them with other applications) should be cleared by ubuntu automatically after a while.

I very clearly said what I wanted. Does Ubuntu keep temp files like Windows does when the PC is shut down.

I have had Firefox configured the past few years so all private data is cleared when I close Firefox. History, cookies are cleared. I do not save passwords. I do not keep what is in forms or search bar. I do not remember what I have downloaded. I do not accept third party cookies. There are no exceptions. 

Ok, what was I talking about? Oh, can a site deposit a file in the temp file/s in the PC and remain there after shutting down? Yes or No?

I have been using Linux for four years and I know there are differences the way the software works and the way Firefox works. I am surprised this got so complicated.

Rich

---

### Post by kansasnoob on 2008-07-30
> **sandeepy said:**
> i have a question here ... is the .mozilla path true even for mp3/video files played using mplayer ? I sometimes find that some mp3s get buffered in /tmp but not always. where else cud they be ?

To a degree yes! But there is always a forensic record of everything you do on the internet.

---

### Post by Shazaam on 2008-07-30
> **richg said:**
> 
Ok, what was I talking about? Oh, can a site deposit a file in the temp file/s in the PC and remain there after shutting down? Yes or No?Rich
AFAIK no, nothing can be put in /tmp because it is owned by root. You would have to be logged in as root and surfing the web for badware to gain access to anything besides your home folder.
You DO take a risk installing apps downloaded from the internet, especially if it needs root to install. Make sure that you trust where you get the app from.

---

