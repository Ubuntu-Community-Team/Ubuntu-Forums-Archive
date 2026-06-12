---
title: "How to get bookmarkers from Firefox"
date: 2011-12-20
forum: New to Ubuntu
---

### Post by BeMyManikin on 2011-12-20
I switched to ubuntu, and I have a dual op with it and windows. I now can't log into windows, and I was wondering if there was any way of getting those bookmarks? I believe it was Firefox 3.6

---

### Post by Momof9Blessings on 2011-12-21
I went into windows today and exported as a html file....

With the browser maxamized, click on "bookmarks", click "show all bookmarks".

At the top, click Import and Backup.... you might try import from another browser???

---

### Post by drmrgd on 2011-12-21
Can you access your Windows partition from Ubuntu?  Also, what version of Windows are you running?

If you can access your Windows partition, then you'll need to search for your profiles folder for Firefox.  For me, on Windows 7 at work, my profile folder is located:

```
C:\Users\drmrgd\AppData\Roaming\Mozilla\Firefox\Profiles
```

On Windows XP it's similar, but I can't quite remember the path to a users application data.  I think it's something like:

```
C:\Documents and Settings\<username>\Application Data\Mozilla\Firefox\Profiles\
```

Once you've found your profile folder, you can either copy the whole thing to your Ubuntu partition, or just get one of the bookmark backups and import that in.  The advantage of the whole profile is that you'll also have your saved browsing history and settings and such.  

Hope it helps!

---

### Post by BeMyManikin on 2011-12-22
> **drmrgd said:**
> 

```
C:\Documents and Settings\<username>\Application Data\Mozilla\Firefox\Profiles\
```Once you've found your profile folder, you can either copy the whole thing to your Ubuntu partition, or just get one of the bookmark backups and import that in.  The advantage of the whole profile is that you'll also have your saved browsing history and settings and such.  

Hope it helps!
THIS WAS IT! THANK YOU!!!!! I've been trying to get these since I moved to ubuntu, I forgot about the application data and was looking directly into Mozilla Firefox. At least I can learn from this experience.

---

### Post by drmrgd on 2011-12-22
My pleasure!  Glad I could help.

---

