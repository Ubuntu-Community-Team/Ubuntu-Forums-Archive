---
title: "How to create a web site maintainer user"
date: 2019-05-17
forum: New to Ubuntu
---

### Post by steen-rabol on 2019-05-17
Hi

What is the best / correct way to create a user that can do website maintenance?

I do know how to create a new user, but I do not know what is the best / correct setup of the users permissions or which group the user should be member of. 

The purpose of the user is to do automated deployments and occasional manual updates like 'Composer update' etc.

Thanks in advance

---

### Post by TheFu on 2019-05-17
There is no 1-way, correct way, to do any Unix systems work.  _Best_ is highly subjective as well and would depend on many factors you haven't shared.

On some systems, I just add my normal userid to the web-data group and make certain that group has write permissions where necessary. These are low-risk systems.

On other systems, I use NFS read-only mounts to prevent any local users, including root/sudoers, on them from modifying **any** files at all. These are high-risk systems.

There are a multitude of setups possible, but for medium risk systems available over the internet, I generally keep everything read-only except for the 3 minutes during which updates are being applied. Then I put the directories back into read-only access. 

For automatic deployments, the tool used would matter. We use ansible and it is part of the sudoers, so permissions aren't an issue, except when read-only NFS is used.  Our tasks modify the NFS server first, then do the updates on the NFS client, then both are reset back to read-only as the task completes.

I suspect you are seeking specific advice about php webapps, not webapps in general, yes?  Here, we don't allow php webapps directly on the internet. Our users must be internal network users or using a full VPN. This decision drastically reduces the attackers from the entire world to 50 people, most of which are not computer or network gurus.

---

### Post by steen-rabol on 2019-05-18
> **TheFu said:**
> There is no 1-way, correct way, to do any Unix systems work.  _Best_ is highly subjective as well and would depend on many factors you haven't shared.

Yes, I agree 100% that it is subjective, and I admit that my question could have been formulated better


> **TheFu said:**
> On some systems, I just add my normal userid to the web-data group and make certain that group has write permissions where necessary. These are low-risk systems.

This is more what I am looking for, but my question is then: How do I check / figure out where the write permission is needed?


> **TheFu said:**
> There are a multitude of setups possible, but for medium risk systems available over the internet, I generally keep everything read-only except for the 3 minutes during which updates are being applied. Then I put the directories back into read-only access. 

This would also be fine with me in this case, I simply just don't know what i need to do e.g. should I chmod 777 for a few minutes and then back to xxxx (xxxx is the part that I do not know how to figure out)


> **TheFu said:**
> For automatic deployments, the tool used would matter. We use ansible and it is part of the sudoers, so permissions aren't an issue, except when read-only NFS is used.  Our tasks modify the NFS server first, then do the updates on the NFS client, then both are reset back to read-only as the task completes.
To the best of my knowledge sudo requires that a password is entered, so how can that happen in a automated way?

> **TheFu said:**
> I suspect you are seeking specific advice about php webapps, not webapps in general, yes? 

yes, php developed webapps/sites

I use a package (Laravel-deployer, which is based on deployer.org) to deploy and my hope / goal is to 'configure' 1 user that can be used as the 'deployment' user - i just do not know what permissions to give or which groups the user should be part of (yes, www-data i know)

I think I got off on the 'wrong' foot on the current server as i used sudo a lot, so that means that the files have 'screwed' up file permissions / owner, so that I need to get fixed so I can get to a better place :)

I hope my question makes more sense now

Thanks!

---

### Post by TheFu on 2019-05-18
Every webapp is different. There is no standard.  In theory, the documentation about the webapp should outline what is needed to perform updates.  Most don't provide exact commands, so you'll need to read and understand what they mean. Each part/tool should have some documentation for an upgrade process. Start with the webapp files, see what it says. If it isn't clear, move onto each tool/library involved. The docs for them might be better.

NEVER use chmod 777.  That is for people who don't understand permissions. 775 should be the least restrictive.  Running a web server means you need to understand file and directory permissions.  The correct directory permissions are the most restrictive that still work. That's the answer. It is common for only 1 directory to need write permissions by the userid running the process. If all the data is stored in a DBMS, then only the log files might need write permissions.  As a server admin, a complete understanding of multi-user environments and permissions is mandatory.  

Also, probably best to not assume anyone else uses the same webapp, unless it is really, really, popular.  Then 20% might.  For example, I know next to nothing about wordpress.  We don't use it. Wouldn't know how to upgrade it safely and based on what I've read about their update process, I'm not impressed.

So, hopefully, someone else here will read your last post, see which tools you are using, and respond with a link to the documentation.

sudo doesn't always require a password. There are settings to allow specific userids to run specific commands with specific options.  If you are an admin, this is basic, required, knowledge.

Perhaps making the title "Trying to update A, B, C php webapp"  where A, B, C lists to main tools involved would get more eyes?  People skim the titles to decide if they can help or not.  If you put "How-to", then people will think YOU are writing a tutorial. I maintain about 30 websites and had some time. That's the only reason I posted. Sorry I'm no help. Good luck.

---

