---
title: "Proper file system folder for Thunderbird program files?"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by carbon512 on 2012-06-14
[SIZE=2]For various reasons, I manually installed Thunderbird 11.0 on my  Ubuntu 11.04 laptop.  I've locked down  11.04 since most everything works right on my machine, so I am not  doing auto updates of much of anything. I found and installed  Thunderbird 11.0 manually and it works fine.
  
I only know enough Ubuntu stuff to make myself dangerous though, and in doing this, I ended up with various versions of Thunderbird  all over my file system. 

I can start the Thunderbird version I want by  navigating to the desired folder and running that shell  script. But any thunderbird shortcut I create for my task panel ends up opening  the default older version of Thunderbird, or not working at all. And  [/SIZE][SIZE=2]no[/SIZE][SIZE=2] "mailto" links will open[/SIZE][SIZE=2]Thunderbird anymore, even though browsers etc. show Thunderbird as the app to use.
  
I have created a mess. Where should all my Thunderbird 11 files be;  meaning, in which folder -- usr/lib? or usr/lib/thunderbird? or usr/bin?  or usr/[username] ? or...? Yes, I have tried all those places and more...
  
If I remove thunderbird entirely using the software center, and then  re-install it, I end up getting an old version again, even though I have  updated the repository. And not all thunderbird files are removed --  the ones I stuck in odd places myself still remain of course.
  
What's the simplest way of cleaning this up or at least getting my mailto links and panel shortcuts working again?
  
Thanks.[/SIZE]

---

### Post by forrestcupp on 2012-06-14
If you have Synaptic installed, you can search for Thunderbird, right click on it, and choose Properties. In that window, click the "Installed Files" tab, and it will show you all of the directories that Thunderbird is installed to, which are a lot.

---

### Post by MG&amp;TL on 2012-06-14
Typically, user programs should go under /usr/bin/ - see here for a complete list: [http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

---

### Post by ajgreeny on 2012-06-14
Use the ppa for TB and you can get v13.

Use command ```
sudo add-apt-repository ppa:mozillateam/thunderbird-stable
``` and you are good to go, though you may need to try to get rid of all the manually installed cruft related to the various installations you've made.

---

### Post by carbon512 on 2012-06-14
Well I figured out the thunderbird folder for my version needed to be in /usr/lib, but that I needed the link to the shell script for that version to be in /usr/bin. So my main concerns above have been solved!  Panel shortcut works, mailto links work, etc. These tips helped me search and learn, thanks. I should still clean up the extra files though.

I had run 
```
sudo add-apt-repository ppa:mozillateam/thunderbird-stable
``` several times but only just now discovered "force version" in Synaptic, so that explains why the old version kept re-installing, despite my best effors.

There was some issue I had with Thunderbird 12, which I why I went down to 11... I cannot recall what though. I use Lightning with it, maybe it was tied to that? Next time I feel adventurous I'll try Thunderbird 13. Does the Thunderbird Indicator plugin work with it? It doesn't work with Thunderbird 11 and I do miss it. I get the bubble notifications, but no colored indicator on the envelope icon.

---

### Post by forrestcupp on 2012-06-15
That's the main problem with using the PPA. Sometimes it takes a while for some of the addons to catch up.

---

