---
title: "can't see Windows shared folders"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by jtx472 on 2008-07-16
When I go to "Network" I can see both of the computers upstairs but cannot access their shared folders.  I installed Samba but don't really know how to use it.  I can't understand what I'm missing.  When I installed Ubuntu last year I had no problem accessing the Windows shared files upstairs.  Thanks for any suggestions.  I'm sure somebody out there has a solution.

---

### Post by NT4usB on 2008-07-16
There really has been a lot written about [configuring samba]("http://www.google.com/search?hl=en&q=site%3Aubuntuforums.com+samba+windows+share&btnG=Google+Search") here.
Read a little, then come back.
First thing comes to mind, did you create a user (your Linux user) on the Windows machines and give them permissions on the Windows machines.

---

### Post by jtx472 on 2008-07-17
Finally figured it out.  Use Connect To Server/Windows Share/then the IP address.  Thats one way.  But the easiest, most convenient way that discovered was to download and use the Samba Browser.  Once I identified the computers upstairs I marked them as favorites.  Now I just open the browser, click Favorites, and have access to the upstairs computers.

---

