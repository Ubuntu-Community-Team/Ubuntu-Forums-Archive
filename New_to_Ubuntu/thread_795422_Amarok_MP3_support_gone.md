---
title: "Amarok MP3 support gone"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by Igniteflow on 2008-05-15
MP3 support in my Amarok seems to have disappeared.  Any idea what could be the cause?  I have the right GStreamer plugins and it was working previously.  Not really sure what might have cause it as I haven't used it for about a week and have installed and updated quite a few programs since. Any suggestion would be appreciated.

---

### Post by oliviacond on 2008-05-16
amarok prefer xine.
```

sudo apt-get install amarok-xine libxine1 libxine1-ffmpeg

```

---

### Post by logos34 on 2008-05-16
or maybe you need

libk3b2-extracodecs

---

### Post by Igniteflow on 2008-05-17
Thanks for the suggestions everyone, I followed both of them, but unfortunately they didn't solve the problem.  I already had the correct xine drivers/files installed from the mediubuntu repositories, I tried reinstalling both the advised files and Amarok itself as advised in another similar thread (sorry, I found that after posting this one!), but to no avail.
I've now uninstalled Amarok and am using Exaile now. I'd like to return to Amarok again though if anyone can tell me where I've gone wrong.

---

### Post by NightwishFan on 2008-05-17
Perhaps delete the .amarok configuration folder. It should be hidden in your home folder somewhere. It should create a new one on its next run, which may fix any problems it had.

---

### Post by Xiong Chiamiov on 2008-05-17
It's ~/.kde/share/apps/amarok, and I'd recommend renaming it, rather than deleting it, so you don't lose all your configuration and stuff.

---

### Post by NightwishFan on 2008-05-17
Thanks sir. I was just about to install amarok to try give a better tutorial since my post was vague. :KS

---

### Post by logos34 on 2008-05-17
I'm not sure this helps, but there was a recent update to Amarok which might have caused some mischief.  For me it actually fixed a glitch with fetching album covers from amazon.  Maybe you could try rolling back to the previous version

---

