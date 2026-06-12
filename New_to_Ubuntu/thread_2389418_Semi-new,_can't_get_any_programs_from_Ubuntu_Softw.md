---
title: "Semi-new, can't get any programs from Ubuntu Software"
date: 2018-04-16
forum: New to Ubuntu
---

### Post by dave1662 on 2018-04-16
I had 14.xx a couple of years ago. Worked fine until I tried to update to 16.4. Totally locked and froze the Ubuntu portion of the hard drive in that computer.
It was going to cost me big time to get a shop to remove the entire Ubuntu section of that PC and I still haven't had that done.

Last week I installed the 16.4 LTS in a core I 7 laptop, it is working fine and I was able to download and install SagCAD and LibreCAD
Now suddenly I can't download anything from Ubuntu Software.
 If I click on any of the Editors picks or recommended office software, all I get is a slowly turning circle.
If I click on anything in the Categories section, all I get is white boxes with 3 dots inside them

Am I doing something wrong?

---

### Post by QIII on 2018-04-16
> **dave1662 said:**
> It was going to cost me big time to get a shop to remove the entire Ubuntu section of that PC and I still haven't had that done.

Somebody was playing you.  There's no reason for that to cost you anything at all.  Please start a new thread asking specifically how to do that.  You'll get asked a lot of questions so others can understand what is going on.  Answer as best you can.

> Last week I installed the 16.4 LTS in a core I 7 laptop, it is working fine and I was able to download and install SagCAD and LibreCAD
Now suddenly I can't download anything from Ubuntu Software.
 If I click on any of the Editors picks or recommended office software, all I get is a slowly turning circle.
If I click on anything in the Categories section, all I get is white boxes with 3 dots inside them

Am I doing something wrong?

Probably not.  An update may have gotten interrupted or any number of things.  From what source did you download and install the software and how did you install it?  Let us know that and we can start taking some steps to help diagnose the problem.

---

### Post by dave1662 on 2018-04-17
I have only downloaded from the Ubuntu website, I try not to download except from the direct source.  I followed all instructions very carefully, using Rufus (I think the name was) to make a bootable USB stick. 
That worked well for a few days until I decided to go ahead and install, The install went smoothly from the stick.
After install it checked for updates, and I let it install all of those.

I then found a couple of CAD programs and installed those,  ALL installs come direct from Ubuntu Software

Then a couple of days later I thought I would see if WINE is available, I made a search for it and all I got was a slowly turning circle.

Today the update icon came on, and I did the update thinking maybe it would fix things. It did not.

---

### Post by QIII on 2018-04-17
Would you please use the terminal and issue the following:

```
sudo apt update && sudo apt upgrade
```

and post the entire thing back here between code tags?  That will give us some diagnostic information to work from.

For the code tags, you can paste your text, highlight it and then click the # symbol in the menu buttons above the text entry box.  Alternatively, you can type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after it.  The square brackets are required.

---

### Post by dave1662 on 2018-04-19
Okay I did that, and I received a huge amount of stuff and it asked if I wanted to upgrade 13 packages, so I hit Y and it upgraded them.  Still no change in Ubuntu Software (does not work)
Received another huge amount of text after upgrade.

You say to post everything between code tags,  How do I find or recognize them?  I am not good in programing. I saved the entire results in writer, 3 full pages, it would be one heck of a post, but I can if that is what you want.

Thank you for helping me, I like Ubuntu because it seems to run smoother on my laptop and doesn't have so much junk running in the back ground. The cooling fan runs almost continuously on Windows but only rarely on Ubuntu.

---

### Post by monkeybrain20122 on 2018-04-19
Install synaptic and forget about Ubuntu software, it only list a small fractions of software available anyway 

```
sudo apt install synaptic
```

synaptic is a gui package manager, it doesn't have the pretty pictures of  US, but it is a lot more powerful and it is not that hard to use.

---

### Post by dave1662 on 2018-04-23
Well every thing has fixed itself, or the last update fixed something they screwed up before.
Any way it's all working now, so I am not concerned with this issue any more.

---

### Post by Geoffrey_Arndt on 2018-04-26
Just a last quick note . . . in the future, be careful NOT to open synaptic or UbuSoftwareCenter concurrently.   Only 1 package manager must be running at one time, else problems arise.   Also, be sure to let all updates finish completely (so, if you have a BIG update, make sure you have PC plugged in and don't do anything risky that could cause the system to freeze or reboot.

---

### Post by monkeybrain20122 on 2018-04-26
> **Geoffrey_Arndt said:**
> Just a last quick note . . . in the future, be careful NOT to open synaptic or UbuSoftwareCenter concurrently.   Only 1 package manager must be running at one time, else problems arise.   Also, be sure to let all updates finish completely (so, if you have a BIG update, make sure you have PC plugged in and don't do anything risky that could cause the system to freeze or reboot.

Also if offered partial updates say no.

---

