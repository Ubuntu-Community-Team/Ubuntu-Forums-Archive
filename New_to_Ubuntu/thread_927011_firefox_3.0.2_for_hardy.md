---
title: "firefox 3.0.2 for hardy?"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by Knacker on 2008-09-22
I'm having endless, unfixable problems with FF 3.0.1. Is there a version after 3.0.1 that I can get for hardy? Or, better, does anyone know when the next official firefox update is coming for hardy users? I've looked for an answer and can't find one. 

Anyone? Please? 

Need some hope that flash,nspluginwrapper, etc. problems are going to be fixed or I've got to start moving things over to opera again. 

Thanks!

---

### Post by Tatty on 2008-09-22
It is highly unlikely that FF will be updated in the hardy repos to 3.0.2 unless there is a major security flaw found which makes it essential.

Software versions in the repos are locked after each release to keep each  release stable.

8.0.2 will be included in Ibex i believe, which is to be release at the end of october.

If you want the latest FF in the meantime you will have to download and install it manually.

---

### Post by Mornedhel on 2008-09-22
> **Tatty said:**
> Software versions in the repos are locked after each release to keep each  release stable.

Well security and bugfix releases are sometimes pushed to the repositories, as well. Sometimes even feature releases, as long as they're minor releases.

---

### Post by Knacker on 2008-09-22
thank a lot for your reply! that's too bad. is it a really bad idea to manually install a newer version of FF? it's either that or opera... and, if it's do-able, where would i go for a newer version of firefox?
sorry if these are dumb questions. thanks again!!

---

### Post by Tatty on 2008-09-22
> **Mornedhel said:**
> Well security and bugfix releases are sometimes pushed to the repositories, as well. Sometimes even feature releases, as long as they're minor releases.

Usually It is only serious security issues or minor bugfix's.  Adding features after a final ubuntu release is rare, and only really happens in special circumstances.

---

### Post by SuperSonic4 on 2008-09-22
No, it should be OK but it is much harder to compile from source than to install from the repos

---

### Post by Knacker on 2008-09-22
well, i guess my question is where do i look to see if a bugfix is on the way and/or if there is a newer/more stable version of firefox? 

my sense, after having tried to sort out the constant crashing problems with 3.0.1. that I'm not the only person (!!) having trouble with this version of FF.

---

### Post by billgoldberg on 2008-09-22
I don't see why, if 3.0.1 made it in, 3.0.2 wouldn't get into the Ubuntu repo.

---

### Post by Tatty on 2008-09-22
Well, having a look at the firefox website, 3.0.1 appears to be the latest stable version. so i wouldnt reccomend trying to compile the development version yourself.

What sort of problems are you having with firefox?  If it is crashing, it may be worth running it from a terminal to see if it gives any error messages.

---

### Post by billgoldberg on 2008-09-22
> **Knacker said:**
> well, i guess my question is where do i look to see if a bugfix is on the way and/or if there is a newer/more stable version of firefox? 

my sense, after having tried to sort out the constant crashing problems with 3.0.1. that I'm not the only person (!!) having trouble with this version of FF.

When a new version of firefox comes out you could always install it manually from the .tar.gz file they provide.

If you don't know how to install it, you could google "install firefox 3.0.2 in ubuntu" and lots of guides will pop up hours after it's out.

However, you should wait a while to see if it gets into the repos.

---

### Post by SunnyRabbiera on 2008-09-22
really if its just a small minor relese it wont appear in the hardy repositories.
If its a really major security update then you might see it but firefox 3.0.2 isnt that different from 3.0.1 so there is no need to update.

---

### Post by Tatty on 2008-09-22
> **billgoldberg said:**
> I don't see why, if 3.0.1 made it in, 3.0.2 wouldn't get into the Ubuntu repo.

Because the Hardy repo is now considered "stable", so unless there is a vital reason to update to 3.0.2 then it will be left at 3.0.1, as this is known to work.

There are sometimes exceptions to this rule, such as FF3 being updated from beta to RC to final release in Hardy.  But i would be surprised if it went from 3.0.1 to 3.0.2 without a major security issue to force the change.

---

### Post by aysiu on 2008-09-22
Has 3.0.2 even been released?

---

### Post by Mornedhel on 2008-09-22
> **Tatty said:**
> But i would be surprised if it went from 3.0.1 to 3.0.2 without a major security issue to force the change.

Well, at some point there *will* be a security release. And Hardy is LTS...

---

### Post by philinux on 2008-09-22
If it is going to pop up in Hardy it will come from the backports. Which are easily enabled.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)


Else upgrade to Intrepid..

---

### Post by linux5uper on 2008-09-22
Have you tried the fix for those packages you mentioned?:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

It fixed ff3 crashes for me. This was written by the guy who worked on pulseaudio I think.

---

### Post by tarahmarie on 2008-09-22
Actually, I'm using Firefox 3.0.2 right now.  It's in the repos.  When I installed using "sudo apt-get install firefox-3.0" it automatically got me the latest version.  If it's any help, here are the repos I've added to my source list...

[http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu)
[http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu)
[http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu)

---

### Post by Tatty on 2008-09-22
> **tarahmarie said:**
> Actually, I'm using Firefox 3.0.2 right now.  It's in the repos.  When I installed using "sudo apt-get install firefox-3.0" it automatically got me the latest version.  If it's any help, here are the repos I've added to my source list...

[http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu)
[http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu)
[http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu)

Are you sure you arent using the backports repo?  My firefox in hardy is 3.0.1

---

### Post by tarahmarie on 2008-09-22
Quite sure; I have no backports enabled.

---

### Post by aysiu on 2008-09-22
> **tarahmarie said:**
> Quite sure; I have no backports enabled.
I don't see any Firefox 3.0.2 in the repos:
[http://packages.ubuntu.com/search?keywords=firefox&searchon=names&suite=hardy&section=all](http://packages.ubuntu.com/search?keywords=firefox&searchon=names&suite=hardy&section=all)

As a matter of fact, I don't see Firefox 3.0.2 even on the Firefox homepage.

---

### Post by Mornedhel on 2008-09-22
I'm using backports, and my Firefox is still 3.0.1.

Does Cutting-Edge Kubuntu (with KDE 4.x) maintain some other repositories ?

---

### Post by anjilslaire on 2008-09-22
3.0.1 here as well.

[http://www.mozilla.com/en-US/firefox/all.html]("http://www.mozilla.com/en-US/firefox/all.html")

There is no 3.0.2 as of yet from Mozilla

---

### Post by aysiu on 2008-09-22
> **anjilslaire said:**
> 3.0.1 here as well.

[http://www.mozilla.com/en-US/firefox/all.html]("http://www.mozilla.com/en-US/firefox/all.html")

There is no 3.0.2 as of yet from Mozilla
That's what I'm saying. There is no released 3.0.2 for anyone on any platform, as far as I know.

---

### Post by Mornedhel on 2008-09-22
'K, so it all boils down to the same for the OP : no 3.0.2 right now. It probably wouldn't have fixed the flash problems anyway.

Just so you know, there are plenty of flash problems in Opera as well.

---

### Post by TheLions on 2008-09-22
> **Mornedhel said:**
> 'K, so it all boils down to the same for the OP : no 3.0.2 right now. It probably wouldn't have fixed the flash problems anyway.

Just so you know, there are plenty of flash problems in Opera as well.

you can always install firefox 32bit in which flash works:

[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

---

### Post by Knacker on 2008-09-22
cool.thanks all!!

---

### Post by stormtrooprdave on 2008-09-23
You can get it now from the mozilla ftp site:

[http://releases.mozilla.org/pub/mozilla.org/firefox/releases/]("http://releases.mozilla.org/pub/mozilla.org/firefox/releases/")

---

### Post by Kow on 2008-09-23
Might as well wait for the Ubuntu update... I would assume they will do one for hardy since 3.0.2 is a 'fix' release, ie it fixes stuff. They do add some features, but ubuntu devs will likely cherry-pick some items. So, even if the version of mozilla in the ubuntu update says 3.0.1 it will include backport patches cherry-picked from the 3.0.2 changes.

Snippet from 3.0.2 rel notes:
> 
Fixed  several security issues.
Fixed several stability issues.
Fixed issue that caused some users with customized toolbars to have their Back and Forward buttons go missing (bug 426026)


---

### Post by Tatty on 2008-09-23
3.0.2 is currently in intrepid.

---

### Post by kansasnoob on 2008-09-24
> Need some hope that flash,nspluginwrapper, etc. problems are going to be fixed or I've got to start moving things over to opera again.

I swear on a stack of Aesop's Fables that this works, just do what I said in post #7 here:

[http://ubuntuforums.org/showthread.php?t=919695](http://ubuntuforums.org/showthread.php?t=919695)

Really!

BTW, I'm playing with Intrepid and so far flash works great but it's still in Alpha so things break .......... although much less often than I've seen before.

---

### Post by anewguy on 2008-09-24
I realize that installation from Mozilla itself would be more involved than that from repositories, but I was reading this thread because of problems in 3.0.1 as well.  I got to where people where saying 3.0.2 is not available even from Mozilla and had to interject - if you go to Mozilla and request a download for English/Linux it IS 3.0.2 right on the download.  I'm going to try installing this just to see if I can get around some problems as well.

---

### Post by marcordenis on 2008-09-24
My Firefox just updated to 3.0.2 automatically (Update Manager)...

---

### Post by kansasnoob on 2008-09-24
Well, in exactly one month the Intrepid RC comes out, and based on the Alpha 6 it's great!

No Flash problems!

---

### Post by wolfie2x on 2008-09-24
I had flash probs in 3.0.1 and got'em fixed by installing Flash 10 plugin.

see this thread: [http://ubuntuforums.org/showthread.php?t=926661]("http://ubuntuforums.org/showthread.php?t=926661")

to install see this: [http://ubuntuforums.org/showpost.php?p=5587712&postcount=472]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472")

---

### Post by anewguy on 2008-09-24
> **marcordenis said:**
> My Firefox just updated to 3.0.2 automatically (Update Manager)...

You are correct sir!!  I downloaded the package from Mozilla and shortly after doing so the automatic updates kicked in and installed 3.0.2 anyway!

dave :)

---

### Post by keshacoggins on 2008-09-24
I have used mozilla firefox all the version started from 2.0 and till 3.0. I find very good using with that. And as this 3.02 came. I find more handy and comfortable with this...
----------------
Kesha

[Internet Marketing]("http://www.drivenwide.com")

---

### Post by hfdragon on 2008-09-24
> **marcordenis said:**
> My Firefox just updated to 3.0.2 automatically (Update Manager)...

I updated FF this morning to 3.0.2 and now I don't have any password anymore... :(

All stored passwords have been removed !

Anyone else has this problem ??

---

### Post by k3lt01 on 2008-09-24
No my passwords are all there but the update made me re-enter the Username for the first time and then the passwords appeared. The other thing it did was change my homepage to Firefox Home.

---

### Post by NWAdawg on 2008-09-24
> **marcordenis said:**
> My Firefox just updated to 3.0.2 automatically (Update Manager)...

I updated just a few minutes ago. all passwords, bookmarks, history, themes & plugins still there and working.

---

### Post by Zero Prime on 2008-09-24
I wish I wouldn't have updated.  Now all the fixes that worked with my dark themes don't work any more.  My buttons are dark on dark.  Some of my text boxes are black on black.  This sucks.

---

### Post by billgoldberg on 2008-09-24
> **hfdragon said:**
> I updated FF this morning to 3.0.2 and now I don't have any password anymore... :(

All stored passwords have been removed !

Anyone else has this problem ??

No I don't have that problem.

---

### Post by SuperSonic4 on 2008-09-24
My passwords have been fine too.

---

### Post by presence1960 on 2008-09-24
I got updated to Firefox 3.0.2 last night. There were 6 updates I was notified about and 3 or 4 had to do with Firefox.

---

### Post by reginak on 2008-09-24
I know this is a no-no, but I installed updates this morning without even looking at what they were. Now Firefox is all hosed up. The search engine box doesn't work, I get an error when I even try to type in it. And I get a similar error when I try to get somewhere using the address box. I only got here because I had the forums bookmarked. Nothing happens when I go to About Mozilla Firefox under the Help menu, so I don't even know if I have "upgraded" to 3.0.2. 

Help?

---

### Post by ThrobbingBrain66 on 2008-09-24
> **reginak said:**
> I know this is a no-no, but I installed updates this morning without even looking at what they were. Now Firefox is all hosed up. The search engine box doesn't work, I get an error when I even try to type in it. And I get a similar error when I try to get somewhere using the address box. I only got here because I had the forums bookmarked. Nothing happens when I go to About Mozilla Firefox under the Help menu, so I don't even know if I have "upgraded" to 3.0.2. 

Help?

Maybe a silly question, but have you tried restarting the browser at all?  After I upgraded, my browswer was completely unresponsive.  I had to kill it through System Monitor and then everything worked fine.

---

### Post by reginak on 2008-09-24
Yeah, I did. As soon as I restart Firefox I get this:

ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],hidden)
5:()
6:()
7:currentEngine()
8:get_currentEngine()
9:updateDisplay()
10:init()
11:([object XULElement],0)

---

### Post by billgoldberg on 2008-09-24
> **reginak said:**
> Yeah, I did. As soon as I restart Firefox I get this:

ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],hidden)
5:()
6:()
7:currentEngine()
8:get_currentEngine()
9:updateDisplay()
10:init()
11:([object XULElement],0)

```
sudo apt-get autoremove firefox --purge
```

then

```
sudo apt-get install firefox
```

---

### Post by reginak on 2008-09-24
OK, thanks.  I won't lose my bookmarks, etc?

---

### Post by kostkon on 2008-09-24
> **reginak said:**
> OK, thanks.  I won't lose my bookmarks, etc?
You'll lose them. So, before doing this, backup your current Firefox profile.

---

### Post by kintoandar on 2008-09-24
Same problem here.
The password manager isn't working, I've tryed to purge firefox and reinstall but the problem continues. 

Going to restore an older backup and wait for more feedback from the community, certainly there isn't only two users with the same glitch.

---

### Post by reginak on 2008-09-24
OK, worth a try.  Thanks

---

### Post by reginak on 2008-09-24
Still have the same problem.  Is there a way to tell it to install 3.0.1 instead of the latest version?

---

### Post by kostkon on 2008-09-24
> **reginak said:**
> Still have the same problem.  Is there a way to tell it to install 3.0.1 instead of the latest version?
Maybe Firefox is OK, but for some reason your profile misbehaves.

You could try to run Firefox with a new fresh profile and test the password manager on a site.

To do it, open a terminal, and give
```
firefox -profilemanager
```
create a new profile and start Firefox with it. You don't need to make it the default one.

If everything works OK, then it means that your current profile is corrupted or something like that. You can then try to migrate from this profile to your new one (e.g. transfer bookmarks, extensions, etc. You will not be able to move any data sensitive stuff like passwords etc. from the old to the new profile, so you'll need to login to all of your sites again, etc).

---

### Post by reginak on 2008-09-24
> **kostkon said:**
> 
To do it, open a terminal, and give
```
firefox -profilemanager
```
create a new profile and start Firefox with it. You don't need to make it the default one.

Hmmm...  when I type that command, Firefox opens ... with my own profile (my homepages), and still the same error screen.

---

### Post by hfdragon on 2008-09-24
The password problem is known :

[https://bugs.launchpad.net/firefox/+bug/270429]("https://bugs.launchpad.net/firefox/+bug/270429")

The problem is not comming from firefox, but xulrunner.

Here is the (temporary) workaround :

```
sudo su -
wget http://uk.archive.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.3_i386.deb
wget http://uk.archive.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.3_i386.deb
dpkg -r --force-depends xulrunner-1.9 xulrunner-1.9-gnome-support
dpkg -i xulrunner-1.9_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.3_i386.deb xulrunner-1.9-gnome-support_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.3_i386.deb
exit
```

I hope this can help...

---

### Post by reginak on 2008-09-24
My problem is not with passwords, it's with using the search engine, and the address box. I can only get to pages through existing bookmarks or links, I can't use google and I can't type the address in directly.

Still stuck....
Regina

---

### Post by reginak on 2008-09-24
**sigh** As it turns out, I had another instance of Firefox running without knowing it. It did not show up on the status bar at bottom of the desktop, along with an Office document I thought was closed. I shut down and started back up ("restart" doesn't actually work for me, it freezes, but that's another issue), and now everything seems to be working fine!

Thanks for your patience, all!

---

### Post by issih on 2008-09-24
I saw a similar problem, search box not working, also preference windows were opening absolutely tiny, and with no content.

I got irritated and restarted the X server and everything has been fine since...

Just thought I'd let people know

---

### Post by social_flea on 2008-09-24
I just updated to Firefox 3.0.2 on Ubuntu 8.04.1 AMD 64 and it works fine. I'm surprised that they released the update so quickly! It usually takes a week or so. I guess Intrepid' development is helping Hardy.

---

### Post by darkmatterhari on 2008-09-24
> **issih said:**
> I saw a similar problem, search box not working, also preference windows were opening absolutely tiny, and with no content.

I got irritated and restarted the X server and everything has been fine since...

Just thought I'd let people know

I had the same issue on both my home and work PCs.  Restarted X per this comment and things seem better now.  Address bar and search bar working again, yay!  After X restarted and I relaunched FF I got a pop-up that 2 add-ons were incompatible versions, being Xulrunner en-GB 1.9 and Firefox en-GB-3.0 (language packs).  I would guess that if restarting X doesn't work for someone you could try disabling or uninstalling these manually.

---

### Post by The_Dark_Lord on 2008-09-25
If you want to use the official ubuntu tar from mozilla,com use this script, its fully automatited and they even got there own forums here so i guess i can say its support by ubuntu, i use it and have no problems what so ever

```
ubuntuzilla.wiki.sourceforge.net
```

---

### Post by steveneddy on 2008-09-25
It's in the repos now.

---

### Post by steveneddy on 2008-09-25
It's actually 3.0.3 now.

---

### Post by t0p on 2008-09-26
Today's update gave me firefox 3.0.3, amongst some other stuff.

---

### Post by oldsoundguy on 2008-09-26
flash 10 beta works fine .. a LOT better than 9.x.  So you have a choice if you are running the Ubuntuzilla (Mozilla) version of Firefox on earlier builds .. you can do your update to 3.03 at the site and then go get Flash 10 from Adobe and install it.  I did so with no problems.

---

