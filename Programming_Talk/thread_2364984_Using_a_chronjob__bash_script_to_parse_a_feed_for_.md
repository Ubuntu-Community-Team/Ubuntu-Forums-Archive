---
title: "Using a chronjob / bash script to parse a feed for keywords"
date: 2017-06-30
forum: Programming Talk
---

### Post by steve234 on 2017-06-30
Evening all,

I'm a Linux NooB and want to up my game. Did a bit of work on page-scraping back in the day (10+ years ago) and want to implement something similar on my local machine for gaming.

I am on Dicord / reddit groups for gaming, but often the info on there is spam-tastic and feeds / custom notifications are non-existent.

I want my local machine to be able to ping my Android phone (via remote notifier, or emial / whatever) when certain events happen. These events will have keywords.

Am I right in thinking I can:

(1) logon to a Discord channel / subreddit / FB stream with bash (using the wget session-cookies method); and 

(2) every X minutes (via chronjob) parse the stream using grep or similar to isolate keywords and fire off a notification if something interesting is happening?

---

### Post by TheFu on 2017-06-30
There is much more useless javascript these days that get in the way of sucking down forum-like things.
There is a project called Sovereign on github that has a huge list of things you can self-host.  One of those is called Wallabag. It is like "Read-it-later." I don't use those sites you mention, but it works for most normal websites.

There are some other interesting projects in that list.

Sovereign is a deployment tool designed to leverage Ansible to deploy a bunch of self-hosted stuff. It isn't good at maintaining those projects or upgrades to newer releases, however.  That makes it a show-stopper for me.

---

### Post by steve234 on 2017-08-02
Thanks @TheFU, I am hoping to overcome the js issue by using lxml or similar in a pyton script to parse the disord channels / web pages I'm interested in.

Currently I am having issues with apt-get (posted separately) so this is on hold.

---

