---
title: "how to delete all firefox favorites in ubuntu"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by ulindel on 2008-08-31
On importing favorites it said "...overide existing?....", but obviously did not so favourites are triplicated, how can I delete ALL AT ONCE before I import them again?
thanx,           nick

---

### Post by jolx on 2008-08-31
well you should delete anything to do with bookmarks in ~/.mozilla/firefox/*wateva*.default

---

### Post by wolfen69 on 2008-08-31
go to home folder>ctrl+h>look for .mozilla folder>firefox>something.default>and delete bookmarks.html

---

### Post by lovinglinux on 2008-08-31
Install [Bookmark Duplicate Detector]("https://addons.mozilla.org/en-US/firefox/addon/1553") extension, restart Firefox then click Bookmark > Search for duplicates.

---

### Post by ulindel on 2008-08-31
went:- home folder>ctrl+h>look for .mozilla folder>firefox>something.default>and delete bookmarks.html 
& deleted favourites.default
But all are still there.

I got Bookmark Duplicate Detector but deletes nothing, just saves them where it wants??

Where do I go wrong?

---

### Post by lovinglinux on 2008-08-31
> **ulindel said:**
> went:- home folder>ctrl+h>look for .mozilla folder>firefox>something.default>and delete bookmarks.html 
& deleted favourites.default
But all are still there.

I got Bookmark Duplicate Detector but deletes nothing, just saves them where it wants??

Where do I go wrong?

When you open Duplicate Bookmark Detector you should see something like this:

[[IMG]http://img401.imageshack.us/img401/5044/screenshotee0.th.png[/IMG]](http://img401.imageshack.us/my.php?image=screenshotee0.png)

In the top of the window you see the list of duplicated bookmarks. The number for each bookmark is the number of copies. Select one of them and all places were you can find copies will be listed in the bottom of the window. Then select the copies you want to remove and click "Remove". A pop up like the one showing in the middle of the image above will appear asking for confirmation. Just click OK and the copy will be deleted.

---

### Post by ulindel on 2008-08-31
unfortunately the "Remove" bit is missing here.

---

### Post by ulindel on 2008-08-31
AHaaaaaa.... found the remove hiding at the bottom by changing screen resolution.

But is ridigulously slow as I ended up with 5600 favourites, 4900 dublicates.

Surely must be something wrong with my installation & another way to get rid of these.

---

