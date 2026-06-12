---
title: "Firefox and Ubuntu"
date: 2012-05-05
forum: New to Ubuntu
---

### Post by loseby on 2012-05-05
Is there any way I can bring my windows bookmarks for Firefox to Ubuntu ? Have a bookmark file named bookmarks2011-12.30.json

I cant see the options in the Ubuntu versions for adding or importing bookmarks

---

### Post by 2ta8gdfte on 2012-05-05
I use firefox sync to link all my computers with the same bookmarks, it is in edit-preference. Not sure if this helps.

---

### Post by codemaniac on 2012-05-05
You can export all your firefox bookmarks on windows and import it on Ubuntu Firefox .
[http://support.mozilla.org/en-US/kb/Exporting%20bookmarks%20to%20Opera](http://support.mozilla.org/en-US/kb/Exporting%20bookmarks%20to%20Opera)

---

### Post by loseby on 2012-05-05
> **codemaniac said:**
> You can export all your firefox bookmarks on windows and import it on Ubuntu Firefox .
[http://support.mozilla.org/en-US/kb/Exporting%20bookmarks%20to%20Opera](http://support.mozilla.org/en-US/kb/Exporting%20bookmarks%20to%20Opera)

had a look and that doesnt work  ... ubuntu version doesnt have that option


> **2ta8gdfte said:**
> I use firefox sync to link all my computers with the same bookmarks, it is in edit-preference. Not sure if this helps.


I see it and it makes sense but the problem is I saved the bookmarks and atm I cant access windows ( different thread and problem ) to use the sync feature


I am puzzled as in Windows versions it was just a case of backing up and restoring... I guess a different file system but the funny thing is I managed to use Gorilla to get my Password safe files from Win7 ( I can see the files just cant boot into it ) and it worked brilliantly

---

### Post by 2ta8gdfte on 2012-05-05
Can you get into windows from mounting the windows in Ubuntu? if so copy and paste the whole firefox in ubuntu so you have all the files, I forget the export but it is fairly straight forward.

You probably know this as far as getting to the FF in windows.

---

### Post by codemaniac on 2012-05-05
> **losbey said:**
> had a look and that doesnt work  ... ubuntu version doesnt have that option





I see it and it makes sense but the problem is I saved the bookmarks and atm I cant access windows ( different thread and problem ) to use the sync feature


I am puzzled as in Windows versions it was just a case of backing up and restoring... I guess a different file system but the funny thing is I managed to use Gorilla to get my Password safe files from Win7 ( I can see the files just cant boot into it ) and it worked brilliantly
I am not on a ubuntu GUI right now , but there must be an option in Firefox toolbar for exporting and importing bookmarks .

---

### Post by 2ta8gdfte on 2012-05-05
Yeah the json is for a restore in the bookmarks-show all book marks in the import export dropdown it looks like.

---

### Post by loseby on 2012-05-05
> **codemaniac said:**
> I am not on a ubuntu GUI right now , but there must be an option in Firefox toolbar for exporting and importing bookmarks .

Nope....  I have wasted a lot of minutes looking but from what I have found out its all about "sync" these days

If I am wrong...please tell me:(

---

### Post by robert shearer on 2012-05-05
Firefox>Bookmarks>Show all Bookmarks 
and the window that opens should have import/export options.

and when in Firefox Ctrl+shift+O  opens the library window with Import and backup options.

Otherwise what version of Ubuntu and Firefox are you using ?

---

### Post by loseby on 2012-05-05
> **robert shearer said:**
> Firefox>Bookmarks>Show all Bookmarks 
and the window that opens should have import/export options.

and when in Firefox Ctrl+shift+O  opens the library window with Import and backup options.

Otherwise what version of Ubuntu and Firefox are you using ?


Am using the version that installed with 12.04  .....Mozilla Firefox for Ubuntu Canonical - 1.0

and in the Windows version the bookmarks have the import/export

---

### Post by sammiev on 2012-05-05
> **2ta8gdfte said:**
> Yeah the json is for a restore in the bookmarks-show all book marks in the import export dropdown it looks like.

+1 Use it all the time. :)

---

### Post by robert shearer on 2012-05-06
> **losbey said:**
> Am using the version that installed with 12.04  .....Mozilla Firefox for Ubuntu Canonical - 1.0

and in the Windows version the bookmarks have the import/export

As you can see other posters to this thread are using 12.04 and the same version of Firefox as you and all report the same navigation procedure to save and restore bookmarks.

Is your install a standard partitioning with Ubuntu as a separate O.S or are you using Wubi via Windows...??

If all else fails then go to your home folder and on the global menu choose View>hidden folders and delete the .mozilla folder. This will remove any **and all** Firefox configurations you may have deliberately or inadvertantly caused.

Then in a terminal run..
```
sudo apt-get purge firefox
```
to remove your current Firefox install and then run..

```
sudo apt-get install firefox
```
to cleanly reinstall Firefox and see if the restore/save options are now available to you.

Before you do this though what happens when you select Ctrl+shift+O when in Firefox...??  anything at all or nothing...?

> and in the Windows version the bookmarks have the import/export

Yes and we all have it in Ubuntu too.

---

### Post by loseby on 2012-05-06
actually I have Ubuntu 12.04 on 2 seperate machines and they are both the only o/s on these pc's

both have the exact same problem with backup and restore, I have used this backup and restore for a while and know where it is located yet on both Ubuntu installs its not there

 it doesnt really matter anymore and in a way its good ...have cleaned out a lot of junk from my bookmarks by adding them as I go   :-)


BUT still am very curious to why its only happening with my installations....1 x usb stick and the other by dvd

and I am not going to delete or restore firefox as I have already started getting what I needed

btw: how do you do a screen capture ?   would love to do one and post the pics

note: I did select encrypt my home folder when I was installing

---

### Post by buzzingrobot on 2012-05-06
In Firefox 12.0 on Ubuntu 12.04, the bookmark import/export function is here:

Bookmarks --> Show All Bookmarks --> Import and Backup

---

### Post by sammiev on 2012-05-06
> **buzzingrobot said:**
> In Firefox 12.0 on Ubuntu 12.04, the bookmark import/export function is here:

Bookmarks --> Show All Bookmarks --> Import and Backup

Yes that is all that is required. :) +!

---

### Post by loseby on 2012-05-07
Well am looking at it on another PC ( am on the windows PC here ) and notice that it is also missing the following

Organize  

Views


as well as the "Import and Backup"

it as the 2 arrows and the search bookmarks but the rest aint there

---

### Post by alphacrucis2 on 2012-05-07
> **losbey said:**
> Well am looking at it on another PC ( am on the windows PC here ) and notice that it is also missing the following

Organize  

Views


as well as the "Import and Backup"

it as the 2 arrows and the search bookmarks but the rest aint there

In Ubuntu 12.04 the bookmarks menu with the Import and backup on the global menu are at the top of the screen. You have to mouse over the top bar to make the menu appear.

---

### Post by loseby on 2012-05-07
SOLVED


yes..... have found it but in a slightly different place

when you select bookmarks . show all bookmarks it opens the libary window which in windows shows the "organise/views/Import and Backup" options but not in this version

Now on the top bar on the screen it shows firefox web browser on the left and on the rightyour date time mail music icons

BUT  .... I just found that if I push the mouse onto that line it then just shows the following

Firefox Organize Views Import and Backup on the left with the date/music/etc etc on the right

Is that how you view it ?

---

### Post by alphacrucis2 on 2012-05-07
> **losbey said:**
> SOLVED


yes..... have found it but in a slightly different place

when you select bookmarks . show all bookmarks it opens the libary window which in windows shows the "organise/views/Import and Backup" options but not in this version

Now on the top bar on the screen it shows firefox web browser on the left and on the rightyour date time mail music icons

BUT  .... I just found that if I push the mouse onto that line it then just shows the following

Firefox Organize Views Import and Backup on the left with the date/music/etc etc on the right

Is that how you view it ?


Yes. A disappearing global menu is poor design IMO. You are at least the second person to have this problem. Most people would not guess that the option you are looking for is available in the hidden global menu.

---

### Post by coldjeanz on 2012-05-07
Took me like 2 seconds to realize right away he was having trouble bc he couldn't find the menu. 

MAKE THE GLOBAL MENU PERMANENT!!!

---

### Post by loseby on 2012-05-07
> **coldjeanz said:**
> Took me like 2 seconds to realize right away he was having trouble bc he couldn't find the menu. 

MAKE THE GLOBAL MENU PERMANENT!!!

well its a pity I didnt have your input earlier

I am only a now and then fiddler with Ubuntu and really only use it for Banking..... now I am going to use it as my primary system

anyway..... GLOBAL MENU  ?   is that a firefox or ubuntu thing ?

---

### Post by coldjeanz on 2012-05-07
It's a Unity thing which is the desktop environment you are currently using within Ubuntu 12.04

---

### Post by robert shearer on 2012-05-07
@losbey,
So when asked several posts earlier....

> what happens when you select Ctrl+shift+O when in Firefox...?? 

Did you even try that...?
Because that would have opened the library window with the save/restore options **even if you couldn't find the global menu **and would have given feedback on just what was happening.

Glad you finally found it, though following the advice given and reporting the results is your way to assist the community in improving your Ubuntu experience.  ;)

---

### Post by loseby on 2012-05-08
> **robert shearer said:**
> @losbey,
So when asked several posts earlier....



Did you even try that...?
Because that would have opened the library window with the save/restore options **even if you couldn't find the global menu **and would have given feedback on just what was happening.

Glad you finally found it, though following the advice given and reporting the results is your way to assist the community in improving your Ubuntu experience.  ;)

yes ... I tried ctrl..shift..O and it opened the window but the save/restore option wasnt there

and as this was a clean install and no options were tweaked and not knowing anything about the "global menu" I felt that I was under attack as distinct from been helped

In the past I have had brief play arounds with Ubuntubut this time I have decided to have Ubuntu as my main system and use Windows for basically playing games

---

### Post by robert shearer on 2012-05-08
OK, if you are having trouble with the Global Menu integration for Firefox then perhaps it would be advantageous to disable it and see if that works for you.
It is very simple and can be re-enabled easily at any time.

go...Firefox (then run the mouse pointer to the top left of the screen to reveal the global menu) 
then>Tools>Add-ons and disable the 'Global Menu bar integration' and restart Firefox.

You should now have the full menu bar showing within the current Firefox window.

---

### Post by loseby on 2012-05-09
I have disabled it and now everything is where I like it to be

thankyou

---

