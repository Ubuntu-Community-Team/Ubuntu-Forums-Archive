---
title: "Run command when new mail arrives at gmail/evolution"
date: 2007-12-26
forum: Programming Talk
---

### Post by KarT on 2007-12-26
Hi there!

Is there any simple way to check the Gmail inbox directly to see if there is any unread mail? If not, is there any way to trigger an event when a new mail arrives at Evolution?

My ideia is simple: I have an Asus G1 and it has a led for new mail. My ideia is to create a very simple background program that checks for unread e-mail at the Gmail Inbox every X seconds and, if there is any, it turns the light on and if there is nothing new, it turns it off.

The above would be the best, but I have no ideia about connecting and making that check in C/C++.

If it is impossible/way too hard, is it possible to use evolution for that?

Thanks

---

### Post by CptPicard on 2007-12-26
The Gmail inbox can be checked as an rss feed. Look at the browser's RSS icon when browsing the inbox. Grab that URL and check the feed periodically. I've got the feed in Akregator... and I'm sure KDE has a DCOP event for "new stuff in feed" so it would be doable through that.

---

### Post by engla on 2007-12-26
There is the package **mail-notification** in the repositories.. it can work with custom mail servers or gmail, multiple accounts and more things. I'd guess it also supports custom commands since it's pretty configurable.

---

### Post by G|N| on 2007-12-27
The new Specto is what you need!
My dev specto branch has a (new) option to run a specific command when an event has happened (new gmail message is supported as an event!)

Get it here:
[https://code.launchpad.net/~woutc/specto/specto-woutc](https://code.launchpad.net/~woutc/specto/specto-woutc)

It is still in development but i use it daily at home and it seems to work without problems...


You will need to use bzr to get the sources: [http://m0n5t3r.info/stuff/bzr-quickref/bzr-quickref.pdf](http://m0n5t3r.info/stuff/bzr-quickref/bzr-quickref.pdf)

edit: POP3 and IMAP will also be supported soon!

---

### Post by KarT on 2007-12-27
I really really want to keep it simple. I just want to run a command when uread mail is detected and run a different comand when there is no unread mail.

Is your app able to perform that?

Thanks!

---

### Post by G|N| on 2007-12-28
> **KarT said:**
> I really really want to keep it simple. I just want to run a command when uread mail is detected and run a different comand when there is no unread mail.

Is your app able to perform that?

Thanks!

Currently it is not possible to perform an action when there are no unread mails anymore...but i could propose it as a extra feature...
Could you give me a good example from what you want to do when there are no unread mails anymore?

And i wouldn't say specto is a simple application, but it is possible to run it  in the terminal (without gui).

---

### Post by KarT on 2007-12-28
When there are no unread mail I want to turn off the "unread mail" led...

---

