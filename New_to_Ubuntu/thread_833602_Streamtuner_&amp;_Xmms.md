---
title: "Streamtuner &amp; Xmms"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by sonnyrme on 2008-06-18
This is probably a simple one for you guys, but I am lost.
When I click on a stream in  Streamtuner to tune in to, it tells me it cannot play it. No xmms file or folder. The repo's did not have xmms but had xmms2. I downloaded that ( along with plugins I thought I might need).
Went back to Streamtuner & retried & it still says no xmms.What can I do? Help please.

---

### Post by Technoviking on 2008-06-18
Goto **Streamtuner --> Edit --> Preferences --> Applications** and change xmms Listen to .m3u and Listen to stream from **xmms %q** to **totem %q**.

You can also install mplayer and use **mplayer %q**.

---

### Post by vvvladut on 2008-06-21
Can anyone tell me what happened to the XMMS media player? It's no longer in the repositories, only XMMS2, which I have installed but cannot find in the menu. Where is XMMS and what is XMMS2?

---

### Post by avtolle on 2008-06-21
XMMS was (and is) an audio player which by "look and feel" resembled Winamp. I understand it was dropped from the Ubuntu repositories because it wasn't being maintained in a current state (from memory, which may be, and is often, wrong). Audacity is a fork of XMMS, and can be found in the repositories. IIRC, one may build a current version of XMMS from source, there were threads on this back in April about the time 8.04 was released. Don't know what XMMS2 is, but hazard a guess that it is a fork from the original XMMS project.

---

### Post by vvvladut on 2008-06-21
I installed Audacity, and to my pleasant surprise, it looks exactly like XMMS, which in turn looked and worked much like Winamp, which is why I loved it. Forget about XMMS2 then, problem solved. It even integrates well with Stream tuner!

---

### Post by avtolle on 2008-06-21
Glad it worked for you. I neglected to mention that I had installed Audacity and was quite pleased with it for some of the same reasons you are. If you would, please mark this thread "Solved" by use of the thread tools.

---

### Post by markbuntu on 2008-06-21
There is a thread around here somewhere about getting the xmms debs for Hardy for both 386i and amd64. I tried it on both and it works fine. In fact I am using streamtuner with xmms right now on my amd64 hardy. No need to build from source code just download the debs and install with GDebi Package Installer. 

Contrary to popular belief xmms is alive and well, just not in the Hardy repository.

If streamtuner worked with rythmbox I would not have bothered but I don't care much for audacity and totem is not quite the thing for listening to streaming audio.

---

### Post by Eisenwinter on 2008-06-21
I installed xmms from source, with the deb packages I encountered dependency problems.

I also had to install libxmms-perl from source, it's a library for Perl, to retrieve info from, and control XMMS.

---

### Post by sonnyrme on 2008-06-22
Sorry , been gone a couple of days. Yes I tried changing the preferences in Stream tuner but it goes right back to the xmms setting. I have audacity but Streamtuner only wants to play through xmms. I am going to uninstall streamtuner & re-install it. might have been a bad download, since none of these will work.
Thanks guys.

---

### Post by casperfelix on 2008-08-24
> **sonnyrme said:**
> This is probably a simple one for you guys, but I am lost.
When I click on a stream in  Streamtuner to tune in to, it tells me it cannot play it. No xmms file or folder. The repo's did not have xmms but had xmms2. I downloaded that ( along with plugins I thought I might need).
Went back to Streamtuner & retried & it still says no xmms.What can I do? Help please.

Install "audacious" and then change streamtuner's prefrences to "audacious %q". Audacious is a sweet little program.

---

