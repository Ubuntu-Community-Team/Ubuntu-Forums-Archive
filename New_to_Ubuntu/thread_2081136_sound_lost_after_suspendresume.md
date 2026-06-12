---
title: "sound lost after suspend/resume"
date: 2012-11-06
forum: New to Ubuntu
---

### Post by omerderi on 2012-11-06
I am using Ubuntu 12.4 precise LTS.
My problem is that sound output is lost after suspend/resume! 
any help?

---

### Post by NikTh on 2012-11-06
Hi , 
after resume try this command in terminal (CTRL+ALT+T) and see if sound come back .

```
sudo alsa force-reload
``` 

Thanks

---

### Post by omerderi on 2012-11-06
> **NikTh said:**
> Hi , 
after resume try this command in terminal (CTRL+ALT+T) and see if sound come back .

```
sudo alsa force-reload
``` 

Thanks

Thanks "NikTh" ..

I tried that but to no avail..
I also tried muting & unmuting the sound but that also didn'r work. I still have to "restart" the system whenever I wanted the sound back.

---

### Post by PinkFloyd102489 on 2012-11-06
After you lose sound, does your audio device still appear in the Sound Settings or is it gone?

---

### Post by marin123 on 2012-11-06
Try restarting pulseaudio, it's more likely to fail.

```
pulseaudio -k
```

---

### Post by omerderi on 2012-11-06
> **PinkFloyd102489 said:**
> After you lose sound, does your audio device still appear in the Sound Settings or is it gone?


Yes, the audio device is still there in the Sound Settings after the sound is lost ..

---

### Post by omerderi on 2012-11-06
> **marin123 said:**
> Try restarting pulseaudio, it's more likely to fail.

```
pulseaudio -k
```


Thanks "marin123" ..
As you expected, that also didn't work ..

---

### Post by omerderi on 2012-11-12
> **omerderi said:**
> I am using Ubuntu 12.4 precise LTS.
My problem is that sound output is lost after suspend/resume! 
any help?

The same problem also happens after Logout/Login ..

---

