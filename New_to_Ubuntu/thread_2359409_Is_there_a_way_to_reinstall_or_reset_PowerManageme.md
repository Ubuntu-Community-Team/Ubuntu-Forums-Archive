---
title: "Is there a way to reinstall or reset PowerManagement?"
date: 2017-04-23
forum: New to Ubuntu
---

### Post by shawdotion on 2017-04-23
For a certain reason I decided to try and edit a part of PowerManagement that dealt with my audio "**/usr/lib/pm-utils/power.d/intel-audio-powersave**". I opened up the file in nano and messed something up somehow and I believe I erased the content of the file. The code I used was:
```
sudo nano /usr/lib/pm-utils/power.d/intel-audio-powersave

```

My audio is working for the most part but the sound quality is worse than before. The only thing I can surely tell is that the sub-woofer isn't being used and I'm not sure how to enable it again. 

I believe what caused it to stop working is me tampering and messing up the intel-audio-powersave file.  

Currently I have no idea how to fix this problem but I'm guessing I'd need to find a way to restore that file to it's default self and I'm unsure how to do that. 

Thanks.

---

### Post by Autodave on 2017-04-24
You can go into *synaptic* and find "power manager" and then re-install it from there. If that doesn't work, try uninstalling it completely and then reinstalling.

---

### Post by TheFu on 2017-04-24
I'd use a backup.  You know, those things everyone tell you to make, automatically, daily?  They are really handy for things like this.  Plus, backing up /etc/ is really easy. It is relatively tiny.  You could just tgz everything in /etc/ and easily keep 120 days without using much storage.  /etc/ is one of those directories that is absolutely critical to a running system.  

For most desktop users, if they backup /etc/, a list of all the installed packages and their HOME, that would be a great backup that could be restored in 45 min.

BTW, Autodave's suggestion to purge/reinstall should also work.

---

