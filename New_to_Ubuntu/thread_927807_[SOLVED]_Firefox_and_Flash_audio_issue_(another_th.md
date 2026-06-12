---
title: "[SOLVED] Firefox and Flash audio issue (another thread)"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by oldsoundguy on 2008-09-23
I am putting this in beginner because this area gets the quickest responses.
(I am not a total beginner)

Ubuntu 7.10
Firefox 3.0.1 (from the Mediabuntu repository, not from Synaptic or the regular repositories)
Adobe Flash 9.0.124 from Synaptic
Alsa base, oss & util from Synaptic (no other Alsa is installed)

It basically does not work this way for Youtube, especially. Zip in the way of audio.

ALL other audio works just fine.  Amarok will play audio from my USB drives on my networked machines without a problem.  (thanks to the developers for fixing the volume control problem on 5.1 digital surround, BTW!) 

I can also play video (with audio) from the same USB drives, so the issue is JUST with the Firefox and Flash.  

I know that Ubuntu, in reality, has nothing to do with either program's development, but am hoping there is a really non convoluted way to fix the issue without waiting months for the other two companies to acknowledge that there is problem.

Have spent way too much time on this in searching the forums.  Mostly all have "fixes" that I have done already or are seriously outdated and not really related to the current problem with the newest releases.

---

### Post by mevets on 2008-09-23
You tried switching everything in **System > Prefs > Sound** to ALSA instead of their defaults? This really sounds like a pulseaudio problem.

---

### Post by kansasnoob on 2008-09-23
Well first of all make sure you have Sun Java 6 installed. Just go to synaptic and click on search, then type in sun-java6, then install:   

    * sun-java6-jre
    * sun-java6-bin
    * sun-java6-plugin
    * sun-java6-fonts

Try that! If you want to see just what plugins you have installed then type; about:PLUGINS in the URL box.


Now, I have been using Flash 10 Release Candidate in Hardy with great results. Unfortunately I haven't been able to find a .deb for Gutsy, but the Download for Linux (TAR.GZ, 3.78 MB) is here:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Instructions to install here:

[http://www.cyberciti.biz/tips/linux-install-flash-player-10.html](http://www.cyberciti.biz/tips/linux-install-flash-player-10.html)

But, if I recall correctly, I'd have sworn that I had Flash working properly in Gutsy without too much fiddling around:confused:

---

### Post by linux5uper on 2008-09-23
Have you tried this fix?

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

It's as recent and 'official' as it gets, from a pulseaudio developer (afaik).

---

### Post by kansasnoob on 2008-09-23
> **mevets said:**
> You tried switching everything in **System > Prefs > Sound** to ALSA instead of their defaults? This really sounds like a pulseaudio problem.

Gutsy didn't use Pulse Audio.

---

### Post by kansasnoob on 2008-09-23
> **linux5uper said:**
> Have you tried this fix?

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

It's as recent and 'official' as it gets, from a pulseaudio developer (afaik).

Again, this is Gutsy. Gutsy didn't use Pulse audio.

---

### Post by linux5uper on 2008-09-23
> **kansasnoob said:**
> Again, this is Gutsy. Gutsy didn't use Pulse audio.

Excuse me, but could you actually read the title of the thread in the link before you comment? It actually says 'Hardy Heron', unless I'm hallucinating.

---

### Post by mevets on 2008-09-23
> **kansasnoob said:**
> Gutsy didn't use Pulse Audio.

sorry, missed they version number quoted in 1st post. Id attribute the problems with flash 10 then.

---

### Post by kansasnoob on 2008-09-23
> **linux5uper said:**
> Excuse me, but could you actually read the title of the thread in the link before you comment? It actually says 'Hardy Heron', unless I'm hallucinating.

I read:

>  Firefox and Flash audio issue (another thread)
I am putting this in beginner because this area gets the quickest responses.
(I am not a total beginner)

**Ubuntu 7.10**
Firefox 3.0.1 (from the Mediabuntu repository, not from Synaptic or the regular repositories)
Adobe Flash 9.0.124 from Synaptic
Alsa base, oss & util from Synaptic (no other Alsa is installed)

---

### Post by linux5uper on 2008-09-23
> **kansasnoob said:**
> I read:

I apologize,  my mistake. 

I might have used this solution on my Gutsy install

[http://www.derekhildreth.com/blog/how-to-fix-the-no-sound-issue-in-firefox-flash/](http://www.derekhildreth.com/blog/how-to-fix-the-no-sound-issue-in-firefox-flash/)

it was long ago though.

---

### Post by oldsoundguy on 2008-09-23
Ubuntu 7.10 = Gutsy

Thus far, none of the above .. have the Java installed already, ALSA is default and as noted WORKS. And. as I noted, most of the supposed fix threads, although worked for others for their problem(s), did NOT work on this particular issue.

I have been using Linux in one form or another for nearly 5 years, but last October switched to relatively full time use because Gutsy proved to be the first system that worked out of the box on all of my computers.  Allowing me to add the programs I needed to function on a day to day basis and to put Windows in the "use only when needed for Adobe and Media and otherwise ignore it" category.

I had NO issues with Flash or Firefox using same until the latest upgrades. (and I do NOT want to go back to FF 2.x)

This is NON CRITICAL.  Just an annoyance that will be worked out eventually. (but I WILL try using the Flash 10 if all else fails .. normally don't like using Betas on my main machine .. just common sense.)

---

### Post by kansasnoob on 2008-09-23
I can assure you that the Flash 10 RC works very well in Hardy. I have even used it in Xubuntu 8.04 which I believe still uses Alsa rather than Pulse Audio. (I can't actually "swear" that Xubuntu 8.04 uses alsa, I'm just relying on memory, I don't have an Xubuntu box in the house)

I just hate installing tar.gz stuff!

---

### Post by kansasnoob on 2008-09-23
I had a thought, perhaps a silly one, try going to synaptic and searching for gstreamer.

Then install everything that starts with gstreamer .......... really! It won't break anything.

I'm thinking especially gstreamer0.xx-alsa (the xx is version # and I don't know what it is in Gutsy), but I always install ALL gstreamer. Good, bad, ugly, etc!

---

### Post by oldsoundguy on 2008-09-23
gstreamer has been installed since day one.  

I may try some stuff on one of the non-critical Ubuntu machines to see IF it will work.  I most assuredly do NOT want to dump this box with some upscrewed patch as 99% of my on line stuff and home project stuff goes through it!

FOLLOWUP!
Installed Flash 10 .. no joy, same issue with YouTube!

---

### Post by oldsoundguy on 2008-09-23
FOUND THE PROBLEM! .. now using Flash 10, but in messing with things it kludged Alsa.
This thread: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
Has the method for re-installing (thus repairing) Alsa!

No thank you button on the post, but the guy deserves a big thanks!

---

