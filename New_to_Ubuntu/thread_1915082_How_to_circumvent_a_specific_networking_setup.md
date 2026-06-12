---
title: "How to circumvent a specific networking setup"
date: 2012-01-25
forum: New to Ubuntu
---

### Post by cantide5ga on 2012-01-25
I just recently setup an old laptop as a webserver running Ubuntu using a LAMP stack.  It is connected directly to an ethernet port from the wireless router.  My main computer is a Windows 7 machine that connects to the router wirelessly for internet.  

The server is experimental and for testing only, so nothing fancy is going on.  The rest of the drive would be perfect for back-ups and the like.  I would like to create a network involving the webserver and my Windows 7 laptop so that I can share between them exclusively with no internet involvement in doing so (probably redundant to state, but wanted to be clear).  My progress so far is installing Samba and need to get the two systems to see each other.

I hate to ask this as I know the answer is out there, I just don't know exactly what I should be asking when doing searches. I understand this involves some networking details which I am rusty on, so throwing some tutorials my way would be suitable.  Of course ANY recommendations would be appreciated.

EDIT: In just thinking of the structure, can my Win7 machine talk to the router which in turn talks to the wired server, or am I looking at a ad hoc wirless network between the two?  Regarding the latter, I've had some issues with Linux working with wifi adapters in the past so I would like to avoid this solution for this and future setups.

---

### Post by sudodus on 2012-01-25
I think that SSH is easier to set up. Look at the following post
[[COLOR="Red"]_http://ubuntuforums.org/showpost.php?p=11638769&postcount=2_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11638769&postcount=2")

---

### Post by sandyd on 2012-01-25
> **cantide5ga said:**
> I just recently setup an old laptop as a webserver running Ubuntu using a LAMP stack.  It is connected directly to an ethernet port from the wireless router.  My main computer is a Windows 7 machine that connects to the router wirelessly for internet.  

The server is experimental and for testing only, so nothing fancy is going on.  The rest of the drive would be perfect for back-ups and the like.  I would like to create a network involving the webserver and my Windows 7 laptop so that I can share between them exclusively with no internet involvement in doing so (probably redundant to state, but wanted to be clear).  My progress so far is installing Samba and need to get the two systems to see each other.

I hate to ask this as I know the answer is out there, I just don't know exactly what I should be asking when doing searches. I understand this involves some networking details which I am rusty on, so throwing some tutorials my way would be suitable.  Of course ANY recommendations would be appreciated.

EDIT: In just thinking of the structure, can my Win7 machine talk to the router which in turn talks to the wired server, or am I looking at a ad hoc wirless network between the two?  Regarding the latter, I've had some issues with Linux working with wifi adapters in the past so I would like to avoid this solution for this and future setups.
just connect both with a router

---

### Post by sudodus on 2012-01-26
> **sandyd said:**
> just connect both with a router
+1
Several wifi cards and adapters work out of the box with linux. Look at the following link
[[COLOR="Red"]_https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported_[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

---

### Post by cantide5ga on 2012-01-26
Looks like I might have been digging to deep on this one.  Will report back ASAP.  Thanks folks.

---

