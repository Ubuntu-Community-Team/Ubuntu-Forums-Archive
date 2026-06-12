---
title: "HOWTO: Ogle (Best DVD Player)"
date: 2005-01-01
forum: Outdated Tutorials &amp; Tips
---

### Post by RU63 on 2005-01-01
After spending weeks trying to get all my DVDs and rented DVDs to work in Linux, using MPLayer(No DVD menu SUCKS!!!) and Xine(sound lag made me cry), I came across Ogle (Has MEnu and No sound lag).  Ogle is the easiest to install, but I never found a howto on Ubunto site, so her eis what i did: 

1. Do the Extra-Repository thing - (look at starter guide)
2. TYPE:  sudo apt-get install ogle
3. TYPE:  sudo apt-get install ogle-gui
4. Install libdvdcss2 - (look at starter guide)
5. Restart gnome

I have watched 3 DVDs today... I am very happy.   BTW... My setup is now: Ogle for DVDs and MPlayer for mpegs and the like.  Make sure u have also installed the right codecs (look at starter guide).

Peace,

---

### Post by drmagoo on 2005-01-03
Sweet! Quick to install, easy to use. I had been fussing with some other venues to watch movies, but this ended the fussing. Highly recommended.

---

### Post by wulf on 2005-01-03
I've found Xine (specifically Gxine) has worked very smoothly, with no sound lag. I haven't had to adjust it but I think there was a slider under preferences that was something to do with sound lag - maybe that could solve your problems.

The only issues I've had with Gxine are:

1) It segfaults when I try to run it in full screen mode. However, since I like to watch movies in widescreen format that's not a particular issue as the picture still fills the full width of the screen.

2) I haven't figured out how to get back to the root menu of the DVD easily (I can't find anything in the GUI to do that... maybe there's a key combination I'm missing).

Overall though, it works pretty well. 

Wulf

---

### Post by nocturn on 2005-01-03
[QUOTE=RU63]
I have watched 3 DVDs today... I am very happy.   BTW... My setup is now: Ogle for DVDs and MPlayer for mpegs and the like.  Make sure u have also installed the right codecs (look at starter guide).
[/QUOTE]

I'm glad it works for you.
I checked the Ogle page on freshmeat, and it says that Ogle was last updated in 2003, is this project dead?

---

### Post by oddabe19 on 2005-01-03
[QUOTE=nocturn]I'm glad it works for you.
I checked the Ogle page on freshmeat, and it says that Ogle was last updated in 2003, is this project dead?[/QUOTE]
 i was browsing their cvs repository, and it looks like there are a few things that have been updated within 2 years.... but alot of it says 4 years or more :-(

---

### Post by jsgotangco on 2005-01-14
Strange, OGLE was only playing sound on my install but no video...

On Xine, it showed video but no sound...

On VLC, everything worked flawlessly...almost all my DVDs had good playback...

---

### Post by chascon on 2005-01-14
Yes, I agree ogle is the best DVD player, choppy but good sound on my iMac G3 xine. Xine is just choppy as ogle, but xine pops and crackles as if it were a cereal comercial.  Perhaps this is alsa that I presume it comes along with.

Of And I forgot ubuntu's ogle's stop button does work.  Everything else does, but not stop.  

I also believe ubuntu could be more conservative with processing power as debian's ogle plays almost perfect (with a little choppyness) on my iMac G3 while ubuntu's is so choppy it is unviewable (on the same G3).

Yes I know tht a G3 is not optimal for viewing DVDs.  I think this sort of comment is a cop out.  And this sort of comment is not the point.  The point is that I have seen that DVDs can be viewable on a G3, thus there is much room for improvement here.  Besides OS X plays DVDs just fine.  Thus it is doable.  I just don't kow if this improvement is ogle related specifically or OS related.  

Now that I think about it.  If Ogle has been dead for the last few years, then it is reasonable to assume that Ogle in debian's sarge is probibly the same version (or close at least) of Ogle in warty, thus it should play just as well on the same computer.  Given that I testify that Ogle does not play equally well on sarge as it does on warty and that I've tested it on the same hardware, then it is the OS at fault.  Ubuntu plays DVDs less efficiently than it's predecessor.  Perhaps this should be looked at.  

I am running a debian xserver (daenzer's sid dri-trunk) cause ubuntu's xserver crashes my computer so this may skew my observations.

---

### Post by rwabel on 2005-01-16
[QUOTE=RU63]After spending weeks trying to get all my DVDs and rented DVDs to work in Linux, using MPLayer(No DVD menu SUCKS!!!) and Xine(sound lag made me cry), I came across Ogle (Has MEnu and No sound lag).  Ogle is the easiest to install, but I never found a howto on Ubunto site, so her eis what i did: 

1. Do the Extra-Repository thing - (look at starter guide)
2. TYPE:  sudo apt-get install ogle
3. TYPE:  sudo apt-get install ogle-gui
4. Install libdvdcss2 - (look at starter guide)
5. Restart gnome

I have watched 3 DVDs today... I am very happy.   BTW... My setup is now: Ogle for DVDs and MPlayer for mpegs and the like.  Make sure u have also installed the right codecs (look at starter guide).

Peace,[/QUOTE]

Thanks for the how-to but I get this error message upon starting ogle:
rwabel@RALPH:~ $ ogle
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdread: Can't open file VIDEO_TS.IFO.
ERROR[ogle_nav]: faild to read VIDEO_TS.IFO
DVDSetDVDRoot:: Root not set

---

### Post by chascon on 2005-01-17
The procedure RU68 recommended, the one you followed doesn't work for ppc.  So you might have problems because of this.

If you read that error ogle gives you in term you notice that it'll want you to read a README.  And if you go there to read it'll tell you to run the script below.
/usr/share/doc/libdvdread3/examples/install-css.sh

Incedently, the above script works for both pc and ppc.

I think you have to run it sudo

Moral of the story?  Read your term messages.

The script makes ogle and xine-ui both play DVDs.  Totem with gstreamer? (the default backend for totem at install) doesn't work with this.  

Be warned, the ogle stop button doesn't work, at least not for me (only ogle problem).
xine-ui's sound snap crackles and pops for me, although the picture is just as good as ogle's.

update: It just occured to me that you might have managed to install css using the apt-get method.  Just remove it and install with script.  It's the only way that worked for me.

---

### Post by rwabel on 2005-01-17
[QUOTE=chascon]The procedure RU68 recommended, the one you followed doesn't work for ppc.  So you might have problems because of this.

If you read that error ogle gives you in term you notice that it'll want you to read a README.  And if you go there to read it'll tell you to run the script below.
/usr/share/doc/libdvdread3/examples/install-css.sh

Incedently, the above script works for both pc and ppc.

I think you have to run it sudo

Moral of the story?  Read your term messages.

The script makes ogle and xine-ui both play DVDs.  Totem with gstreamer? (the default backend for totem at install) doesn't work with this.  

Be warned, the ogle stop button doesn't work, at least not for me (only ogle problem).
xine-ui's sound snap crackles and pops for me, although the picture is just as good as ogle's.

update: It just occured to me that you might have managed to install css using the apt-get method.  Just remove it and install with script.  It's the only way that worked for me.[/QUOTE]

Well I'm on PC and not PPC.
I've now tried to downgard to the version from the script. But this didn't change anything.
Still same problem:
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Can't open file VIDEO_TS.IFO.
ERROR[ogle_nav]: faild to read VIDEO_TS.IFO
DVDSetDVDRoot:: Root not set


p.s. I did read the term message, but I didn't understand it :-)

---

### Post by trinaryouroboros on 2005-11-08
[QUOTE=rwabel]Well I'm on PC and not PPC.
I've now tried to downgard to the version from the script. But this didn't change anything.
Still same problem:
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Can't open file VIDEO_TS.IFO.
ERROR[ogle_nav]: faild to read VIDEO_TS.IFO
DVDSetDVDRoot:: Root not set


p.s. I did read the term message, but I didn't understand it :-)[/QUOTE]

to go around the Root problem normally I do
> ogle /media/cdrom1

there are other roots you can use, but also, something I've been noticing is that I get this list of ERROR[ogle_nav]: faild to read VIDEO_TS.IFO when trying to watch certain DVD burns...

I noticed on the last post here: [http://www.linuxquestions.org/questions/archive/2/2005/03/4/293637](http://www.linuxquestions.org/questions/archive/2/2005/03/4/293637)

He may be on to something. The problem burn I've had so far is a burn done in Windows. Now the odd thing is that the Set-top DVD standard Players work fine with this burn...yet Ubuntu spews that error message above, minus the root problem. Strange - but this is a project indeed, I intend to get to the bottom of it. Perhaps there is an alternative way to do this with symlinks.

---

### Post by sskennel on 2005-11-09
To get Breezy to start playing a DVD with Ogle as soon as I inserted it in the optical drive, I went to the System menu, then Preferences, Removable Drives and Media. In the Multimedia tab, I changed the command for Video DVD Discs to:

```
ogle -u gui %d
```

-- Roger

---

### Post by mshumer on 2008-07-15
I know this is an old link but I wanted to add info. 
Sony PCG-R505DL laptop, Ubuntu 8.04. Worked perfectly first time. Now I can see all the chapters without guessing what is on the dvd.

---

### Post by Nullack on 2008-07-15
Totally false. Ogle is deprecated. Mplayer does have dvd nav - libdvdread, libdvdnav togther with libdvdcss2. This is the most up to date method for Linux dvd playback.

Sorry, but the problem is you dont know what your doing not mplayer.

---

