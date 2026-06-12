---
title: "Upgrade"
date: 2013-02-12
forum: New to Ubuntu
---

### Post by Barney-R on 2013-02-12
I realise the following questions are extremely basic, but I'd rather ask now than possibly regret it later.

I'm somewhat belatedly planning to upgrade from Ubuntu 10.10 to 12.04 from a CD. I'll do this as an upgrade rather than a clean install, but I need to be sure I won't lose anything important in the process.

Can somebody please advise me as to any precautions I need to take before starting the upgrade?

I use cookies to remember log-in details for various sites (including this one), I have a number of important e-mails (as well as my account settings) in Thunderbird, and there are a few bookmarks in FireFox I'd rather not lose.

My Home folder, and anything else that may need protecting can be copied to a partition on a separate physical drive if necessary.

Will a second user account be adversely affected by the upgrade?

Will software I've installed be affected?

My previous experience of this kind of thing is limited to installing Ubuntu (10.10) to a new (blank) hard drive when the old drive failed, so I'm not entirely sure what I'm doing.

---

### Post by oldos2er on 2013-02-12
> **Barney-R said:**
> I'm somewhat belatedly planning to upgrade from Ubuntu 10.10 to 12.04 from a CD. I'll do this as an upgrade rather than a clean install, but I need to be sure I won't lose anything important in the process.

You can't upgrade directly from 10.10 to 12.04, you'd need to go from 10.10 to 11.04 to 11.10 to 12.04. That's an awful lot of upgrading and potential for something to go wrong, especially considering 11.04 is no longer supported.

Much easier to run a clean install of 12.04. You can create a list of installed applications to use once you get 12.04 installed: [http://stackoverflow.com/questions/187629/how-do-i-preserve-installed-applications-when-migrating-ubuntu-to-another-platfo](http://stackoverflow.com/questions/187629/how-do-i-preserve-installed-applications-when-migrating-ubuntu-to-another-platfo)

No matter which way you upgrade, backup any important data first.

---

### Post by ACubed10 on 2013-02-12
well the 1st thing I will tell you is to go on the Ubuntu Software Center and get a good backup utility.  Make a back up of at least your home folder.  This way if the upgrade goes wrong and you have to reinstall you will be ok.  Personally I have never upgraded, I've always backed up then clean installed. 

Im pretty sure the command to begin the upgrade is 
```
sudo do-release-upgrade
```

---

### Post by ibjsb4 on 2013-02-12
A big source of trouble are PPA's.  The upgrade will normally handle it, but not always.  I would suggest disabling ppa,s and not trusting the upgrade to do it for you.

And to be really safe, you can backup your whole system to another drive with something like clonezilla. 

[http://clonezilla.org/](http://clonezilla.org/)

Or maybe even back it up to a zip (tar) file.  Lots of backup ideas here:

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=system+backup&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=system+backup&sa=Search&cof=FORID:9)

---

### Post by ibjsb4 on 2013-02-12
Oldos2er has the better idea.  Backup your installed packages and go with a fresh install.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=backup+installed+packages&as_qdr=all&sa=Google+Search&lang=en&siteurl=](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=backup+installed+packages&as_qdr=all&sa=Google+Search&lang=en&siteurl=)

---

### Post by offgridguy on 2013-02-12
> **oldos2er said:**
> 
much easier to run a clean install of 12.04. You can create a list of installed applications to use once you get 12.04 installed: [http://stackoverflow.com/questions/187629/how-do-i-preserve-installed-applications-when-migrating-ubuntu-to-another-platfo](http://stackoverflow.com/questions/187629/how-do-i-preserve-installed-applications-when-migrating-ubuntu-to-another-platfo)

no matter which way you upgrade, backup any important data first.

+1

---

### Post by Barney-R on 2013-02-12
Thank you all for your fast responses.

Obviously a clean install is best, but then I'd lose all my cookies, and I don't remember my log-in details for some sites. I'd also have to reinstate all my settings. When I ran the CD recently it offered an upgrade as an alternative to a clean install. That's what made me think it could be the easier option.

Am I right in thinking the terminal command given by ACubed10 would re-enable the option to upgrade on-line? If I did this (assuming nothing went wrong), would I still be able to keep my settings, e-mails, bookmarks etc?

(I haven't really studied the terminal yet. I use it for a few things, but I don't really know what I'm doing.)

If upgrading, are there any advantages/disadvantages of one method over another (on-line against CD)?

I agree 100% with the following "*no matter which way you upgrade, backup any important data first*". I'll certainly do that with everything I can, but it usually happens that something gets overlooked.

What is a PPA? (mentioned by ibjsb4)

I could make a complete system backup as "insurance" (as shown in the following thread), but I don't really want a backup of 10.10.

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by ibjsb4 on 2013-02-12
Personal package archive (PPA).  Its a third party source to software packages that gets a lot of use by ubuntu users.  You won't find these packages in the software center unless you have added them.

[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

Want to know if you have any?  Open a terminal and enter:

```
cat /etc/apt/sources.list.d/*
```

If that command comes back empty then you have not added any.  Or if you have added any third party software, it can show up there.

---

### Post by Barney-R on 2013-02-12
Thanks for that, ibjsb4. I've got getdeb and medibuntu, plus Thunderbird and Opera (though I only use Opera on sites that don't like FireFox).

I's also like to thank oldos2er for the link to the e-book "I want to tell you the story of how you can take back control of your computer", which I've downloaded and started to read.

---

### Post by oldfred on 2013-02-12
Your Firefox & Thunderbird profiles are in /home in .  or hidden folders. I actually moved both profiles to my shared NTFS data partition and also copy to my laptop when I travel. That way I have all my same bookmarks & profiles. Best to houseclean all old emails to make it a bit smaller first. I only lose cookies when I do the full houseclean in Firefox, but I think that is on of the options to not houseclean,.

So a good backup of /home is most important as almost all programs save data & settings in /home. If multiple users then /home will include both. But if you do a new install be sure to use same names in the same order or else you have to change some UIDs or update ownership.

---

### Post by Barney-R on 2013-02-12
Thanks for that oldfred. Just two more questions and I think I'll be ready.

Firstly, can I just overwrite the existing FireFox and Thunderbird files after the upgrade (to be sure they contain all the relevant data)?

Secondly, am I right in thinking the terminal command "sudo do-release-upgrade" will re-enable upgrading from within Ubuntu?

Good point about clearing unwanted e-mails btw.

---

### Post by oldos2er on 2013-02-12
> **Barney-R said:**
> Am I right in thinking the terminal command given by ACubed10 would re-enable the option to upgrade on-line? If I did this (assuming nothing went wrong), would I still be able to keep my settings, e-mails, bookmarks etc?

I'm not sure how the command *sudo do-release-upgrade* will behave when upgrading to an EOL version. Maybe ACubed10 could expand on that if possible.

> (I haven't really studied the terminal yet. I use it for a few things, but I don't really know what I'm doing.)

If upgrading, are there any advantages/disadvantages of one method over another (on-line against CD)?

I agree 100% with the following "*no matter which way you upgrade, backup any important data first*". I'll certainly do that with everything I can, but it usually happens that something gets overlooked.

What is a PPA? (mentioned by ibjsb4)

I could make a complete system backup as "insurance" (as shown in the following thread), but I don't really want a backup of 10.10.

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

As mentioned, you only really need to backup your /home/user settings. I'm assuming you don't have a separate /home partition; you might want to consider creating one because it makes upgrading the OS much easier. 

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

[http://www.howtogeek.com/116742/how-to-create-a-separate-home-partition-after-installing-ubuntu/](http://www.howtogeek.com/116742/how-to-create-a-separate-home-partition-after-installing-ubuntu/)

---

### Post by Barney-R on 2013-02-12
Thanks for that, oldos2er, and for the useful links. I've got a much better idea what I'm doing now, but before marking the thread as solved, I'll just wait and see whether ACubed10 (or anyone) can shed some light on the "sudo do-release-upgrade" command.

If not, I'll just back everything up and try it to see what happens.

---

### Post by oldfred on 2013-02-12
For me to get both Firefox & Thunderbird to use old profile, I start them and they create a default new profile. I then go into profile.ini and change from the default to the old one I just copy into the same location next to the new one.

new Same for both Tunderbird & Firefox, just . folder is different.
[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

### Post by Barney-R on 2013-02-14
Thanks for all your help everyone.

I've learned a lot, but mainly I've realised there are so many things that could go wrong, and so much that I don't yet understand, that I've decided on a clean install.

I'm backing everything up, making notes of all the passwords I can remember, e-mail settings (at least Thunderbird makes them easy to find), copying important e-mails, my address book, wanted bookmarks and anything else I can think of, and when it's all done I'll install 12.04 (single boot) with a separate /home partition.

It seems the software repositories for 10.10 are disappearing, so there's not much point trying to keep it any longer.

Thanks again for all your help. I'll mark this thread as solved.

---

### Post by clive littlewood on 2013-02-14
Hi

Just a couple of points that might help in future.

For all your internet passwords use Last Pass in any browser, this will retain all your passwords and it is then easy when using a clean install.

If your using chrome or firefox you can sync all your data to the cloud and then on a clean install all the data will be synced back to the new browser.

Hope this helps

Clive

---

### Post by oldfred on 2013-02-14
If you have the separate /home or separate data partitions you can put the new install in 10 to 25GB. Then you have old install to use if you have issues with new version and can still use old one until you resolve issues.

I often suggest the separate /home but actually use separate data partitions and keep /home with just the hidden files & folders inside / (root). 

       Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

