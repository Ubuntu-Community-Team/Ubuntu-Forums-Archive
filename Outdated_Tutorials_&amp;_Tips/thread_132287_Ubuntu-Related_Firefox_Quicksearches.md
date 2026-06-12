---
title: "Ubuntu-Related Firefox Quicksearches"
date: 2006-02-18
forum: Outdated Tutorials &amp; Tips
---

### Post by dmartin on 2006-02-18
Firefox, Mozilla, and some other Mozilla-based browsers support something called Quicksearches.  This enables you to do custom searches from the Address bar.  Here's a guide on how to create some Ubuntu-related Quicksearches that I find very helpful.

In Firefox:
Click the Bookmarks dropdown menu, the click Manage Bookmarks.
Click the New Bookmark button.

Input these bookmark settings for an Ubuntu Forums Quicksearch:
```
Name:  
Ubuntu Forums Quicksearch

Location: 
http://ubuntuforums.org/search.php?do=process&query=%s

Keyword: 
ubuntu
```
Hit "Ok" (button)

Now, you can search the Ubuntu forums for "wesnoth" by typing "ubuntu wesnoth" in the Address bar.  Repeat the process for these searches -

Ubuntu Wiki (eg, uwiki wesnoth):
```
Name:
Ubuntu Wiki Quicksearch

Location:
https://wiki.ubuntu.com/?action=fullsearch&context=180&fullsearch=Text&value=%s

Keyword:
uwiki
```

Ubuntu Bugzilla (eg, ubugs wesnoth):
```
Name: 
Ubuntu Bugzilla Search

Location:
https://bugzilla.ubuntu.com/buglist.cgi?bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&bug_status=NEEDINFO&bug_status=UPSTREAM&bug_status=PENDINGUPLOAD&field0-0-0=product&type0-0-0=substring&value0-0-0=%s&field0-0-1=component&type0-0-1=substring&value0-0-1=%s&field0-0-2=short_desc&type0-0-2=substring&value0-0-2=%s&field0-0-3=status_whiteboard&type0-0-3=substring&value0-0-3=%s

Keyword: 
ubugs

```

If you don't like my keywords, you can set them to whatever you would like.  If you have some other Ubuntu-related quicksearches of your own, please share.

---

### Post by citral on 2008-07-10
> **dmartin said:**
> 
```
Name:  
Ubuntu Forums Quicksearch

Location: 
http://ubuntuforums.org/search.php?do=process&query=%s

Keyword: 
ubuntu
```


Do you have a fix for when you search with spaces in between? Firefox correctly %20's them, but the forum doesn't pick it up correctly. try it.

Citral

---

### Post by Mozzer on 2009-04-10
Bump.

> **dmartin said:**
> In Firefox:
Click the Bookmarks dropdown menu, the click Manage Bookmarks.
Click the New Bookmark button.

Input these bookmark settings for an Ubuntu Forums Quicksearch:
```
Name:  
Ubuntu Forums Quicksearch

Location: 
http://ubuntuforums.org/search.php?do=process&query=%s

Keyword: 
ubuntu
```
Hit "Ok" (button)

I'm having problems with this too, it says "Your submission could not be processed because the token has expired." I found this link somewhere else on the forum:

[http://www.ubuntuforums.org/search.php?do=process&showposts=0&quicksearch=1&s=&query=%s](http://www.ubuntuforums.org/search.php?do=process&showposts=0&quicksearch=1&s=&query=%s)

which works better but gives me the %20 problem that citral mentioned. Any ideas?

---

### Post by darthmob on 2009-04-10
rightclick on the search field and select *add a keyword for this search*. multiple search terms work for me that way.

---

### Post by AldenIsZen on 2009-11-20
I did the right click add to keyword, but I get the token expired error if I do it while logged in eventually. (few days?) I tried doing it while logged out, but then it gives me an error to hit the back button and try again if logged in. I would really like to get this fixed.

---

