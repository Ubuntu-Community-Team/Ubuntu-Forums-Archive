---
title: "DVD shrink issues"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by Akuma Shiro on 2008-09-18
I had to do a clean install of Ubuntu because of the upgrade bug, and now I am unable to get DVD shrink to work right.

It keeps coming up with  either failed to read the drive or something like copy protected and I might not have permission to read the drive.

Any ideas?

---

### Post by C.S.Cameron on 2008-09-18
What version re you using?
I just tried v3.2.0.15 from Afterdawn and it seems to work fine with wine.
I usually use dvd decrypter first and then 'open files' with shrink.

---

### Post by Akuma Shiro on 2008-09-18
I believe it is 3.2
I tried the most recent release (which I believe is the one you mentioned) and both are giving me the same issue, saying I either do not have permission to access my dvd drive or the drive failed to load because it is not ready. It seems as though the two errors happen one after another.

I am curious about if it is just an error with gusty, because it worked fine in 7.10

---

### Post by C.S.Cameron on 2008-09-18
I'm using hardy now but recall it worked ok in gutsy.
Is your disk de-crypted?, don't think shrink will decrypt them.

---

### Post by Akuma Shiro on 2008-09-19
Before I had to reinstall Linux, I never had to decrypt any dvd before copying it in dvd shrink.

Would it have something with not having the right codec's or lib files you think?

---

### Post by C.S.Cameron on 2008-09-19
I use dvd decrypter 3.5.4.0 then dvd shrink.
Have a found few discs that even decryter won't do.
Have you tried Shrink with a second disk?
Possibly one that has already been decrypted to see if it will open it?
I'll try shrink with non unencrypted disk if I can find one.
DVD Decrypter works well with wine.

Well, I gave shrink a try with a non decrypted disk and it decrypted OK.
Now I'm trying to figure out why I started using decrypter?
I seem to recall having problems with a few disks that shrink would not touch.
Thanks you have saved me some time in the future.

I am running a fresh Xubuntu, the only codecs I have installed are the ones for movie player.

---

### Post by Akuma Shiro on 2008-09-19
Main reason I started using dvd shrink in linux is because it wouldn't work in windows. Now it works in windows and not linux!

I will keep playing with it in Linux. I have a laptop that runs only Ubuntu, and I will play with that and see if it has the same issue.

---

### Post by malty on 2008-10-30
I don't know if you have sorted your problem as the post is 4 weeks old however..
In your county copying encrypted media is highly illegal, if you wish to carry on, and assuming that the discs are for your own use, the following may be helpful.
DVD Decrypter.. install with wine, the only problem is DVD drive identification, select..tools/settings/IO/ASPI.WNASPI32.DLL Some Recent discs cannot be decrypted by this prog, for this you will need DVD FAB Decrypter platinum, not a free prog.

DVD shrink.. install with Wine, works flawlessly.

I use Nero 3 to burn the discs (always Taiyo Yuden TY02 for the best results).

The above gives 100% results, never any coasters.

I live in hope that Nero will Linuxify at least Nero 6 so that I can use this to recode.

---

