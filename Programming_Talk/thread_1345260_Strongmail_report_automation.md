---
title: "Strongmail report automation"
date: 2009-12-03
forum: Programming Talk
---

### Post by Perkins on 2009-12-03
I am working for a company which uses the Strongmail mailer package.  They were too cheap to buy the extra module for report generation, so I have to do it.  Needless to say, this is sub-optimal as there are many other things they also wish me to do at the same time, and I occasionally make mistakes.

I have managed to automate a fair portion of the other things they wish me to do using a portable version of cygwin, perl, and winmacro.  (I am working on eliminating the winmacro portions as they are clunky.)

Strongmail is where I hit a wall.  The interface is web-based, but I can't seem to manage to navigate the authentication using wget.  I have told it to save both normal and session cookies, but cannot seem to get in.

Now, I can load up the page in lynx and log in just fine, but lynx doesn't have much of a way to automate grabbing the specific pages I need.  My next thought was elinks, because it's supposed to share session data between multiple, concurrent instances.  So I could log in myself, and then the script should be able to join the session and pull the pages I need.  The problem is that I cannot seem to figure out how to compile elinks under cygwin with SSL support.

Normally I'd go ask on the cygwin forum if anybody can offer any pointers, but the people there remind me of this:  [http://xkcd.com/293/]("http://xkcd.com/293/")

So, I am hoping somebody here might have a fresh idea.  I am debating at the moment between trying to compile elinks' dependencies from scratch under cygwin (which will be a pain, and has no guarantee of success) and using portable VirtualBox to get myself a full-blown linux environment where I could just install elinks and go (which is overly bulky and I only have a 4gb flash drive.  Not to mention that they seem proud of the fact that they are a "Windows Shop.")

If there's anybody reading this who knows enough about Strongmail to suggest where I might have gone wrong with wget, or who knows of an easier way to compile elinks in cygwin, or has an idea I have completely missed, I would be greatly appreciative of a little help.

---

### Post by pvconley on 2009-12-04
Depending on what your company purchased, there are two sets of APIs that can be used to pull data from a StrongMail server.

Can you tell me what system & version you are using and what type of report you are trying to produce?

---

### Post by Perkins on 2009-12-04
They want an email notification sent out when a campaign starts, an email when one ends containing the percentage which failed, and notification while it is running if the failed or deferred messages exceed a certain threshold.

I will see if I can find out the system and version.  If I had to guess, I would assume that they probably bought the cheapest, most basic package available.

---

### Post by pvconley on 2009-12-07
Hi - This should be easy enough through the API. You'll have to poll for the mailing status and mailing results but the data is all available.

The StrongMail distro contains the documentation for the API or you can post your question to [http://forums.strongmail.com/](http://forums.strongmail.com/) under the API/Development forum.

---

### Post by Perkins on 2009-12-07
Thank you very much.  Now that I know where I'm looking I can hopefully figure it out.

---

### Post by pvconley on 2009-12-08
You are welcome and good luck!

If you hit any snags, the StrongMail forums are a great source of info and my support team will be all over answering any questions.

---

### Post by Perkins on 2010-01-13
Well, the snags in question turned out to be the people in charge of the server...

Fortunately, a friend of mine asked for help with a different programming challenge, which led me to stumble across the Win32::IE::Mechanize PERL module.  Very nifty little thing, let me automate everything they were having me do manually in under 100 lines of code.

---

