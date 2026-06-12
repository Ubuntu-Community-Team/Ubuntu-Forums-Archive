---
title: "[SOLVED] wish to be able to read error messages"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by nalinib on 2008-05-27
Hi everybody,

This is my first post.

I have received requested ubuntu live cd few days back and I am trying to understand it fully before I permanently install it on hdd.

Presently I am running the live cd.

My first expression is "fantastic".  I have spread a word to my friends and relatives and will be copying the cd and distributing them.

I have few questions.  I hope to get the clarifications from experienced members.

My first question.

[COLOR="Red"]How can I read the error messages ?[/COLOR]

I get an error message at the boot time but it disappear very fast so I canot read it fully. (I tried pressing pause button but the message does not pause).

The message reads something like this "... pci... BIOS bug...".

The message disappears and ubuntu loads and I can use it.  So I wonder what the message is all about.

I wish I should be able able to read all those error messages before I install ubuntu on hdd.

Thanks

nalinib

---

### Post by sayakb on 2008-05-27
Press Ctrl+Alt+F1 during the boot to reveal background text.

---

### Post by nalinib on 2008-05-27
Thanks "LinuxIsInnovation" for lightning quick reply.

presently I am "in" Ubuntu.  I will try the suggested trick next time I boot up ubuntu and post the outcome here. (Next time means after few hours)

Thanks again

nalinib

---

### Post by sayakb on 2008-05-27
In case if you are using Hardy, do press the key combination only after the orange bar completes oscillating left-right and starts filling up from left. :)

---

### Post by lisati on 2008-05-27
See [http://ubuntuforums.org/showthread.php?t=805632&highlight=bios+bug+timer+connected](http://ubuntuforums.org/showthread.php?t=805632&highlight=bios+bug+timer+connected) - it's possibly related, along with [http://ubuntuforums.org/showthread.php?t=790869&highlight=bios+bug+timer+connected](http://ubuntuforums.org/showthread.php?t=790869&highlight=bios+bug+timer+connected)

---

### Post by nalinib on 2008-05-27
Thanks "LinuxIsInnovation"

I will remember to use key combination at appropriate time.

But one thing needs to be clarified here:) the error messages appears before the orange bar appears (Yes I am using hardy) and I do not find any problem in using ubuntu (except broadcom wlan driver required, but I don't use any wireless network so that is insignificant for me).

Thanks lisati

Those threads seem to be useful.  But I first should know what exactly the error message is.

Thanks for your replies.  I will come back.

nalinib

---

### Post by sayakb on 2008-05-27
That is fine. Even after the orange bar comes, the messages would stay there. Pressing the key combination would show the message.

---

### Post by nalinib on 2008-05-27
Hi

I used "ctrl-alt-F1" and saw the error message.  Thanks "LinuxisInnovation".

The message reads :

[   27.489426] PCI : BIOS BUG found
Loading please wait

Then the loading process started with information that firmware for wlan should be downloaded and installed.

Thus it appears that wlan firmware is the only problem and this problem is insignificant for me as I do not use wlan.

Still I would like to know whether installing firmware fix would make permanent changes to my motherboard rom/BIOS (wlan is on board) ?

And if it is so will there be any problems using vista which came preloaded with my hp-compaq laptop with AMD Turion64 and phoenix bios?

Thanks "LinuxIsInnovation" and "lisati"

nalinib

---

### Post by sayakb on 2008-05-27
That doesn't seem like a serious error. If you think that your problem has been solved, please mark this thread as Solved. :)

Dave

---

### Post by hyper_ch on 2008-05-27
you can also search your log files. They are at /var/log... you may want to have a look at /var/log/sys.log

---

### Post by Golem XIV on 2008-05-27
> **hyper_ch said:**
> you can also search your log files. They are at /var/log... you may want to have a look at /var/log/sys.log

... and don't forget System -> Administration -> System Log :-)

---

### Post by nalinib on 2008-05-27
Thanks hyper_ch and Golem XIV

Very useful information.

May I wait till I get the answer to my querry "Will downloading and installing firmware make permanent changes to my system BIOS/wlan rom and will it have any adverse effect on vista installation ?"

I will wait till tomorrow and then close the thread marking it "solved".

---

### Post by sayakb on 2008-05-27
> **nalinib said:**
> Thanks hyper_ch and Golem XIV

Very useful information.

May I wait till I get the answer to my querry "Will downloading and installing firmware make permanent changes to my system BIOS/wlan rom and will it have any adverse effect on vista installation ?"

I will wait till tomorrow and then close the thread marking it "solved".

You might post a separate thread for this query in the proper section of the forum.
Btw, if you "upgrade" your BIOS, there are very less chances of Vista getting screwed-up.

---

### Post by nalinib on 2008-05-27
Thanks all

I am marking this thread "solved"

nalinib

---

