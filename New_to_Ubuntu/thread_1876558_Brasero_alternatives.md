---
title: "Brasero alternatives?"
date: 2011-11-06
forum: New to Ubuntu
---

### Post by d4m1r on 2011-11-06
Hey guys, so far have been using Nero under my Windows 7 partition to burn but I figuired I'd try out Brasero as it came with my 11.04 install. At first glance, I really like the interface and it provides pretty much all the options/features that I use Nero for BUT...its painfully slower:(

A full 4.7GB DVD (data) takes Nero under 5 minutes to burn but the same task in Brasero takes 20+ minutes....Any suggestions?

---

### Post by Mark Phelps on 2011-11-06
Try K3B -- it's in the Software Center.

---

### Post by Rex Bouwense on 2011-11-06
I didn't much care for Braserio either and changed to Xfburn which is also in the repositories.

---

### Post by d4m1r on 2011-11-06
> **Mark Phelps said:**
> Try K3B -- it's in the Software Center.


Has a high rating to so I gave this a shot and installed it but it won't launch from my unity bar...I pinned it to the launcher and its there, but when I click on it the icon flashes for about 30 seconds, the app doesn't run, and then stops flashing.

Yes I know I can launch it by searching for it (and it works then) but I'd like to get this fixed as well...any ideas?

---

### Post by fleamour on 2011-11-06
May have to enable KDE compatibility in Compiz settings.  Someone will guide you no doubt...

---

### Post by bluexrider on 2011-11-06
Nero has a Linux version that works very well. I used it under Windows 7 then switched to Ubuntu and used the same registration number. 

Or use K3B.

---

### Post by llamabr on 2011-11-06
I still use cdrecord from the cli.  Completely configurable, and if you use it with the -vvv flag, it is very verbose.

---

### Post by beew on 2011-11-06
> **d4m1r said:**
> Has a high rating to so I gave this a shot and installed it but it won't launch from my unity bar...I pinned it to the launcher and its there, but when I click on it the icon flashes for about 30 seconds, the app doesn't run, and then stops flashing.

Yes I know I can launch it by searching for it (and it works then) but I'd like to get this fixed as well...any ideas?

You may have to logout and log back in or restart your computer. I know you shouldn't have to but I notice this behavour for some applications in 11.04. Somehow the launchers don't get totally "registered" unless you restart. Funny thing is I also have a classic menu installed in Unity (through ppa) though seldom used, the classic menu applet picks up the new launchers immediately without having to reboot or logout.

---

### Post by d4m1r on 2011-11-06
Thanks for the tips guys.

@k3b, seems to be working, but again, burn time for a 4.7GB data DVD is about double that of Nero under Windows 7 (10min vs 5min). Why would it take so much longer considered its burning exactly into the same format (ISO9660)?

@Nero, thanks for the heads up I'll be giving it a try but I hope not command line only....

@Unity launcher, yah actually I noticed that too...Ok, I'll see if a restart will fix this.

Can anyone confirm their burner software is able to do 4.7GB in around 5min?:(

---

### Post by marin123 on 2011-11-06
Go to Brasero, Edit-> Plugins, and uncheck File checksum and Image checksum. That will save you at least half of the time.
I was considering switching to something else, but now it's working fine. I also vote for K3B, but I don't use it anymore, so I don't know about the problems with launching...

---

### Post by d4m1r on 2011-11-07
The main issue with Brasero is its glitchy...it spit out an error when burning a basic data dvd using default settings, and I had to throw the disk away because neither my PC or my DVD player (can read data DVDs) would read it...it is a common issue from the looks of the reviews on Brasero.

@K3B, the issue seems to be with write speed. Nero in Windows 7 burns @ 16x which is the max the DVDs I use support, but even when I manually specify K3B to burn @ 16x, it doesn't, and burns @ 5-8x...Anyone had this issue before? 10 minutes is not a huge deal, but I do a **ton** of burning and that is double the time so...

I'll give the Nero linux version ago in the hopes that it will burn @ 16x like it does under Windows 7

---

### Post by d4m1r on 2011-11-07
Well hate to say it but....proprietary wins against open source in this case.

@Brasero, clean interface but buggy. Produced an error the first data DVD I tried to burn so I had to throw out the disc.

@K3B, not as an appealing interface as Brasero, but worked perfectly fine. Burned a full 4.7GB data DVD in 10 minutes and it played fine.

@Nero, we have a **winner**! Version 4 includes Nero Express which looks and functions exactly like the version I love under Windows 7. It is almost as fast as well. Burned a full 4.7GB data DVD in 6 minutes, not sure why it took a whole minute longer under Ubuntu but that is not a big deal.

I can confirm Nero is able to burn at and maintain MAX speed, depending on your DVDs and DVD drive (in my case, it burned consistently at 16x while K3B would burn at 5-8x).

---

