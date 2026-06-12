---
title: "No sound after 11.10 update"
date: 2012-04-22
forum: New to Ubuntu
---

### Post by poscomp on 2012-04-22
Ubuntu 11.10 was working fine. Update manager said there were 300+ updates so I did the update. Everything ran fine but now I have no sound. Mute is off and sound volumes are at their highest levels. I have a mutiple boot system. When I boot to Windows 7, sound works. When I boot to Ubuntu 10.04, sound works. No sound in 11.10. I am at a loss. I know it's not hardware but how do I fix the software? Please help. Right now, to view movies or listen to music, I must boot to another OS.

---

### Post by NikTh on 2012-04-22
First thought . 
Open terminal and give this command ```
sudo /sbin/alsa force-reload
``` 
Second thought . 
Open terminal and write ```
alsamixer
``` check the options. Maybe something its mute there. If automute is enabled then disable it. 
Third thought . 
```
 sudo dpkg-reconfigure alsa-base alsa-utils pulseaudio pulseaudio-utils
```

---

