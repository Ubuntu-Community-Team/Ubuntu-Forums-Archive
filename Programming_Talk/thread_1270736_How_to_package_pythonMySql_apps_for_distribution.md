---
title: "How to package python/MySql apps for distribution"
date: 2009-09-20
forum: Programming Talk
---

### Post by aaronp on 2009-09-20
Hi all,

I'm currently developing an application using python and it utilises a mysql database via mySqlDb. It works on my machine for testing with no issues, of course because I've configured it to do so and I have all the rights to do anything I need to.

I'm wondering, if I decide to package it for other people to use, how do I go about getting the mysql setup right when someone runs/installs the app?

e.g.
1. What if they don't have MySQL on their PC?
2. Even if they do have MySQL, how will my app be able to create databases without privileges to the existing mysql database?
3. If I they do allow a database to be created, won't they just be able to 'play' with the database via the backend/MySQL interface and then corrupt it so the program won't work properly?

I have this 'assumed' idea in my head that you package the app with it's own fresh copy of MySql and then install it, create privileges, db, tables etc. at the time of installation, and then the DB is completely quarantined from the broader system - not sure if this is realistic or not though??

Can anyone explain how it works, or point me to some resources?

thanks
Aaron

---

### Post by geirha on 2009-09-20
Packaging mysql along with your app is not the way to go, it's not the way to do it in linux at least. You should rather provide documents that explain what needs to be done to get your app running. Another thing you can do is to add support for [sqlite](http://en.wikipedia.org/wiki/Sqlite), which won't require the user to install anything extra. Amarok has done it this way, install it and see how it does it.

---

### Post by aaronp on 2009-09-20
Thanks for that, I'll check out SQLite. I take it there is a different python library to use this?

So, assuming I stick with mysql do I just document that mysql is a dependency and then maybe as part of the install/setup process they are asked to provide their mysql password in order to give the app the right privileges to create a database and use it gonig forward?

---

### Post by slavik on 2009-09-20
create a 'wizard' that would ask the user relevant info and ask them the name of db or if they would like one created.

I tend to specify what db to use and create an account just for the app which is limited to that db.

---

### Post by aaronp on 2009-09-20
> **slavik said:**
> create a 'wizard' that would ask the user relevant info and ask them the name of db or if they would like one created.

I tend to specify what db to use and create an account just for the app which is limited to that db.

great thanks, that's what i was thinking.

my only concern was them being able to get into the db i created via the root account but now that i think of it - who cares? it is really their data and if they want to stop their app from working by corrupting it's database then power to them (they'll probably just fix all my bugs anyway!!)

thanks
Aaron

---

### Post by sunchiqua on 2009-09-20
> **aaronp said:**
> great thanks, that's what i was thinking.

my only concern was them being able to get into the db i created via the root account but now that i think of it - who cares? it is really their data and if they want to stop their app from working by corrupting it's database then power to them ([COLOR=Red]**they'll probably just fix all my bugs anyway!!**[/COLOR])

thanks
Aaron

:lolflag:

---

