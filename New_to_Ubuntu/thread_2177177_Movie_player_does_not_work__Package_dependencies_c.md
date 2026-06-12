---
title: "Movie player does not work : Package dependencies cannot be resolved"
date: 2013-09-27
forum: New to Ubuntu
---

### Post by davie1994 on 2013-09-27
Hi guys - I'm fairly new to this ubuntu malarkey but here's to hoping someone can help.

My movie player does not work, and when I try to get the session installer to update the relevant packages it comes up with an error stating that "package dependencies cannot be resolved" and then a whole load of detail that goes like this

 The following packages have unmet dependencies:

gstreamer0.10-plugins-ugly: Depends: libc6 (>= 2.7) but 2.15-0ubuntu10.4 is to be installed
                            Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
                            Depends: libglib2.0-0 (>= 2.31.2) but 2.32.3-0ubuntu1 is to be installed
                            Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.35.2) but 0.10.36-1ubuntu0.1 is to be installed
                            Depends: libgstreamer0.10-0 (>= 0.10.35.2) but 0.10.36-1ubuntu1 is to be installed
                            Depends: libmad0 (>= 0.15.1b-3) but 0.15.1b-7ubuntu1 is to be installed
                            Depends: liborc-0.4-0 (>= 1:0.4.16) but 1:0.4.16-1ubuntu2 is to be installed
                            Depends: libstdc++6 (>= 4.1.1) but 4.6.3-1ubuntu5 is to be installed
gstreamer0.10-plugins-ugly:i386: Depends: libc6 (>= 2.7) but 2.15-0ubuntu10.4 is to be installed
                                 Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
                                 Depends: libglib2.0-0 (>= 2.31.2) but 2.32.3-0ubuntu1 is to be installed
                                 Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.35.2) but 0.10.36-1ubuntu0.1 is to be installed
                                 Depends: libgstreamer0.10-0 (>= 0.10.35.2) but 0.10.36-1ubuntu1 is to be installed
                                 Depends: libmad0 (>= 0.15.1b-3) but 0.15.1b-7ubuntu1 is to be installed
                                 Depends: liborc-0.4-0 (>= 1:0.4.16) but 1:0.4.16-1ubuntu2 is to be installed
                                 Depends: libstdc++6 (>= 4.1.1) but 4.6.3-1ubuntu5 is to be installed


Any suggestions?

Much appreciated

Davie

---

### Post by ibjsb4 on 2013-09-28
> gstreamer0.10-plugins-ugly: Depends: libc6 (>= 2.7) but 2.15-0ubuntu10.4 is to be installed

The version 2.15 is a 12.04 package and the requested package (2.7) is a 13.04 package.  Which Ubuntu version are you running?

[http://packages.ubuntu.com/precise/libc6](http://packages.ubuntu.com/precise/libc6)

---

### Post by davie1994 on 2013-10-02
12.04. Would it be easier if I updated to 13.04?

---

### Post by ibjsb4 on 2013-10-02
> **davie1994 said:**
> 12.04. Would it be easier if I updated to 13.04?

A lot of good things are being said about 13.04.  If it was me, I think I move on, but remember 12.04 is supported till 2017 and 13.04 support ends in a few months.  You will have to upgrade every 6 months or so.

Also, I have full backup.  So if things goes bad, I can restore.  Can you?

---

### Post by davie1994 on 2013-10-02
Got a back up for current system on a DVD drive. I assume that's adequate

---

### Post by ibjsb4 on 2013-10-02
> **davie1994 said:**
> Got a back up for current system on a DVD drive. I assume that's adequate

If your happy with it, so am I :D

You have to upgrade to 12.10 first.  Then 13.04.

GUI
[http://www.ubuntu.com/download/desktop/upgrade](http://www.ubuntu.com/download/desktop/upgrade)

In terminal
[https://help.ubuntu.com/lts/serverguide/installing-upgrading.html](https://help.ubuntu.com/lts/serverguide/installing-upgrading.html)

and
[https://help.ubuntu.com/community/QuantalUpgrades](https://help.ubuntu.com/community/QuantalUpgrades)

---

### Post by mc4man on 2013-10-02
> **ibjsb4 said:**
> The version 2.15 is a 12.04 package and the requested package (2.7) is a 13.04 package.  Which Ubuntu version are you running?

[http://packages.ubuntu.com/precise/libc6](http://packages.ubuntu.com/precise/libc6)
That is/was not the issue, more likely the Op hasn't updated his sources, doesn't currently have 'updates' enabled  & or has some proposed packages or ppa installed.

The version of libc6 in 13.04 is 2.17, not 2.7 which is from ages ago ( & the apt line was just >= 2.7 which 2.15-0ubuntu10.4 certainly qualifies, 2.15-0ubuntu10.4 is from precise-updates

---

### Post by SeijiSensei on 2013-10-03
If I were you, I'd install SMPlayer instead:  "sudo apt-get install smplayer".

---

### Post by heir4c on 2013-10-03
Maybe this link is useful:
[http://ubuntuforums.org/showthread.php?t=2177382&highlight=Depends%3A+libc6+%28%26gt%3B%3D+2.7%29+2.15-0ubuntu10.4+installed](http://ubuntuforums.org/showthread.php?t=2177382&highlight=Depends%3A+libc6+%28%26gt%3B%3D+2.7%29+2.15-0ubuntu10.4+installed)

---

### Post by ibjsb4 on 2013-10-03
> **mc4man said:**
> The version of libc6 in 13.04 is 2.17, not 2.7 which is from ages ago ( & the apt line was just >= 2.7 which 2.15-0ubuntu10.4 certainly qualifies, 2.15-0ubuntu10.4 is from precise-updates

Right you are, I misread it. But methinks the op is now running 13.04

---

### Post by craig10x on 2013-10-03
Also a suggestion: Also install VLC Media Player...it's nicer then movie player (although there is nothing wrong with movie player, really)...;)

But i would go with upgrading to 13.04...lots of improvements since 12.04....upgrade to 12.10 first then 13.04...when 13.10 is released you can upgrade to that and so forth...
Always keep a back up (as you mentioned you do) for your important data and documents...That is just in case things ever go wrong and you need to do a clean install...

---

### Post by davie1994 on 2013-10-03
> **SeijiSensei said:**
> If I were you, I'd install SMPlayer instead:  "sudo apt-get install smplayer".

Ok Thanks for all your advice guys. Have tried what seems like the easiest option and installed smplayer. Unfortunately tried to play a few DVDs on it and just came up with blank screen (music seems to work fine though). Does anybody know if there is a reason for this? Something to do with copyright maybe?

---

### Post by SeijiSensei on 2013-10-03
Have you installed the **ubuntu-restricted-extras** package and the extra step required to install libdvdcss2?  [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

In SMPlayer, go to Options > View Logs > Mplayer and see what is reported.  If you see errors about obtaining the DVD's keys, then you need to follow the instructions in that link.

---

### Post by craig10x on 2013-10-03
Yeah...assuming you have ubuntu restricted extras installed (and if not...do install) also grab libdvdcss2 (that you need for playing encrypted dvds)....i think VLC took over maintenance for that now so i believe you can grab that from their website...also would suggest you install VLC media player from ubuntu software center, with libdvdcss2 it should play those movies very nicely...

I just checked VLC's website...it is a bit confusing what you are supposed to do to get the libdvdcss2 file....it use to be maintained by medibuntu website but they are now defunct and VLC took that over but perhaps someone else here can explain how you get it now (i am curious myself)....It looks like they don't supply a deb file to install it like medibuntu use to do...i thought they would...

---

### Post by mc4man on 2013-10-04
> **craig10x said:**
> Yeah...assuming you have ubuntu restricted extras installed (and if not...do install) also grab libdvdcss2 (that you need for playing encrypted dvds)....i think VLC took over maintenance for that now so i believe you can grab that from their website...also would suggest you install VLC media player from ubuntu software center, with libdvdcss2 it should play those movies very nicely...

I just checked VLC's website...it is a bit confusing what you are supposed to do to get the libdvdcss2 file....it use to be maintained by medibuntu website but they are now defunct and VLC took that over but perhaps someone else here can explain how you get it now (i am curious myself)....It looks like they don't supply a deb file to install it like medibuntu use to do...i thought they would...

The actual new packages can all be found here
[http://download.videolan.org/debian/](http://download.videolan.org/debian/)

New libdvdread4 packages with a modified "/usr/share/doc/libdvdread4/install-css.sh" will be available in the near future, currently in saucy & otherwise in the various release's 'proposed' repos
Ex. raring> 

libdvdread (4.2.0+20121016-1ubuntu1.1) raring; urgency=low

  * Replace medibuntu with VideoLan in install-css.sh LP: #1223928

 -- Jonathan Riddell <jriddell@ubuntu.com>  Wed, 11 Sep 2013 16:31:06 +0100

---

### Post by Bucky Ball on 2013-10-04
VLC and ubuntu-restricted-extras. I don't see any reason to upgrade/install.

Movieplayer is ok but not the pick of the bunch (IMHO).

---

### Post by craig10x on 2013-10-04
@mc4man: thanks...they could make it a little easier to find that page on their website...all i was finding was tar files...debs are so much easier...
@buckyball: yeah i agree with you...and yep vlc media player is the best for him to install....

As far as doing all those upgrades...well maybe not for his movie player problem... but i just wanted him to be aware there have been many changes and improvements in case he wants to consider it..

So, What's the deal with libdvdread packages?  you mean that can be used instead of libdvdcss2?  And we will eventually be able to get that from the ubuntu repos directly???

Oops...never mind...i see that that file is only for reading it...and that you still need to actually install libdvdcss2 which is not available from ubuntu....i am glad to see VLC took over the maintaining of the file, although they should make it a bit easier to find then they do right now...

---

### Post by SeijiSensei on 2013-10-04
> **craig10x said:**
> you still need to actually install libdvdcss2 which is not available from ubuntu

Did you read the link I posted above to the discussion about restricted extras, in particular the part about how to install libdvdcss2?

---

### Post by mc4man on 2013-10-04
All means to get libdvdcss2 should be viable.
The libdvdread script should still work in eariler than 13.10 to get from medibuntu server unless one installs the new libdvdread4 from -proposed which will retrieve from videolan (at some point all current Ubuntu releases will get the new libdvdread4 & modified script

Alternately one can get manually from videolan as linked above or if inclined just add the videolan repo & install like any other package

Info here or in screen which shows videolan repo added
[http://www.videolan.org/developers/libdvdcss.html](http://www.videolan.org/developers/libdvdcss.html)

---

### Post by craig10x on 2013-10-04
@SeijiSensei: sorry...i missed it...thanks for calling it to my attention....
ahh...interesting!  So if you have installed ubuntu restricted extras then you already have libdvdread installed and then VLC Media Player can automatically play an encrypted dvd WITHOUT going outside (3rd party) to get libdvdcss2....Good to know! :D

I guess the only time then you would need libdvdcss2 (assuming that you use VLC which i do) is if your were using k3b to "rip" an encrypted dvd to make an unencrypted copy (Use to do that though these days don't often anymore)...

---

### Post by SeijiSensei on 2013-10-05
No, you still have to download libdvdcss2 separately by running the script described in that linked document.  It is not installed automatically along with restricted-extras.

---

### Post by davie1994 on 2013-10-13
Hey guys,
Just a quick message to say many thanks for your suggestions. Things are working fine on the DVD front now after having installed ubuntu restricted extras and libdvdcss2, although being able to do that took a bit of removing some other conflicting software. Many, many thanks for your support and sorry for the delay in replying!

---

### Post by Bucky Ball on 2013-10-13
All good. Please mark as 'Solved' to help others from 'Thread Tools' at top right. ;)

---

