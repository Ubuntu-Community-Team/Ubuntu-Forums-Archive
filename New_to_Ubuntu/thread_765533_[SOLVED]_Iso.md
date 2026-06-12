---
title: "[SOLVED] Iso?"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by Ahunt on 2008-04-24
I have been on Ubuntu for a year, but I am certainly feeling like a total beginner today.

I went from Ubuntu 7.4 to 7.10 via the upgrade process. That was very easy - one click and it was done. 

To move to 8.4 I thought I would do a fresh install. So I downloaded the .iso and then burned it onto a CD-R. My Ubuntu PC is set to boot to CD first on start-up. So I booted to it and nothing happened - it just checked the CD and then installed 7.10 as per normal from the hard disc. I tried booting to the CD on my alternate (Windows XP) PC and the same thing happened - no installer came up. Clicking on the .iso file achieves nothing also.

I know that I am probably doing something very basic wrong here. What?

---

### Post by kk0sse54 on 2008-04-24
1.did you check the CD for defects?
2. did you try the alternate installer?

---

### Post by swoll1980 on 2008-04-24
right click it(the iso file) then click burn to disk you have to burn it as a iso image not info. The right click thing does this automatically

---

### Post by Mazza558 on 2008-04-24
Did you use an ISO burner (e.g "burn to disk" on Ubuntu) or did you just copy the file to CD?

---

### Post by Ahunt on 2008-04-24
Actually I downloaded it on Windows XP and burned it to CD there (Ubuntu PC was in use, of course) as a straight .iso file.

I have the .iso file, so I can re-burn it if need be.

---

### Post by Mazza558 on 2008-04-24
> **Ahunt said:**
> Actually I downloaded it on Windows XP and burned it to CD there (Ubuntu PC was in use, of course) as a straight .iso file.

I have the .iso file, so I can re-burn it if need be.

There's your problem.

Download ISO Recorder for Windows (it's just a small freeware program).

[http://isorecorder.alexfeinman.com/download/ISORecorderV2RC1.msi]("http://isorecorder.alexfeinman.com/download/ISORecorderV2RC1.msi")


Click on your ISO file and choose it to be burnt at as low a speed as possible.

---

### Post by Ahunt on 2008-04-24
Thanks for that info.

I downloaded the ISO burner and re-recorded the .iso file onto a new CD using that. It seemed to work fine.

I tried booting it in the Ubuntu PC and and the boot-up ignored it.

I tried booting it in the Windows XP PC and it booted to the Ubuntu screen. I tried testing the CD for errors and came up with an error reading the disc. I assume that I have a bad .iso download and that I need to start again?

---

### Post by Mazza558 on 2008-04-24
> **Ahunt said:**
> Thanks for that info.

I downloaded the ISO burner and re-recorded the .iso file onto a new CD using that. It seemed to work fine.

I tried booting it in the Ubuntu PC and and the boot-up ignored it.

I tried booting it in the Windows XP PC and it booted to the Ubuntu screen. I tried testing the CD for errors and came up with an error reading the disc. I assume that I have a bad .iso download and that I need to start again?

Yes, either that or a bad CD or Burner. I'd try downloading it again first.

---

### Post by Ahunt on 2008-04-24
Well the CD did read and the burner does other jobs just fine, so it is likely a faulty .iso file.

I will try downloading the .iso again. It took seven hours on DSL (which is normally 3.008 MBps here) so I think perhaps the servers are just way too choked up to give a good image right now. Maybe I will try again in a week or two when the demand drops.

Thank so much for your help!

---

### Post by Mystix on 2008-04-24
What I would do if you already have it downloaded is burn it as an .iso to a cd at a 4x burn rate, will take a little longer but this is what I had to do to get a cd that would work.

---

### Post by mister_pink on 2008-04-24
You can check your iso file for defects, rather than just downloading it again. Look here: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

And for the hardy md5s: [http://releases.ubuntu.com/8.04/MD5SUMS](http://releases.ubuntu.com/8.04/MD5SUMS)

---

### Post by Ahunt on 2008-04-25
Thanks for the advice on that. I did try another CD burn at a very slow burn rate (1X). It still came up with the same error on boot-up, so I think I have a corrupt download.

After wrecking three CDs I have learned my lesson - wait at least a week after a new release. The server congestion makes getting a clean download unlikely, even on a pretty fast DSL connection.

mister_pink:

Thanks for that info. This is all new to me.

I did download the "Install-winMd5Sum.exe" to check the file on Windows and the hash is totally different from the one at [http://releases.ubuntu.com/8.04/MD5SUMS](http://releases.ubuntu.com/8.04/MD5SUMS). 

I can only conclude that file I have is corrupt.

---

### Post by hyper_ch on 2008-04-25
yes it is...

and I suggest to you to

(1) download the ISOs throught bittorrent --> that will auto-hash-check the files so they won't be corrupted

(2) get a couple of CD-RWs...

---

### Post by Ahunt on 2008-04-25
Thanks for the info. I have lots of CD-RWs. I was lead to believe that they should be burned on CD-Rs. 

I was also trying to create a disc that, once I had installed 8.4 on my Ubuntu 7.10 PC I could give away to friends. I prefer to hang onto the RWs!

We have a problem with Bell Nexxia seriously throttling all Bit Torrent here in Ontario and so they download very, very slowly with a high risk of errors.

I am constantly amazed - I have been working on computers since 1978 and I always seem to be one piece of critical information short of being able to get the job done.

I think the [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) page needs to link to all of this info on checking the image and how to burn an iso to a CD properly and what type of CD to use in a step-by-step fashion. Any real Windows newbie trying to get Ubuntu will be totally lost and will have given up long before this stage.

---

### Post by hyper_ch on 2008-04-25
change your ISP if they trottle P2P traffic ;)

well, for giving CDs away I rather order a couple through shipit.... you know, they look professional and you can give those to other people and they will take it a lot more serious.

---

### Post by Ahunt on 2008-04-25
The problem is that Bell Nexxia owns all the lines to the houses in Ontario. All the ISPs lease the lines from them. Cable is the only other option, but it is throttled, too by Rogers, who own the cable. All BitTorrent traffic is therefore throttled here. It has been all over the news here recently. There is no other choice, except dial-up.

---

### Post by hyper_ch on 2008-04-25
that sux :(

---

### Post by Ahunt on 2008-04-25
Basically you learn to live with monopolies as far as possible.

The latest move is that Bell Nexxia has applied to the courts to force the regulator to allow Bell Nexxia to throw all the other ISPs off their wires. DSL and cable will then be unaffordable to individuals here. Our little, local not-for-profit ISP will be forced back to dial-up only. Hopefully the courts won't allow it.

---

### Post by Zralou on 2008-04-25
Just a quick query, I thought the CDRW are 650mb capacity?.  In which case, Ubuntu won't fit on one, it needs 690mb, or is that just the Kubuntu?.

Sara Lou

---

### Post by hyper_ch on 2008-04-25
there are 700mb CDRWs.... old standard used to be 640mb per CD-R(w)

---

### Post by aeiah on 2008-04-25
i was gonna suggest bittorrent too, but it sucks that you're stuck with a monopoly isp that throttles. here in the uk, nearly all ISPs have throtting or 'fair use' policies that punish you for downloading a lot, but i dont think the throttling is as bad as in america and canada. still, if the servers are really slow and they dont throttle your torrents too much you could always check it out. or try and find an ubuntu mirror that's located somewhere where the population will be asleep

---

### Post by Ahunt on 2008-04-25
Good point.

The ".iso" file I downloaded for Ubuntu was 631 MB, so it should fit on a CD-RW.

Incidentally for anyone reading this thread with the same problem - there is Ubuntu documentation on how to do all this. It should be linked from the download page, but it isn't.

It is at:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by linux phreak on 2008-04-25
The ubuntu 8.04 iso is 699 MB in size.

---

### Post by Ahunt on 2008-04-25
That might explain how corrupted my file was!

---

### Post by Mazza558 on 2008-04-25
> **Ahunt said:**
> That might explain how corrupted my file was!

It's amazing it even loaded in the first place...

---

### Post by Ahunt on 2008-04-27
I thought I would write a quick conclusion to this tale. On Friday night I tried an ".iso" download from a quieter mirror and got the complete file in 45 minutes. WinMD5Sum tested it and declared that the hash marks matched. I used the Alex Feinman ISO recorder to burn it on a CD-R at 1X and tested the CD. It failed. I figured it must be a bad CD, so I burned another one at 4X and that one passed! (sounds like "burned down, fell over and sank into the swamp")

The installation of Hardy Heron went fine, at least as soon as I had figured out "PolicyKit" to the point where I could give myself permission to open the CD drive. PolicyKit is a bit overboard for home users, although maybe okay for office or places like public libraries.

We are now up and running with Hardy Heron. Overall it is very impressive - better than Gutsy and even better than Windows XP. Vista is a sad joke next to Hardy Heron!

My thanks again to everyone who contributed here. As always the community support here on the forum is amazing and makes any Ubuntu glitches easy to solve! Thank you!

---

### Post by mister_pink on 2008-04-27
Other Kings said I was daft to build a castle in a swamp, but I built it all the same, just to show 'em...

Sorry. Glad to hear you got it working though!

---

