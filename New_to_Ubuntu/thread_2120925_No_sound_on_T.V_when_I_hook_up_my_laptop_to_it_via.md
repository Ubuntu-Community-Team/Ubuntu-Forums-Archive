---
title: "No sound on T.V when I hook up my laptop to it via HDMI"
date: 2013-02-27
forum: New to Ubuntu
---

### Post by Jimjim438 on 2013-02-27
The sound only comes from my laptop how do I make it so that it comes from my T.V?

---

### Post by ptn107 on 2013-02-27
After you hook up to the hdmi cable, you need to go to System Settings -> Sound -> Output (tab) and on the left where it says 'play sound through' make sure the hdmi option is selected and the output volume set to 100% (it should set the volume for you).

---

### Post by I8NY on 2013-02-28
Make sure your GPU/laptop supports that function to begin with.  Newer AMD video cards (6xxx and greater) have audio chips built in the card and should automatically.  Nvidia, I think, has the drivers pass your audio signals from the audio chip through the Nvidia video card.  I don't know if that driver function is supported in the Linux.  This is all on based on a small amount of research so don't take it as a straight fact.

---

### Post by Jimjim438 on 2013-02-28
> **I8NY said:**
> Make sure your GPU/laptop supports that function to begin with.  Newer AMD video cards (6xxx and greater) have audio chips built in the card and should automatically.  Nvidia, I think, has the drivers pass your audio signals from the audio chip through the Nvidia video card.  I don't know if that driver function is supported in the Linux.  This is all on based on a small amount of research so don't take it as a straight fact.
It works when I use Windows 7

---

### Post by Jimjim438 on 2013-02-28
> **ptn107 said:**
> After you hook up to the hdmi cable, you need to go to System Settings -> Sound -> Output (tab) and on the left where it says 'play sound through' make sure the hdmi option is selected and the output volume set to 100% (it should set the volume for you).
I don't have the sound setting.

---

### Post by Mark_in_Hollywood on 2013-03-01
You may have to add your user name to the **sound** group. If that isn't helpful, all I have is this:

[http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240)

which is very thorough.

---

