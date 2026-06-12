---
title: "music syncing to ipod, but not showing up"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by readyartbrut on 2008-04-25
Hi, I was hoping someone could help, maybe I am just being dumb but I cant get any music syncing software to work properly with my ipod, it puts the music on the ipod but the ipod says no music, it is driving me crazy. I have tried a few applications but for an example lets say yamipod.

---

### Post by nina_aoki on 2008-04-25
So let's work backwards here:  

Is the iPod mounting properly?

Does your iPod start and work with its own software?  

Is this a new iPod?

Did you recently erase this iPod and reinstall the software?  If so, how?

What format are the music tracks encoded in?  iPods do not support Ogg Vorbis files - so you would need to use MP3 or some other Apple happy audio codec.

You could try gtkpod.  Start by trying to copy one file to the iPod and see if that works.  In my experience trying to get an iPod to sync with a library using something other than iTunes doesn't generally work -- but maybe someone else has a better answer here.

- nina

---

### Post by MONODA on 2008-04-25
what ipod do you have?

---

### Post by readyartbrut on 2008-04-25
I have an 80gb ipod classic, I am running gutsy, my ipod mounts no problem, the vast majority of my music library is in mp3 format. The ipod has played music when it was previously synced using itunes/xp, since then it has been reset.

---

### Post by Saya on 2008-04-25
> **readyartbrut said:**
> it puts the music on the ipod but the ipod says no music
Was there any music before you synced from Ubuntu? If so, ouch. I wouldn't sync iPods with Ubuntu because it's not reliable enough.

---

### Post by readyartbrut on 2008-04-25
hmmm thats bad news for me then as I have a brand new ipod and I dont dual boot, so in effect my ipod is useless on ubuntu. I think I would rather give up the ipod than give up ubuntu.

---

### Post by Saya on 2008-04-25
> **readyartbrut said:**
> hmmm thats bad news for me then as I have a brand new ipod and I dont dual boot, so in effect my ipod is useless on ubuntu. I think I would rather give up the ipod than give up ubuntu.
Before I bought my Mac I synced in iTunes in Windows in VMware in Ubuntu. Way overcomplicating it, but way more safe too.
If you don't want to go that far, I suggest Exaile, it's worked for me.

---

### Post by adult swim on 2008-04-25
are you using amarok?

---

### Post by readyartbrut on 2008-04-25
I think people may be getting confused, I have tried a number of software applications and they all present the same problem, I am certain that it isn’t down to the software, but in all probability down to the user. I appreciate the suggestions for software and when I know that the issue no longer exists I will try alternatives to my current application, Yamipod and if I could guarantee that it’s the software I would really try anything. 
I was hoping that someone could see a rudimentary error on my part, (syncing to ipod, music on ipod but ipod doesn’t recognise that music exists on it) and suggest possibly what I am doing incorrectly, I hasten to add, the syncing is done by a push button in the applications (as I said in my original post I have tried many) and not me willy nilly dropping the files anywhere.
Could this be related to the db file? Could it be that itunes used to rename the music files RQ84F etc and that all software I have used retains the original name?  
I thank you all for the replies so far.

---

### Post by Saya on 2008-04-25
The one thing I can think of is that the database is messed up and you should do a reset (in iTunes).

---

### Post by readyartbrut on 2008-04-26
Thanks for all the suggestions. I followed the instructions here

[http://www.pqdvd.com/blog/ipod/ipod-classic/how-to-sync-amarok-with-ipod-classic-3rd-generation-ipod-nano/](http://www.pqdvd.com/blog/ipod/ipod-classic/how-to-sync-amarok-with-ipod-classic-3rd-generation-ipod-nano/)

It all works fine now.

---

### Post by Trampis on 2008-04-27
I have this exact problem, only my ipod is a brand new 4gig nano, serial A1236. I used Gtkpod and put the music on my ipod. All my music players recognize there to be music on said ipod, and the ipod even read "2.9 gigs free" so the files are on there, just not showing up under "music" If i look at the space allocated on the ipod it tells me i have put the music in my ipod under "other" It seems the Ipod cannot access the files. Does anyone know how to force the ipod to recognize the music as such?

---

### Post by readyartbrut on 2008-04-27
Although the link to the instructions is specific to Amarok, I think the first few steps relate to this generic problem.

---

### Post by steampunk on 2008-04-27
THANK YOU THANK YOU THANK YOU x infinity!

I just bought my first iPod today and ran into this same problem and was unable to find anything online that helped until I ran across this thread. w00t!

---

### Post by steampunk on 2008-04-28
hrm, looks like I spoke too soon. the files still aren't showing up on my iPod Nano 8GB :/

---

### Post by Trampis on 2008-04-28
I followed the Amarok how to. The files are being transfered to my ipod, my ipod still does not recognize the files as music. 
I have noticed some problems with model number, my Ipod is clearly a sixth generation silver ipod nano, that is just what it is, the model number on the back reads "A1236", However, there is no model number like that in Amarok's menu. Could this be affecting this problem?

---

### Post by Trampis on 2008-04-28
I hear that hardy offers 6th gen Ipod support with gtkpod. Perhaps this is a solution? Does anyone who has this problem run hardy?

---

### Post by Raistlinbuntu on 2008-04-28
> **readyartbrut said:**
> 
Could this be related to the db file? Could it be that itunes used to rename the music files RQ84F etc and that all software I have used retains the original name?  

Have you tried [GNUPOD]("http://www.gnu.org/software/gnupod/")?
It also resolves all the problems with the ipod-shuffle sync.

---

### Post by Steah on 2008-08-04
A bit delayed, but for those reaching this post with the same problem:

Check the version number of whichever software you choose to use and ensure it is sufficiently recent.  Using gnupod as an example, one might not necessarily think that much had happened between version 0.99 and 0.99.6 ... but a nano 3g (A1236) will not work with the former while working beautifully with the latter.

---

### Post by simpsonsfan74 on 2008-09-25
I had this same problem. I was about to follow the instructions in this thread when I noticed that libgpod2 does not exist in the Hardy packages, but libgpod3 was already installed.  What I did was:
"sudo ln -s libgpod.so.3.0.0 /usr/lib/libgpod.so.2" (no quotes)

I then restored the iPod to it's original settings from iTunes under Windows, and rebuilt the database with Banshee.  This seems to have fixed the problem for me.

---

