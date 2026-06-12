---
title: "[SOLVED] YAEPP - Yet Another Eclipse PDT Problem"
date: 2007-09-21
forum: Programming Talk
---

### Post by galvao on 2007-09-21
Greetings, everyone.

I've recently installed eclipse manually, the one which comes with less things on it (called Europa). It's the latest version, BTW, 3.3

Well, I've tried installing PHP Debugger Tools (PDT) exactly how it's described in it's website and everything ran smooth.

My problem is I can't see NOTHING related to PHP / PDT on eclipse, even if I start it with the -clean option. When I try to open a php file, for example, it opens in a external editor. In the preferences I just don't see a PHP section...

Can anyone please give me some help? I've took a look on other topics about this, but I'm extremely newbie for some things so I'm kinda scared of making things even worst.

If someone would be kind enough to guide me step by step I'd be forever greatfull.

TIA,

---

### Post by potsofdirt on 2007-10-12
I was experiencing a similar problem to you. After looking in the workspace/.metadata/.log file and googling some of the error messages I found a Russian page that helped.

First, everyone said I needed to go to Window->Open Perspective->Other and select PHP. I did not have the PHP option.

The issue seems to be what version of Java I was running. The Russian page recommended 1.5. Here's how to get it running:

sudo apt-get install sun-java5-jre
sudo update-alternatives --config java
# Select v1.5.0

Now you should be able to fire up Eclipse and select the PHP perspective.

---

### Post by galvao on 2007-10-15
potsofdirt:

Thanks **a lot **for your reply, everything works fine now.

---

