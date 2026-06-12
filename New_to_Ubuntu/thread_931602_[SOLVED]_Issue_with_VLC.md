---
title: "[SOLVED] Issue with VLC"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by panand178 on 2008-09-27
My VLC player was working perfectly fine till the last two days. I have been using it without any problem since I installed Hardy Heron back in April. 

But since the last two days whenever I play any movie on VLC it suddenly uses up all my 2 GB of RAM and my system hangs. Does anybody know why this might be happening and that too all of a sudden.

---

### Post by wolfen69 on 2008-09-27
reinstall doing the following:
```
sudo apt-get purge vlc
```then ```
sudo apt-get clean
```then ```
sudo apt-get autoremove
``` then ```
sudo apt-get install vlc
```

---

### Post by panand178 on 2008-09-28
> **wolfen69 said:**
> reinstall doing the following:
```
sudo apt-get purge vlc
```then ```
sudo apt-get clean
```then ```
sudo apt-get autoremove
``` then ```
sudo apt-get install vlc
```

Thank you! I tried you removing VLC and re-installing as you had mentioned but the newly installed VLC's also eating up all my RAM. :(

Just to let you know I have this problem only with VLC. Totem works just fine. 

However the problem with Totem in watching movies is that it puts my monitor to sleep every 5-10 minutes, even though I have my power Management features disabled and my screensaver set to 2 hrs.

---

### Post by jemate18 on 2008-09-28
can you type
```
top
```

and find the memory usage of VLC?

---

### Post by mc4man on 2008-09-28
Maybe try going into home directory and deleting the .vlc folder (hidden). Note if you've changed any setting in vlc you'll have to do that again, 

> However the problem with Totem in watching movies is that it puts my monitor to sleep every 5-10 minutes, even though I have my power Management features disabled and my screensaver set to 2 hrs. 

If your display is going to sleep while watching a dvd in totem then it should also be going to sleep if you were doing nothing. In other words if you booted up and walked away for 10 - 20 min. is the display asleep when you come back?

**If so **then what you can do is set the 'regard computer as idle after' time to *less* than the time it's taking for the display to be put to sleep. 

The setting in power management (x min.- never) doesn't kick in *until* the computer is considered idle.

If your using a screensaver then I'd set the idle time to just below the display sleep time.
If your not using a screensaver you could set the idle time to any time well below the sleep time.

---

### Post by HittingSmoke on 2008-09-28
> **panand178 said:**
> My VLC player was working perfectly fine till the last two days. I have been using it without any problem since I installed Hardy Heron back in April. 

But since the last two days whenever I play any movie on VLC it suddenly uses up all my 2 GB of RAM and my system hangs. Does anybody know why this might be happening and that too all of a sudden.

You might try reinstalling codecs as well. I had a similar problem when I had a bad installation of my video codecs. Any time I tried to play a video the system would hang or crash.

---

### Post by drs305 on 2008-09-28
Did you by any chance upgrade to the new version of VLC in the past couple of days? If so, you may want to revert to the older version to see if the problem perists.

If not, you might consider upgrading to VLC 0.9.3. There have been some good improvements. The easiest way to upgrade is to add this repository by going to System, Admin, Software Sources > Third Party Software and adding this repository:
```

deb http://ppa.launchpad.net/c-korn/ubuntu hardy main

```  
Usual disclaimer about this not being an official repository.

Once added, run "sudo apt-get update" and "sudo apt-get upgrade" to install the newer version of VLC.

---

### Post by panand178 on 2008-09-29
Hi All,

Thank you for all the responses/suggestions/solutions. What really worked for me finally was a combination of the following two posts:

> **wolfen69 said:**
> reinstall doing the following:
```
sudo apt-get purge vlc
```then ```
sudo apt-get clean
```then ```
sudo apt-get autoremove
``` then ```
sudo apt-get install vlc
```

> **mc4man said:**
> Maybe try going into home directory and deleting the .vlc folder (hidden). Note if you've changed any setting in vlc you'll have to do that again, 


This seems to have solved my problem for the time being. 

I am also interested in finding out more about VLC 0.9.3. I checked out the screenshots and all on the website and it looks cool. How stable is the current version? Has anyone been facing any issues with this?

P.S: Since purpose for starting this thread has been solved, I am marking this thread as "Solved". However I would like to hear from you all on VLC 0.9.3.

---

### Post by mc4man on 2008-09-29
> However I would like to hear from you all on VLC 0.9.3. 

I've tried 0.9.2 on hardy (built and from the korn repo) and both .9.2, .9.3 on intrepid.(more so on intrepid, where I'd reserve judgment for a bit, and retry from a fresh beta install

It looks like it will be a nice improvement, it terms of dvd movie playback it's broken to some degree (from what I've observed)
Mainly from the *autorun* (default player) for commercial titles. It ranges from working, to opening and crashing, to not opening at all. (newer titles are more of a problem.(auto run on hardy and intrepid

**Going vlc -> file -> open disk generally works well.(dvd's,audio cd's**

Going vlc -> file -> open directory generally fails (with a VIDEO_TS on hdd

In intrepid vlc is added a default choice for both dvd and audio cd. 
Again *autoplay* of com. dvd's, audio cd's is broken ( at least here

Changing vlc's default launch command to vlc %m solves some of the issues ( auto playing commercial dvds becomes flawless
As yet I don't see any downside to changing it, only potential improvements.

As far as .avi's nothings changed, some work, some don't, some audio, no video. ( as comparison all I've tried work fine in mplayer, xine-ui

---

### Post by panand178 on 2008-10-01
> **mc4man said:**
> I've tried 0.9.2 on hardy (built and from the korn repo) and both .9.2, .9.3 on intrepid.(more so on intrepid, where I'd reserve judgment for a bit, and retry from a fresh beta install

It looks like it will be a nice improvement, it terms of dvd movie playback it's broken to some degree (from what I've observed)
Mainly from the *autorun* (default player) for commercial titles. It ranges from working, to opening and crashing, to not opening at all. (newer titles are more of a problem.(auto run on hardy and intrepid

**Going vlc -> file -> open disk generally works well.(dvd's,audio cd's**

Going vlc -> file -> open directory generally fails (with a VIDEO_TS on hdd

In intrepid vlc is added a default choice for both dvd and audio cd. 
Again *autoplay* of com. dvd's, audio cd's is broken ( at least here

Changing vlc's default launch command to vlc %m solves some of the issues ( auto playing commercial dvds becomes flawless
As yet I don't see any downside to changing it, only potential improvements.

As far as .avi's nothings changed, some work, some don't, some audio, no video. ( as comparison all I've tried work fine in mplayer, xine-ui

Hmmm... Right now I think I will wait for the final release. As you know my VLC just got working and I don't want to mess around with it so soon and end up with more problems... :)

---

