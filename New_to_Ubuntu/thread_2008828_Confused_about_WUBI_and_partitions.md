---
title: "Confused about WUBI and partitions"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by rthatchjr on 2012-06-23
Hello all, I just did the WUBI windows install of 12.04LTS on my HP laptop with windows 7, I set the partition size to 30gigs, now I am thinking that I did not make it big enough, I am wanting to install some microsoft stuff and a game through wine and I need to expand my partition, I am reading about others doing the same thing, but everyone seems to start off with " as long as you did not use WUBI" did I make a mistake by using the WUBI installer? I hate to think so, it was bar none the easiest install I have ever done, Questions is how do I expand my partition now that I did it through WUBI?
                          Thank you

                          Russell

---

### Post by kdane4 on 2012-06-23
Hi,

Did you create a partition of 30 gigs beforehand or you're referring to the 30 gigs you allotted to the virtual disk when you used the wubi installer? Just wanted to clarify to avoid confusion..

---

### Post by kdane4 on 2012-06-23
Heres a link for resizing the virtual disk for WUBI.. Im not sure but I think the maximum size for the virtual drive for WUBI is only 30 gigs.. But to be sure, you can just wait for one of the experts especially BCBC to confirm this one.. :)

[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

---

### Post by rthatchjr on 2012-06-23
I am guessing it is the virtual partition, since I did not actually size anything, I just let WUBI handle it all.

---

### Post by kdane4 on 2012-06-23
After [reading various threads]("http://ubuntuforums.org/showthread.php?t=1795328"), I think your best option is to do a [migration to a real dual boot system]("http://ubuntuforums.org/showthread.php?t=1519354")

Cheers!! :popcorn:

---

### Post by Frogs Hair on 2012-06-23
A Wubi installation is intended for trial use , but I know people who use Wubi for extended periods without problems . Re-sizing the virtual disk is possible and works for many users. Moving a Wubi installation to a partition is more complicated the installing a traditional dual boot.

---

### Post by Mark Phelps on 2012-06-23
> **rthatchjr said:**
> ... I am wanting to install some microsoft stuff and a game through wine ...
BEFORE you do that, go to the WineHQ site, select the application compatibility database -- and look up the app/game and version you want to run under Wine.

Wine does not run everything, and some things it does not run at all.  IF you find no listing for the app/game, it's probably not going to work.  IF you find a listing but the rating is silver or lower, installing it is going to be a waste of time because some functionality won't work.

Just trying to save you a lot of work struggling to get MS Windows stuff working in Linux. 

>  and I need to expand my partition, I am reading about others doing the same thing, but everyone seems to start off with " as long as you did not use WUBI" did I make a mistake by using the WUBI installer? I hate to think so, it was bar none the easiest install I have ever done, Questions is how do I expand my partition now that I did it through WUBI?
Basically ... you - don't!  Wubi did not do the install to its own partition, so there is no partition for you to expand.

As mentioned, you can TRY migrating Wubi to its own partition -- but if Win7 came preinstalled on your laptop, it's very likely that it already has the maximum of 4 primary partitions allocated.  Which means, you can NOT add another partition for holding Ubuntu.

You need to go into Win7, open the Disk Management utility, and count the number of partitions (MS calls them "drives") that you see.  There may be a couple of hidden ones -- one very small one for the Win7 boot files, another larger one with the Recovery Windows image.

---

### Post by rthatchjr on 2012-06-28
Thank you all for the quick replies, I apoligize for taking so long to say thank you, I ended up setting aside a partition for ubuntu, I am glad I did it, thank you for the ratings in "Wine" I am trying to get World of Warcraft working and was going to use MS office, but have changed my mind on the office, Libre seems to be working great! WoW not so much, lol.

---

