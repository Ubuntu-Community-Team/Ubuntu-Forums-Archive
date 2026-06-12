---
title: "Hardy Video Hell"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Jasethemuss on 2008-04-30
Hi there,

I've had a few ongoing problems with video which I haven't had much trouble resolving after trawling the site and further afield. I've followed all the steps here [http://ubuntuforums.org/showthread.php?t=766683&highlight=mplayer+hardy](http://ubuntuforums.org/showthread.php?t=766683&highlight=mplayer+hardy)
but am still having trouble on a couple of embedded video sites.

I can play quicktime movies from the apple site fine, but some others I'm just give me a blank screen with no ability to right click for menu options or anything. For example, does anyone know what I would need to view the video on this site here: 

[http://www.tv3.co.nz/VideoBrowseAll/3NewsLiveStream/tabid/387/Default.aspx]("http://www.tv3.co.nz/VideoBrowseAll/3NewsLiveStream/tabid/387/Default.aspx")

Although mplayer and its firefox plugin are installed, embedded videos don't show any acknowledgement that they're using mplayer (e.g. the mplayer icon in the corner of the screen, the loading % etc). Is this normal for 8.04 now, or is it actually using another application possibly?

Thanks in advance...

---

### Post by Roger D on 2008-04-30
Perhaps you need to install Flash - go to Synaptic

Roger D

---

### Post by Jasethemuss on 2008-05-01
Thanks Roger - I already have flash installed though; version 9.0.124 according to synaptic.

---

### Post by diablo75 on 2008-05-01
Try Applications>Add/Remove, change the filter to show "all available applications", and then do a search for the word "restricted".  Check off "Ubuntu Restricted Extras" if it's not already checked, and then click Apply.  This will install Java as well as a bunch of video codecs.

I'm not exactly sure why, but I have no problem playing the video.  The source HTML appears to reference a WMV file in there....

---

### Post by FreewheelinFrank on 2008-05-01
The Mplayer plug-in comes up for me, but then it just shows "stopped".

---

### Post by diablo75 on 2008-05-01
> **FreewheelinFrank said:**
> The Mplayer plug-in comes up for me, but then it just shows "stopped".

I'm running a fresh install of 8.04, and Firefox is using totem-player by default instead of mplayer.  If you're getting mplayer, you could try hitting the play button a few times.  Sound stupid, but most of the time it does the trick...

---

### Post by Jasethemuss on 2008-05-01
> Try Applications>Add/Remove, change the filter to show "all available applications", and then do a search for the word "restricted". Check off "Ubuntu Restricted Extras" if it's not already checked, and then click Apply. This will install Java as well as a bunch of video codecs.

I'm not exactly sure why, but I have no problem playing the video. The source HTML appears to reference a WMV file in there....

I'd already installed the restricted extras - double checked as per your suggestion, but it was ticked. The problem seemed to occur after I ran a bunch of recommended system updates. It had been working previously, but it's a mystery to me what's actually changed.

---

### Post by Jasethemuss on 2008-05-01
I'm thinking of uninstalling all the plugins and firefox and then running through a fresh install of everything I need based on the tutorial mentioned above. Also, I think I may have accidentally wiped one of the lines on my sources list. A previous post on another thread [http://ubuntuforums.org/showthread.php?t=739119](http://ubuntuforums.org/showthread.php?t=739119) gave a sample default list:
> ## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security multiverse


Does that look sound, or should I be using something else?

---

### Post by Perfect Storm on 2008-05-01
Uninstall **totem-mozilla** it usually interfer with mplayer-plugin.

---

### Post by Jasethemuss on 2008-05-01
Un> install totem-mozilla it usually interfer with mplayer-plugin.

Yeah, I gathered that after reading a few other similar forum questions, but I made sure I'd uninstalled that before I posted here. So, it shouldn't be a case of totem interfering. Thanks though.

---

### Post by por100pre1 on 2008-05-01
Weird. I can't even access that webpage. :(

---

### Post by Jasethemuss on 2008-05-02
Maybe I should do a clean install of Hardy, given that I upgraded from Gutsy? I'd want to make sure I didn't lose all my data though...
I would just shrug my shoulders and accept I can't play some formats, but I pay for a subscription to a jiu-jitsu site, so it's just money down the drain and I don't want to have to cancel it if there's a chance of solving the problem.

Any advice?

---

### Post by Jasethemuss on 2008-05-03
I'm glad I'm already bald, else I woulda had a bleeding scalp from tearing my hair out over the hours I've spent on this. The good news is I've finally sorted the problem. It was a conflict between mozplugger and the mozilla-mplayer plugin. As soon as I removed mozplugger, bingo. 
I still couldn't get it to work with the gnome-mplayer though and reverted back instead to the regular mplayer app, but I'm happy with that.

Thanks for the tips everyone.

---

