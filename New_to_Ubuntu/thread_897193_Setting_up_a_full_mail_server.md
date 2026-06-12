---
title: "Setting up a full mail server"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by jodaan on 2008-08-21
I found threads in here on mail servers, but I couldn't determine whether or not those were just private servers for home networks, or if these were set up to be remotely accessed.  I need to set up a remote access mail server for a small home business. I need to be able to access it on the network, and from hotels etc across the country. Can someone point me to a tutorial for that?

I have a little experience in Linux, but its been a few years. I'm trying to get some good solid tutorials and get back into it.

---

### Post by meanburrito920 on 2008-08-21
Why are you attempting to set up your own file server? Why not use a hosted one, then you dont have to worry about all that.

---

### Post by Cheesehead on 2008-08-21
You only need a mail server *if you are actually hosting* homebusiness.example.com.  In fact, your mailserver should be included in your web hosting or ISP package.

You *don't* need a mailserver if are simply sharing mail from one (or more) accounts among several computers.

For example, if you have three computers and one mail account and you want all three to have synchronized in-boxes:
1) Use an IMAP mail service (like gmail)
2) Use a POP mail service, and adjust the 'advanced settings' to 'leave the mail on server' for 30 days or so.

Synchronizing outgoing mail is easy on IMAP; easy but more annoying on POP - just cc: all outgoing mail back to your common inbox.

Since Evolution and Thunderbird will handle multiple IMAP and POP accounts, you can use the same strategy for a dozen computers and a dozen accounts.

I use this system to share mail among five computers and seven accounts across two locations (home and work), and it continues to work well when on trips or vacations *because I don't host a mailserver*.

---

### Post by stmiller on 2008-08-21
> **jodaan said:**
> I found threads in here on mail servers, but I couldn't determine whether or not those were just private servers for home networks, or if these were set up to be remotely accessed.  I need to set up a remote access mail server for a small home business. I need to be able to access it on the network, and from hotels etc across the country. Can someone point me to a tutorial for that?

I have a little experience in Linux, but its been a few years. I'm trying to get some good solid tutorials and get back into it.

A mail server is a box that sends/receives email for a domain. :) I'm not sure that is what you want...

If you need webhosting or online storage, check out 1and1.com or other hosting companies. You can get a Linux server and storage for $5/month. 

I would highly suggest paying for hosting now, and experiment with Linux on your own to build up your Linux chops.

---

