---
title: "Firefox 2 not working"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by kanna1620 on 2008-05-03
Hi all. I have upgraded my Ubuntu box from 7.10 to 8.04. Its cool. But in the new version of Ubuntu, default firefox is the firefox3 beta 5, but not firefox 2. If I open the firefox-2 also, it is opening the firefox-3 beta 5. I made the **/usr/bin/firefox** to point to the **/usr/lib/firefox/firefox-2.** But still firefox-2 is not opening. All the web pages are being opened by the firefox 3 beta 5 only. How can I make the default web browser to firefox 2? Any help would be appreciated.

---

### Post by arthritisankle on 2008-05-03
I have a question similar to this.  I have newly installed linux for the first time and I would like to switch to firefox 2.  I added firefox 2 with the ADD/REMOVE APPLICATIONS app, but it will not allow me to remove "Firefox".  It says I have to use the Synaptic Package Manager, but there are so many "firefox" packages as well as "mozilla-firefox" packages, and I don't want to remove something that could mess things up.  Are there any that I should worry about removing.  I'd like to keep my preferences, passwords, add-ons and such.

Any help would be appreciated.  As you can probably tell by the question, I am very new to ubuntu.  I appreciate your patience.

---

### Post by kanna1620 on 2008-05-03
> **arthritisankle said:**
> I have a question similar to this.  I have newly installed linux for the first time and I would like to switch to firefox 2.  I added firefox 2 with the ADD/REMOVE APPLICATIONS app, but it will not allow me to remove "Firefox".  It says I have to use the Synaptic Package Manager, but there are so many "firefox" packages as well as "mozilla-firefox" packages, and I don't want to remove something that could mess things up.  Are there any that I should worry about removing.  I'd like to keep my preferences, passwords, add-ons and such.

Any help would be appreciated.  As you can probably tell by the question, I am very new to ubuntu.  I appreciate your patience.

Hey dont worry about all those packages which are related to firefox. You can go with the Synaptic Package Manager and un-install it from there.You will face no problem. And regarding bookmarks and password: all the bookmarks can be exported to an html file from the firefox. And the passwords are stored in ~/.firefox folder. You can save that file.

---

### Post by asgard_command on 2008-05-03
I removed Firefox 3 and replaced it with 2 using synaptic. I also had to delete the profile which is the ~/.mozilla file otherwise Firefox 2 didn't work right with it's extensions.
Removing the profile does mean you have to start with a totally fresh install so it is worth saving your bookmarks at least if nothing else.

---

### Post by FredB on 2008-05-03
For firefox 2 die-hard : firefox 3.0rc is going to be released soon and extension coders will upgrade their code.

Smell like coffin for firefox-2 ? My source ? Blockers bug for Firefox 3.0rc1 release :

[http://ffextensionguru.wordpress.com/2008/04/28/weekly-update-2008-04-28/](http://ffextensionguru.wordpress.com/2008/04/28/weekly-update-2008-04-28/)

and Bug list :

[http://tinyurl.com/2ubyvm](http://tinyurl.com/2ubyvm)

6 remaining for now... ;)

---

### Post by arthritisankle on 2008-05-03
I was able to remove firefox 3 and install firefox 2 easily enough, but it didn't fix my problem.

I was trying to log in to my account on citicards.com and the top half of the page wouldn't show up.  I assumed it had something to do with firefox 3, but it doesn't work with firefox 2 or galeon either.  

I would appreciate any suggestions.  I really like ubuntu so far and I'd hate to have to switch back to windows.  Thanks

---

