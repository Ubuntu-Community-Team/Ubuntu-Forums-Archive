---
title: "Ubuntu Phone developing"
date: 2013-01-07
forum: Programming Talk
---

### Post by marin123 on 2013-01-07
Hello!

I started developing an app for Ubuntu Phone.

I have a few questions about the app, if anyone knows.

What is the best way to persist data? Sqlite?

How will 2 layouts be implemented (mobile & desktop layout)? Will I write 2 separate QML files?

Is there any news about the SDK? Will they write GPS class that I will be able to use?

Thanks! :)

---

### Post by pompel9 on 2013-01-07
The only ones that know is canonical. I would advise you to contact them.

---

### Post by AstroLlama on 2013-01-07
it's all uncharted territory, my friend. you are blazing new trails.

---

### Post by marin123 on 2013-01-07
Well, I hope to put my flag somewhere in that uncharted territory :)

I have already left my details to Canonical, now I'm waiting for them to share the SDK.

---

### Post by marin123 on 2013-01-10
I made some progress and wanted to share if anyone can make a use of it.

For persisting data, you can use sqlite (no need to install on your computer) by using LocalStorage.openDatabaseSync() function. The DB file is in /home/user/.local/share/Nokia/QtQmlViewer/QML/OfflineStorage/Databases/ directory. You can view it with sqlitebrowser.

You can get the GPS data with QtLocation.coordinates() method. Right now, I don't know will this be the way of getting GPS data or it will be implemented somehow else.
I'm waiting to install Ubuntu on my phone to try it out.

---

### Post by haqking on 2013-01-10
[http://developer.ubuntu.com/get-started/gomobile/](http://developer.ubuntu.com/get-started/gomobile/)

---

