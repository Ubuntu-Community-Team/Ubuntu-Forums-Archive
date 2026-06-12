---
title: "HOWTO:  Fix screensaver for KDE 3.5.3"
date: 2006-06-27
forum: Outdated Tutorials &amp; Tips
---

### Post by Lil_Eagle on 2006-06-27
If you have updated your KDE from [http://kubuntu.org]("http://kubuntu.org") then you might have noticed that there is a bug with the screensaver not activating automatically, even when the box is checked to do so.

To fix this, go to: [http://megaflexdestiny.net/bits/kde353screensaverfix/]("http://megaflexdestiny.net/bits/kde353screensaverfix/") and download the file libkdeinit_kdesktop.so.

Install it:```
sudo cp /usr/lib/libkdeinit_kdesktop.so /usr/lib/libkdeinit_kdesktop.so.old
sudo cp Desktop/libkdeinit_kdesktop.so /usr/lib/

```

Of course you'll have to change the second command to point to where the file really is.

Once you've copied that file, restart X by pressing <CTRL><ALT><BKSP>, or reboot your machine.

Your screensaver should work.

There are both 32 bit and 64 bit versions of the necessary file.  These files were created by compiling the latest snapshot of kdebase from kde.org.

EDIT: Filename spelled incorrectly, now fixed.

---

### Post by Hobbsee on 2006-06-28
The edgy packages were fixed with this last night, and the dapper packages should soon be rebuilt with this fix.

Please do not use an unofficial fix in the mean time, as the proper fix is so close.

---

### Post by Lil_Eagle on 2006-06-28
> Please do not use an unofficial fix in the mean time, as the proper fix is so close.

How are we supposed to know that?  I mean, think about it.  KDE 3.5.3 was released on June 1, 2005, the same day that Dapper was released, yet the ubutuntu repositories 4 weeks later still only have 3.5.2 in them.  For those of us who knew KDE 3.5.3 was available (since it was mentioned on the Kubuntu website) it was tempting to upgrade.  Especially after reading about the numerous bug fixes.

The version that was released had a bug with the screensaver.  According to KDE, that bug was squashed on June 14.  Yet, noone listened to the complaints about the sceensaver.  The solution was rather simple.  Recompile kdesktop with the bugfix provided by KDE.

While it may not suit your fancy to use "unstable" code, no one is forcing you to do so.  It is entirely up to you what you do to your system.  You don't have to download the file, nor install it.

I thought the broken screensaver was a major enough issue to warrent an immediate bug fix and all I did was provide a simple method for others to fix the aformentioned bug.  

Do you not think that the screensaver is a high priority?  What about in a setting where security is important.  You walk away from your computer, thinking that your screensaver will kick in a minute, and since you have it set to lock, you think that once it starts that your session is safe.  If however, the screensaver never starts, then it will not lock, thus your session is still open to anyone who happens to walk by.

Now this may sound a little drastic, but people do think that way.  Surely a better solution would be to manually lock the session whenever one leaves their computer.  I can assure you not many people do that, including me.

---

### Post by Rastareefer on 2006-07-06
Thanks for the fix.

I am glad the "Edgy packages" have been fixed but as a newbie I am afraid I wouldn't know an edgy package if it hit me in the face much less what to do with it.

Hence, I am gratefull for the fix and instruction guide that even a newbie can comprehend.

I mean if the bug has been fixed, where do we get the fix & how does one install it?
Is this going to be a complete download of K/Ubuntu and instalation?

---

### Post by arizonagroovejet on 2006-07-06
[QUOTE=Rastareefer]
I am glad the "Edgy packages" have been fixed but as a newbie I am afraid I wouldn't know an edgy package if it hit me in the face much less what to do with it.
[/QUOTE]

The next version of Ubuntu, currently in development, is called Edgy Eft. Edgy packages are packages are for people already using the development versions of Edgy Eft. 

[QUOTE=Rastareefer]
I mean if the bug has been fixed, where do we get the fix & how does one install it?
Is this going to be a complete download of K/Ubuntu and instalation?[/QUOTE]


The fix has been done in the KDE source code. (The problem is a KDE problem not a Kubuntu problem - users of other distros have also found the screensaver not working.)  For the fix to be easily available for Dapper one of the Kubuntu maintainers has to make a new version of the kdeskop package including the fix and put it in the Dapper repos. Such a package would show up automatically in adpet-notifier for you to install.
Having no idea when that would happen and being tired of having no screensaver  I came up with my own solution to the problem and made it available to those who wanted to try it.
If you've installed the fix file from my website then installing a kdestop package delivered via adept should overwrite it. If the new kdesktop package includes the fix then your screensaver should keep working, if not it'll probaby stop working again.

If/when a new kdestop package appears for Dapper I'll be testing it to see if it fixes the screensaver problem and if it does then I'll modify the webpage to indicate the the bug is now fixed in the latest Kubuntu updates and that people should use those instead. 

Hope that clarifies things a bit for you,

mike

---

### Post by Rastareefer on 2006-07-06
Yes, thanks.
You seem to have nailed it all.

---

### Post by casperlingus on 2006-07-10
Is there a reason the link is down?  Is there somewhere else from where I can get the updated *.so file?  

In fact, 2 days ago my office decided to make a rule requiring 5-minutes-til-screensaver-locking rule.  I think I'm the only one that's not compliant at the moment (the only linux user, too).

I guess I'll apt-get xscreensaver and run that for now.

Casper...

---

### Post by arizonagroovejet on 2006-07-10
> **casperlingus said:**
> Is there a reason the link is down? 

Not that I'm aware of. I can access the site fine right now both fromhome and from another place I have shell access.
What are you seeing - a 404, a 'forbidden' message or just timing out?

> **casperlingus said:**
>  Is there somewhere else from where I can get the updated *.so file?  

Yes, email me (see profile) and I'll email you back.

---

### Post by Lil_Eagle on 2006-07-11
One thing I noticed was that when I upgraded to Edgy, I kept getting the message that libkdeinit_kdedesktop.so was not a system link.  It didn't cause any problem, but during the upgrade the message appeared at least 20 times.  Since then, I have downgraded back to dapper because Edgy was too unstable for me.

While I don't mind broken packages once in a while, the kernel being broken is not something that I can accept.  It's probably fixed by now, but I figured I'd just wait until the second or third alpha.

Why dapper is still kde 3.5.2 I have no idea.  I would expect a backports package, but more than a month after the release of 3.5.3 it still isn't to be seen.  The packages on kubuntu.org are the same ones that were there a month ago as well.

It seems that most effort is going to edgy, even though dapper is LTS.  I suppose that means LTW (long term waiting) as well.

---

### Post by mexlinux on 2006-07-14
Your file semi-solved my problem, It blanks the screen but it does not start the screen saver...

Well, we can always use xscreensaver anyway

---

### Post by Lil_Eagle on 2006-07-14
Are you sure the screensaver is selected?  If it blanks your screen then we know it at least can tell that you aren't using the keyboard or mouse for a period of time.

I can assure you that the 64-bit version works.  You'll have to ask arizonagroovejet about the 32-bit verison because that one is his doing.

---

### Post by Hobbsee on 2006-07-15
> **Lil_Eagle said:**
> How are we supposed to know that?  I mean, think about it.  KDE 3.5.3 was released on June 1, 2005, the same day that Dapper was released, yet the ubutuntu repositories 4 weeks later still only have 3.5.2 in them.  For those of us who knew KDE 3.5.3 was available (since it was mentioned on the Kubuntu website) it was tempting to upgrade.  Especially after reading about the numerous bug fixes.

The version that was released had a bug with the screensaver.  According to KDE, that bug was squashed on June 14.  Yet, noone listened to the complaints about the sceensaver.  The solution was rather simple.  Recompile kdesktop with the bugfix provided by KDE.

To be truthful, i've known about that patch for quite a while, (ie, since we got the link in kde bugs about it), but it's taken me a while to get access to those packages - sure, i can compile a fix, but i cant give you all ssh into my laptop to grab the fix. (and there were issues about "is it built cleanly, will it screw up other users systems, etc") However, now we actually have the fix, it's compiled, it works, and it's going on to the other developer's hard drive, so that he can upload it to kubuntu.org.

As you may have heard, a debian machine got hacked into, so a lot of the ftp is down while they tighten it all up.

I'm hoping that this wont happen again, at least in it not taking so long.  It came at a particularly bad time when all the main merges needed to be done by, so it slid.  UVF was on the 13th, so we all have more time now, can do the universe packages more slowly, and fix some of the bugs as we go.

> While it may not suit your fancy to use "unstable" code, no one is forcing you to do so.  It is entirely up to you what you do to your system.  You don't have to download the file, nor install it.

Sure, and when you file a bug on malone about "hey, foo doesnt work now", i'll say "well, i cant reproduce this on my system, no one else can, so therefore it's your problem, because it was probably your unofficial fix that screwed it up.

> I thought the broken screensaver was a major enough issue to warrent an immediate bug fix and all I did was provide a simple method for others to fix the aformentioned bug.  

Do you not think that the screensaver is a high priority?  What about in a setting where security is important.  You walk away from your computer, thinking that your screensaver will kick in a minute, and since you have it set to lock, you think that once it starts that your session is safe.  If however, the screensaver never starts, then it will not lock, thus your session is still open to anyone who happens to walk by.

Then you lock your screen.  set a computer shortcut for it.  I do it all the time out of habit.  ctrl+alt+tab is my shortcut.  And i'd still call a broken X a bigger issue than a broken screensaver.

If you're wanting to track this, keep looking at [https://launchpad.net/distros/ubuntu/+source/kubuntu-meta/+bug/52142](https://launchpad.net/distros/ubuntu/+source/kubuntu-meta/+bug/52142)
which i'll update when the dapper versions are also on kubuntu.org.

Sorry about the fix taking so long.  I'm working at seeing that we can get this done more efficiently next time.  And I only check the forums once in a blue moon, hence the long wait times for a reply.

Hobbsee
Kubuntu Developer.

---

### Post by Hobbsee on 2006-07-15
I also have kopete 0.12.1 debs for dapper if anyone's interested.  They should have msn webcam support too.  Please test them.

They are at:

[www.buntudot.org/people/~hobbsee/kopete](www.buntudot.org/people/~hobbsee/kopete) - and they will be put on kubuntu.org, when the ftp is up and running again.

The source is there too, so you're free to compile them with any extra libs, etc, that you like.  Also, they werent made with the evil checkinstall.

---

### Post by editrix on 2006-07-15
Sorry, I'm confused. I installed Kubuntu Dapper a couple of weeks ago. The screensaver worked for a few days, then stopped working. Is this the bug, or have I got another issue? 

I'm using GDM rather than KDM. Could that have an effect?

Should I use Lil_Eagle's fix, or wait for an update?

---

### Post by Lil_Eagle on 2006-07-15
> I'm using GDM rather than KDM. Could that have an effect?No, GDM has nothing do to do with the bug.  It's in KDE 3.5.3, so if you didn't upgrade to 3.5.3 then your screensaver should still work since dapper uses 3.5.2.

Arizonagroovejet made the original patch for 3.5.3 to fix the problem, but since he was only using the 32-bit version, his patch didn't work for me, so using advice from him, I compiled a 64-bit version and he kindly hosted the patch on his website, and the wrote the howto so people whould know about it.

> Sure, and when you file a bug on malone about "hey, foo doesnt work now", i'll say "well, i cant reproduce this on my system, no one else can, so therefore it's your problem, because it was probably your unofficial fix that screwed it up.Now, that is low.  One of the reasons I run Linux is so that I can choose what to do with my computer.  You do not see a bug report on malone from me, because I didn't think it warranted one due to the fact that a fix is available.  My fix was simply to compile the KDE snapshot, and replace the faulty library with one that was working.  I didn't rewrite any code, nor did arizonagroovejet.  All we did was honestly do what should have been done (in a cleaner way to be sure) by the kubuntu staff.

I can understand that there are delays with fixes, especially if the problems are with the originial developers and not with the ubuntu/kubuntu staff.  However, I noticed that the kdesktop deb (which is the offending package) that is on kubuntu.org is dated June 14, as compared to most of the other packages dated May 29.  What I don't understand is why that is so, and why the bug is still present.

Nor do I understand why KDE 3.5.3 has not been backported to dapper since it's in edgy (and working fine by the way).  If Kubuntu is on even par with Ubuntu, as it should be according to all documentation, then surely the important fixes in KDE 3.5.3 should be backported to dapper.

There should be no need to request something like this.  Surely you and the other developers know that KDE is the backbone of kubuntu and whenever there is a stable release it should be available for the users, that's why it's on kubuntu.org is the first place I assume.  Why can't stable packages be included in the ubuntu repositories is what I would like to know.

---

### Post by editrix on 2006-07-15
Lil_Eagle, you're quoting two different people in the above post. I'll deal with my questions:

> **Lil_Eagle said:**
> No, GDM has nothing do to do with the bug.  It's in KDE 3.5.3, so if you didn't upgrade to 3.5.3 then your screensaver should still work since dapper uses 3.5.2.

Well, it looks like I somehow upgraded, because I have 3.5.3. Maybe in the automatic updates? There were over 90 of them, so I didn't read every one.

> **Lil_Eagle said:**
> Arizonagroovejet made the original patch for 3.5.3 ... I compiled a 64-bit version 

I have a 32-bit machine. I've already downloaded the fix, and it looks like I should use it. I just wanted to verify that:
a) My bug was *the* bug, and
b) that your fix was the only fix that was going to happen any time soon.

Thanks.

---

### Post by Lil_Eagle on 2006-07-15
I was aware about quoting two people, that's why I quoted.

Perhaps 3.5.3 has finally made it into backports after all.  I haven't checked today.  I do know that the version that was on kubuntu.org as of last night still had the bug.

As for the authenticity of the patch, I can tell you that the 64-bit version works fine because I compiled it myself.  Arizonagroovejet did the 32 bit version (and he is the one that told me what to compile to fix the bug) so I would imagine that his version works as well.  The link at the beginning of this thread is his web site.

To be honest I would prefer not to have install a library like this.  Debian and Ubuntu aren't designed that way, that's why we have .deb files and apt.  But since there are no .deb files that I know of that fix this issue (unless you grab them from edgy) this workaround is the only solution.

I can tell you how to upgrade to the version that is in edgy.  All you have to do is change the dapper to edgy in your sources.list, then do ```
sudo apt-get update && sudo apt-get install kubuntu-desktop
```Then change your sources.list back to dapper and then apt-get update again.  I wouldn't recommend doing that, but it is a technique that is well known with debian to get sarge to have some packages from sid, but to remain the stable sarge.

---

### Post by editrix on 2006-07-15
> **Lil_Eagle said:**
> I was aware about quoting two people, that's why I quoted.

And I was working on the assumption there'd be some third party out there reading this thread, but not from the beginning :-)

> **Lil_Eagle said:**
>  Perhaps 3.5.3 has finally made it into backports after all.... 

And if it has, should it not be included in the next set of updates?

> **Lil_Eagle said:**
>  As for the authenticity of the patch ...  Arizonagroovejet did the 32 bit version ...The link at the beginning of this thread is his web site.

Ah. That's where I got confused. I thought it was yours. You're having a lot of trouble with this good deed you've done. And, yes, I do consider it a good deed.

> **Lil_Eagle said:**
>  To be honest I would prefer not to have install a library like this.

Neither am I, which is why I've been bugging you.

I've copied your instructions for the upgrade to edgy. Not sure now which I'll try first, the library or the upgrade. I'm on dialup, so probably the former. If you see a post screaming for help on either screensavers or the whole desktop, it'll most likely be me. :-)

Thanks for your help.

---

### Post by Lil_Eagle on 2006-07-16
I wouldn't try that edgy upgrade that I mentioned.  I did a test to see what would happen, and it turns out that a lot of broken packages would be created if one did it.

If someone is really interested in Edgy, then doing the dist-upgrade is a much better method.  Even better, since edgy is quite unstable now since it is in heavy development, install dapper onto a free partition and upgrade that to edgy, that way, the dapper install that you use on a daily basis would still be in tact.  When Edgy has an ISO, then installing dapper wouldn't be needed.

As for making this thread, I still stand by the fact that it is/was a necessary fix.  I know that I don't always lock my session as I should because I am frequently sidetracked away from my computer.  I don't like the idea of someone else having access to my files without me knowing what they are doing.  Locking the session through the screensaver is my only alternative.

As of tomorrow, I will be losing my ISP, so it may be a while before I am back.  Rest assured, I will still be tinkering my system in the meantime.

Hopefully someone else will take up the defense of this fix while I am gone.  I know that a lot of peoiple have used it, and so far only one complaint.

---

### Post by Hobbsee on 2006-07-16
> **Lil_Eagle said:**
> I can understand that there are delays with fixes, especially if the problems are with the originial developers and not with the ubuntu/kubuntu staff.  However, I noticed that the kdesktop deb (which is the offending package) that is on kubuntu.org is dated June 14, as compared to most of the other packages dated May 29.  What I don't understand is why that is so, and why the bug is still present.

Check the changelog for what was updated, if you really want to know.  I dont remember what in particular it was, as i've been doing a lot of merging lately.

> Nor do I understand why KDE 3.5.3 has not been backported to dapper since it's in edgy (and working fine by the way).  If Kubuntu is on even par with Ubuntu, as it should be according to all documentation, then surely the important fixes in KDE 3.5.3 should be backported to dapper.

Were you ever around for the breezy release?  kde 3.4.3 slipped in at the last minute, with minimal testing.  It seemed to work, but there were many problems, which we found with more extensive testing.  I suspect that decision was made as we were very close to release.  That mistake wasnt eager to be made again.

> There should be no need to request something like this.  Surely you and the other developers know that KDE is the backbone of kubuntu and whenever there is a stable release it should be available for the users, that's why it's on kubuntu.org is the first place I assume.  Why can't stable packages be included in the ubuntu repositories is what I would like to know.

Kubuntu.org is for updated packages, and a few (hidden) testing packages.  However, we dont know everything, and didnt know about this fix until someone happened to see it and point it out.  And then it sat on the To-Do list, with all the main merges, etc, that had to be done.  

If you've seen an important patch that the devs dont know about, feel free to file a bug about it, with a link to the upstream bug report with the patch.  That's the quickest way to make sure we at least know about the thing.

Oh, and "Kubuntu Staff" - there's only one paid member doing kubuntu specific stuff (+ the guy in charge of artwork).  The rest are volunteers.  It's much more helpful to come and learn how to fix things than to sit here and talk about how they're so bad.  Things tend to get fixed quicker that way.

Anyway, i'm off to do more merges and bug fixes, so i probably wont end up reading this thread again.

Hobbsee

---

### Post by Lil_Eagle on 2006-07-16
Before my internet connection dies, I want to reply one last time to Hobbsee.

I would be glad to help with the development of Kubuntu, but alas I am not a good enough artist nor programmer in C++ (yet) to handle any tasks.  If you think that all I have been doing is complaining then you are mistaken.

I applaud the efforts of Mr. Riddell and all of the volunteers on the kubuntu team.  Without them there would be only gnome...  I ordered 10 CDs of Kubuntu from shipit, and have given away 8 of them to friends, encouraging them to give it a try.  I help others on the forums whenever I can.

I certainly wouldn't do that, nor would I be using Kubuntu myself if I didn't think it was the best Linux distro suited for me, although I don't agree with all of the modifications of KDE for "simplicity"  I can always compile my own version.  

I can't say that all of my machines are kubuntu because they aren't.  My kids both have edubuntu on their machines, and I have a debian sarge server as well (on a pitifully slow celeron 600 with 64mb RAM).

My only goal in creating the 64-bit version of the kde screensaver fix and creating the howto is to help out.  There were many messages about the problems with the screensaver, and when I saw that Mike had created a patch, I wrote him and asked how he did it so that I could also patch my system.  He was kind enough to create a howto for me.  I used his howto to compile the patch and he hosts it on his website along side his 32-bit patch and the same howto that he wrote for me.  Anyone is welcome to compile their own version instead of using our binaries.

I realize that everyone is busy with Edgy, so there is little time to fix dapper issues.  I waited for several weeks for the screensaver issued to be fixed, and would have continued waiting had I not stumbled upon Mike's fix.

Do your best in making Edgy the ubuntu that everyone will want on their desktop.

---

### Post by pahbi on 2006-07-21
I haven't installed this fix yet, but I appreciate it being posted.  I bookmarked the page and will install it when I get some time, as I miss my screen savers.  

If I recompiled KDE using the fixed source code would that also fix the problem?  Maybe that would be an interesting project for me to try to figure out.

- Pahbi

---

### Post by arizonagroovejet on 2006-07-21
> **pahbi said:**
> 
If I recompiled KDE using the fixed source code would that also fix the problem?

It's kinda what I did. I didn't recompile all of KDE though, just worked out which bits I needed to compile to get the file the patch had been applied to and compiled those.
There are now instructions on the page for building the fix file yourself from source if you prefer not to use the binary I built.

---

### Post by random.chance on 2006-07-30
I just applied this fix to Mepis 6.0 and it worked great for me. Thanks Lil_Eagle!! That's the great thing about Linux and open source in general - someone knows how to fix it!

---

### Post by Rastareefer on 2006-09-09
So, if this problem is fixed, how come I just installed and upgraded Kubuntu 6.06 to the KDE 3.5.3 desktop, did all the updates and the screen savers still don't kick in?
](*,) ](*,) ](*,)

---

### Post by arizonagroovejet on 2006-09-09
> **Rastareefer said:**
> So, if this problem is fixed, how come I just installed and upgraded Kubuntu 6.06 to the KDE 3.5.3 desktop, did all the updates and the screen savers still don't kick in?
](*,) ](*,) ](*,)

The problem is fixed in 3.5.4 not 3.5.3.

---

### Post by Rastareefer on 2006-09-09
Oh, I see...
How does one get 3.54 when the package mangers only list the previous version?

---

### Post by arizonagroovejet on 2006-09-10
> **Rastareefer said:**
> Oh, I see...
How does one get 3.54 when the package mangers only list the previous version?

[http://kubuntu.org/announcements/kde-354.php](http://kubuntu.org/announcements/kde-354.php)

---

### Post by Rastareefer on 2006-09-10
Thanks for the info.
I did the upgrade and checked that KDE has been upgraded to V3.5.4 however the screen savers still refuse to kick in.
Previously to upgrading KDE, I did the fix posted on this board and am now wondering if this is the reason the screen savers won't kick in after the upgrade.

---

### Post by arizonagroovejet on 2006-09-10
> **Rastareefer said:**
> Thanks for the info.
I did the upgrade and checked that KDE has been upgraded to V3.5.4 however the screen savers still refuse to kick in.
Previously to upgrading KDE, I did the fix posted on this board and am now wondering if this is the reason the screen savers won't kick in after the upgrade.

Did you log out and in again after updating to 3.5.4? If not then do so and see if the screensavers work then. I've seen mention of other people with screensavesr not working in 3.5.4. This thread [http://kubuntuforums.net/forums/index.php?topic=7535.0](http://kubuntuforums.net/forums/index.php?topic=7535.0) for example. Not 

Installing a newer version of KDE should have overwriten the libkdeinit_kdesktop.so file I created as a fix so having used it shouldn't be of any consequence after you've updated KDE. (Shouldn't as far as I know. No warranty etc etc...)  I added the repo, installed all the packages adept suggested and my screensavers worked again. You can check if the file has been overwriten by doing

```
$ md5sum /usr/lib/libkdeinit_kdesktop.so
```

and

```
$ ls -l /usr/lib/libkdeinit_kdesktop.so
```

If the md5sum is not the same as stated at [http://megaflexdestiny.net/bits/kde353screensaverfix/](http://megaflexdestiny.net/bits/kde353screensaverfix/) and the date shown by ls is  2006-08-03 then the fix file was overwritten.

---

### Post by Rastareefer on 2006-09-10
Appreciate the help. Many thanks.
t looks like the orignal fix has been overwritten.
Must be something in KDE 3.5.4

---------------------------------------------------------------------------


steve@AMD:~$  md5sum /usr/lib/libkdeinit_kdesktop.so
351d2db833a14e792fe12999e073aa87  /usr/lib/libkdeinit_kdesktop.so
steve@AMD:~$ ls -l /usr/lib/libkdeinit_kdesktop.so
-rw-r--r-- 1 root root 617472 2006-08-03 19:28 /usr/lib/libkdeinit_kdesktop.so
steve@AMD:~$

---

