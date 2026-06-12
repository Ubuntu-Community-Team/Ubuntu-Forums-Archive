---
title: "[SOLVED] Firefox Question?"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by mariane_08 on 2008-07-28
OK I'm a beginner so here are two basic questions about Firefox!

1. How do I set it so it does NOT automaically load Firefox when I boot up? right now it goes straight into Firefox every time.

2. I understand the Hardy install disk I downloaded has Firefox 3 beta on it (at least that's what I read in a Linux mag the other day) So I looked at the Firefox 3 download and got the impression that it's no longer beta (correct me if I'm wrong)

I downloaded Firefox 3 and it's now on my desktop as a tar folder. I clicked on extract and extracted it to the desktop and now have a second Firefox folder there. My original Firefox shortcut remains. How do I get it to update? or have I gone about this in the wrong way? Please tell me how I should do this (asssuming the download is more recent than the original install version)

Thanks

---

### Post by Mhurst1 on 2008-07-28
Firefox loads at startup?? Does it go to a certain page?? If you ran the updater you have firefox 3.0.1 which is not a beta.

---

### Post by rockerphil on 2008-07-28
my advice is to open up a terminal and run this

sudo apt-get update

then run this

sudo apt-get dist-upgrade

that should update your system. hope it helps,

Phil

edit: with Linux you rarely have to download a program from a web site to install it, simply look in either the Add/Remove, Synaptic Package Manager, or you can do your own package management via the command line with either apt-get or aptitude

---

### Post by RuleMaker on 2008-07-28
1) To remove firefox from startup:
go to System->Preferences->Sessions->Startup Programs(tab) and remove firefox from there.
2) If you have updated your system after installation then you have updated your firefox too, it should be 3.0.1 now. To update firefox manually:
in terminal type:
```
gksudo firefox
```
In firefox select Help->Check For Updates

---

### Post by alzie on 2008-07-28
Welcome to the forums :)

What both of the previous posters has said is correct.  If you've installed your updates you should be fully up to date with firefox.

If there are programs that you are looking for I'd suggest looking in the repositories (>System>Administration>Synaptic Package Manager)  It will ask for your password and then you can search for any programs you like.  Click on them and click on apply and they are downloaded and installed for you.  No tarballs etc.

I'd also suggest looking through pschocats' tutorials :  [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

I've found them very helpful.

I hope this helps you

---

### Post by mariane_08 on 2008-07-29
OK thanks. I guess I went about this the wrong way by clicking on the download in the Firefox website. I clicked on download manager and it updated my system (inc Firefox) in no time flat! I just have the two files on the desktop from my earlier failed attempt so I just delete these right?

Re Startup: I went to System/administration/sessions. There is no Firefox listed under the Startup tab ! :confused:

It usually defaults by going to the "Welcome to Ubuntu" page. However, last night it was going to my last viewed pages. Today it's back to the default

---

### Post by alzie on 2008-07-29
I'd look in "Session Preferences" under the tab "Session Options" to make sure the Automatically remember running applications when logging out is not clicked.

Its the only other option I can think of at this time.

I hope it helps

---

### Post by mariane_08 on 2008-07-30
> **alzie said:**
> I'd look in "Session Preferences" under the tab "Session Options" to make sure the Automatically remember running applications when logging out is not clicked.

Its the only other option I can think of at this time.

I hope it helps

No that's definately not clicked and I've checked several times. So I'm stumped as to why it's still Loading Firefox!

---

### Post by sheepsheds1 on 2008-07-30
Regarding Firefox 3.0.1, although it isnt in the beta stages anymore, its an official "stable" release, I have experienced many problems with it. Quite a large portion of websites do not currently support this new version, for example [www.travelinecymru.co.uk](www.travelinecymru.co.uk) (transport planner). However, I do think its got some good new features in it, including the ability to drag pics from the page to your files. nice touch! 

M!

---

### Post by UbuntuNerd on 2008-07-30
you could try Firefox 2 from synaptic package manager maybe that would help!!!

---

### Post by silkstone on 2008-07-30
Try this...

Look in System/Preferences/Sessions and select the middle tab (Current Session). Select all lines relating firefox, and then click the 'Remove' button. Then logout and login again.

---

### Post by mariane_08 on 2008-07-30
> **silkstone said:**
> Try this...

Look in System/Preferences/Sessions and select the middle tab (Current Session). Select all lines relating firefox, and then click the 'Remove' button. Then logout and login again.

I tried that and no change! What's also launching after boot up along with Firefox is File Browser. Does this tell us anything?? I'm sure tis all stems from something I clicked without realizing it :confused:

---

### Post by alzie on 2008-08-03
I found a possible solution for this.

Close all programs you do not want launching at boot (ie firefox)
Open sessions preferences and click on "Session Options"
Click on "Remember Currently Running Applications"
Reboot and see if that fixes it.

I hope this helps

---

### Post by mariane_08 on 2008-08-03
> **alzie said:**
> I found a possible solution for this.

Close all programs you do not want launching at boot (ie firefox)
Open sessions preferences and click on "Session Options"
Click on "Remember Currently Running Applications"
Reboot and see if that fixes it.

I hope this helps

YES!!! Bingo! that's done it! Many thanks!

---

