---
title: "Assistance with creating a small business network"
date: 2013-11-29
forum: New to Ubuntu
---

### Post by lee.moreau on 2013-11-29
Hey everyone, not sure if this is an absolute beginner question as I've used Linux lots before but always CentOS etc.  Just confused if I need Ubuntu Server to do this or how I'd set this up as I couldn't find anything in the Server manual.  I don't want to use Windows since I think I need Windows server for what I want, but it's not that critical I have it set up this way, so if I can't do this with Linux I'd just use Windows 7.

- We are a small business, and previously my reps used laptops which always caused problems as they would take them home and install stuff on them, or they would spill coffee in them, and so I decided for all new reps I just want desktops.

- To start and for the next year or two at least, there will be 2-3 desktop computers that my part time reps will use.  I already have these, they are Core i5, 300GB hard drive, 4GB ram etc, so hardware wise they are good and I don't need them to be thin clients or anything.

- My main requirement, is that I'd prefer to not have a dedicated computer per rep, but instead a desktop that they can log into.  Basically I want a rep to come in, be able to sit down at ANY of the desktops, log into their account, and have their desktop come up with their files, bookmarks, preferences and so on.  I'm not even sure if this is possible unless I make the computer more like a thin client, but I don't want to sacrifice performance just for this ability, as otherwise I'll just assign them computers they have to use.

- In terms of applications and files, literally everything is online, so we use Salesforce, Google Apps, etc so that part is easy.  For files we use Google Drive as our network file server, so they wouldn't even be accessing files on the server unless I move us to using a network share.

So not really sure how I do this or where to look.  Like would all the user accounts be created on Ubuntu Server and then I'd install Ubuntu desktop and log in with those usernames?  Not sure how that would work as I have Ubuntu desktop in a virtual machine right now and the login screen doesn't give any option for connecting as a user that isn't listed on the system.

To do what I want do I basically need to set the clients up as thin clients, or is it better if I just forget the whole server thing and assign a computer to an actual person instead of having them hot desk?  Thanks!

---

### Post by jdeca57 on 2013-11-29
I've never done this, but [https://help.ubuntu.com/lts/serverguide/network-file-system.html](https://help.ubuntu.com/lts/serverguide/network-file-system.html) states 'There is no need for users to have separate home directories on every network machine. Home directories could be set up on the NFS server and made available throughout the network.' So the answer would be to set up an nfs on a server, and make an account for each user on each machine, with an nfs home on the server. They log in from any computer and have exactly the same home directory and personal defaults. But the programs run on their own hardware.

---

