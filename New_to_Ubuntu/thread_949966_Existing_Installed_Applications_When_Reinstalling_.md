---
title: "Existing Installed Applications When Reinstalling the OS?"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by H.Callahan on 2008-10-16
Ok, I am beginning to feel a bit anxious about the upcoming updates and the updates following that.

I installed 7.10 on an old machine to try it out.  I was happy with it and configured it and installed apps and basically got everything the way I wanted it.

Then I got the urge to upgrade to 8.04.  I upgraded rather than do a complete re-install as I don't know what all I have installed and how I got them all configured.  Well, the upgrade kinda blew up on me and now my system is somewhat unstable.

8.10 is lurking around the corner and 9.04 after that.  Based on my experience, I am assuming that a complete reinstall with a newer version is preferable to upgrade -- same situation as with Windows.  However, with Windows, if you want to do a clean reinstall, all the applications that you have have to be reinstalled and reconfigured as well.  

I know **most** <-(key word here) applications keep their config file in the /home directory.  Backing that up is a no-brainer.  But, how do I find out what all is installed and where the config files actually are?  What about files like fstab that I have customized to mount things where I want them?  What about other system level files that I may have tweaked to get things to work?

Obviously, I have not kept copious notes about everything that I did.  I probably will not do so in the future.  So, my question is, am I going to have to go through this fire drill every six months?  Is there any way to ease the pain of redoing EVERYTHING with a new OS every 6 months?

---

### Post by Therion on 2008-10-16
Download [QuickStart](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11) and backup your /home, /, and /config directories.

---

### Post by Paqman on 2008-10-16
No problem. All the config files are in /home as you say, and the system can spit out a list of all the installed software:
```

dpkg --get-selections > installed-software

```

To reinstall all those packages in one step you'd use:
```

dpkg --set-selections < installed-software

dselect

```

Although this will reinstall ALL packages, some of which may be obsolete on the new version. You can always edit the text file to remove all the system bumf and only include things you recognise as stuff you've installed yourself.

---

### Post by celticbhoy on 2008-10-16
[http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html](http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html)

Have a look here for what you got installed

---

### Post by Zill on 2008-10-16
> **H.Callahan said:**
> ...So, my question is, am I going to have to go through this fire drill every six months?  Is there any way to ease the pain of redoing EVERYTHING with a new OS every 6 months?
Unless you always want the "latest and greatest" there is no reason at all to upgrade every six months.  "If it ain't broke don't fix it" is a very wise maxim. :-)

The current LTS release, Hardy (8.04), is supported until April 2011, longer for the server version.

[https://wiki.ubuntu.com/Releases]("https://wiki.ubuntu.com/Releases")

---

### Post by celticbhoy on 2008-10-16
of course if your system is running fine using software from the repos and you wait a couple of weeks to check out any potential probs there is no reason why you should have any trouble after an upgrade

---

### Post by H.Callahan on 2008-10-17
> **Zill said:**
> Unless you always want the "latest and greatest" there is no reason at all to upgrade every six months.  "If it ain't broke don't fix it" is a very wise maxim. :-)

The current LTS release, Hardy (8.04), is supported until April 2011, longer for the server version.

[https://wiki.ubuntu.com/Releases]("https://wiki.ubuntu.com/Releases")

My understanding is (and it may be wrong) that if you don't upgrade to the latest version, that you don't get the latest updates to installed packages.  For example, if I stay with 8.04 for a while and, say, Firefox upgrades to version 4, I won't be able to get the lastest version because FF3 is what is supported in 8.04.  Isn't that correct?  If so, one is kinda forced to stay with a fairly current version of the OS, to make sure that you have recent versions of the software.

(Thanks to all that offered suggestions.  I will give them a try and see how they work.)

---

### Post by snowpine on 2008-10-17
> **H.Callahan said:**
> My understanding is (and it may be wrong) that if you don't upgrade to the latest version, that you don't get the latest updates to installed packages.  For example, if I stay with 8.04 for a while and, say, Firefox upgrades to version 4, I won't be able to get the lastest version because FF3 is what is supported in 8.04.  Isn't that correct?  If so, one is kinda forced to stay with a fairly current version of the OS, to make sure that you have recent versions of the software.

(Thanks to all that offered suggestions.  I will give them a try and see how they work.)

You are correct that Firefox 4 will never be in the 8.04 repositories; however, there are other ways to install software. One way is using the Ubuntu "backports" which is basically an alternate repository containing newer versions of applications. The other way is to download the hypothetical FF4 from the Mozilla website and install it into 8.04 from the .deb's. 

Check out any of the recent threads on OpenOffice 3 for a case study.

---

### Post by eternalnewbee on 2008-10-17
> **H.Callahan said:**
> My understanding is (and it may be wrong) that if you don't upgrade to the latest version, that you don't get the latest updates to installed packages.  For example, if I stay with 8.04 for a while and, say, Firefox upgrades to version 4, I won't be able to get the lastest version because FF3 is what is supported in 8.04.  Isn't that correct?  If so, one is kinda forced to stay with a fairly current version of the OS, to make sure that you have recent versions of the software.

(Thanks to all that offered suggestions.  I will give them a try and see how they work.)

Hi there.
Correct me if I'm wrong, but I don't think upgrading Ubuntu influences updating Firefox.

---

### Post by snowpine on 2008-10-17
> **eternalnewbee said:**
> Hi there.
Correct me if I'm wrong, but I don't think upgrading Ubuntu influences updating Firefox.

When I dist-upgraded from Gutsy to Hardy, my Firefox upgraded from 2.x to 3.x.

I think that if you've installed Firefox through another method (i.e. not from the Ubuntu repositories) then it does not upgrade when you dist-upgrade. But I am not 100% sure on that one.

---

### Post by eternalnewbee on 2008-10-17
> **H.Callahan said:**
> My understanding is (and it may be wrong) that if you don't upgrade to the latest version, that you don't get the latest updates to installed packages.  For example, if I stay with 8.04 for a while and, say, Firefox upgrades to version 4, I won't be able to get the lastest version because FF3 is what is supported in 8.04.  Isn't that correct?  If so, one is kinda forced to stay with a fairly current version of the OS, to make sure that you have recent versions of the software.

(Thanks to all that offered suggestions.  I will give them a try and see how they work.)

Hi there.
Correct me if I'm wrong, but I don't think upgrading Ubuntu influences updating Firefox.

---

### Post by Malac on 2008-10-17
Rather than do a dist-upgrade you could just wait a few weeks then change the /etc/apt/sources.list entries from hardy to intrepid.
It's *definitely* not one of the recommended methods but I have done this on one of my machines from Breezy right through the updates to Hardy without any problems.
That way my settings files e.g. /etc/fstab, installed software and so on stay how they are. The only time I ever had trouble with this was the changeover from /dev/hdX to /dev/sdX notation in fstab.

As with *any* major upgrade, even the official way, do a full backup of your whole system then you can always return to that if it mungs up somewhere.

Hope this helps.

---

### Post by LowSky on 2008-10-17
> **Malac said:**
> Rather than do a dist-upgrade you could just wait a few weeks then change the /etc/apt/sources.list entries from hardy to intrepid.
 

I would not do that, it leads to too many issues

---

### Post by Malac on 2008-10-17
> **LowSky said:**
> I would not do that, it leads to too many issues
As I said I only ever had the one problem(issue) with the fstab notation change in all the "transitions" but your mileage may be different.

---

### Post by eternalnewbee on 2008-10-17
> **LowSky said:**
> I would not do that, it leads to too many issues

I don't know what kind of issues, but I still agree, because it sounds too technical for the "eternalnewbee"...
I say that, not because I'm too lazy to learn, but because I'm playing advocate to the devil...
If you know what I mean...
Live long and may the Ubuntu force be...

---

### Post by Paqman on 2008-10-17
> **LowSky said:**
> I would not do that, it leads to too many issues

Neither would I. There's a proper upgrade system provided. Why avoid using it?

---

### Post by H.Callahan on 2008-10-17
> **Paqman said:**
> Neither would I. There's a proper upgrade system provided. Why avoid using it?
Because the using the proper upgrade from 7.10 to 8.04 has caused my system to become unstable.  Not being a Linux god, I am at a bit of a loss as to what to do with it.  ...and reading through the notes it seems that the upgrade vs. total reinstall causes problems.  (That doesn't surprise me, as the same thing exists in Windows.  One should never upgrade from one Windows version to another -- a reinstall is always better, although a lot more painful).  With essentially a new version of Ubuntu coming out every 6 months, that is a whole lot of pain to go through in a short amount of time.

---

### Post by Zill on 2008-10-17
> **H.Callahan said:**
> My understanding is (and it may be wrong) that if you don't upgrade to the latest version, that you don't get the latest updates to installed packages.  For example, if I stay with 8.04 for a while and, say, Firefox upgrades to version 4, I won't be able to get the lastest version because FF3 is what is supported in 8.04.  Isn't that correct?  If so, one is kinda forced to stay with a fairly current version of the OS, to make sure that you have recent versions of the software.
Correct, but you could always use the backports as suggested by snowpine.

However, you have to ask yourself if you really *need* FF4.  Ubuntu updates will ensure that FF3 receives all the latest security updates so you will only miss the latest "bells and whistles" - that you may not *really* require. ;-)

I am still running Dapper (6.06) on my primary PC, as it is a rock-solid distro that does everything I *need* very reliably.  I will upgrade eventually, but to the latest LTS version i.e. Hardy 8.04, which I trust will then have a similar level of reliability.

---

### Post by jerome1232 on 2008-10-17
I see backports has been mentioned. :) Other than backports yes versions are frozen with the release, security related things are patched in so say ssh says versions 1.4- are vulnerable and Ubuntu uses 1.3, well your not actually vulnerable because Ubuntu patched the fix into our version.

I personally am starting to skip every other upgrade, and prefer starting from a clean slate and reconfiguring everything, since it is those configurations that often is causing the breaking when upgrading.

---

### Post by H.Callahan on 2008-10-17
I wish the repositories were more open.  I would like to see all current versions of all applications available to all releases.  If a particular program (say the hypothetical FF4) requires a minimum release version, then it should tell me that and I can make the decision on whether I want to upgrade releases to support it.  If, however, it will run fine on my current release, then it should be available for me to install.

Yes, I realize that I could go to Mozilla and download it, but that puts me back in the Windows model of distribution in that I have to go website to website looking for newer versions of software.  That seems to be anti the Ubuntu software distribution model, right?

---

### Post by jerome1232 on 2008-10-17
You could try Debian, it's on a rolling release schedule.

---

### Post by philinux on 2008-10-17
The backports are exactly for things like FF whatever version and OO type stuff even for a LTS version.
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

I think I'm right in saying that Debian does not include the latest and greatest.

---

### Post by snowpine on 2008-10-17
> **H.Callahan said:**
> I wish the repositories were more open.  I would like to see all current versions of all applications available to all releases.  If a particular program (say the hypothetical FF4) requires a minimum release version, then it should tell me that and I can make the decision on whether I want to upgrade releases to support it.  If, however, it will run fine on my current release, then it should be available for me to install.

Yes, I realize that I could go to Mozilla and download it, but that puts me back in the Windows model of distribution in that I have to go website to website looking for newer versions of software.  That seems to be anti the Ubuntu software distribution model, right?

Actually, the "Ubuntu software distribution model," as I understand it, is that everyone using the same release has the same package versions, unless you specifically and manually install a different version. This gives each release a certain identity, stability, and consistency. 

It's like if I go to my Honda mechanic and say "I need new brakes for my 2003 Civic." I don't want them to give me the 2008 version because it's newer and therefore "better." If I choose to hot-rod my car and install the 2008 brakes myself, I would be doing so at my own risk. :) My expectation is that the factory-authorized mechanic (i.e. the Ubuntu repository) should install the "correct" (i.e. tested and stable) version that best fits my make and model.

---

### Post by snowpine on 2008-10-17
> **jerome1232 said:**
> You could try Debian, it's on a rolling release schedule.

You are thinking of Debian Sid, the "unstable" branch. Debian "stable" (currently Etch, soon to be Lenny) upgrades even slower than Ubuntu.

---

### Post by jerome1232 on 2008-10-17
Yes but it's on a rolling release schedule. I just meant as to version freezing. 

Ubuntu is based on Debian unstable when it's released correct?

You are correct about Debian stable not being the latest and greatest, but unstable is pretty new.

---

### Post by snowpine on 2008-10-17
> **jerome1232 said:**
> 
Ubuntu is based on Debian unstable when it's released correct?


My understanding is the Ubuntu folks take a "snapshot" of Debian Sid every 6 months and use that as the starting point for the next Ubuntu release.  

And of course I forgot to mention Debian "testing" (currently Lenny). So there are always three different Debian releases (stable, testing, unstable) at any given time. Depending on your needs you can choose which is best for you. There is no release schedule; testing does not get promoted to stable until it is really, really stable. It's a cool system, in my opinion.

---

### Post by Paqman on 2008-10-17
> **H.Callahan said:**
> Because the using the proper upgrade from 7.10 to 8.04 has caused my system to become unstable.  Not being a Linux god, I am at a bit of a loss as to what to do with it.  ...and reading through the notes it seems that the upgrade vs. total reinstall causes problems.  (That doesn't surprise me, as the same thing exists in Windows.  One should never upgrade from one Windows version to another -- a reinstall is always better, although a lot more painful).  With essentially a new version of Ubuntu coming out every 6 months, that is a whole lot of pain to go through in a short amount of time.

Fair enough, but the official method is either Update Manager or a reinstall, so that's probably the advice you should stick to in Absolute Beginners.

I wouldn't equate an Ubuntu reinstall with a Windows one, either. Windows is a nightmare to reinstall, as you have to reinstall every single app one at a time, and do endless reboots. With well supported hardware, a pre-formatted disk, a seperate /home and a list of your installed packages it shouldn't take any more than an hour tops to install Ubuntu.

---

### Post by H.Callahan on 2008-10-17
> **snowpine said:**
> It's like if I go to my Honda mechanic and say "I need new brakes for my 2003 Civic." I don't want them to give me the 2008 version because it's newer and therefore "better." If I choose to hot-rod my car and install the 2008 brakes myself, I would be doing so at my own risk. :) My expectation is that the factory-authorized mechanic (i.e. the Ubuntu repository) should install the "correct" (i.e. tested and stable) version that best fits my make and model.

I see it more like if my radio/CD player broke in my 2003 Civic.  If the 2008 radio/CD features an auxiliary port, can read MP3 CDs, has built in satellite radio and will fit in the hole occupied by the old radio and use the same electrical harness, I definitely want the option to install it in my 2003 Civic.  I can choose not to and get a 2003 replacement, but I definitely would like the option.

---

### Post by jerome1232 on 2008-10-17
> **H.Callahan said:**
> I see it more like if my radio/CD player broke in my 2003 Civic.  If the 2008 radio/CD features an auxiliary port, can read MP3 CDs, has built in satellite radio and will fit in the hole occupied by the old radio and use the same electrical harness, I definitely want the option to install it in my 2003 Civic.  I can choose not to and get a 2003 replacement, but I definitely would like the option.

That's what the backports repos are. Word for word.

---

