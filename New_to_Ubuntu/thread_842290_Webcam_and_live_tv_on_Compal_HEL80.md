---
title: "Webcam and live tv on Compal HEL80"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by martindoom on 2008-06-27
Hi all.

I started this thread afew days ago [http://ubuntuforums.org/showthread.php?t=832540](http://ubuntuforums.org/showthread.php?t=832540) but it seems to have run it's course. I did get many of my initial problems solved but the following are still unresolved:

1. Get my webcam working (integrated on a Compal HEL80c) I found this, [http://www.linux-projects.org/modules/news/](http://www.linux-projects.org/modules/news/) but none of the downloads seem to work (i get an error messeage mentioned in one of my posts in this thread), so i must need the kernel listed at the same link, i guess, but don't know where to put it once i've downloaded it as it tells me i need to choose an association/program to open it with (i have the same prob with Realplayer 11 for Linux.

2. Get the TV card working. MythTV says i need gxine but again this is getting too technical for my current ability, what with the additional instructions found here [http://www.mythtv.org/wiki/index.php/Video_capture_card](http://www.mythtv.org/wiki/index.php/Video_capture_card) for my lifeview flyTV hardware. Really need to immerse myself in the basics of the 'terminal' etc.

3. Get Skype working with video. I think Skype 2.0 for linux will do this but it's no use unless the webcam works first.

For problem 1 i've downloaded sn9cxxx_2.13-1ubuntu1_i386.deb and patch-2.6.25.9 but i don't know where to put the patch and when i try to intall the driver i get 'Error: Dependency is not satisfiable: linux-image-generic'

For problem 2 i'm clueless doh!

Any help is greatly appreciated.

---

### Post by nothingspecial on 2008-06-27
Have you tried cheese?

```
sudo apt-get install cheese
```

Then to run it just ```
cheese
```

After installing that on my laptop Skype with web cam magically worked. Don`t know how though.

---

### Post by martindoom on 2008-06-27
Don't know why but my e-mail alerts are erratic so didn't see your reply for a bit. I'll give it a try but my webcam's not functioning at all right now.

I'm basically doing everything as an experiment to get one of these laptops fully functioning b4 September 1st when schools start as that's what i do...Help low budget, less important (to the politicians) schools have the same scope as urban schools mainly in Eastern Europe. You can see all at [http://www.tehne.ro/education/tehne_romania_ngo.html](http://www.tehne.ro/education/tehne_romania_ngo.html) although this link is for the 'Mother' organisation in Romania as it's a very new program here in Estonia and as such,so far, without a website.
.

**(Edit)** Well...it didn't work. The important point for me here is that the Compal HEL80 has some specific problems listed in the link in OP of this thread. The official Ubuntu 8.04 test of compatibility with the HEL80 says that the webcam will work but i need to install the kernel and driver listed,again, in the OP of this thread. At the risk of sounding rude...could someone pleeeeaaase just tell me what to do with the software i've downloaded on the passive advice of other's with the same rig???!!!

You've all helped me get this far in only a week. Are these 2 problems really so out there that i should forget about resolving them? I'm reading, amongst others, Beginning Ubuntu Linux - From Novice To Professional (2006 - yes i know it's out of date but you try finding something more modern out here in Estonia!), Ubuntu for Non-Geeks (2nd Ed), Ubuntu Linux - Bible [2007] so i am trying to learn and resolve my own problems. 

Please help based on the threads criteria or suggest another forum location that might have an idea how to resolve these probs!

All the best and i'm on my knees doing the religious thing...hoping and praying.

---

### Post by mlapaglia on 2008-10-07
super old thread i know, but support should be coming in intrepid for the hel80's webcam driver.

they are under heavy development right now, if you check launchpad there are a few bugs reported for this.

---

