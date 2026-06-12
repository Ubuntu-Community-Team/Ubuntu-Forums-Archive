---
title: "ie (internet explorer) tab in Firefox"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by matyasfalvi on 2008-08-04
Hi!

I added the ie tab to my Firefox recently because I couldn't access my banks homepage properly so I thought that will help. 

However I receive the following message after trying to open the homepage [www.cib.hu](www.cib.hu) in an ie tab:

> Additional plugins are required to display all media on this page

and then I hit the > install missing plugins button. After that I receive: > No suitable plugins were found and the process finishes.

Anyone any suggestions on how to resolve this or may be some one knows other options to deal with sites that do not support firefox or linux.

Thank you!

---

### Post by sh4d0w808 on 2008-08-04
Hello matyasfalvi (vagy matyasfoldi?),

Maybe the Java plugin missing from your Firefox, I recommend U to check it. (Üdvözlet Fehérvárról!)

---

### Post by gjoellee on 2008-08-04
if this happened on the the front page there I have no idea why it happened, however are you sure you have flash installed, if you have flash might be broken!
Go to you home folder and press CTRL+H and then go in to ".mozilla" and go to "plugins" if it is a file called "libflashplayer.so" there delete it, and if it isen't there you just don't have flahs installed

now check out this website: [http://www.ubuntu-unleashed.com/2008/05/howto-install-flash-player-10-astro.html](http://www.ubuntu-unleashed.com/2008/05/howto-install-flash-player-10-astro.html)

---

### Post by sailor2001 on 2008-08-04
you might have to install  ie4lin........ google that

---

### Post by james_vanb on 2008-08-04
Link for install of ies4linux:

[http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux)

---

### Post by stevoo on 2008-08-04
i think ie4Lin is the way to go.

The plugin for FF isnt really working that good for us :(

---

### Post by scottuss on 2008-08-04
I may be wrong but doesn't this extension just create an instance of the Web Browser control in Windows (ie, internet explorer) inside Firefox.

Therefore I would say it wont work on Linux as it doesn't have Internet Explorer.

---

### Post by philinux on 2008-08-04
> **scottuss said:**
> I may be wrong but doesn't this extension just create an instance of the Web Browser control in Windows (ie, internet explorer) inside Firefox.

Therefore I would say it wont work on Linux as it doesn't have Internet Explorer.

Correct it cannot work. Only ies4linux will work. The ie tab addon is for windows boxes.

---

### Post by matyasfalvi on 2008-10-25
Hi All!

Thanx for the useful replies!

I finally got my bank's website work even the online banking part in firefox. i simply installed all java plugins and apps available on the planet :-)

In addition I installed wine and after that ies4linux as well. However I am having some issues with ies4linux:

[LIST=1]
[*]Some how I cannot get the java plugins to work (i.e. I have downloaded them but I still cannot access sites that need java. (see attached pictures 1st updated the system, 2nd update successful, 3rd installed java, 4th still receiving the error message java virtual machine is missing)
[*]I know this will sound strange but it is only possible to run ie4linux once during a session that means that after I close ie4linux I cannot reopen it again. To open ie4linux again i'd have to restart.
[/LIST]

Any help is much appreciated!



(Ps: sh4d0w808! Én meg üdvözöllek Bp.r&#337;l)

---

### Post by dog-soldier on 2008-10-25
for what its worth i went to your banks site useing opera and didnt get any pop-ups at all.

---

### Post by matyasfalvi on 2008-10-25
Hi dog-soldier!

I have the following applications installed:

[LIST=1]
[*]Sun Java 6 Runtime
[*]Sun Java 6.0 Browser Plugin
[/LIST]

and i am using firefox as a browser.

This is how i got the site to work!

Ps: U can get the Java Runtime and the Plugin by going to **Applications/ Add/Remove** and then set **show** to **All available applications** type in **search** _java_ and then u'll be able to find them. To install just check the box then press Apply Changes.

---

### Post by dog-soldier on 2008-10-26
i just went there with firefox and had no trouble. 
i just have flash and java installed on the computer and the default for firefox. since i dont ever really use firefox anymore.

---

