---
title: "libc6-dev not installing in edgy"
date: 2007-06-01
forum: Programming Talk
---

### Post by thug007 on 2007-06-01
Can anyone help-out please?   I am using Synaptic to attempt to install libc6-dev, having used the Update Manager immediately previously.

The result in Synaptic is my Screenshot1... attached.
My sources.list is attached as sources_31May07.txt

Two tabs in the Preferences part of Synaptic are attached:   Screenshot3 & 4.

I cannot see my own way out of this one.


Regards

---

### Post by 5-HT on 2007-06-01
Are you running Edgy or Feisty?

You have a version conflict between libc6 (Feisty's version) and libc6-dev (Edgy's version). Synaptic is trying to install Edgy's libc6-dev while you either have Feisty's libc6 installed or Synaptic's trying to pull it in to satisfy libc6-dev dependencies.
If you just upgraded to Feisty, please change all instances of "edgy" for "fiesty" in your sources.list (and comment out fiesty-backports for the moment) and update the package list: should do the trick.

If you are running Edgy, can you please post the version of libc6 you have installed. Also, if you are running Edgy, have you been playing with Synaptic's distribution prefs (not running Ubuntu at the moment, can't check what the default is for that)

cheers

---

### Post by thug007 on 2007-06-01
Thanks for your reply 5-HT.

Installed vn of libc6 is     2.5-0ubuntu14      as U suspected.

I think this must be due to my unsuccessful upgrade to Feisty  (please see the only other thread I have started in the forums about this).   I eventually terminated the upgrade to Feisty - not a happy position to be in.  After the termination I had to change references to feisty which the upgrade had made in my /etc/apt/sources.list back to edgy.  I made these changes using gedit and not by using Synaptic itself.  After the first signs of the trouble  about which this thread is,  I also included multiverse  and also edgy-backports after reading other libc6-dev forum posts.

Regards

---

