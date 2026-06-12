---
title: "The same azureus configuration for ubuntu and MS system"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by vprasaj on 2008-10-21
Hi,

(Google won't help. So here is the question.)

I am running azureus in linux. Is it possible to run azureus in windows with the same configuration and torrents?

Like this: I download something in ubuntu. Then I close azureus, reboot to windows and then I start azuresu. That downloads from ubuntu now continues in windows.

I use the same profile for thunderbird in ubuntu and windows. Is something like that possible for azureus? If not, maby some other client?

---

### Post by gandaran on 2008-10-21
if linux and windows can see the same disk, yes, you add the same torrent and same download folder to both azureus then one can pickup where the other just left.

---

### Post by vprasaj on 2008-10-21
Thank you for a quick replay.

Are you sure about that? Won't azureus start checking every time? Does torrent files contain information, where it stopped download or is the azureus configuration?

It sounds logical. But I just want to be sure. I don't want to mess something up. If there is nothing to mess up, then ill try. :)

---

### Post by PocketDog on 2008-10-21
Azureus in the other OS will check the data, sure. But if the download location is the same for both OSs then that won't matter either: It'll just verify the existing data and carry on where the other version left off.

---

### Post by vprasaj on 2008-10-21
Can this be done without checking? Sometimes there is a tons of data and checking would last for a long time.

---

### Post by PocketDog on 2008-10-21
No, if you want to switch OSs during downloads then re-checks are essential I'm afraid. A 'quick-resume' would over-write  data in an existing download if, say, Ubuntu's been downloading and you've booted into Windows. A force-recheck on a paused download would be required in that case

---

### Post by vprasaj on 2008-10-21
I was hoping this would be possible withouth checking, just to specify paths for torrent information.

(Like: for windows--> config is in default folder, set all folders the same as on alternative system to absolute location, torrent information is in x:\home\some_user\.azureus\....)

But this would be great. Not the matter of system and people could use the same download or upload torrents. Data is stored and paths are the same. I think this could not be such a big thing to implement, because it is just the matter of paths. 

Well it is (was) my wish.

Thank you PocketDog for clarify this.

---

