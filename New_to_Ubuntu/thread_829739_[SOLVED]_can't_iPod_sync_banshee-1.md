---
title: "[SOLVED] can't iPod sync banshee-1"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by methodmarvel on 2008-06-15
**_SOLUTION LOWER IN THIS POST FOR CONVENIENCE _**

I've installed the latest greatest banshee 1.0 and want to sync my ipod with it. I do not want to use gtkpod, amarok or anything else.

My problem is though it recognizes my ipod there is no "sync to ipod" button or anything like that. There is no button to simple "add this track" etc either - even in right click menus.

I've installed libipoddevice sharp-ipod etc and still no solution.

HAL etc is finding my ipod fine it just there appears to be no sync/add feature which I believe there definitely is in this new version.

**_SOLUTION SOLUTION SOLUTION SOLUTION_**

So, lucky lucky you ubuntu forums - I've found a solution and remembered to come back and tell you about it.
[COLOR="Red"][B][SIZE="4"][CENTER]
READ THE WHOLE POST[/CENTER][/SIZE][/B][/COLOR]

Forget banshee and get songbird release candidate 1.

You can get it from [http://wiki.songbirdnest.com/Developer/Articles/Builds/Nightly_Builds]("http://wiki.songbirdnest.com/Developer/Articles/Builds/Nightly_Builds").

[B]TO INSTALL: I simply right clicked the file and selected "extract here". Then I double clicked the file inside the new folder "Songbird" called "songbird" which cause the program to launch. To make it all a bit neater I moved the folder "Songbird" to my home folder and changed it's name to ".songbird" which makes it a hidden folder. Then I created a launcher with the command "/home/username/.songbird/songbird". You'll need to change username to your username on your system eg phil
[/B][COLOR="Red"][I]
NOTE: A release candidate is like a late beta phase for software - It's finished as far as the programmer is concerned but is still open for changes before the final 1.0 is released. If you're reading this later and **1.0 or later is released, get that version (from [http://getsongbird.com/]("http://getsongbird.com/"))** as it will probably also have this sync feature unless they pull a banshee on us.[/I][/COLOR]

Songbird rc1 has a sync feature so similar to itunes it's perfect. It works better than amarok with my ipod as there is little config with mounting etc. so is good for linux beginners. It also looks much better than amarok, banshee, exhale etc etc... It also has built in skremer search and internet mp3 blog searching capabilities.

The only thing I'm unsure of is podcasts - which it call "subscriptions". I've signed up for the keith and the girl podcast using it but no episodes have appeared or downloaded. Maybe when a new episode is released it will be downloaded.

---

### Post by aussiedini on 2008-06-15
I dont think banshee can write to an ipod, only read.

---

### Post by methodmarvel on 2008-06-15
> **aussiedini said:**
> I dont think banshee can write to an ipod, only read.
The newest version (not from the repos) is meant to be able to.

---

### Post by methodmarvel on 2008-06-17
It suddenly started working today but only by dragging the tracks onto the "ipod" label. I still can't work out a sync option.

---

### Post by wariskampar on 2008-06-17
i also wonder where is the sync button. according to banshee official webpages, there is one. i will try your method though.

---

### Post by kpkeerthi on 2008-06-17
> **methodmarvel said:**
> The newest version (not from the repos) is meant to be able to.
And the version in repo (banshee 0.13.2) can read/write/sync with an iPod.

---

### Post by methodmarvel on 2008-06-17
> **kpkeerthi said:**
> And the version in repo (banshee 0.13.2) can read/write/sync with an iPod.
Fairly certain the repo version can't write - but even if it can it's not what is being asked.

I think I might of made it sync some how. I connected it and deleted all my tracks and then it said "syncing to ipod" and "flushing to disk" and all the songs are on there. For a while it said in the file bar (music, movies, other, pictures spread thing) it was all "other". Now I've reconnected it is says that it's music. I'm wondering what will happen when I add more to my library and connect my ipod.

---

### Post by wariskampar on 2008-06-17
reading your last post i think the problem lie in current db in our IPOD. Like in my case, before this I use Amarok to sync my music to IPOD therefore 'maybe' Banshee could not use the db. The only workaround is to delete the current database and re-sync again using Banshee instead. I will try this but need to sort out available space in my Music folder first. I also experience the not-accurate audio indicator bar in Banshee as well!

---

### Post by garoth2 on 2008-06-17
Check this bug:

[http://bugzilla.gnome.org/show_bug.cgi?id=536018](http://bugzilla.gnome.org/show_bug.cgi?id=536018)

Automatic syncing to iPod slated for version 1.1

---

### Post by kpkeerthi on 2008-06-18
> **methodmarvel said:**
> Fairly certain the repo version can't write - but even if it can it's not what is being asked.

If it was not what you were looking for, please ignore my post. 

> **aussiedini said:**
> I dont think banshee can write to an ipod, only read.
I read the post from aussiedini mentioning that banshee can only read from iPods. I just wanted to help saying even the old version in the repo can write to iPod so others are not mislead. 

And for the sake of others having trouble synching banshee-1 to iPod, 

**Banshee 0.13.2 can read/write/sync to iPods. I have personally used it to sync with my iPod Video 5.5 Gen .**

---

### Post by wariskampar on 2008-06-18
just found out that there are gtkpod db in my IPOD (no wonder banshee show 7GB other in it indicator bar). However, when i restore my IPOD using iTunes, banshee still can sync the audio files. It manage somehow to prompt a message about do not recognizing my IPOD and ask me to rebuild the database. Hoewever nothing seem to work after I click on the rebuild button. So, for now, bye bye Banshee. I'll stick with Amarok which is more straight forward and works out of box. Anyway, kpkeerthi, could you tell us how you do it because i'm using the same IPOD as you

---

### Post by kpkeerthi on 2008-06-18
> **wariskampar said:**
> Anyway, kpkeerthi, could you tell us how you do it because i'm using the same IPOD as you

It was straightforward. Just plugged in my iPod and banshee(0.13.x)  saw it. All I had to do was click the "Synchronize iPod" button.

[IMG]http://www.simplehelp.net/images/banshee/ban11.png[/IMG]

[http://www.simplehelp.net/linux/how-to-use-banshee-to-manage-your-ipod-in-ubuntu/](http://www.simplehelp.net/linux/how-to-use-banshee-to-manage-your-ipod-in-ubuntu/)
[http://www.gnomejournal.org/article/30/the-banshee-music-player-an-introduction](http://www.gnomejournal.org/article/30/the-banshee-music-player-an-introduction)

---

### Post by wariskampar on 2008-06-18
wow! that is easy. However when i use banshee 0.13.x back then i didnt see the synchronize button on top right. banshee didnt even recognize my IPOD. maybe there was other database in my IPOD then. Now, when i already shifted to banshee 1.0, the synchronize button is not even implemented by the developers as was confirmed in numerous blog. i love banshee (Gnome) but for the hassle i rather stick with Amarok (until they re-introduce sync button!)

---

### Post by methodmarvel on 2008-06-19
> **kpkeerthi said:**
> It was straightforward. Just plugged in my iPod and banshee(0.13.x)  saw it. All I had to do was click the "Synchronize iPod" button.

[IMG]http://www.simplehelp.net/images/banshee/ban11.png[/IMG]

[http://www.simplehelp.net/linux/how-to-use-banshee-to-manage-your-ipod-in-ubuntu/](http://www.simplehelp.net/linux/how-to-use-banshee-to-manage-your-ipod-in-ubuntu/)
[http://www.gnomejournal.org/article/30/the-banshee-music-player-an-introduction](http://www.gnomejournal.org/article/30/the-banshee-music-player-an-introduction)

I *don't* get that button.

People are unlike to miss such a huge freaking button if they *are* getting it.

---

### Post by wariskampar on 2008-06-19
maybe you've misunderstood. banshee 0.13 did not even recognize my IPOD! i think the problem was there was other db in my IPOD then. I wish I read your posr earlier but now I already use Amarok. Banshee 1.0 do not have the button!
ps: I'm using Banshee 1.0 to listen to mp3 and Amarok for my IPOD

---

### Post by kpkeerthi on 2008-06-19
> **methodmarvel said:**
> I *don't* get that button.

People are unlike to miss such a huge freaking button if they *are* getting it.
> **kpkeerthi said:**
> And the version in repo (banshee 0.13.2) can read/write/sync with an iPod.

**Screenshot of Banshee 0.13.2 on my laptop:** Note the Sync iPod Button at top right.

---

### Post by wariskampar on 2008-06-19
I manage to somehow use Banshee to transfer my mp3 to iPod. My earlier assumption about existing database was confirmed. Banshee 1.0 however miss the sync button, and the only way to transfer music files is by drag and drop.

---

### Post by julianna on 2008-06-20
[http://banshee-project.org]("http://banshee-project.org")

This is where you will find the answers to the IPOD question...and yes, there is a sync feature.  I've used it and so far, so good...best of luck

---

### Post by garoth2 on 2008-06-20
> **julianna said:**
> [http://banshee-project.org]("http://banshee-project.org")

This is where you will find the answers to the IPOD question...and yes, there is a sync feature.  I've used it and so far, so good...best of luck

I find it really confusing when people say there is a sync feature in Banshee 1.0 - it causes me to really question my own sanity because I really can't find this functionality in there.

As I posted previously in the thread, there is no "sync" feature in Banshee 1.0, in the sense that there is no button that automatically copies songs, podcasts, and videos to/from your ipod to make your ipod library and local library equal to one another.

See the bug:
[http://bugzilla.gnome.org/show_bug.cgi?id=536018](http://bugzilla.gnome.org/show_bug.cgi?id=536018)

The library sync feature is targeted for version 1.1

Please correct me if I'm wrong

---

### Post by garoth2 on 2008-06-20
> **garoth2 said:**
> I find it really confusing when people say there is a sync feature in Banshee 1.0 - it causes me to really question my own sanity because I really can't find this functionality in there.

As I posted previously in the thread, there is no "sync" feature in Banshee 1.0, in the sense that there is no button that automatically copies songs, podcasts, and videos to/from your ipod to make your ipod library and local library equal to one another.

See the bug:
[http://bugzilla.gnome.org/show_bug.cgi?id=536018](http://bugzilla.gnome.org/show_bug.cgi?id=536018)

The library sync feature is targeted for version 1.1

Please correct me if I'm wrong

I just confirmed this on the IRC channel (#banshee on irc.gnome.org)

---

### Post by wariskampar on 2008-06-20
There is absolutely no sync button in Banshee 1.0. Period

---

### Post by iraiscoming223 on 2008-06-23
> **wariskampar said:**
> There is absolutely no sync button in Banshee 1.0. Period

LoL I was having the same trouble... Happy to read I'm not that mad, and it's really missin a Sync Ipod Button :P

---

### Post by screaminj3sus on 2008-06-26
I was GOING crazy over this, They Blatantly advertise on the page that 1.0 has a sync button! They really need to change this I just spent like an hour trying to sync it with banshee 1 to find out there isn't a friggin sync button. Ridiculous. Besides that the new banshee is amazing though.

---

### Post by iraiscoming223 on 2008-06-26
> **screaminj3sus said:**
> They Blatantly advertise on the page that 1.0 has a sync button! They really need to change this

Completely agree!

---

### Post by methodmarvel on 2008-07-02
It needs a sync feature more than anything - I find it hard to stay on top of what I have added and what I haven't. Today I looked at my song numbers and I had 380 in my library and 379 on my ipod. 

**"What the hell am I missing?!"**

I couldn't just drag and drop the whole library on it as it would duplicate tracks. I didn't want to search through and find the offending track. So I had to delete all the music on my ipod and redrag the whole library on it. Then it started saying it was "syncing" - **this isn't what syncing is**:mad:.

---

### Post by wariskampar on 2008-07-03
I've give up Banshee altogether (Itunes is the best for IPOD and therefore I already re-install my XP on VirtualBox). My priority when I installed Banshee was to sync with my IPOD, but since the feature is not yet implemented, it was like beat the purpose. I was also frustrated with it sluggishness handling Video Podcast (BestOfYouTube) and this give me more reason to re-use Itunes(can edit AlbumArt on the fly, can add lyric which can be viewed in IPOD, Podcast readiness in Itunes Store etc). On the positive side, giving more time I think Banshee can be better but until then "I'm sorry! I was so impatient".

---

### Post by screaminj3sus on 2008-07-03
> **wariskampar said:**
> I've give up Banshee altogether (Itunes is the best for IPOD and therefore I already re-install my XP on VirtualBox). My priority when I installed Banshee was to sync with my IPOD, but since the feature is not yet implemented, it was like beat the purpose. I was also frustrated with it sluggishness handling Video Podcast (BestOfYouTube) and this give me more reason to re-use Itunes(can edit AlbumArt on the fly, can add lyric which can be viewed in IPOD, Podcast readiness in Itunes Store etc). On the positive side, giving more time I think Banshee can be better but until then "I'm sorry! I was so impatient".

Yeah same here, I would just have stayed with rhythmbox, but banshee can sync with the ipod but I installed it and was very disappointed.

---

### Post by methodmarvel on 2008-11-10
So, lucky lucky you ubuntu forums - I've found a solution and remembered to come back and tell you about it.
[COLOR="Red"][B][SIZE="4"][CENTER]
READ THE WHOLE POST[/CENTER][/SIZE][/B][/COLOR]

Forget banshee and get songbird release candidate 1.

You can get it from [http://wiki.songbirdnest.com/Developer/Articles/Builds/Nightly_Builds]("http://wiki.songbirdnest.com/Developer/Articles/Builds/Nightly_Builds").

[B]TO INSTALL: I simply right clicked the file and selected "extract here". Then I double clicked the file inside the new folder "Songbird" called "songbird" which cause the program to launch. To make it all a bit neater I moved the folder "Songbird" to my home folder and changed it's name to ".songbird" which makes it a hidden folder. Then I created a launcher with the command "/home/username/.songbird/songbird". You'll need to change username to your username on your system eg phil
[/B][COLOR="Red"][I]
NOTE: A release candidate is like a late beta phase for software - It's finished as far as the programmer is concerned but is still open for changes before the final 1.0 is released. If you're reading this later and **1.0 or later is released, get that version (from [http://getsongbird.com/]("http://getsongbird.com/"))** as it will probably also have this sync feature unless they pull a banshee on us.[/I][/COLOR]

Songbird rc1 has a sync feature so similar to itunes it's perfect. It works better than amarok with my ipod as there is little config with mounting etc. so is good for linux beginners. It also looks much better than amarok, banshee, exhale etc etc... It also has built in skremer search and internet mp3 blog searching capabilities.

The only thing I'm unsure of is podcasts - which it call "subscriptions". I've signed up for the keith and the girl podcast using it but no episodes have appeared or downloaded. Maybe when a new episode is released it will be downloaded.

---

### Post by hachel on 2008-12-08
hi there,
I wouldn't call that a solution.

Anyway, the newest banshee version syncs automatically, see attatchment.

and see here: [http://banshee-project.org/download/](http://banshee-project.org/download/)
on how to get the newest version

---

### Post by methodmarvel on 2008-12-09
> **hachel said:**
> hi there,
I wouldn't call that a solution.

Anyway, the newest banshee version syncs automatically, see attatchment.

and see here: [http://banshee-project.org/download/](http://banshee-project.org/download/)
on how to get the newest version

Looks much better! 

*installs*

Of course I'd consider going back to banshee for the simple CD ripping options - which is, of course, also planned for songbird. Also, banshee definitely has better podcast support.

*installed*

Seems ok but I was wrong about the podcast support being better. It doesn't let me save my Podcasts to a separate folder from my music. I'd rather it not have the functionality at all than dump all my podcasts in with my tunes. Podcasts are transient, music files aren't = required separation.

Shame the open source community doesn't plough into one project sometimes.

*quick performance comparison*

Both songbird and banshee take around 9% of my RAM to play the same song. Songbird uses 8% of my CPU while banshee uses 4%. I'm sure if I move the windows around and try and do more things with songbird it'll take up more CPU but when just playing they seem pretty equal.

*flaws*

Songbird - No CD rip, poor podcast support ("subscriptions"), occasional performance issues (rendering, I think), slow menus (eg preferences, probably because it's not GTK)

Banshee - Poor podcast support (no separate saving folder), ugly on default ubuntu theme (hardy), generally ugly (GTK isn't really sexy)

*conclusion*

Songbird wins.

Banshee needs to look better but is limited by how good gtk can look and, for a lot of users, how good it can look in the ubuntu theme. "But you can change your theme!" - I shouldn't have too. Do mac users rush out to change their theme? Do windows vista users? I appreciate I can but by default I shouldn't crave/need a theme change to get my setup looking good. It is more of an ubuntu issue than banshee.

Banshee also need the ability to save podcasts to a separate folder from music. Podcasts are transient, music files aren't = required separation.

Songbirds performance will only get better, CD support is coming and it looks good. I'm sure better podcast/subscription support is in the works too.

---

### Post by perroazul on 2009-04-15
has anybody tried to sync an Ipod with banshee 1.4.3's library?
it copies the playlists ok, but the ratings are not synced or the play count. 
does anybody have the same problem??

---

### Post by Wobblybob on 2009-11-21
Banshee 1.6 Beta 2 (1.5.1) in the karmic repos auto syncs my music collection on an iPod 80G black classic. Looks like I'm back to using Linux to manage my iPod, goodbye itunes and xp.

---

