---
title: "Cannot mount video dvd"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by beew on 2011-10-22
Hi, 

I have a strange problem that I would need some help.

I have two video dvds that I cannot mount in Ubuntu in one machine (machine A), when inserted I can hear the dvd drive grinding away but the dvds would not mount. I have no problem mounting and watching video dvds on this machine in Ubuntu except for these two. I have tried Ubuntu 10.10 and 11.04 and both fail to mount these two dvds on machine A. 

However, machine A has a small windows partition, one of the dvds mounts and plays in Wndows.

Now my Ubuntu 11.04 installation is portable, I installed it in an external drive and it can be booted from different machines. I boot it off a much older crappy laptop (machine B) and suddenly I can play both dvds!  Since it is portable this was the same Ubuntu11.04 installation that I tested on both machines, all settings and configurations are exactly the same.

Sorry if this is a bit confusing, basically

1) the dvds are ok since I can play them in machine B 

2) Ubuntu is ok since in machine B both play in Ubuntu (11.04)

3)DVD drive in machine A is ok since I have played dvds on it many times in Ubuntu. I have never had any problem except for these two.

4) yet at least one of them actually plays in machine A as well but in Windows.

I am wondering why I can't  even mount these 2 in machine A in Ubuntu, what  could have been the problem and how I can fix it.

Thanks.

---

### Post by beew on 2011-10-23
Additional information. I am sure I was able to play one of the DVDs in Ubuntu for machine A for a few times before.

Is it possible that the culprit is the regional code thingy? How do I find out?

Thanks.

---

### Post by kemtnbkr on 2011-10-23
Do you have libdvdcss2 installed?  supposedly that is region-independent; that might help you resolve your issue potentially.

That has worked for me in the past, although I think all the DVDs I own are all from the same region.  Other than that suggestion, though, it's over my head.:(

---

### Post by beew on 2011-10-23
> **kemtnbkr said:**
> Do you have libdvdcss2 installed?  supposedly that is region-independent; that might help you resolve your issue potentially.

That has worked for me in the past, although I think all the DVDs I own are all from the same region.  Other than that suggestion, though, it's over my head.:(

It is installed. Like I said I can play most dvds except for these two (so far).

But then come to think of it if it is a regional code issue would the dvds at least mount? ATM they don't even mount, the dvd drive just humming on forever.

---

### Post by kemtnbkr on 2011-10-23
Yeah that's odd.  Before I had any DVD libraries installed, I think I could still mount the DVD and see the .VOB video files and the other stuff on it; they were just mixed up and split into a bunch of files, but I could still watch the movie if I wanted, it would just take undue effort.  I never have time to watch movies so I haven't really ever messed around too much with DVDs and such, sorry I can't be of more help.

---

### Post by beew on 2011-10-24
Bump!

---

### Post by beew on 2011-10-25
Something strange has happened. I borrowed a dvd from my roommate to test the ripping software. When inserted the dvd drive was humming along for almost 5 minutes without mounting, just when I was about to give up it mounted and played! After the first successful mount subsequent  mounting becomes much faster when reinserting the dvd. The two dvds that refused to mount before now suddenly works, upon inserting the dvds mount and play almost instantly!

I have no idea what happens. It is almost like my roommate's dvd has unlocked something.. My problem is solved but I would still want to hear a possible explanation. 

Any theory? Thanks.

---

### Post by beew on 2011-10-26
Bump! I really want to hear an explanation even though the problem is solved,--that's why I haven't mark it as "solved" yet.

---

### Post by beew on 2011-11-06
Yeah, that is weird. I had a dvd that I was able to play. But suddenly it stopped mounting anymore. Since I have been watching some foreign films lately on DVD (without problems) and this one is American I figured it might have something to do with regional code. I installed regionset from the repo and ran it just to see if the dvd-drive has been somehow set to the wrong region(I hadn't done anything with it but what the heck), it said the dvd drive has not been set to any region. I exited without changing anything, then inserted the DVD and it plays again.

What is going on???

---

### Post by beew on 2011-11-06
I found something even stranger. Turns out there is this Chinese dvd which is the culprit. After playing it several other dvds would not mount when inserted into the dvd drive, it just keep humming on. Then there is a Japanese dvd which can reverse it. If I insert the Japanese dvd into the drive and  just run regionset and then exit without changing anything, all the other dvds play again!!!!

I am really interested in a theory for that!

---

### Post by hansdown on 2011-11-06
I have a similar problem, beew.

In my case, the dvd drive is seriously bad quality.

The disks just thrash about, and don't play.

Plugging an msi wind portable dvd writer works for me.

Be careful how many times you change the region code.

You're allowed to change it 5 times, then it locks, to the last setting.

---

### Post by beew on 2011-11-06
> **hansdown said:**
> I have a similar problem, beew.

In my case, the dvd drive is seriously bad quality.

The disks just thrash about, and don't play.

Plugging an msi wind portable dvd writer works for me.

Be careful how many times you change the region code.

You're allowed to change it 5 times, then it locks, to the last setting.

Hi, I actually didn't change the region code, I just ran regionset and it showed the current code (which is not set) and then it asked me if I want to set it, I typed no and exited and that was  it. This is the strange part!

My dvd drive is in reasonably good shape and most dvd play smoothly, but there are odd ones that exhibit strange behavours like I described. Problems are rare but there is a pattern to them. I am trying to understand the pattern. :)

---

### Post by hansdown on 2011-11-06
You've got me thinking, beew.

```
sudo lshw
```

in a terminal, will tell you the make and model.

Mine, is a Hitachi-LG.  HL-DT-ST  GH4on.

---

### Post by beew on 2011-11-06
TSSTcorp CDDVDW TS-L633C

---

### Post by hansdown on 2011-11-06
There was a bug report, for 10.04, where the disc would not mount, but if the disk was in at startup, it would work correctly.

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/554433](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/554433)

---

### Post by beew on 2011-11-06
> **hansdown said:**
> There was a bug report, for 10.04, where the disc would not mount, but if the disk was in at startup, it would work correctly.

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/554433](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/554433)

This does not describe my situation. If I insert an audio CD it mounts and plays 100% of the time (provided it is a format that the player can recognize of course, vlc pretty much plays anything). 

If it is a video DVD then it usually mounts and plays, except for a few odd ones. The behaviour is that they once play and then one day they just stop mounting at all after playing some other dvd (or dvds, there can be a few like this). It is as if playing this dvd some how locks down the drive against those few that afterwards cannot mount,  But somehow they all play again after running regionset with yet another dvd in the drive, even though I have not actually reset the regional code. So the mere fact of inserting this second dvd in the drive and running regionset when it is in it unlocks the drive for those which were locked out before by playing the first dvd.

It is not a Ubuntu bug btw, because I used to have a Windows partition. When Ubuntu couldn't mount these dvds, neither could WIndows and when they play in one they play in the other (there are some that windows could mount but couldn't play because of codecs, but that was a different issue and I didn't really care as long as they played in Ubuntu) I didn't set the  regional code in Win either, but there was a thing that did the same thing in WIndows as regionset, again all I did was opening it to check the regional code and then closed it without changing anything, it didn't occur to me before that this was relevant because haven't set anything and I spent very little time on Windows anyway, but now it is clear after I have tried a few times with regionset.

---

### Post by hansdown on 2011-11-06
O.K.

It's the kind of thing, that bugs me, so I'll keep looking.

It's so similar to my situation, that makes me want to search more.

Strange, about the different dvd discs doing that.

---

### Post by beew on 2011-11-07
After a few more trials it seems that the regionset thing may be just incidental. There seems to be certain dvds that can't be played  one after another. Playing  one would result in the other not mounting (but not vice versa, some can always play, but playing them may result in others not mounting), and when that happen,  playing some other dvd would unlock the drive for those which have been locked out.

---

### Post by kromine on 2011-11-08
So now the question is...How do you actually mount the CD/DVD drive?

---

### Post by beew on 2011-11-08
> **kromine said:**
> So now the question is...How do you actually mount the CD/DVD drive?

What do you mean? Just insert a disk and it mounts automatically (in most cases they do)

---

### Post by beew on 2011-11-09
Hi, to the mods, I am wondering if it is possible to move this thread to the multimedia forum. On second thought, it was probably more appropriate to have posted it there in the first place.

Thanks.

---

### Post by beew on 2011-11-09
Tested with more dvds. Turns out regionset has nothing to do with that.

To summarize: There are some dvds that don't mount at all.. But.. somehow if I insert another dvd first (not all, but among a few), wait til it starts playing back and then remove it and reinsert one of those (the not mounting ones), it plays immediately. So the second dvd somehow unlocks the drive for the first one?

On the flip side, there are some dvds that, if I play them first, some other ones would stop mounting. So it would seem that somehow the first dvd has locked the drive for the second one. The second one would play again if I insert, start playing and then remove one of the "unlocking" disks.

Very strange!!!

---

### Post by beew on 2011-11-10
bump!

---

### Post by beew on 2011-11-12
This is getting really interesting!

I found one DVD with this peculiar property. Whenever I stick it into the DVD drive it never mounts if it is the first DVD to be inserted during the session. However it starts playing immediately if some other random dvd has been inserted and mounted earlier in the session.

So it gets locked out 100% of the time if  no other dvd has been mounted in the drive during the session, and mounting any dvd would unlock it !

Please, I really want to know why!

---

### Post by westie457 on 2011-11-12
It certainly is very strange behaviour to be getting from VLC. I have vague memories of reading in the VLC web site that the region-cracking software unlocks the DVD drive without writing to the firmware. Re-writing the region code on the drive will lock the drive to one region only. As has already been posted this is not the issue you have and is only an observation from me.

Could this be the problem and possible solution, [http://forum.videolan.org/viewtopic.php?f=13&t=70719](http://forum.videolan.org/viewtopic.php?f=13&t=70719) caused by one DVD and somehow repaired with a different one.

---

### Post by beew on 2011-11-12
Hi,

I am not sure if the link has to do with the issue, at least not apparent. For the dvd to be unlocked I don't have to play another one in any media player, just mounting it will do. And when a dvd is "locked" it doesn't mount at all. Moreover I use Mplayer2 for dvd playback mostly, not VLC. Mplayer2 is statically linked to its own ffmpeg so it shouldn't have anything to do with the ffmpeg bug described in the link, I have also never installed from the debian ppa in question.

---

### Post by westie457 on 2011-11-12
Hi TBH it was only a theory and they are the first things to be proved wrong usually. Until your last post I had no idea you are using Mplayer2, there was a mention of VLC which led me to check their site.

The only thing I can think of is the TOC of that dvd has a minor but critical error in it and possibly the only way to check is using a hex-editor to look at it. To me there is no obvious way to repair this.

---

### Post by SirWeazel on 2011-11-12
beew, sounds like your problem might be similar/related to the plextor drive bug. I wasted a lot of time trying to fix or find what was causing the issue, luckily i had an extra drive i could swap out and fixe my issues.

Dvd drives are pretty cheap, it might just save you from more headache and at least possibly narrow down the possible problems if you just swap out the drive. Swapping out the drive would narrow down 2 possiblities (#1 faulty drive and/or #2 drive incompatiblity)

See these other threads, maybe they can provide some insight?
[http://ubuntuforums.org/showthread.php?t=1816499](http://ubuntuforums.org/showthread.php?t=1816499)
[http://ubuntuforums.org/showthread.php?p=11110732#post11110732](http://ubuntuforums.org/showthread.php?p=11110732#post11110732)

---

### Post by beew on 2011-11-12
Hi Thanks.

Mc4man's solution to his problem by inserting an audio CD first in interesting. 

But I am not sure it is the same problem that I am having,--though there is some similarity.  First I don't think I have a plextor drive (TSSTcorp CDDVDW TS-L633C) Also I have no problem mounting and playing commercial dvd most of the time, it is just that playing (or simply mounting) "some" of them in certain order would either prevents some from mounting, or enables them to play if they have been previously prevented from mounting. 

It is very strange, but it is not a major problem (as I can always play a dvd, if having to go through the annoynance of mounting another dvd first) I am more curious than desparate. Also swapping the dvd drive would not be a good option since this is a laptop.

---

### Post by beew on 2011-11-15
Bump!

---

