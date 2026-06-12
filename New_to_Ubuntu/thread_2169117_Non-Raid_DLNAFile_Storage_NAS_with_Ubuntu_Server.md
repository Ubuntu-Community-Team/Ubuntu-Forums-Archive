---
title: "Non-Raid DLNA/File Storage NAS with Ubuntu Server"
date: 2013-08-20
forum: New to Ubuntu
---

### Post by Joshua_Griffing on 2013-08-20
I know there are a million posts out there for creating a NAS from Ubuntu server but I believe each question is a little different.  I have a few question's to ask in this one post so bare with me as I explain my wants and see if anyone can help.  I am very tech savvy, just when it comes to linux I am completely out of the loop.  I know the basics of networking but it has been almost ten years sense I actually did any networking so I'm a little rusty. 

[INDENT]1. I am wanting to create a NAS with DLNA share capability for movies and music, which will be on two separate 3TB drives.   Here in lies the first question, is there a way to setup Ubuntu server as a NAS with out setting up RAID? 

2. The NAS is also going to house 4 - 500GB drives for the 4 computers in the house to backup data to and take with them if they ever move out or there internal drive crashes.  How do I setup passwords for each of these 4 drives so only the user can access it?  My mother does taxes and would like a safe place to backup the tax forms so no one can see the personal information on said files.  I know RAID is the best setup for any type of NAS but with a few of the people in the house leaving in the next few years I wanted them to be able to grab there drive out of the setup and plug it into there tower or and external enclosure without have to wipe it and start all over.

[/INDENT]
[INDENT]3. I am going to be attaching this to a pfsense DIY router through gigabit ethernet, is there anything special I will have to program into the pfsense box to allow for the traffic that the NAS may receive?[/INDENT]

If any of this is possible please let me know a few options I can try to research and learn before I dive into this.  I am really just looking for information more so than coding help. I can pickup on coding without any problem, its just trying to find the information out there is like finding a needle in a hay stack, everyone wants to use raid and freenas.   Thank you ahead of time for the support and any help you can give on this matter would be greatly appreciated.

---

### Post by lukeiamyourfather on 2013-08-20
> **Joshua_Griffing said:**
> 
1. I am wanting to create a NAS with DLNA share capability for movies and music, which will be on two separate 3TB drives.   Here in lies the first question, is there a way to setup Ubuntu server as a NAS with out setting up RAID? 

Yes, install Ubuntu on one of the drives and then simply mount the second drive wherever you want (like /data or /movies). RAID is completely optional just like it is with any other system install, for example Windows.

> **Joshua_Griffing said:**
> 
2. The NAS is also going to house 4 - 500GB drives for the 4 computers in the house to backup data to and take with them if they ever move out or there internal drive crashes.  How do I setup passwords for each of these 4 drives so only the user can access it?  My mother does taxes and would like a safe place to backup the tax forms so no one can see the personal information on said files.  I know RAID is the best setup for any type of NAS but with a few of the people in the house leaving in the next few years I wanted them to be able to grab there drive out of the setup and plug it into there tower or and external enclosure without have to wipe it and start all over.

Each user can have an account setup on the server and then set the ownership for the directories to their respective user. Permissions can be set so other users can't read the files if desired. When setting up the network shares with Samba (or whatever) don't allow guest access.

> **Joshua_Griffing said:**
> 
3. I am going to be attaching this to a pfsense DIY router through gigabit ethernet, is there anything special I will have to program into the pfsense box to allow for the traffic that the NAS may receive?

Not sure, if it's like any other router it won't matter for local traffic. If you want the server to be accessible outside of the local network that's another story. You might reconsider NAS4Free because it can do everything you want and would be easier to setup.

---

### Post by Joshua_Griffing on 2013-08-20
Thank you for your quick reply to my questions.  I have a few more to add this this now that you have given me some information on the task.

1. Would installing the server OS on a 16gb thumb stick work for this type of setup or would I be better off using a smaller hd or ssd?
2. With setting up the separate user account's, will they be able to access the drive from there Windows system with a user name and password to transfer there backup's/saves? And would using NFS be better than Samba or is Samba the best option for network share?
Final one for now.
3. Would I be better off using mediatomb or ps3mediaserver for the dlna to access the movies/music on the ps3/xbox360?

---

### Post by lukeiamyourfather on 2013-08-21
> **Joshua_Griffing said:**
> 
1. Would installing the server OS on a 16gb thumb stick work for this type of setup or would I be better off using a smaller hd or ssd?

If you're using something like NAS4Free that's meant to run from a USB flash drive it would work just fine. Ubuntu would technically work but I would be reluctant to run it all the time from a USB flash drive because it's bigger, updates more frequently, and generally is more of a pig than small dedicated appliance platforms.

> **Joshua_Griffing said:**
> 
2. With setting up the separate user account's, will they be able to access the drive from there Windows system with a user name and password to transfer there backup's/saves? And would using NFS be better than Samba or is Samba the best option for network share?

As far as I know NFS doesn't offer per user authentication for shares, so if you want each user to have to enter a password for accessing the share go with Samba. Also some platforms don't have native support for NFS (like Windows).

> **Joshua_Griffing said:**
> 
3. Would I be better off using mediatomb or ps3mediaserver for the dlna to access the movies/music on the ps3/xbox360?

There are a lot of options but I'm not familiar with any of them, that might take some trial and error to see what you like or what works best for you.

---

### Post by gordintoronto on 2013-08-21
One thing to consider: Ubuntu Desktop can do everything Ubuntu Server can do -- and it has a bunch of GUI tools which will simplify your life. Performance is not as wonderful, but nothing you said indicates that you need a high-volume server.

---

