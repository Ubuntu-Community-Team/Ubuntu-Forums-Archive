---
title: "Music freezes - Cursor movement fixes it oO?"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by Bubba3 on 2012-05-01
Yesterday, I installed Ubuntu 12. Apart from installing programs (why is there no small program unzipping .tar.gz for me?), I dont regret my decision.


One small, yet unnerving thing:
Sometimes, **when I listen to music, it just kind of freezes**. Like when an LP gets stuck. And when I move my cursor, it unfreezes again. So, no big problem, but really annoying when you're on your bed listening to music and have to get up to get the music going again :)
Freezing music happens most often on grooveshark.com and 8tracks.com.


(Oh, and one other small thing: When I'm watching cartoons, after 10mins, Ubuntu slowly starts to darken the screen until the monitor is eventually fully dark. Why does Ubuntu not recognize I'm watching something like Windows does? (I know I can change energy settings to 1h or so, but I want Ubuntu to recognize Im watching movies.))

---

### Post by ubudog on 2012-05-01
Welcome to the forum!

You might want to have a look at the 'Power' settings, and the 'Brightness & Lock' settings.

As for the music, could it be a thing with the site?

---

### Post by Bubba3 on 2012-05-01
Thanks for the welcome :)
The music freezing is definitely not a thing with the websites, because before yesterday (when i used w7), everything went perfectly smooth, so I dont suppose its got anything to do with the source of the music.

And for the darkening screen: I already found out about those settings, i was just wondering whether i could tune ubuntu in order to recognize when im watching movies, so it doesnt shut the monitor down then. Because normally, I want the monitor to go black in about 10 mins of inactivity, while when watching a movie, there should be 3 hours of undisturbed watching. And obviously, I dont want to change the settings before and after every movie I watch :)

By the way, thanks for the quick reaction. Ive read a lot of stuff on linux forums, and I have to say, I like the community very much.Seems so much more open and friendly than its Windows-equivalent.

---

### Post by lastMan on 2012-06-08
Hi folks, 

I have the very same problem with 12.04. Music/audio freezes the desktop, mouse movement fixes it. This is independent of the source. It happens with Rhythmbox or youtube or anything else. 

Any ideas how to fix it?

---

### Post by lastMan on 2012-06-19
Finally I realized that on my site it is **not sound related at all**.
Stop any other applications, esp. any sound, start the system monitor and switch to the resources tab. On my system the resource consumption graph stops within the first 60 seconds because of a system/desktop freeze. That means the sound is not the cause of the issue but only a symptom. Still a mouse movement or keyboard input fixes it for some time. 

I found out that it is related to AMD C1E power saving options. As a workaround I disabled the C1E option in the motherboard bios (Asus-M5A97-PRO).

See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1012806](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1012806)

---

