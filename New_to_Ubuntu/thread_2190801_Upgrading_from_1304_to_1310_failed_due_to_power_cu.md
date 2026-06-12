---
title: "Upgrading from 13:04 to 13:10 failed due to power cut."
date: 2013-11-29
forum: New to Ubuntu
---

### Post by maxxmenon on 2013-11-29
Hello friends,

I was upgrading from 13:04 to 13:10 when the lights went off and my computer tripped or switched off after a long beep from the UPS. I was not in place, hence I could not figure out what exactly happened. 

But when I switched the system on (remember it was in the intervening process of writing the downloaded packages on to the system when this happened) it would not mount the file system and it goes to the terminal prompt 

It says 

filesystem check or mount failed 
a maintenence shell will be provided 

(I do not remember what exactly more is there....as I am writing from the Windows system which is also on the same system) 

The command prompt is shown as 

root@maxx:~# 

Nothing else happening - PLEASE help ...I need to retrieve the system back as on the system folders that is downloads and dwhelper and documents I have lots of personal and important information that I do not wish to lose. 

Your help is appreciated.

---

### Post by grahammechanical on 2013-11-29
Try running the live session and accessing that partition to retrieve your documents. Then you may have to re-install. Sorry.

Regards.

---

### Post by maxxmenon on 2013-11-29
> **grahammechanical said:**
> Try running the live session and accessing that partition to retrieve your documents. Then you may have to re-install. Sorry.

Regards.

How do I runn the live session? My computer has a dual boot - the default takes me to Ubuntu and the other to Windows 7 (from where I am writing). I apologise but it seems a bit tough for me to do so. If you would kindly explain in simple terms what must I do. 

How is a live session run? Use an old CD? I mean I may have an older version of Ubuntu with me - and maybe that would work (I am wildly guessing) and using the same CD can I be able to install the latest version?

Thank you in advance. 

Regards.

---

### Post by philinux on 2013-11-29
Initially you can run any live cd that boots to back up data. It doesn't have to be the same as installed. 

From there you could use fsck to check the root partition but I agree with Graham.  Quickest fix after backing up data in this case is reinstall the version of your choice.

---

### Post by jdeca57 on 2013-11-29
If you're using Windows 7 and the default ext4 this thread may help you to back things up: [http://ubuntuforums.org/showthread.php?t=2099399](http://ubuntuforums.org/showthread.php?t=2099399)

---

### Post by maxxmenon on 2013-11-30
> **philinux said:**
> Initially you can run any live cd that boots to back up data. It doesn't have to be the same as installed. 

From there you could use fsck to check the root partition but I agree with Graham.  Quickest fix after backing up data in this case is reinstall the version of your choice.

I think I might want to try that. Hopefully if I can back up the files first and then reinstall it (maybe using the same CD and backtrack versions then come to the right track) - I am praying it would all go fine. :(

Thank you

---

### Post by maxxmenon on 2013-11-30
> **jdeca57 said:**
> If you're using Windows 7 and the default ext4 this thread may help you to back things up: [http://ubuntuforums.org/showthread.php?t=2099399](http://ubuntuforums.org/showthread.php?t=2099399)

Not sure what the default is - its my friend who has installed this on my computer. Maybe he would recollect and help.

I have this diskinternals software but its not helpful - I can see the swap disks visible through the software, but when I click to access it, I cannot.

Thank you for your suggestions.

---

### Post by jdeca57 on 2013-11-30
> **maxxmenon said:**
> Not sure what the default is - its my friend who has installed this on my computer. Maybe he would recollect and help.

I have this diskinternals software but its not helpful - I can see the swap disks visible through the software, but when I click to access it, I cannot.

Strange that you only see swap disks - that's not what you want. I suggested this because it's easy to save your work on a working system, but of course the alternative is also perfectly valid and will work no matter what FS your friend installed. Unless the power loss corrupted your drive. Let's hope that's not the case.

---

