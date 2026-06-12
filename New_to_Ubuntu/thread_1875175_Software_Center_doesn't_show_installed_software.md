---
title: "Software Center doesn't show installed software"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by Deanobats on 2011-11-04
Hi there,
I'm very new to Linux, having only a little experience in the past with Unix on a Silicon Graphics. The history is that I had an old Dell Latitude D830 laptop with a dying installation of XP on it, so thought I'd try Ubuntu. After a few trys, I got windows wiped and Ubuntu 11.10 installed. I even managed to get the troublesome Broadcom wifi enabled. However, installing software has proved interesting, a steep learning curve for me. I open Software Center, and I can see software to install, and installing it works fine, but there is nothing in the lists that shows up in the 'installed software' tab, just a listing of catergories. I can see installed software listed in synapic though.

Also, installing a ppa for say Jdownloader does not appear in software center or synaptic, even though I have enbaled the repositories. i have no idea if these two things are related?

Any ideas?

Ta!

Dean

I should add that in 'Installed Software' there are some 1600 items listed in the 'show technical' box at the bottom, but clicking this doesn't show any of them.

---

### Post by jmajeremy on 2011-11-04
After you install something thru the software centre, are you able to run the program? Does it get added to the applications menu?

As for Jdownloader, make sure you run ```
sudo apt-get update
``` before you look for it in the repositories. I think software centre usually does this automatically, but might be worth doing it manually in the terminal just to be safe.

---

### Post by Deanobats on 2011-11-04
Thanks for the reply. if I install something through the software center it appears, and it runs fine. Then I check in the 'installed software' tab, there is nothing there, even after a reboot. Oddly, the only thing I can get to appear in the installed software tab of the software center is google earth by dropping the tab down to show 'other'.

As for JDownloader, I've done the sudo apt-get update, which appears to work, but JDownloader doesn't appear in dash, software center or synaptic. I don't know if these two issues are related.

---

### Post by Rex Bouwense on 2011-11-04
When you go to installed software, click on the little arrow below each category and the programs for that category while be visible  I believe that is how it works.  Enjoy.

---

### Post by Deanobats on 2011-11-04
Aha!!!! Fantastic!!!! The little teeny weeny arrow thing, that did it! I had tried clicking on the category but that didn't work. I hadn't realised that clicking on the arrow would do it. Now all i have to do is resolve my issue with JDowloader. One small step at a time. And thanks again!

Dean

---

### Post by jmajeremy on 2011-11-04
Have you tried doing ```
sudo add-apt-repository ppa:jd-team/jdownloader && sudo apt-get update && sudo apt-get install jdownloader && sudo apt-get upgrade
```?

---

### Post by Deanobats on 2011-11-04
Hi, the add-apt-repository works, it downloads, but the apt-get update returns:
E: Type ‘src’ is not known on line 2 in source list /etc/apt/sources.list.d/jd-team-jdownloader-oneiric.list

I'm not sure what that means!

Oh an now neither software center or synaptic opens. Synaptic opens then shows the same error
E: Type ‘src’ is not known on line 2 in source list /etc/apt/sources.list.d/jd-team-jdownloader-oneiric.list
and then closes! Arghhh!

Whew, now we're back. The file jd-team-downloader-oneiric.list actually read:

```
deb [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) oneiric main
src [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) oneiric main

when I think it should have read:

deb [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) oneiric main
deb-src [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) oneiric main
```

And then both synaptic and software manager failed to open.

So I had to use sudo gedit to edit it.

 Now at least they open even if I still have no JDownloader. I think I'll leave it at that and just use Tucan, that does work, though not with Rapidshare at the moment, but that's a problem for another day...

---

### Post by Rex Bouwense on 2011-11-05
You are aware that you can only use either the Software Center or Synaptic.  I don't believe that you can use them simultaneously.  I mean you can use them both but not at the same time.  At least I think that is how it works.

---

