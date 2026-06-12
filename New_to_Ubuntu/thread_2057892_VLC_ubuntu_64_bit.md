---
title: "VLC ubuntu 64 bit"
date: 2012-09-14
forum: New to Ubuntu
---

### Post by ibbill on 2012-09-14
When I try and install VCL player from the software centre I get the following 


vlc: Depends: vlc-nox (= 2.0.3+git20120913+r385-0~r41~precise1) but 2.0.3+git20120913+r385-0~r41~precise1 is to be installed
     Depends: libavcodec-extra-53 (>= 4:0.8-1~) but 4:0.8.3ubuntu0.12.04.1 is to be installed
     Depends: libavutil-extra-51 (>= 4:0.8-1~) but 4:0.8.3ubuntu0.12.04.1 is to be installed
     Depends: libc6 (>= 2.15) but 2.15-0ubuntu10.1 is to be installed
     Depends: libfreetype6 (>= 2.2.1) but 2.4.8-1ubuntu2 is to be installed
     Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
     Depends: libqtcore4 (>= 4:4.8.0) but 4:4.8.1-0ubuntu4.2 is to be installed
     Depends: libqtgui4 (>= 4:4.7.0~beta1) but 4:4.8.1-0ubuntu4.2 is to be installed
     Depends: libsdl-image1.2 (>= 1.2.10) but it is not going to be installed
     Depends: libstdc++6 (>= 4.6) but 4.6.3-1ubuntu5 is to be installed
     Depends: libtar0 but it is not going to be installed
     Depends: libva-x11-1 (> 1.0.15~) but it is not going to be installed
     Depends: libxcb-composite0 but it is not going to be installed
     Depends: libxcb-keysyms1 (>= 0.3.8) but it is not going to be installed
     Depends: libxcb-randr0 (>= 1.1) but it is not going to be installed
     Depends: libxcb-xv0 (>= 1.2) but it is not going to be installed
     Depends: zlib1g (>= 1:1.2.3.3.dfsg) but 1:1.2.3.4.dfsg-3ubuntu4 is to be installed
vlc-plugin-notify: Depends: vlc-nox (= 2.0.3+git20120913+r385-0~r41~precise1) but 2.0.3+git20120913+r385-0~r41~precise1 is to be installed
                   Depends: libc6 (>= 2.8) but 2.15-0ubuntu10.1 is to be installed
                   Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but 2.26.1-1 is to be installed
                   Depends: libglib2.0-0 (>= 2.12.0) but 2.32.3-0ubuntu1 is to be installed
                   Depends: libgtk2.0-0 (>= 2.8.0) but 2.24.10-0ubuntu6 is to be installed
vlc-plugin-pulse: Depends: vlc-nox (= 2.0.3+git20120913+r385-0~r41~precise1) but 2.0.3+git20120913+r385-0~r41~precise1 is to be installed
                  Depends: libc6 (>= 2.8) but 2.15-0ubuntu10.1 is to be installed
                  Depends: libpulse0 (>= 1:1.0) but 1:1.1-0ubuntu15.1 is to be installed

Thanks for your help

---

### Post by ibbill on 2012-09-14
I was missing tualatrix in the repositories thanks

---

### Post by ibbill on 2012-10-05
Wow I just ran an update and it removed VLC player and now I get the same message as the one I posted in the original.

Not sure how the update would delete the vlc player but it did. Any help would be greatly appreciated.

---

### Post by newb85 on 2012-10-05
Have you installed Ubuntu Restricted Extras?

---

### Post by ibbill on 2012-10-05
NewB85 thanks for the reply yes I have them installed.

VLC was working just find done the last set of updates and it removed VCL how or why I have no idea.

I have purged vlc also and tried to reinstall no luck. Thanks again for any help.

---

### Post by mc4man on 2012-10-06
Possibly the ppa you are using published the 32 bit but not the 64 bit packages. 
In that case on a 64 bit install you could of updated an "all".deb (those are done in the i386 build) without matching 64 bit updated packages, this would cause your current ones to be removed due to dep. issues
The all.deb would have been in this case "vlc-data"

So if not squared away yet then  wait a bit for all the 64 bit vlc packages to publish or - remove vlc-data, update your sources & install the prior ppa 64 bit version of vlc.

reference ppa page - [https://launchpad.net/~videolan/+archive/stable-daily/+packages](https://launchpad.net/~videolan/+archive/stable-daily/+packages)
 showing not all published yet... in screen

Edit: - 
there is also another probable issue with 12.04 vlc packages from that ppa - see here
[http://ubuntuforums.org/showthread.php?t=2066755](http://ubuntuforums.org/showthread.php?t=2066755)
and here
[https://answers.launchpad.net/ubuntu/+question/210401](https://answers.launchpad.net/ubuntu/+question/210401)

As shown in screen 2 the current amd vlc package still deps on **only** fonts-freefont-ttf so  can't be installed in 12.04 as that package doesn't exist
(it's a 12.10 package
So in any event you'll need to wait for the ppa to fix it's 12.04 packages or provide fonts-freefont-ttf yourself

---

### Post by ibbill on 2012-10-06
mc4man thank you ever so much.I have always used 32bit but thought I would try the 64 bit. oops I was wrong.

I have  goggled for this problem and never found any help or final solution that  you have provided.Your awesome. Partner

---

### Post by ibbill on 2012-10-06
mc4man  Are you kidding me oh my.I installed the gnome media player and was using that while I was trying to find an answer to this problem.

The thread you posted did it

[http://ubuntuforums.org/showthread.php?t=2066755](http://ubuntuforums.org/showthread.php?t=2066755)  this thread fixed the problem and I installed VCL from the software centre.

Followed wamai post. Not sure when the fonts were installed maybe when I installed gnome player.

Note I also have on another partition Mint Mate 13 installed 64 bit but have no problem with VLC media player 2.0.3 Twoflower 

Partner I yield to you your awesome thanks again for you help.marking solved

---

