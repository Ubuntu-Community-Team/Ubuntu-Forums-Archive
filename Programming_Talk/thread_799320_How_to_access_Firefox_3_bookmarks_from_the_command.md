---
title: "How to access Firefox 3 bookmarks from the command line?"
date: 2008-05-18
forum: Programming Talk
---

### Post by Yuzem on 2008-05-18
On the firefox forums someone told me to use sqlite but it doesn't work.

It tells me that the database is locked:
Error: database is locked
If I close firefox it tells me:
Unable to open database ".mozilla/firefox/adnu2zvf.default/places.sqlite": file is encrypted or is not a database

Here it is the post on mozillazine:
[http://forums.mozillazine.org/viewtopic.php?t=655853](http://forums.mozillazine.org/viewtopic.php?t=655853)

---

### Post by aysiu on 2008-05-19
In answer to your thread title question: ```
nano -B ~/.mozilla/firefox/adnu2zvf.default/bookmarks.html
``` should do it.

What might solve the post problem is: ```
mv ~/.mozilla ~/.mozilla.old
firefox &
```

---

### Post by Yuzem on 2008-05-19
> **aysiu said:**
> In answer to your thread title question: ```
nano -B ~/.mozilla/firefox/adnu2zvf.default/bookmarks.html
``` should do it.
That is the old bookmark file. I need to access the new bookmarks: places.sqlite (firefox 3)

> **aysiu said:**
> 
What might solve the post problem is: ```
mv ~/.mozilla ~/.mozilla.old
firefox &
```
If I do that I will lose all my bookmarks, extensions and settings and what would be the effect?

---

### Post by Yuzem on 2008-05-20
aysiu: Could you move this thread to the [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39") sub forum or I should ask again there?

What I really want to know is how to access firefox3 bookmarks form bash to add support for them to [avatar-factory]("http://www.gnomefiles.org/app.php/Avatar_Factory").

I realize that the Programming Talk sub forum is a better place for this question.

Thanks.

---

### Post by Can+~ on 2008-05-20
Having the command line interface of sqlite3 (sqlite3 package on synaptic)

```
sqlite3 places.sqlite
```

```
sqlite> .databases
seq  name             file                                                      
----------------------------------------------------------
0    main             /home/canxp/places.sqlite    
```

```
sqlite> .tables
moz_anno_attributes  moz_favicons         moz_keywords       
moz_annos            moz_historyvisits    moz_places         
moz_bookmarks        moz_inputhistory   
moz_bookmarks_roots  moz_items_annos    
```

> sqlite> SELECT * FROM moz_bookmarks

That last one produces a huge output.

Use the sqlite3 module of python, or the one on C, if you need to do something else with this data.

I made a copy of the file on my home folder by the way. Most probably, the error you get is that you're trying to open the database while firefox has a lock on it.

*edit*
Also, there's a little trick with firefox, you can make another account for your testing, open firefox with:

```
firefox-3.0 -ProfileManager
```

That will let you create new profiles (that are stored in the .mozilla folder), with that you can test without screwing with important data.

---

### Post by Yuzem on 2008-05-20
Thanks, that worked but I still can't access the database if firefox is running:
```
Error: database is locked
```
If a copy places.sqlite to temp dir I still get an error:
```
Unable to open database "places.sqlite": file is encrypted or is not a database
```

I don't need to do any advanced thing. I just need to parse all the bookmarks to manipulate them with bash.

Is there a simple command to export the bookmarks to a text format that can be accessed with cat, grep, sed etc...?

---

### Post by nofrak on 2008-05-28
The bookmarks.html file is generated from the places database, so if all you need is to read in the files and parse them that should do it.  Otherwise you'll have to go through sqlite3. The database locks when you're using firefox so that firefox can be sure it's stable.

---

### Post by Zugzwang on 2008-05-28
> **Yuzem said:**
> If a copy places.sqlite to temp dir I still get an error:
```
Unable to open database "places.sqlite": file is encrypted or is not a database
```


Did you close firefox before trying that? I'm asking because it worked for Can+~. The file itself might be in an unreadable state before the database is closed.

---

### Post by Yuzem on 2008-05-28
But the bookmarks.html file is not updated by firefox.
It gets imported the first time that firefox 3 is executed but when changes are made to the bookmarks it doesn't get updated.

Edit: No, I didn't close firefox. I want to access the bookmarks even if firefox is running like in previous versions.

---

### Post by mssever on 2008-05-28
SQLite3 doesn't permit simultaneous connections. Only one process can have an sqlite database open at a time. So unless you can convince Firefox to close its database (perhaps via an extension?), you can't do what you want.

---

### Post by ace007 on 2008-08-09
The solution is here...

enter "about:config" in firefix 3.0 address bar. Find the settings "browser.bookmarks.autoExportHTML" double click it to change the boolean entry to "true".  Now when you shut down Firefox a new bookmarks.html with your updated bookmarks will be created in your firefox profile folder.

---

### Post by Yuzem on 2008-08-09
Thanks that works.

I would still prefer to be able to access the bookmarks without having to shutdown firefox or ask the user to set a custom option.
That is from the point of view of someone making an application that needs to access the firefox bookmarks.

---

### Post by englandschorsch on 2009-02-18
> **Yuzem said:**
> Thanks that works.

I would still prefer to be able to access the bookmarks without having to shutdown firefox or ask the user to set a custom option.
That is from the point of view of someone making an application that needs to access the firefox bookmarks.

I totally agree. I want to write a krunner plugin under KDE 4 that tries to match firefox bookmarks, because so far only konqueror bookmarks are supported.
Being able to access firefox bookmarks through sqlite would be very helpful.

---

### Post by cszikszoy on 2009-02-18
> **englandschorsch said:**
> I totally agree. I want to write a krunner plugin under KDE 4 that tries to match firefox bookmarks, because so far only konqueror bookmarks are supported.
Being able to access firefox bookmarks through sqlite would be very helpful.

I'm trying to write a GNOME Do plugin that better handles firefox's bookmarks.  Right now we just parse the JSON files in the profile directory, but getting access to places.sqlite would be ideal.

I've also thought about writing a firefox extension that would expose bookmark data to dbus.

---

### Post by Can+~ on 2009-02-18
Whoa, this post is old.

Instead of asking the user to shutdown firefox, why don't you wait that the user closes it, then, silently open the sqlite file, copy the bookmarks and update the gnome-do/krunner db?

---

### Post by englandschorsch on 2009-02-18
> **Can+~ said:**
> Whoa, this post is old.
That's what I thought. ^^

> **Can+~ said:**
> Instead of asking the user to shutdown firefox, why don't you wait that the user closes it, then, silently open the sqlite file, copy the bookmarks and update the gnome-do/krunner db?
Yeah, probably. I'm new to this whole Linux world, so I don't know yet, how krunner really works and whether it has a db at all. I guess it must, because otherwise it wouldn't be so fast.

---

### Post by cszikszoy on 2009-02-18
> **Can+~ said:**
> Whoa, this post is old.

Instead of asking the user to shutdown firefox, why don't you wait that the user closes it, then, silently open the sqlite file, copy the bookmarks and update the gnome-do/krunner db?

That would definitely work, although it's non-ideal.  Do works by creating an "Item Source", in this case, firefox bookmarks are the items.  I would have to create a local (to gnome-do) cache of the bookmarks, and if the user added a new bookmark in firefox these would be out of sync until they restarted firefox.

I've also thought about just making a copy of places.sqlite, reading that, then deleting it, but that db is pretty big (mine is 10 MB with 4-5 bookmarks) and IO gets expensive...

---

### Post by Can+~ on 2009-02-18
> **cszikszoy said:**
> That would definitely work, although it's non-ideal.  Do works by creating an "Item Source", in this case, firefox bookmarks are the items.  I would have to create a local (to gnome-do) cache of the bookmarks, and if the user added a new bookmark in firefox these would be out of sync until they restarted firefox.

I've also thought about just making a copy of places.sqlite, reading that, then deleting it, but that db is pretty big (mine is 10 MB with 4-5 bookmarks) and IO gets expensive...

It not only stores bookmarks, but also history. Mine is 148 KB with 50+ bookmarks but 1 week of history.

---

