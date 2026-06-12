---
title: "Sound for multiple programs"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by I[AM]SMRT on 2008-05-09
After finally getting my sound in flash to work, I've found that I can't get my sound going in more than one program (i.e. I can't get sound in Firefox and rhythmbox at the same time). I've tried the following fixes to no avail:

[http://ubuntuforums.org/showthread.php?t=44753](http://ubuntuforums.org/showthread.php?t=44753)
[http://ubuntuforums.org/showthread.php?t=101125](http://ubuntuforums.org/showthread.php?t=101125) (I tried esd and alsa)

I've got:

Hardy Heron (XP dual boot)
Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller

Suggestions?

---

### Post by I[AM]SMRT on 2008-05-15
I just found something out, my problem appears to be mainly with flash and my music players at the same time. I can use rhythmbox and movie player at the same time.

I think this may have something to do with my problem. The only way I could get sound for flash working was putting this in my startup sessions:

ln -s /tmp/.esd-1000 /tmp/.esd

Can someone help me out here?

---

### Post by markbuntu on 2008-05-15
I had that problem but I do not remember exactly how I fixed it but I think I used the gnome alsa mixer and selected mix and everything else so that all the sounds from everywhere will go to the same place. I can hear a flash playing in firefox and  rythmbox internet radio at the same time.

Like I said, I don't really remember how I did it but it was something simple in one of the sound mixers.

---

### Post by Awareness on 2008-05-15
I still havent tried it out but check out [this]("http://ubuntuforums.org/showthread.php?t=790579#9") ;)

---

