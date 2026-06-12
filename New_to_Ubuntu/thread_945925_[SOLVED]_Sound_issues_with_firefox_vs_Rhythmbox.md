---
title: "[SOLVED] Sound issues with firefox vs Rhythmbox"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by baddnady23 on 2008-10-12
Anyone know why if i have RB open sound won't play through firefox or visa versa?  I have to close both apps and then open the one i want to have sound work on in order to get it to work.  Ugh...

---

### Post by linux4life88 on 2008-10-12
This is very strange indeed. What version of Ubuntu are you using (8.10, 8.04, 7.10, ect).

---

### Post by baddnady23 on 2008-10-12
8.10 all updated.  Same thing happens for vlc too

---

### Post by Muffinabus on 2008-10-12
> **linux4life88 said:**
> This is very strange indeed. What version of Ubuntu are you using (8.10, 8.04, 7.10, ect).
I don't see it as strange at all.  In fact, I think it's very normal.  I've seen countless posts of people with the same problem (including myself) and have seen posts to fixes that don't seem to work.  I even had someone tell me that it's just Pulse Audio and nothing can be done about it.

---

### Post by linux4life88 on 2008-10-12
Since you are using a Beta version of Ubuntu, it could be a bug that hasn't been solved yet. I hope a developer sees this thread so they will now about this issue.

---

### Post by baddnady23 on 2008-10-12
haha stupid me.  8.04 i was just eager to say 8.10

---

### Post by linux4life88 on 2008-10-12
> **baddnady23 said:**
> haha stupid me.  8.04 i was just eager to say 8.10

I'm sorry then, I would not know what the problem is. I've never had that problem before. Sorry I could not help.

---

### Post by Zachx65 on 2008-10-12
[Have you seen this thread? It includes this snippet. Might be the place to go.]("http://ubuntuforums.org/showthread.php?t=205449")
> 
**_Getting more than one application to use the soundcard at the same time_**

    * You might want to play a game and listen to music on your favorite music player at the same time. To do this successfully, you will have to use ALSA since it supports this feature the best. On all the music players I know of, you can configure the sound engine, to any module that is available.

    *
      The setting is usually found under something like Tools >>> Configure >>> Player Engines.

    *
      For games, it is a bit more tricky since there is not always a way to configure the player engine directly. Most games, however, do support the OSS. ALSA has an OSS module that allows OSS applications to use the ALSA driver.

    *
      To do this you will need the alsa-oss package
      Code:

      ```
sudo apt-get install alsa-oss
```

    *
      After doing this step, it is very easy to use alsa-oss. In the shell, you can type 'aoss' then the name of the program name you want to use with alsa-oss.

---

### Post by baddnady23 on 2008-10-12
zach's response seemed to fix it with competing with vlc but the issue still remains with firefox :(

---

### Post by paris_alex on 2008-10-12
I faced similar problems, what i did was to go to "System > Preference > Sound" switch to ALSA. Solved it for me!

---

### Post by baddnady23 on 2008-10-12
> **paris_alex said:**
> I faced similar problems, what i did was to go to "System > Preference > Sound" switch to ALSA. Solved it for me!
Genius!  Thanks alot! Everything seems to be working fine now!

---

