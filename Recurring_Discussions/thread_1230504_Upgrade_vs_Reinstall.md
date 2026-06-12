---
title: "Upgrade vs Reinstall"
date: 2009-08-03
forum: Recurring Discussions
---

### Post by slakkie on 2009-08-03
From another thread, where I made my initial rant, but I think it deserves its own thread.. 

Why are people advising fresh installs over upgrading?

I have been upgrading all my Ubuntu PC's from version 5 (when I started with Ubuntu). I've had one problem when upgrading from 8.04 to 8.10 on the day 8.10 got released. Reinstalled 8.04 (who needs backup eh?!) a couple of days later. It was an Intel driver issue in xorg, pretty crucial on a desktop. But I would have had that problem even if I did a fresh install. Which is mostly the argument to do a fresh install, otherwise you'll end up with problems.. 

If I would have done that upgrade now I would not have any problems. I would probably, no, I know I would have upgraded directly to the latest stable version to see if the bug got fixed, which would have been the case.. 

Maybe it is me, I don't like to reinstall because it is so the [#1 bug to do](https://launchpad.net/bugs/1). Or is it because a reinstall... an upgrade is so much more logical to do, if your release is supported you can upgrade to a current release use that one for a while and upgrade later on. 

If you have an EOL release, I can maybe understand it a bit better, but even then, it is possible to upgrade without too much of a problem to a current release.

So, it is just me who thinks we should not advise reinstalls when an upgrade does the same or should the community activly support fresh installs because that is just easier or less error prone..?


Ps. If this is in a wrong forum, you can move it, didn't know where to put it, installs and upgrades, community cafe or here..

---

### Post by HappyFeet on 2009-08-03
I think it is just a personal decision. But, if you look around the forums, you will see a lot of people that have had problems after upgrading, such as sound no longer works, screwed up video drivers, etc.

I personally, refuse to upgrade and always do fresh installs. Besides, upgrades actually take longer than fresh installs for most people. It only takes me 7 or 8 minutes to do the base install, (yes, I have a very fast computer) and another 45 min. or so to get back all my apps that I use. Being that quick, why would I want to spend several hours upgrading and then take a chance that something may not work right? Plus, I keep all personal files on separate drives, so I don't need to worry about backing up and restoring those.

If you have no problems upgrading, that is fine if that is what you prefer, but I could not stand it, knowing there may be left over cruft and configuration files that may not play nice with the new OS.

Also, it is a well known fact that fresh installs are *usually* more problem free. (I have my own pc repair business, and know these things ;) )  I know 3 people personally that upgraded their ubuntu machines and later regretted it, and wound up doing a fresh install anyway. I'm not saying that upgrading will always lead to problems, but there is less likliehood  of problems with a fresh install.

Like I said, it is more of a personal choice than anything else. Good luck with your upgrades in the future.

---

### Post by ajgreeny on 2009-08-03
I think it is better to do a clean install and start again, personally, particularly if there are a lot of third party repositories used by the system.  If you use only applications that are from the ubuntu repos I suspect it is probably easier to upgrade, but if you have added various ppa repos and maybe wine and medibuntu and others you are probably in for a disappointment.

Also even on my comparatively slow computer compared to HappyFeet's, I can download the new iso in about 20 mins, install in another 20 mins and add all my extras in about an hour at most, so an upgrade is much slower and I can't do anything while it happens.

---

### Post by Tamlynmac on 2009-08-03
> HappyFeet
Like I said, it is more of a personal choice than anything else.

I've had a number of individuals (I've assisted with the installation of Ubuntu) upgrade (online) and none have complained to me that they've had any issues with upgrading. I'm certain they would have notified me immediately. :D

I can visualize issues and objections to both options. For example, I had 8.04 disk (that I used religiously and protected) that apparently failed with age. You can imagine the outcome (without detail) of the next install. I immediately grabbed a new disk and the reinstalled went smoothly. I also know users that have poor net connects that literally prohibit online upgrading or even downloading of the new version file, without temping fate.

So, I must agree with HappyFeet.

Just seems logical to use what works - until it doesn't, then select a different option. Isn't choice a wonderful thing?

---

### Post by slakkie on 2009-08-04
> **HappyFeet said:**
> I think it is just a personal decision. But, if you look around the forums, you will see a lot of people that have had problems after upgrading, such as sound no longer works, screwed up video drivers, etc.


The forums are being used more by people who have problems then by people who do not need to ask a question. So based on only forum results you can only say that a particular percentage of people have problems with some upgrades of Ubuntu. People who have succesfully upgraded are generally not heard on the forums (or irc/maillinglists).

> 
I personally, refuse to upgrade and always do fresh installs. Besides, upgrades actually take longer than fresh installs for most people. It only takes me 7 or 8 minutes to do the base install, (yes, I have a very fast computer) and another 45 min. or so to get back all my apps that I use. Being that quick, why would I want to spend several hours upgrading and then take a chance that something may not work right? Plus, I keep all personal files on separate drives, so I don't need to worry about backing up and restoring those.


An upgrade doesn't take that long, you forget that you need to download the ISO, and the upgrade process first has to download all packages, which takes  just as long as downloading the ISO. Then you need to burn the ISO. I think, from start to finish the upgrade takes just as long as a fresh install, with the added benefit of not losing your configuration of /etc. And no afterwork of adding packages which the default install does not provide, but you needed.

> 
If you have no problems upgrading, that is fine if that is what you prefer, but I could not stand it, knowing there may be left over cruft and configuration files that may not play nice with the new OS.


Have you ever tried to upgrade? I'm just asking since you refuse to upgrade and always do fresh installs.. You can purge removed packages.. Removing their config files, and I don't think packages will use eachother configuration files.

> 
Also, it is a well known fact that fresh installs are *usually* more problem free. (I have my own pc repair business, and know these things ;) )  I know 3 people personally that upgraded their ubuntu machines and later regretted it, and wound up doing a fresh install anyway. I'm not saying that upgrading will always lead to problems, but there is less likliehood  of problems with a fresh install.


Maybe, but I think fresh installs are just as likely to cause problems. If a certain package causes problems it does not matter wheter that package is installed by the upgrade or the fresh install.

> 
Like I said, it is more of a personal choice than anything else. Good luck with your upgrades in the future.

It is a way of working, but I saw in a thread where someone asked questions about an upgrade got a whole bunch of replies to do a fresh install, without any argumentation. I don't think that is a propper way to help people.

---

### Post by HappyFeet on 2009-08-04
Bottom line is to do what you want.

You asked for opinions, and I gave you mine. I'm not going to argue about it or give any more reasons why you should or should not do it. Take care and good luck.

---

### Post by slakkie on 2009-08-04
It is a discussion forum. I just had some remarks on your reply. I'm not saying NEVER reinstall.

---

### Post by 3rdalbum on 2009-08-04
I think the "upgrades don't work properly" anecdotes mostly come from new users, who have messed around with their systems so much that they don't work in the Ubuntu-approved way.

For instance, if you install graphics card drivers manually, then try to dist-upgrade, there will be a driver/kernel mismatch. New users might not realise that they just need to reinstall their driver, and think that "the upgrade didn't work".

Other problems could arise from the semi-intelligence that the Update Manager has, that performs certain system operations over and above what the packages themselves define. If you've already done something that will conflict with what the Update Manager will do, then you will run into troubles.

I've dist-upgraded a number of times and never had any real issues. If you want to start afresh, or you want to make sure you're getting everything that's available in a new Ubuntu install, then do a fresh install by all means. My last dist-upgrade was missing notify-osd and the New Wave theme.

---

### Post by Arthur_D on 2009-08-04
> **3rdalbum said:**
>  For instance, if you install graphics card drivers manually, then try to dist-upgrade, there will be a driver/kernel mismatch. New users might not realise that they just need to reinstall their driver, and think that "the upgrade didn't work".
QFT! I'm doing this, because the recommended driver doesn't work; a bit frustrating having to reinstall it all the time, but at least I get a really up-to-date system (and no, I've never had any problems upgrading Ubuntu or the proprietary NVIDIA driver).

---

### Post by Sef on 2009-08-04
Moved to Recurring Discussions as this is not a new question.

---

### Post by ukripper on 2009-08-04
> **happyfeet said:**
> i think it is just a personal decision. But, if you look around the forums, you will see a lot of people that have had problems after upgrading, such as sound no longer works, screwed up video drivers, etc.

I personally, refuse to upgrade and always do fresh installs. Besides, upgrades actually take longer than fresh installs for most people. It only takes me 7 or 8 minutes to do the base install, (yes, i have a very fast computer) and another 45 min. Or so to get back all my apps that i use. Being that quick, why would i want to spend several hours upgrading and then take a chance that something may not work right? Plus, i keep all personal files on separate drives, so i don't need to worry about backing up and restoring those.

If you have no problems upgrading, that is fine if that is what you prefer, but i could not stand it, knowing there may be left over cruft and configuration files that may not play nice with the new os.

Also, it is a well known fact that fresh installs are *usually* more problem free. (i have my own pc repair business, and know these things ;) )  i know 3 people personally that upgraded their ubuntu machines and later regretted it, and wound up doing a fresh install anyway. I'm not saying that upgrading will always lead to problems, but there is less likliehood  of problems with a fresh install.

Like i said, it is more of a personal choice than anything else. Good luck with your upgrades in the future.

+1 i fully agree with you.

---

### Post by slakkie on 2009-08-04
> **Sef said:**
> Moved to Recurring Discussions as this is not a new question.

Search on topic title must be improved then (since nothing was found, checked for dupes).

---

### Post by schmidtbag on 2009-08-06
for me, upgrading worked, but not well.  when i went from 8.10 to 9.04 from an upgrade, it removed some programs i was still using and i got some random glitches like the nautilus desktop and gnome-panel not starting up when i log in, and my screen resolution would never change either even though i had proper video drivers.  i had to create scripts to start these up manually.  also, after my upgrade, my kernel was stuck at version 2.6.28-11 - it would never go higher.  i also noticed that some of the default preference programs never upgraded.

then after an accident of having half of my home folder deleted, i figured i might as well just reinstall ubuntu and clear up all these little tedious problems.  i did, and then everything worked great

so reinstalling is better than upgrading, at least in my case

---

