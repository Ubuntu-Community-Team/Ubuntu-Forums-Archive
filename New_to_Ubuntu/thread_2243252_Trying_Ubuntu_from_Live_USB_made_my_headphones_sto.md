---
title: "Trying Ubuntu from Live USB made my headphones stop working on my laptop Please help!"
date: 2014-09-07
forum: New to Ubuntu
---

### Post by john_smith17 on 2014-09-07
[COLOR=#000000]I wanted to try using Ubuntu from a USB flash drive alone. So I made it bootable, put in a few apps like Docky and listened to some tunes on youtube. I always use my headphones. When I noticed I can't, or that it's too difficult to get Skype on the live/try desktop, I figured I'll restart and boot back into Windows.[/COLOR]

[COLOR=#000000]My headphones just don't work. If I take em out the then I can hear just fine from my laptop's speakers, but as soon as I plug the headphones back in there's no more sound. I tried restarting a few times and no go. I'm using fairly new and well-kept Razer Kraken Pro. I've no idea what kind of driver issue was caused by this Ubuntu experiment but I really dont feel like reformatting my HDD because of this... I don't use cloud services and I have a few hundred GBs with no external HDD to backup to. Things I can mostly redownload but it'll be a huge pain is the point.[/COLOR]

[COLOR=#000000]Please, and thanks in advance. [/COLOR]:sad::sad:

[COLOR=#000000]*by the way just to double check I plugged the headphones into a Galaxy S3 and there's no problem with them--they work just fine..[/COLOR]

---

### Post by drpjkurian on 2014-09-07
Bootable pendrive probably won't mess with drivers and the proof is that your speakers are working....I guess that problem is not related to your drivers

---

### Post by Vladlenin5000 on 2014-09-07
1. There's nothing you can do in a Linux live session that can impact the already installed OS (it doesn't matter which one). Absolutely nothing. Whatever you're experiencing after booting into Windows is unrelated.

2. At your Windows please check the audio settings (and selected output) with the headphones plugged in. You may need to explicitly select the headphones/front panel/whatever as the output. Most of the times the toggle should be automatic - unlike what usually happens in Linux - but not always (and rebooting with or without the headphones may have something to do with it.

3. Whatever the problem is (in Windows) it should be easily solved. Re-installation isn't required and nobody suggested that.

---

### Post by john_smith17 on 2014-09-07
@Vlad
I kept restarting. Shutting down and then starting up the laptop fixed it.
It was indeed related. And after googling farther, I'm not the only one.
But instead of restarting, one should simply shut down the computer and then turn it on and it will be able to work with Windows.
Looks like what happened was Ubuntu loaded up some driver that has a side-effect if you start Windows (maybe 7 in particular) and restarting doesn't actually completely restart when you consider this only goes away after a shut down.
Peace.

---

### Post by Vladlenin5000 on 2014-09-07
No, it isn't related.

There's a difference between a cold start and a warm one (reboot) and I mentioned that scenario. That - and only that - could have triggered the issue. 
A live session works entirely in RAM; it doesn't boot from or uses the Windows partitions. Now, you can mount it/them during your live session and copy to/from it. Possible, not recommended for obvious reasons BUT unless you explicitly  click on the 'drive' (partition) where your Windows is installed, the Linux live session won't even be aware of it let alone use/change/whatever drivers are there. 

Correlation ISN'T causation. You're just insisting in a quite easily debunkable fallacy.

---

