---
title: "configuring ipod with linux programs"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by cellardoor0994 on 2008-09-10
First of all, I've been using Linux for a while, however I'm not very knowledge about computers or problem solving them.  Hence the beginner thread.

I just got a new 80 gb ipod classic, but I'm having trouble transferring music onto it.  My brother set up my last ipod with my computer, and it worked fine.  I primarily use Amarok, but I can't find a way for it to acknowledge the device, and when I try using Rhythmbox, although it acknowledges it, every time I try to transfer music it closes.  Help?

---

### Post by Zzl1xndd on 2008-09-10
In Amarok try going to Settings -> Configure Amarok -> Media Devices, then try Auto Detect, if that doesn't work try add apple ipod media device.

---

### Post by cellardoor0994 on 2008-09-10
I did do that, so it lists ipod, but when i press connect it doesn't detect a device

---

### Post by dwhitney67 on 2008-09-10
Most Linux/iPod users will probably indicate that 'gtkpod' is the preferred application, and indeed it does succeed in detecting the iPod you have.

I know this for a fact because I too just bought the 80GB iPod classic, and was able to use gtkpod.

Now the lowdown... gtkpod has a poor user interface.  It also does not contain all of the features available in an application such as iTunes.  For that, the closest you can come is probably Amarok.

Another alternative, and this is what I ultimately chose to do, was to install VMware Server 2.0 (beta), and then from there host WinXP.  With WinXP I can use iTunes, thus not only manage the iPod in a proper manner to add music, but also add photos and videos.

P.S.  I had to Samba-share my music, pictures, etc folders so that WinXP could get access to these.

---

### Post by skippuff54 on 2008-09-10
i tried the other day with amarok too and there was nothin doin. amarok can be fickle about some stuff. try mplayer or xine or some other software.

did u notice if the ipod shows up on ur desktop when u plug it in? on hardy, i plugged mine up, and when i double-clicked it to browse files it showed all my music, and i was able to use mplayer to play it. worked fine in mplayer, did ur distro ship with mplayer? if not u can d/l it with apt.

if u don't notice the ipod/storage device icon on ur desktop, u might be havin issues with plug n play (PnP) devices, storage devices or hardware in general. u would need to install a driver/library or enable a script or somethin, beyond the scope of my knowledge and i'm hittin the hay soon. good luck.

---

### Post by skippuff54 on 2008-09-10
ps u can't (to my knowledge) do anything with AAC files in ubuntu. that is apple's proprietary software for ipods, and ur itunes on win or mac will automatically convert ur music to that format so u can't be sharin with others, etc. there's most likely converter software out there to get around this issue.

so far i've just uploaded mp3's to my ipod in ubuntu, usin mplayer. soon to be testin other formats as i prefer my music lossless.

---

### Post by kpkeerthi on 2008-09-10
Though AAC is a restricted format, Ubuntu has [codecs]("https://help.ubuntu.com/community/RestrictedFormats/AAC") (but not installed by default) to play files of such type.

---

### Post by kpkeerthi on 2008-09-10
> **cellardoor0994 said:**
> First of all, I've been using Linux for a while, however I'm not very knowledge about computers or problem solving them.  Hence the beginner thread.

I just got a new 80 gb ipod classic, but I'm having trouble transferring music onto it.  My brother set up my last ipod with my computer, and it worked fine.  I primarily use Amarok, but I can't find a way for it to acknowledge the device, and when I try using Rhythmbox, although it acknowledges it, every time I try to transfer music it closes.  Help?

If nothing else works, you want to try [Songbird]("https://help.ubuntu.com/community/Songbird"). The iPod sync functionality has a striking resemblance to that of iTunes.

---

