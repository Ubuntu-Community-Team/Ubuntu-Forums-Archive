---
title: "I keep losing video/flash"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by The Populist on 2008-09-18
I have had Hardy heron installed since it first came out, and I love the OS. But this flash business is a real pain. I have Firefox 3 installed, and I am running an AMD 64 bit system. 

When I watch videos on youtube or IGN the videos run for awhile, then I suddenly lose all flash functions. The next time I get a page with flash videos, music, or adds, the display is simply a grey area, no video, no audio, no adds. 

Sometimes I can run my computer for a few days and then flash seems to degrade and disappear. Sometimes it takes just a few hours of listening to music on LastFM and watching some IGN videos to lose my flash.

I've tried everything. Gnash, libplayer, all the fixes, but I cant find the perfect installation to make flash run reliably. Does anyone have a solution to this problem?

...

---

### Post by kansasnoob on 2008-09-18
I had excellent luck after following this tutorial:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

Note: There are specific steps for 64bit and i386! (That refers to the version of Ubuntu installed, not system specs.)

And I'm running i386!

Also you can get the i386 version of Flash 10 RC here:

[http://launchpadlibrarian.net/16766494/flashplugin-nonfree_10.0.1.218%2B10.0.0.569ubuntu1%7Eppa2_i386.deb](http://launchpadlibrarian.net/16766494/flashplugin-nonfree_10.0.1.218%2B10.0.0.569ubuntu1%7Eppa2_i386.deb)

---

### Post by kolisikepu on 2008-09-18
> **The Populist said:**
> I have had Hardy heron installed since it first came out, and I love the OS. But this flash business is a real pain. I have Firefox 3 installed, and I am running an AMD 64 bit system. 

When I watch videos on youtube or IGN the videos run for awhile, then I suddenly lose all flash functions. The next time I get a page with flash videos, music, or adds, the display is simply a grey area, no video, no audio, no adds. 

Sometimes I can run my computer for a few days and then flash seems to degrade and disappear. Sometimes it takes just a few hours of listening to music on LastFM and watching some IGN videos to lose my flash.

I've tried everything. Gnash, libplayer, all the fixes, but I cant find the perfect installation to make flash run reliably. Does anyone have a solution to this problem?

...

Pop... I had the same issue as you did.  You can finally put it to bed with this tutorial.

Ubuntu-Freak by the name of Nathan posted this awesome tutorial.  [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Come back to this your thread if it works.  It worked for me and haven't had any problems since. :guitar:



~~~~~~~~~~~~~ I forgot to mention.  You probably only need Parts 1 & 2.

---

### Post by The Populist on 2008-09-18
Thanks for those guides everyone. It worked great except for one thing, Quicktime. I searched the thread and other people are having this problem as well, so I'll wait for the solution.

By the way, how do you thank people in the threads? There is some way to click and thank people for help?

...

---

### Post by KIAaze on 2008-09-18
> **The Populist said:**
> Thanks for those guides everyone. It worked great except for one thing, Quicktime. I searched the thread and other people are having this problem as well, so I'll wait for the solution.

By the way, how do you thank people in the threads? There is some way to click and thank people for help?

...

Look at the bottom right of posts:
"Quote" "Multiquote" "Quick reply" "Thanks"
It's some kind of star medal symbol.

P.S: I also currently have no flash in Intrepid (32-bit). :(
edit: Just solved it by simply doing:
sudo apt-get install --reinstall flashplugin-nonfree

---

