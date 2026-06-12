---
title: "[SOLVED] OOo3 install...Again...broken packages"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by jmcgovern on 2008-10-16
This seems to be a very popular subject lately.  I've attempted to install OOo3, using the instructions found on tombuntu.com.  The install seems to go fine, i get the setup wizard and the command works.  However, once I install the program, Synaptic reports 3 broken packages, and will not let me update till i fix the broken packages.  Fixing the broken packages removes them from the system, which then causes OOo3 to not be able to start, so I'm caught in a loop here.  I've kept 2.4 on the system throughout this process in case something like this happened.  Anyone experienced similar?  It's not critical I have OOo3 I just thought it might be nice.  I can live without it if there's no solution, just want to know if there is one.

---

### Post by thomas228 on 2008-10-21
> **jmcgovern said:**
> This seems to be a very popular subject lately.  I've attempted to install OOo3, using the instructions found on tombuntu.com.  The install seems to go fine, i get the setup wizard and the command works.  However, once I install the program, Synaptic reports 3 broken packages, and will not let me update till i fix the broken packages.  Fixing the broken packages removes them from the system, which then causes OOo3 to not be able to start, so I'm caught in a loop here.  I've kept 2.4 on the system throughout this process in case something like this happened.  Anyone experienced similar?  It's not critical I have OOo3 I just thought it might be nice.  I can live without it if there's no solution, just want to know if there is one.

There seems to be a conflict in the instructions given on tombuntu.com for installing 00o3 and the tutorial found on 

[http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=68)

Step 1 clearly requires you to remove ubuntu's 2.4 version.

you may have to remove 00o3 using tombuntu.com's script: 
sudo apt-get remove ooobasis3.0-base ooobasis3.0-binfilter ooobasis3.0-calc ooobasis3.0-core01 ooobasis3.0-core02 ooobasis3.0-core03 ooobasis3.0-core04 ooobasis3.0-core05 ooobasis3.0-core06 ooobasis3.0-core07 ooobasis3.0-draw ooobasis3.0-en-us ooobasis3.0-en-us-base ooobasis3.0-en-us-binfilter ooobasis3.0-en-us-calc ooobasis3.0-en-us-draw ooobasis3.0-en-us-help ooobasis3.0-en-us-impress ooobasis3.0-en-us-math ooobasis3.0-en-us-res ooobasis3.0-en-us-writer ooobasis3.0-gnome-integration ooobasis3.0-graphicfilter ooobasis3.0-images ooobasis3.0-impress ooobasis3.0-javafilter ooobasis3.0-kde-integration ooobasis3.0-math ooobasis3.0-onlineupdate ooobasis3.0-ooofonts ooobasis3.0-ooolinguistic ooobasis3.0-pyuno ooobasis3.0-testtool ooobasis3.0-writer ooobasis3.0-xsltfilter openoffice.org3 openoffice.org3-base openoffice.org3-calc openoffice.org3-dict-en openoffice.org3-dict-es openoffice.org3-dict-fr openoffice.org3-draw openoffice.org3-en-us openoffice.org3-impress openoffice.org3-math openoffice.org3-writer openoffice.org-ure

before removing ubuntu's 2.4 version.

Remember that these openoffice versions eat up a lot of disk space (see [http://ubuntuforums.org/showthread.php?t=944464)so](http://ubuntuforums.org/showthread.php?t=944464)so) that may be part of your problem although I'm just guessing since your posts just say some packages are broken. A little more discription or actual system output may help someone with more knowledge of how ubuntu works help you solve your delema. Im a ubuntu/linux newbie but I would sure like to see you solve your problem. 

I posted this reply here rather than on 
[http://ubuntuforums.org/showthread.php?t=953487](http://ubuntuforums.org/showthread.php?t=953487)
as that thread was getting a little confused.
Please post the steps you had to take to resolve this delema when you sucsede as there are a lot of users out there that could benifit from your experiences on this matter.

Good luck
Tom

---

### Post by jmcgovern on 2008-10-21
Switching back to my original topic, since it'll be easier to follow, and apologies for the threadjack. I think somethings getting corrupted.  The three broken packages (listed in the other thread about twice or so) are always the same.  I've uninstalled 2.4, completely (sudo apt-get remove --purge), and attempted to install 3.0 several times.  each time it breaks I completely remove 3.0 (using --purge again), reinstall 2.4, and completely remove 2.4 again.  Currently, at least according to synaptic, and my gui menu, i have NO version of openoffice present on my system right now.

---

### Post by thomas228 on 2008-10-21
Did you run the tombuntu.com script (above) for removing 00o3?
Are you running 32 or 64 bit ubuntu / 00o3 download?
Don't know what else to ask right now assuming you read the thread concerning disk space.
After running the script for deleting all of 00o3
you might be able to run a good install assuming you don't have 2.4 installed.
Good luck
Tom

---

### Post by jmcgovern on 2008-10-21
> **thomas228 said:**
> Did you run the tombuntu.com script (above) for removing 00o3?
Are you running 32 or 64 bit ubuntu / 00o3 download?
Don't know what else to ask right now assuming you read the thread concerning disk space.
If you feel after running the script for deleting all of 00o3
you might be able to run a good install assuming you don't have 2.4 installed.
Good luck
Tom
Fixed.  ran the tombuntu scripts for removal, started again with a fresh download, and it worked.  Either the download got corrupted or packages were missed the first time I did the removal.  Such a minor issue to be driving me crazy for three days...

---

### Post by thomas228 on 2008-10-21
Glad to hear it.
Do you have all 7 installed under applications>office?
hope so and again think about putting out a step by step solution including the tombuntu.com script
Thanks for keeping me in the loop
Good luck
Tom

---

### Post by drakeman007 on 2008-10-21
> **jmcgovern said:**
> Fixed.  ran the tombuntu scripts for removal, started again with a fresh download, and it worked.  Either the download got corrupted or packages were missed the first time I did the removal.  Such a minor issue to be driving me crazy for three days...

Wow, glad to read that jmcgovern, now you earn some experience for future troubles, mm you are newbie like me? i have a great book for you to learn some of the command line in ubuntu, tell me if you are interested!.
Regards!
:guitar:

---

### Post by drakeman007 on 2008-10-21
> **thomas228 said:**
> Glad to hear it.
Do you have all 7 installed under applications>office?
hope so and again think about putting out a step by step solution including the tombuntu.com script
Thanks for keeping me in the loop
Good luck
Tom

Hey thanks tomas to help the community in this way, now i know who can get me out of troubles in ubuntu hehehee... 
thanks:popcorn:

---

### Post by thomas228 on 2008-10-21
> **drakeman007 said:**
> Wow, glad to read that jmcgovern, now you earn some experience for future troubles, mm you are newbie like me? i have a great book for you to learn some of the command line in ubuntu, tell me if you are interested!.
Regards!
:guitar:

Thanks for the offer but I have not read the one I have besides google and the wikis are sometimes more convenient. Again thankyou for your complements and you are right in that I am a linux/ubuntu newbie (since I joined this forum). Being a retired EE helps a little.
Again good ubunting
Tom

---

