---
title: "How to easily keep data safe forever"
date: 2008-11-09
forum: Outdated Tutorials &amp; Tips
---

### Post by curvedinfinity on 2008-11-09
**The Problem**

Over the past number of years, I've developed quite a collection of digital photos. I've already had the experience of losing some of my photos when a computer died, or simply by throwing a storage device out that I didn't think to check through.

I imagine myself 20 years down the road, and I sincerely hope all of my personal memorabilia still exists. I have spent time researching different backup options and data backup policy, and have found an elegant solution.

**The Solution**

Solving the problem of data loss is complex because any static storage format deteriorates over time and the risk of damage in storage is ever present, especially in terms of storing things for decades at a time. That's why the best solution is to store data in a dynamic media, one that regenerates itself over time.

An array of redundant hard drives (RAID 1) is exactly what the doctor ordered. As one disks fails every few years, it can be replaced with a new one. The risk of data loss due to media failure is therefore reduced to only when all of the redundant drives fail at the same time. In terms of even a redundant array of two drives, the average failure time is in the hundreds of years.

However, RAID 1 does not account for the issue of damage. Every time a computer is moved, there is the chance that it will be dropped, banged, doused with water, or any number of other catastrophes.

Enter shared hosting. Shared hosting services (usually used for websites) use redundant arrays of disks housed in nice safe facilities which have redundant power and air conditioning, are earthquake proof, and have staff always present ready to fix stuff when it breaks. In other words, they will take much better care of your data than you could ever hope to. To top it off, these services are way cheaper than buying a computer to use as a data server.

The icing on the cake is that Ubuntu has way better networking support than Windows or Mac. The built-in file browser, nautilus, has a virtual filesystem that supports FTP and SFTP, meaning you can open your remote server as if it were just another directory on your computer.

**The Howto**
[LIST=1]
[*]The majority of the task of creating a remote data server will actually just be in picking out which company's service you would like to use. I'll go out on a limb and recommend [Dreamhost]("http://www.dreamhost.com"). Dreamhost costs about $10/mo, has plenty of space and bandwidth, uses Debian, and has excellent support.
[*]After you sign up with the host, you will probably have picked a domain with your purchase, a username, and a password. If you didn't get a domain, you will have been given an IP address instead. If you don't know what's what, just look for your host's instructions for setting up FTP with them (different hosts often have different systems).
[*]In Ubuntu, navigate to Places->Connect to Server
[*]Select SSH for the Service type
[*]Enter the domain or IP address of your server in the Server field
[*]Leave port and folder empty
[*]Enter the username you chose when registering for your host in the User Name field.
[*]Press Connect
[*]A password dialog will pop up, and enter your password. If your Ubuntu user account isn't used by anyone else, its secure to use the "Remember always" function.
[*]You should now be at the root folder of your host. Navigate to your user's directory, which is in /home.
[*]On Dreamhost, your website's directory will now be visible. However, we just want to store data, not publish it to the world.
[*]Make a new directory in this folder called  "Archive".
[*]Go into Archive
[*]Now click Bookmarks->Add Bookmark
[/LIST]

Your remote data server will now be accessible in Places, so in one click you can open your backup archive. You can drag and drop all of the files you want to your archive, where they will be safe, secure, and last for as long as your host doesn't go out of business. Its like heaven for data.

---

### Post by hvollebregt on 2009-05-25
Thanks a lot for this useful tutorial. You triggered me in this idea of using my hosting provider for this.. I will certainly try it!

---

