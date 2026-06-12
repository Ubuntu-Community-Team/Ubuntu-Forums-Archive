---
title: "Continuously running processes?"
date: 2010-10-18
forum: Programming Talk
---

### Post by SRabin on 2010-10-18
I need to poll a set of servers for data continuously, and I thought the best way to do that would be to have a constantly running process that cycles through the servers. I don't want to poll each server too frequently, so monitoring each one independently is out of the question. However, having too much of a delay between requests might cause me to miss some data I want, so the ideal solution would be able to run in multiple threads concurrently. The servers to poll are stored in a MySQL database and sortable by a last_checked timestamp.

First, is my approach here a good choice? Second, how would I go about doing this? I thought about a cron job that started every 5 minutes, but I'm afraid the overlap would eventually lead to a cascade failure.

-S

---

