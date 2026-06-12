---
title: "Loading gaming pc then power failure, Cannot boot ubuntu now!"
date: 2013-07-16
forum: New to Ubuntu
---

### Post by sparky952 on 2013-07-16
Hello, and thank you for reading this!

I am a fairly nooby at ubuntu, so i have kinda no idea what to do :P
Anyway, a few mins ago i turned on my gaming pc to play some minecraft then for some reason the houses RCD tripped (ok, ok i know, un nessory details :P )
Annoyingly it was while ubuntu was booting not while gaming so i have some major corruption it seems. I kinda hope i dont have to reinstall ubuntu....
I get masses and masses of random code and then the /dev diectory errors becuse it dont 'exsist' and throws me into a shell or terminal or whatever.... I know that the /dev exsists due to taking the hard drive out and putting it in a enclosure and checking with my rather crappy old laptop. I searched around the forums a bit and tryed to fsck. It at least stopped the boot loop and gave me some lines of code i have NO IDEA about. Also before you ask me to try and go to recovery in grub, i can't, Thats corrupt too (At least grub is fine :P )

Oh, also here is some things i have tryed.....
```
sudo e2fsck -C0 -p -f -v /dev/sdb1
sudo e2fsck -f /dev/sdb1
sudo fsck.ext4 -f /dev/sdb1
```

Now for some random info that MIGHT help!
Its a 64bit operating system (Ubuntu)
I did unmount when trying fsck
It's a EXT4 file system
I dont wanna lose my gaming data >_<

Hope you can help me! If you need anything just ask. 

[LIST]
[*]:grin: 
[/LIST]

-Sparky

---

### Post by sparky952 on 2013-07-17
Umm... Bump?
Anyone here going to help! I need my gaming pc!

-Sparky

---

### Post by sparky952 on 2013-07-20
Meh... got no help so had to fix on my own... now lost all my files.
I now see how helpfull ubuntu forums realy are...
*Facepalm*

-Sparky

---

### Post by ulyssesAU on 2013-07-20
Sorry you lost the data - I am quite new so would provide zero help on your first problem..

I bought an APC smart UPS and recently also had a power failure - the UPS is set to safely shutdown my server. Worked like a charm and no harm done, I also get emails when power goes and returns. Worth looking into.

---

