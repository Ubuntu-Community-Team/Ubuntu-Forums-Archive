---
title: "Hello NC"
date: 2010-04-12
forum: North Carolina Team - US
---

### Post by 98cwitr on 2010-04-12
Just wanted to pop in and say hello. Just moved to Raleigh a few weeks ago. I have started a career with NCDOT as a senior systems analyst and thoroughly love North Carolina compared to middle Georgia. I've been using Ubuntu specifically for over a year now, and six months clean from Windows...thank God no WUA (Windows Users Anonymous) meetings. I deviled in Fedora Core 5 & 6 back in the day, but really gained Linux footing with Ubuntu 8.04. I would really enjoy getting into linux adminstration and development, but other than going to Amazon and dropping $1000 on reading material, I don't know where to get started. Any pointers? My Regards, Brett.

---

### Post by mark_k on 2010-04-22
Welcome to the state!

I certainly can't pass myself off as anything like a real systems administrator, so take this with a grain of salt. I'm a software developer, and learned the most about system-admin stuff by setting up what I thought was a pretty reasonably-functional yet simple development-infrastructure server (even though it was just me, mostly).

I threw together a server with just about the cheapest parts I could find, and set up pretty normal bits - apache, subversion, trac, bugzilla, email (outbound through a simple relay, some local mailboxes). Then did java and jboss, hudson, oracle/mysql/postgresql for a dev environment that wasn't my laptop (obviously, I'm pretending to be a java web developer these days). For a while, I did some dns for internal machines, and then poked a hole through my home router so the internal app could be seen from the interwebs.

Just going through that setup, for what I selfishly wanted in a development environment taught me tons.

Eventually I tired of that server, so moved it to a vmware instance of ubuntu-server. That let me rebuild the box with some more hardware, learn about raid (which I still struggle with) and setting up backuppc and vmware-server.

I just want to stress that nothing I've done here has been terribly difficult to implement, but even just this short list is head and shoulders above what most folks I work with on a daily basis have done. I'm in awe of folks with 'System Administrator' after their name!

I guess I can only suggest what I've done. Be selfish, find a project that will actually help you (backups are a great place to start - it's a good learning experience and is something every home network should have anyway!) and go forth and implement.

This is a good group with helpful folks. If you have questions and this forum goes quiet, try email and the irc channel.

Oh - and congrats on leaving windows behind. It's a good place to be.
Mark

---

