---
title: "Update manager unresponsive"
date: 2012-05-03
forum: New to Ubuntu
---

### Post by 2muchcoffeeman on 2012-05-03
[I]Ubuntu 12.04
Gateway Nav50 netbook
1GB memory
Atom CPU N450 @ 1.66Ghz x 2
32 bit
260GB HD[/I]


I booted up, then noticed the Update Manager icon sitting in the launcher, with a nice, fat number of "317." I clicked on the icon in the launcher, and . . . nothing. No response. Nothing began whirring in the background. Ubuntu behaved as if the icon weren't even there.

So, I opened a terminal window and ran

[INDENT]sudo apt-get update[/INDENT]

. . . and within the span of 60 seconds, the update was done. I was back to the command-line prompt.

This doesn't seem right.

Usually, when running an update through the Update Manager, the downloading and installing of several hundred MB takes several minutes, using my very basic in-home wireless connection. When I ran the update through the command line, it appeared to take  less than a minute.

I'm guessing I overlooked something, and that I did not truly update Ubuntu through the command line.

Next, I opened System Settings, and went to the System/Settings window. There, I discovered the "install updates" button, and clicked it. At that point, Update Manager opened, found the 317 updates (291.4 MB) waiting to be installed. I clicked "install updates."

Can anyone tell me what just happened? Why was the Update Manager icon unresponsive? What did I fail to do in the terminal window? And why was System Settings/System/Settings->[install updates] able to get the job done when the other methods did not?

I ask this in the name of learning the peculiarities of Ubuntu.

---

### Post by kc1di on 2012-05-03
The command you want to update in teminal is :

```
sudo apt-get update
sudo apt-get upgrade
```

when you do the upgrade you see lots of activity if you don't let us know. 

On my 12.04 install often the update box will sit in the left panel but I can't activate it from there for some reason I always go to the little ubuntu icon in the upper right of the top panel and click on software updates from there and it works fine.

---

### Post by 2muchcoffeeman on 2012-05-03
Thanks, kc1di.

An "update" is different from an "upgrade," correct? I was under the impression that an "update" applies only to the current version of Ubuntu, and that an "upgrade" moves you from one version of Unbuntu to the next. Since I'm already running Ubuntu 12.04, an "upgrade" would be a pointless exercise until Ubuntu 13.0 comes out, right?

Oh, and good tip about the Ubuntu icon in the upper-right. I had forgotten about that.

---

### Post by plucky on 2012-05-03
> An "update" is different from an "upgrade," correct? 


An update downloads the index files for the repositories.
An upgrade actually installs the updatable applications.

> Since I'm already running Ubuntu 12.04, an "upgrade" would be a pointless exercise until Ubuntu 13.0 comes out, right?


Incorrect,you need to run the upgrades to install the updates.

A Release upgrade will install the next release version and is invoked differently.

You can actually use the Update Manager to install the updates.Or you can use the two commands given in the previous reply.

Good Luck

---

### Post by kc1di on 2012-05-03
update = update the repository list
upgrade = install latest version of installed packages
dist-upgrade = distribution upgrade to next version of distro.

In other word you must run update to to tell your local machine which packages have been changed in the repositories. It modifies nothing other than the package list on your machine


upgrade tell the server to download and the local machine to install all new package versions Or you might say it syncs the packages on your machine with those on the repository server. 

dist-uprade for move install all new packages moving your machine from say ubuntu version 11.10 to version 12.04 

hope that helps explain it for you,  when you click the Software update in the menu it does both a update & Upgrade when you tell it to install available upgrades. 

Good luck,
D ;)

---

### Post by 2muchcoffeeman on 2012-05-04
Thank you, plucky and kc1di. Your explanations are very helpful. I appreciate the help I find here in the Ubuntu forums.

---

