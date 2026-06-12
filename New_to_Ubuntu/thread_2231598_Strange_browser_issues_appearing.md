---
title: "Strange browser issues appearing"
date: 2014-06-26
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2014-06-26
The first of several may be the easiest to resolve, though it is not obvious to me at this point.

My Chromium browser shows in "about Chromium" that it is version "34.0.1847.116  Ubuntu 12.04  (260972) " (but I am using Ubuntu 14.04 without Unity)

whereas [http://www.chromium.org/developers/calendar]("http://www.chromium.org/developers/calendar") shows:

35.0.1916.153 is the current stable release. I have tried to figure out how to update, but do not see an option. (I was under the impression that Chromium auto-updated, but maybe not)

Can anyone assist? Thanks.

---

### Post by LastDino on 2014-06-26
Is the PPA in software and update manager still tick marked? If it is, it should automatically update.

---

### Post by Odyssey1942 on 2014-06-26
I am looking at the "more info" for the installed Chromium in the U. Software Center Manager, but do not see the term "PPA". Where do I find it? Thanks.

---

### Post by Odyssey1942 on 2014-06-26
Think I found it under Update Manager. There are four tick options and I have them all ticked except for Pre-released updates, so it shoudl be updating.

However it clearly is not. Should I reinstall?

---

### Post by LastDino on 2014-06-26
Oh, pardon me, I read that as ''Chrome'' browser, ignore my post as it was meant for ''Chrome''. I don't know anything about Chromium, sorry, but someone here might be able to help you, so hang in there ^^

As for re-installing, Chromium like chrome is integrated with your mail if you allow it to, so everything including apps and bookmarks are saved. All you need to do after re-install is enter the same gmail address you used to synch with older Chromium install. So, its your choice, but wait for someone else to chip in here,

---

### Post by grahammechanical on 2014-06-26
About Chromium on my system says

> [COLOR=#303942][FONT=Arial]Version 34.0.1847.116 Built on Ubuntu 14.04, running on Ubuntu 14.10 aura (260972)[/FONT][/COLOR]

I am using Utopic Unicorn (14.10). We have the same version.

Regards.

---

### Post by Odyssey1942 on 2014-06-26
Hello Graham,

The reason I was looking into version numbers is that Chromium will not play YouTube videos. It gives this message:

> An error occurred, please try again later.

Waiting doesn't help, and I was hoping that an update would cure.

We appear to be using the same version (except that mine says Ubuntu 12.04 where yours says 14.04) so what's the deal with the Chromium website saying that 34.0.1847.116 Ubuntu 12.04 (260972) is the current stable version?

In any case, do I need an extension to play YouTube videos?

Edit: Man, I am really losing it (see disclaimer at bottom). Suddenly dawned on me that I am using Ubuntu 12.04, not 14.04. Brain fart!

---

### Post by LastDino on 2014-06-26
Were you able to play those vids before? 

Well, if you've flashplayer plugin and still not able to play. Maybe it is time to move on to 

[https://chrome.google.com/webstore/detail/html5-video-for-youtube/dolajcekhnohkpncmhgledbmndjpblei?hl=en](https://chrome.google.com/webstore/detail/html5-video-for-youtube/dolajcekhnohkpncmhgledbmndjpblei?hl=en)

---

### Post by Dennis N on 2014-06-26
> The reason I was looking into version numbers is that Chromium will not play YouTube videos

Chromium 34 does not support the old adobe flash plugins. Now you need to use the pepperflash plugin.

```
sudo apt-get install pepperflashplugin-nonfree
sudo update-pepperflashplugin-nonfree --install
```

---

### Post by Odyssey1942 on 2014-06-26
Not only did it play them previously, I now find that it still will play some YT videos. Just tried a favourite:

[https://www.youtube.com/watch?v=kPOC-RC3j3Q&list=RDkPOC-RC3j3Q](https://www.youtube.com/watch?v=kPOC-RC3j3Q&list=RDkPOC-RC3j3Q)

(that Mike Farris is some vocalist!) and it started off playing the audio and video, then the video disappeared though the audio works fine. YT went on to the next song for which the video is also black and audio is fine.

DSLReports shows downloading at 4.4Mb so not a pipe issue.

Will take your suggestion and leave this for now and go on to the more serious issue.

Gmail (only) in Chrome (please note switching from Chromium) browser (with no-scripts extension installed) has become very slow, ranging from sluggish to non-responsive. It can take 30 seconds or more to do a search, send an email, open a message, etc, or just not complete it at all.

In all cases, other websites load and function normally. Using an incognito window, gmail functions normally (which is very fast). 

Gmail functions normally in Chromium which is why I was using it.

Any ideas?

---

### Post by Dennis N on 2014-06-26
> Not only did it play them previously, I now find that it still will play some YT videos.

Your old Chromium in Ubuntu 12.04 was an older version that still supported the adobe flashplugins. After you were upgraded to version 34, that is no longer the case. See post #9 to fix this. You can still play some videos probably because of the HTML5 support that Chromium has.

---

### Post by Odyssey1942 on 2014-06-26
Dennis, Thanks for yours. It must have posted while I was writing my previous.

Will try the fix and report back.

Any ideas on the Chrome/Gmail prob?

---

### Post by Odyssey1942 on 2014-06-26
Here is what I got when I ran the code:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package pepperflashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package 'pepperflashplugin-nonfree' has no installation candidate


---

### Post by Dennis N on 2014-06-26
Sounds like that package is not in the 12.04 repositories. What do you get for:

```
apt-cache show pepperflashplugin-nonfree
```

If it says "unable to locate package pepperflashplugin-nonfree"  you have to go to a PPA to get the pepperflash --->

Looks like this is it:

[https://launchpad.net/~skunk/+archive/pepper-flash](https://launchpad.net/~skunk/+archive/pepper-flash)

As to gmail, I don't use Chrome. Chromium works fine for me.

---

### Post by Dennis N on 2014-06-26
Here is an article about the steps needed to install pepperflash and get it working:

[http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html](http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html)

---

### Post by Odyssey1942 on 2014-06-26
Here's the output:
> N: Can't select versions from package 'pepperflashplugin-nonfree' as it is purely virtual
N: No packages found

So it looks like I need to work on the pepperflash install. Will get back to you in a bit. Things are a little crazy here.

BTW, since you are a Chromium user, what version of Ubuntu do you use. In case 12.04, what do you make of the discrepancy between the version I mentioned above, which my 12.04 apparently thinks is current, and the one described as current stable on the Chromium website. Is it only for later versions of Ubuntu?

---

### Post by Dennis N on 2014-06-27
That is exactly the error message I got when I tried installing the pepperflashplugin from 12.04 (using the simulation option). You can also check with Synaptic - it isn't in the precise repositories. At the same time, it seems the version of Chromium that would be installed in 12.04 is 34, so it seems odd that the necessary flash package isn't there as well. There must be a reason.

I installed Chromium on Xubuntu 14.04, and also have it installed on Lubuntu also. The version of Chromium in 14.04 is 34 (specifically 34.0.1847.116-0ubuntu2) same as yours. There has been no upgrade to 35 offered yet.

Version 34 is the latest in Ubuntu for both 12.04 and 14.04.
[https://launchpad.net/ubuntu/precise/+package/chromium-browser](https://launchpad.net/ubuntu/precise/+package/chromium-browser)
[https://launchpad.net/ubuntu/trusty/+package/chromium-browser](https://launchpad.net/ubuntu/trusty/+package/chromium-browser)

My version check in Xubuntu 14.04:

```
dmn@Erica:~$ apt-cache policy chromium-browser
chromium-browser:
  Installed: 34.0.1847.116-0ubuntu2
  Candidate: 34.0.1847.116-0ubuntu2
  Version table:
 *** 34.0.1847.116-0ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe i386 Packages
        100 /var/lib/dpkg/status 

```
In 14.04, I installed the pepperflash with the commands in post #9. It is in the 14.04 repositories. Now we know that won't work in 12.04.

---

