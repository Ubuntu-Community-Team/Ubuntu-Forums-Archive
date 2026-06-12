---
title: "migrating from windows 7 ; thunderbird vs evolution ; nokia sync"
date: 2014-06-15
forum: New to Ubuntu
---

### Post by helkav on 2014-06-15
I am in the process of migrating from windows 7 to ubuntu. everything was going swimmingly - I have a dual boot with w7 (just in case!) setup thunderbird to point to the same profile as w7 so I can easily swap back and forth. My main issue now is I used to use outlook as a calendar and contacts app in w7 because it's all I could find that would sync with my phone (Nokia asha ; S40)

so I want my setup to be like so:
 
to use thunderbird as my email client : I would also like the addressbook kept in sync with my phone somehow

to use some other calendar/contacts app(s) in ubuntu : I tried evolution but I'm stuck setting it up as it's insisting on email setup

to sync my mobile with calendar / contacts somehow : I tried the sync program but when I looked at the contacts it hadn't imported all the info (e.g. missing addresses)

I am open to almost any solution except :

 - any that involves cloud sync
 - migrating email from thunderbird - I really have grown to like tb and also I am beta-testing the next version so I need to keep using it

anybody have any ideas / experiences they would like to share...I would really like to get this to work, there's so much about Ubuntu to love!

---

### Post by amanchesterman on 2014-06-15
I'm not sure if this will help you ...

I use Thunderbird on my laptop (running Xubuntu) to manage my emails. I also use the Lightning calendar extension to Thunderbird, which handles my appointments and to-dos. I also have an Android tablet, and I sync my calendar and to-dos with that via a Gmail account. I think it's possible to sync contacts as well, though I don't have a need for that. Does your phone run Android? If so, something similar might work for you?

---

### Post by helkav on 2014-06-15
thanks, but my phone is Symbian, not Android and anyway I DON'T want to use google (especially google!) or any cloud service as a conduit to do the sync. used to be easier to do this kind of thing...now everybody's expected to go through the cloud...sigh!

---

### Post by amanchesterman on 2014-06-16
Sure, I understand your reluctance to use Google. Over on the Nokia support forum there are several people who sync their phones with Thunderbird via the Google route, and quite a few of them would prefer a different method, so you aren't alone. ;)

The only other method mentioned on the Nokia forum is bluetooth, have you looked into that? Reading the posts there, some people have had limited success with it, but I haven't seen anyone report full bi-directional sync.

---

### Post by helkav on 2014-06-16
I don't think the connection method will really make a difference (i.e. USB or bluetooth) and in fact I have had success connecting the phone via bluetooth, it's just getting a sync program(s) for my contacts / calendar in Ubuntu that REALLY works. I am going to try looking into Akonadi, although it feels like a steep learning curve for this...

---

### Post by mastablasta on 2014-06-16
you could use Outlook 2007 in wine as a last resort.

otherwise what is wrong with using the coud to sync :P if you don't want Google there is always your own could.

---

### Post by Irihapeti on 2014-06-16
It's perfectly possible to sync a Symbian phone without using the cloud. For quite some time, I had Radicale as a CalDAV/CardDAV server, syncevolution as the sync software and a Nokia E63 phone. It can take a bit of fiddling to set up, but once that's done, it seems to work well.

---

### Post by hellybelly on 2014-06-17
radicale looks promising - have you got some nice pointers for me to help set it up on ubuntu : I am currently getting errors, and the various places I have gone to have inconsistent info about setup. if you have managed to do it I would like to benefit from your experience if you don't mind

---

### Post by Irihapeti on 2014-06-19
For a long time, the version available in the repos was an older one, so I just downloaded the package from the developer's site, unpacked it and then started it using the command ```
/home/username/radicale-(version)/radicale.py
``` 

I put that in my application autostart settings so that it started automatically when I logged in.

I don't recall now what I changed in the configuration file, but since I had it and Thunderbird running on the same machine (not accessible from anywhere else) I didn't bother with passwords.

As I didn't document what I did at the time, and it was a long time ago, I don't know that I'm much use for tips etc. :(

---

### Post by hellybelly on 2014-06-20
@irahepti : thanks for this, just wondering : you seem to be implying that you are not using the radicale / CalDAV / CardDAV / evolution combo now?

if you are are you getting all contact and calendar fields to sync correctly without any extra configuration (i.e. is the mapping correct) ?

---

### Post by Irihapeti on 2014-06-20
I just recently setup ownCloud instead. This wasn't because I had any problems with radicale - I wanted to share calendars with my housemate and ownCloud made it a lot easier. ownCloud is still calDAV/cardDAV and works well with syncevolution. All I needed to change was the sync URL.

Syncevolution originally started as software for syncing evolution to syncml phones. It's grown a lot since the early days and you don't need to be running evolution at all now. I use it less than I did because my main phone now is android, not symbian, and there are other apps available for syncing with android.

But to answer your final question, I find that the mappings are correct. If something isn't working, you can post on the syncevolution mailing list and the odds are very good that it will be fixed in the next update. Keep in mind that nokia phones often use an earlier version of vcalendar/vcard, which can affect things.

---

