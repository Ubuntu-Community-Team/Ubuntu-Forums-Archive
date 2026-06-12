---
title: "Usenet client with SSL - does it exist?"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by bobsmith2 on 2008-09-28
I'm looking for a Linux Usenet client that is capable of handling SSL. Does such a thing exist?

---

### Post by cariboo on 2008-09-28
Check out Hellanzb, it is available in the repositories. You can use Add/Remove Programs, Synaptic Package Manager and of course the command line to install it.

Jim

---

### Post by bobsmith2 on 2008-09-28
Thanks cariboo907. I went to the site and read about Hellanzb. I recall having read about it before. There is no reference on the site to SSL, so I just want to confirm before installing... Is Hellanzb able to handle SSL? So far every Usenet client I have read about makes absolutely no mention of SSL in their long lists of features.

---

### Post by bobsmith2 on 2008-09-29
Anyone? Is there a Linux Usenet client with SSL? Can someone either point me to one with SSL, or confirm that no such thing exists? Thanks.

---

### Post by bobsmith2 on 2008-09-30
OK, I'll try again... Is there a Linux Usenet client with SSL? Can someone please: 

1) point me to a Linux Usenet client that is truly SSL ready
2) confirm that no such thing exists 
3) confirm that an SSL ready Usenet client for Linux is on the way
4) provide some other solution short of using XP

This is one major issue that forces me to keep using XP. I'm not a gamer, I don't need Photoshop, and I'm making progress on finding alternatives for things I can do in XP that I can't do (or do as efficiently) in Ubuntu. So this isn't a huge issue at the moment because I can just continue to use XP. But I DO NOT not want to be forced to use Vista when XP becomes defunct.

Anyone?

---

### Post by Widgit on 2008-10-07
The closest thing I have found to an ssl ready client is "nzb" sometimes referred to as the nzb project.

It allows you to download files from an nzb, although no browsing features as of yet.  I've also found it to sometimes be a little flaky, still might be worth a try.

I'd be keen to hear if you hear of any other clients.

---

### Post by mbsjoblom on 2008-10-11
Yes it exists. SABnzbd is a free/open-source cross-platform binary newsreader written in Python.:)
[http://www.sabnzbd.org/](http://www.sabnzbd.org/)

---

### Post by oldos2er on 2008-10-11
slrn can be compiled with SSL, and Pan can be configured to work with stunnel.

---

### Post by bobsmith2 on 2008-10-14
> **mbsjoblom said:**
> Yes it exists. SABnzbd is a free/open-source cross-platform binary newsreader written in Python.:)
[http://www.sabnzbd.org/](http://www.sabnzbd.org/)

Thanks mbsjoblom! I installed it. It took awhile to figure it out, but it works and it does provide access to SSL. I had given up on finding anything. Your help is greatly appreciated.

---

### Post by bobsmith2 on 2008-10-14
> **oldos2er said:**
> slrn can be compiled with SSL, and Pan can be configured to work with stunnel.

Thanks oldos2er. I'm using SABnzbd for nzb files, but I plan to dig into stunnel with Pan for just browsing usenet. From what little I've gathered, stunnel will take some time to figure out, but it will meet my needs if I can get it up and running. Your help is appreciated.

---

### Post by nhasian on 2008-10-14
i can confirm that hellanzb works with SSL.  I use hellanzb in daemon mode and lottanzb as my front end.

---

