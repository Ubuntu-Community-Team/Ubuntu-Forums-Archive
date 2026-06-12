---
title: "Network aware applications (database)"
date: 2011-02-27
forum: Programming Talk
---

### Post by Jacks0n on 2011-02-27
Hi

I'm in the process of developing a desktop based application (Qt), where it will be used in a per office situation. There will be approximately 15 users on average per office. The application is very data centric (HTML reports, contact management, calendars, etc). Some of the data is unique to the whole office, where other data is unique per user. There may be multiple instances of an application per user, and the user may be at a different physical location.

The data will often be modified, added, deleted, etc. Do you know of any "easy" option to sync this in real time? I've looked into using some of the new "cloud" databases like MongoDB and CouchDB, but I don't know if you can easily merge/sync data with them. And there's always the tried and tested MySQL. I'm guessing some sort of middle-ware would have to be developed, where all application instances would have persistent connection open to it. And there's also the issue of polling the server, versus keeping a persistent socket open (Is this scalable? Max there will be 10k offices).

Does anyone have any ideas? Surely there must be some framework which deals with this. I couldn't find much on it... Thanks!

---

