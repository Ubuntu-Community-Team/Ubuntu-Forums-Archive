---
title: "your drives are being checked for errors?"
date: 2011-11-19
forum: New to Ubuntu
---

### Post by RAJASD on 2011-11-19
"your drives are being checked for errors, this may take some time.

disks 1 of 1  (some number % finished)"

when i turn my laptop i get this message. not often like once in 20 days lik that. it take some 20 minutes.

1.what is the reason behind it?

2.is there any problem in my laptop?

3.how can i see the results of checked drives?

thanks...

---

### Post by An Sanct on 2011-11-19
This is a normal disk check for EXT formatted drives, it happens on (to my knowledge) all Linux distributions with EXT drives.

You should also notice, that the disk check activates under two conditions, whichever comes first:
1. it has been **X** days, since your last boot.
2. you have booted **X** times.

The bold X mark resembles the setting you are using, normally *30* is sufficient, so this is the default setting.

You can change this behavior with this command
```
sudo tune2fs -c **X** **[LOCATION]**
```Where the bold X represents the same X as above and [LOCATION] is something like "/dev/hda1", according to your system settings.

PS. The check is really fast and it is not recommended to shut it down totally (X=0), if it bothers you a lot, maybe change it to a bigger number (ie: X=50)

2. nothing is wrong with your machine
3. if there are problems it warns you (normally people do not even notice this check)

---

### Post by CharlesA on 2011-11-19
By default the file system is checked after 30 mounts.

You can change that with tune2fs. For something that isn't rebooted that often, you can increase that or decrease that value if you boot up frequently.

I have mine set to check every 30 days.

---

### Post by rng on 2011-11-19
RAJASD says that it takes about 20 minutes. On my 2 desktops it takes a few seconds- sometimes a minute or so. Twenty minutes is really long. I do not know what would be the reason for that. Is there any error message coming on it?

---

### Post by CharlesA on 2011-11-19
> **rng said:**
> RAJASD says that it takes about 20 minutes. On my 2 desktops it takes a few seconds- sometimes a minute or so. Twenty minutes is really long. I do not know what would be the reason for that.

I'm not sure either. On my server it takes maybe 5 minutes to do a 4TB RAID-5 Array and 2 or 3 minutes for a 3TB USB 3 drive.

No clue why it would be taking 20 minutes to run.

@OP: Have you run fsck from a livecd to see if it takes a long time to complete ?

---

### Post by gandaran on 2011-11-19
> it take some 20 minutes.
which ubuntu version do you have?
I remenber there was one version with this problem (don't remenber exactly which one) but this was fixed after installing the updates.

---

### Post by RAJASD on 2011-11-20
thanks for u all....

im using netbook remix 10.04 
i said approximately 20 minutes, i believe less than that(may b 10 to 15 min).

---

