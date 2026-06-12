---
title: "Firefox 3 Beta 5 Very Unstable in Hardy"
date: 2008-05-07
forum: Recurring Discussions
---

### Post by heroes_on_a_half_shell on 2008-05-07
Hey guys,

I've got 64 bit hardy running on my desktop with very few problems (upgraded from gutsy).  My one major issue has been that FF3 B5 creates a large demand for iowait cpu cycles every few minutes as indicated by the gnome resource monitor. This causes the firefox window to go grey and become unresponsive for a period of ~ 15 secs.  However, I don't believe this qualifies as a crash due to the fact that the webpage being viewed continues functioning.  Ex: a video on youtube or veoh will continue to play, albeit in black and white.

I guess I'd just like to know that this is a known problem, or if it's not, I'd like to know how to report it and maybe fix it, if at all possible.  Overall I like FF3, but I can't deal with this.

Thanks

---

### Post by Half-Left on 2008-05-07
Yes this did it to me as well but I've done a fresh install with reiserfs and it's working fine.

---

### Post by philinux on 2008-05-07
Goto edit>Prefs> Security tab and uncheck the options "Tell me if a website......."

It's a known bug which will hopefully get fixed when RC1 comes out any day now.

---

### Post by billy_big_time on 2008-05-07
Same problem here with a clean install of 32 bit Hardy.  The firefox window doesn't always turn grey but every few minutes cpu usage is at 100% and firefox becomes unresponsive.  Has anyone found a bug report for this?  I've searched a couple of times over the past week and I can't find anyone else with exactly the same problem (or at least not described using the same terms).
What plugins have you got installed?  I've only got noscript with the default theme.

---

### Post by Kevbert on 2008-05-07
Hi, I added a comment to a bug report on FF/Hardy see: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996")
The bug report has been made a bit bloated (many reports) so it may mean you need to make a new bug report on Launchpad.  Also there is a bug report on excessive use of hard disks by FF, unfortunately I don't know the bug number.

---

### Post by Kilz on 2008-05-07
> **heroes_on_a_half_shell said:**
> Hey guys,

I've got 64 bit hardy running on my desktop with very few problems (upgraded from gutsy).  My one major issue has been that FF3 B5 creates a large demand for iowait cpu cycles every few minutes as indicated by the gnome resource monitor. This causes the firefox window to go grey and become unresponsive for a period of ~ 15 secs.  However, I don't believe this qualifies as a crash due to the fact that the webpage being viewed continues functioning.  Ex: a video on youtube or veoh will continue to play, albeit in black and white.

I guess I'd just like to know that this is a known problem, or if it's not, I'd like to know how to report it and maybe fix it, if at all possible.  Overall I like FF3, but I can't deal with this.

Thanks

One option I dont see listed is installing firefox 2, [its in the repositories (universe)]("http://packages.ubuntu.com/hardy/firefox-2"). I did until FF3 is actually released. There are extensions I like that haven't been ported to ff3 yet.

---

### Post by LoneWolfJack on 2008-05-07
I had the same problems with Hardy64 (fresh install). FF very unresponsive, unexplainable CPU usage spikes and half of the plugins are not available for FF3 yet. Who ever decided to include a Beta Browser in a LTS release needs to be slapped.

Considering the other glitches I found in Hardy, I went back to Gutsy64 and will probably wait for 8.10 before I try an upgrade.

---

### Post by felker2 on 2008-05-07
I experience the same on my 8.04 32-bit: it happens each few minutes.

Don't know about my 64-bit system.

Very annoying.

---

### Post by Kilz on 2008-05-07
> **LoneWolfJack said:**
> I had the same problems with Hardy64 (fresh install). FF very unresponsive, unexplainable CPU usage spikes and half of the plugins are not available for FF3 yet. Who ever decided to include a Beta Browser in a LTS release needs to be slapped.

Considering the other glitches I found in Hardy, I went back to Gutsy64 and will probably wait for 8.10 before I try an upgrade.

It took a few minutes after reading this post to see the wisdom behind it. I dont know if you are a new linux user, but I think new users could learn something from your post. What you may ask,

1. The latest and Greatest my not be stable. - Linux software is released as soon as its stable for most people but not everyone. There may be bugs and issues especially from beta software included in the latest release of an operating system.
2. Those that need stability should wait a bit before installing any new release. - No matter how many people test the software, some bugs are going to slip through. Because there is no way to test everything with just the development testers. When a release goes live the numbers increese, bugs are found, then fixed. But it takes time.
3. Your need to have the newest should be limited by your ability to troubleshoot problems. If your first course of action on finding a problem is posting the issue to the forum you may not have the skills needed. Realistically look at how knowlagable you are to fix a bug, if you cant, hold off on new releases. There is no sense having the "newest" thing if its broke and you cant fix it.
4. If you have room dont upgrade your install, add the new install to the disk. - Keep that old working no problems version until you are 100% sure you don't need to boot into it to get something done. In fact I just yesterday deleted my fiesty (I skipped Gutsy, read #5) partition because I wasn't using it. If you have issues , you can always boot into the old install and wait while looking into the problem.
5. Do I really need to upgrade? - New users should ask themselves, "Do I really need to Upgrade?". Does the 6 month old operating system you have installed do everything you need? If so, why subject yourself to possible problems? Even non lts releases get 18 months of support. You can take your time and make sure you need to. You can skip a version altogether if you don't need the updated version or stability looks like a issue. 

Upgrade the smart way, do it from informed choices. Dont fall for hype that can end up causing you headache's.

---

### Post by philinux on 2008-05-07
> **LoneWolfJack said:**
> I had the same problems with Hardy64 (fresh install). FF very unresponsive, unexplainable CPU usage spikes and half of the plugins are not available for FF3 yet. Who ever decided to include a Beta Browser in a LTS release needs to be slapped.

Considering the other glitches I found in Hardy, I went back to Gutsy64 and will probably wait for 8.10 before I try an upgrade.

Please see my previous post. The RC1 will be out shortly

---

### Post by Kilz on 2008-05-07
> **philinux said:**
> Please see my previous post. The RC1 will be out shortly

Shortly? Have you see [the list of things]("http://wiki.mozilla.org/Releases/Firefox_3.0rc1") that need to be done before its released? There are also 10 blocking bugs.

---

### Post by philinux on 2008-05-07
> **Kilz said:**
> Shortly? Have you see [the list of things]("http://wiki.mozilla.org/Releases/Firefox_3.0rc1") that need to be done before its released? There are also 10 blocking bugs.

Yep they said early May. But honestly who knows.

---

### Post by LoneWolfJack on 2008-05-07
Kilz,

the wisdom behind my post was this:

if you [ubuntu/canonical] advertise a LTS release with emphasis on stability, DON'T include BETA software. especially not FF, which is known for having strange issues in every beta release [I'm saying that as someone who downloaded FF when their download-counter was 10k-something, and who has been happily using FF as primary browser ever since].

this has nothing to do with whether someone is a linux novice or not, it's about common sense, at least if we're talking about software that most users will rely on heavily.

> 
1. The latest and Greatest my not be stable. - Linux software is released as soon as its stable for most people but not everyone. There may be bugs and issues especially from beta software included in the latest release of an operating system.


no argument there. but like I said, a beta version of an important software  package doesn't belong in a LTS version. in fact, the problems with FF3 have been reported weeks before the official release. enough time to revert the decision of including FF3. now you have the entire ubuntu world crawling with people having issues with FF. 

luckily, ubuntu has built a reputation for being solid and stable. but some more issues like this and you can bet that every ubuntu article in every computer magazine will remind you that ubuntu happens to knowingly include software that doesn't work properly. ubuntu will get away with that for the 
normal releases for a while. it will not for the LTS releases.

> 
2. Those that need stability should wait a bit before installing any new release. - No matter how many people test the software, some bugs are going to slip through. Because there is no way to test everything with just the development testers. When a release goes live the numbers increese, bugs are found, then fixed. But it takes time.


bugs are not a problem. every piece of software has them. knowingly including a "broken" software in a LTS release is strange. ignoring the cries of users before the official release about this very same problem is weird. especially for a "community based" software product.

> 
3. Your need to have the newest should be limited by your ability to troubleshoot problems. If your first course of action on finding a problem is posting the issue to the forum you may not have the skills needed. Realistically look at how knowlagable you are to fix a bug, if you cant, hold off on new releases. There is no sense having the "newest" thing if its broke and you cant fix it.


Well, I have been working with Linux since Debian 2.0... some time around the mid 90s, even though I have to admit that aside of a short and unhappy adventure with SuSE, I started to use Linux as my primary Desktop OS with the release of Gutsy - which worked almost perfect out of the box.

I can figure out most things, but quite frankly, I don't have the time any more. I can't sit in front of my PC for two hours trying to fix dependency hell or dealing with lousy drivers [which is why I dumped my ATI card for a Nvidia one].

> 
4. If you have room dont upgrade your install, add the new install to the disk. - Keep that old working no problems version until you are 100% sure you don't need to boot into it to get something done. In fact I just yesterday deleted my fiesty (I skipped Gutsy, read #5) partition because I wasn't using it. If you have issues , you can always boot into the old install and wait while looking into the problem.


in fact, I installed Hardy on a brand new machine that I bought just for this purpose. can't afford losing any data or to end up spending a day reinstalling the old OS. so no drama for me, but it hit me when I saw this topic and I felt I needed to add my comment so the people responsible will eventually see that they had a screwup there and that it's not just a couple people who are having issues.

> 
5. Do I really need to upgrade? - New users should ask themselves, "Do I really need to Upgrade?". Does the 6 month old operating system you have installed do everything you need? If so, why subject yourself to possible problems? Even non lts releases get 18 months of support. You can take your time and make sure you need to. You can skip a version altogether if you don't need the updated version or stability looks like a issue.


that's why I keep using Gutsy. but still, having the latest version of a software just feels "right"... if it doesn't happen to be a beta release.

---

### Post by skaboss on 2008-05-07
+1

Including a very unstable release of a very popular soft in a public release of Ubuntu is really a mess...
If only we had choice left between FF2 and 3. Unfortunaltely, last time i tried to uninstall FF3, aptitude proposed to uninstall all gnome-desktop!!!
The worst in this silly situation, is that i suspect Hardy developers (for whom i have the deeper respect) to have included FF3 just because of the better integration in the gnome desktop.... Messing all a great os, just in order to have better icon support in your browser seems quite unbelievable.

---

### Post by Kilz on 2008-05-07
> **LoneWolfJack said:**
> Kilz,

the wisdom behind my post was this:

if you [ubuntu/canonical] advertise a LTS release with emphasis on stability, DON'T include BETA software. especially not FF, which is known for having strange issues in every beta release [I'm saying that as someone who downloaded FF when their download-counter was 10k-something, and who has been happily using FF as primary browser ever since].
this has nothing to do with whether someone is a linux novice or not, it's about common sense, at least if we're talking about software that most users will rely on heavily.


Thats just it, I believe you have this idea that because its released it should be perfect. That isnt always the case with Linux. [URL="http://linux.oneandoneis2.org/LNW.htm"]Read section 3A
[/URL]
> **LoneWolfJack said:**
> 
no argument there. but like I said, a beta version of an important software  package doesn't belong in a LTS version. in fact, the problems with FF3 have been reported weeks before the official release. enough time to revert the decision of including FF3. now you have the entire ubuntu world crawling with people having issues with FF. 

luckily, ubuntu has built a reputation for being solid and stable. but some more issues like this and you can bet that every ubuntu article in every computer magazine will remind you that ubuntu happens to knowingly include software that doesn't work properly. ubuntu will get away with that for the 
normal releases for a while. it will not for the LTS releases.
The decision to include FF3 as I understand it is that Hardy is a LTS, it has 3 years of support. New software is not added after release, those that ran Dapper with Firefox 1.5 understand why they chose FF3. Dapper came out and then FF 1.5 was popular. Then FF2 was released. There is no FF2 for Dapper.
By including FF3 now they guaranteed FF3 for Hardy in year 2 and 3 when FF3 will be the main browser. But there is also the FF2 package in the repos, IF YOU DONT LIKE FF3 INSTALL FF2. I am happily running FF2 right now myself.


> **LoneWolfJack said:**
> 
bugs are not a problem. every piece of software has them. knowingly including a "broken" software in a LTS release is strange. ignoring the cries of users before the official release about this very same problem is weird. especially for a "community based" software product.
 The release is a week or so old now. FF2 is avilable if you dont like FF3. No one is forcing anything on you. The community uproar of "Why isnt FF3 in Hardy" 2 months from now (after the official ff3 release)if it wasn't included would have been deafening. 
Again no one is forcing anything, your choice to continue to use the FF3 browser is exactly that, Your Choice!

> **LoneWolfJack said:**
> Well, I have been working with Linux since Debian 2.0... some time around the mid 90s, even though I have to admit that aside of a short and unhappy adventure with SuSE, I started to use Linux as my primary Desktop OS with the release of Gutsy - which worked almost perfect out of the box.

I can figure out most things, but quite frankly, I don't have the time any more. I can't sit in front of my PC for two hours trying to fix dependency hell or dealing with lousy drivers [which is why I dumped my ATI card for a Nvidia one].
All this time and you havent figured out that installing a release of an operating system less than a month old is a bad idea for people wanting stability and perfection? If not consider this the lesson.


> **LoneWolfJack said:**
> 
in fact, I installed Hardy on a brand new machine that I bought just for this purpose. can't afford losing any data or to end up spending a day reinstalling the old OS. so no drama for me, but it hit me when I saw this topic and I felt I needed to add my comment so the people responsible will eventually see that they had a screwup there and that it's not just a couple people who are having issues.



that's why I keep using Gutsy. but still, having the latest version of a software just feels "right"... if it doesn't happen to be a beta release.

5. Do I really need to upgrade? - New users should ask themselves, "Do I really need to Upgrade?". Does the 6 month old operating system you have installed do everything you need? If so, why subject yourself to possible problems? Even non lts releases get 18 months of support. You can take your time and make sure you need to. You can skip a version altogether if you don't need the updated version or stability looks like a issue.

---

### Post by Kilz on 2008-05-07
> **skaboss said:**
> +1

Including a very unstable release of a very popular soft in a public release of Ubuntu is really a mess...
If only we had choice left between FF2 and 3. Unfortunaltely, last time i tried to uninstall FF3, aptitude proposed to uninstall all gnome-desktop!!!
The worst in this silly situation, is that i suspect Hardy developers (for whom i have the deeper respect) to have included FF3 just because of the better integration in the gnome desktop.... Messing all a great os, just in order to have better icon support in your browser seems quite unbelievable.

```
sudo apt-get install firefox2
```

Did you happen to use Dapper Drake?

---

### Post by liveB on 2008-05-07
I hate to feed the flames, and I'm no where near as experienced with Linux as the main contributers to this thread (Red Hat, Suse: both aborted failures as Windows replacement for me and Ubuntu Gutsy and Hardy).

> knowingly including a "broken" software in a LTS release is strange. ignoring the cries of users before the official release about this very same problem is weird. especially for a "community based" software product.

I have to say that I never really got FF to work "well" on Gutsy and tried Hardy 64 bit (beginning with Alpha 3, I think) and have had virtually NO problems or complaints!  Please, before assuming the mantel of "community", remember that there are CONFLICTING opinions to yours and yours is no more or less valid than OTHERS'.

The move (for me) to Hardy was an act of desperation based in innumerable "glitches, flaws, and heartaches" in both Gutsy 32 bit and 64 bit.  Hardy has reinforced my optimism about Linux, especially because of the smooth and nearly seamless operation of FF3 and other software.  My only problem to date was an ill advised attempt to add sound "stuff" from the studio release that was over my head and did cause FF to lock up -- but it was easily cured.

Bottom line, no choice is perfect for everyone and this is especially true of a complex system like Ubuntu/ Linux.  It's getting better, the developers DESERVE to have our feedback, but don't deserve griping, and nobody has the authority to be "spokesperson" for the community -- so stop claiming to be.

Oh, and can somebody PLEASE fix cinelerra?  Video editing is the only thing I miss about XP!

User-built: ASUS p5n-e, 4GB OCZ 800MHZ, Intel C2Quad 6600, Nvidia 8600, dual Asus lightscribe DVD, Hitachi 320GB HD, Logitech Cordless "Wave" keybd & mouse, Viewsonic 22in LCD, Ultra MD3 Media Center -- All functioning beautifully on Ubuntu Hardy 64 bit Desktop.:KS

---

### Post by LoneWolfJack on 2008-05-07
Kilz,

did you actually read *and* understand what I wrote? You see, what little time I have to post here I don't want spending on arguing about spilt milk.

You're free to think I'm just another linux novice, heck, try to insult me if you feel like it, that's ok if it makes you feel better.

Yet keep this in mind: the goal of ubuntu/canonical is to attract windows users. You can say many bad things about Microsoft. One is that they rush out unfinished products and use the buyers as beta testers. By including FF3, for all the good intentions, ubuntu does the very same thing. Joe average won't care about your reasons. He'll experience problems and link them with ubuntu.

Also, what's going to happen if it'll take another 5 beta's before FF3 goes out of beta? What if the issues for Linux are not fixed for months to come?

It would have been smarter to use FF2 and offer a FF3 package once it's stable.

---

### Post by Kilz on 2008-05-08
> **LoneWolfJack said:**
> Kilz,

did you actually read *and* understand what I wrote? You see, what little time I have to post here I don't want spending on arguing about spilt milk.

You're free to think I'm just another linux novice, heck, try to insult me if you feel like it, that's ok if it makes you feel better.

Yet keep this in mind: the goal of ubuntu/canonical is to attract windows users. You can say many bad things about Microsoft. One is that they rush out unfinished products and use the buyers as beta testers. By including FF3, for all the good intentions, ubuntu does the very same thing. Joe average won't care about your reasons. He'll experience problems and link them with ubuntu.

Also, what's going to happen if it'll take another 5 beta's before FF3 goes out of beta? What if the issues for Linux are not fixed for months to come?

It would have been smarter to use FF2 and offer a FF3 package once it's stable.

I read and understand exactly what you said.
But I think you might want to reread what I wrote.
1. Ubuntu once its released **[COLOR="Red"]will not[/COLOR]** get a major package like Firefox added. 
2. [From past history]("https://bugs.launchpad.net/dapper-backports/+bug/68158") with long term releases (Dapper Drake) we learn that its best to have the newest browser. [Dapper drake was released with Firefox 1.5 and never had Firefox 2]("http://packages.ubuntu.com/search?keywords=firefox&searchon=names&suite=dapper&section=all") because it was released a few months after Dapper Drake.
3. [Firefox 2 exists in the Hardy repositorie]("http://packages.ubuntu.com/hardy/firefox-2")s. 

Therefore you are complaining about what exactly? That its to hard to type 
```
sudo apt-get install firefox-2
```

You seem to think you have a right to complain about this, maybe you do, if I were you I'd demand a full refund.

---

### Post by Half-Left on 2008-05-08
It's acceptable to include FF3 beta in this LTS version, How many people will complain when FF3 is release stable it's not default and why use such a old version in years to come.

Last thing I want in the latest release is a older not very well integrated version of firefox which FF2 is. FF3 fixes alot of stuff and is now I believe the best version of all OS's and a native 64bit version as well.

---

### Post by LoneWolfJack on 2008-05-08
Kilz,

you do seem to have a major attitude problem. in fact, even before I replied to your first reply I knew you're not only known for indeed very helpful posts and scripts, but also infamous for having sheer hatred blazoned all over your posts.

If you think the "doesn't cost you anything so be happy about anything given to you" mentality will get ubuntu anywhere, just go on. But eventually you will find that without users who care, ubuntu will die. Think of the once so popular SuSE, which now only comes like third place behind Ubuntu and probably Mandriva.

There may be valid reasons behind the FF3 issue. Still, currently it is a mess. Considering the problems are far from being unexpected, this could have been solved in a much better way.

Feel free to post some more insults or lectures, but don't expect another reply,

---

### Post by Kilz on 2008-05-08
> **LoneWolfJack said:**
> Kilz,

you do seem to have a major attitude problem. in fact, even before I replied to your first reply I knew you're not only known for indeed very helpful posts and scripts, but also infamous for having sheer hatred blazoned all over your posts.

If you think the "doesn't cost you anything so be happy about anything given to you" mentality will get ubuntu anywhere, just go on. But eventually you will find that without users who care, ubuntu will die. Think of the once so popular SuSE, which now only comes like third place behind Ubuntu and probably Mandriva.

There may be valid reasons behind the FF3 issue. Still, currently it is a mess. Considering the problems are far from being unexpected, this could have been solved in a much better way.

Feel free to post some more insults or lectures, but don't expect another reply,

Your opinion does not reflect reality. IMHO what you are seeing may be a mirror. There have been no insults or attitude, only me pointing out facts and history.

---

### Post by Jouke74 on 2008-05-08
Typing this from my quite very ok working FF3, with sometimes a little surfing pause for the next wave :lolflag: 

The developers put FF3 Beta5 and FF2 in the repros... take the one you like. Not to mention there is still Opera, Swiftweasel, IE in wine for that matter..

Could some moderator please lock this thread?

---

### Post by p_quarles on 2008-05-08
Moved to Recurring Discussions. Keep the personal attacks out of the discussion, please.

---

### Post by 23meg on 2008-05-08
> **heroes_on_a_half_shell said:**
> Hey guys,

I've got 64 bit hardy running on my desktop with very few problems (upgraded from gutsy).  My one major issue has been that FF3 B5 creates a large demand for iowait cpu cycles every few minutes as indicated by the gnome resource monitor. This causes the firefox window to go grey and become unresponsive for a period of ~ 15 secs.  However, I don't believe this qualifies as a crash due to the fact that the webpage being viewed continues functioning.  Ex: a video on youtube or veoh will continue to play, albeit in black and white.

I guess I'd just like to know that this is a known problem, or if it's not, I'd like to know how to report it and maybe fix it, if at all possible.  Overall I like FF3, but I can't deal with this.

Thanks

Yes, it's been [reported and fixed]("https://bugs.launchpad.net/ubuntu/+bug/215728"). Make sure you're using an up-to-date mirror, update your  xulrunner and xulrunner-gnome-support packages, and if the issue persists, try [this]("http://tombuntu.com/index.php/2008/05/07/firefox-3-excessive-disk-io-and-freezing/"), or creating a new profile.

---

### Post by Half-Left on 2008-05-08
Or simply use Epiphany that comes with aload of useful extensions.

---

