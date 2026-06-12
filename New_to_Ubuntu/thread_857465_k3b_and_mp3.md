---
title: "k3b and mp3"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by Joe Soap on 2008-07-12
I'm running hardy on 2 pc's and a laptop.  On the laptop and one pc I can burn audio cd's from mp3 with k3b without any problems.  On the remaining pc I get the following erro when trying to burn an audio cd from mp3 with k3b:

Unable to handle the following files due to an unsupported format:
You may manually convert these audio files to wave using another application supporting the audio format and then add the wave files to the K3b project.

As far as I can see, they all have the same installation, same software, etc.  Where can I start looking to find the problem?

Thanks
Joe

---

### Post by Bachstelze on 2008-07-12
Seriously, man...

[http://www.google.com/search?hl=en&q=Ubuntu+k3b+mp3](http://www.google.com/search?hl=en&q=Ubuntu+k3b+mp3)

```
sudo apt-get install libk3b2-extracodecs
```

---

### Post by Joe Soap on 2008-07-12
Yeah, thanks, done that.

"libk3b2-extracodecs is already the newest version."

Didn't help.

Is there any way I can compare the installation on one pc to the installation on the other?

---

### Post by Bachstelze on 2008-07-12
Yes, you can for example compare the outputs of *dpkg -l* with *diff*.

---

### Post by Joe Soap on 2008-07-12
Thanks, I'd like to try that.  How is it done?

---

### Post by johnnylavah on 2008-10-16
> **HymnToLife said:**
> Seriously, man...

[http://www.google.com/search?hl=en&q=Ubuntu+k3b+mp3](http://www.google.com/search?hl=en&q=Ubuntu+k3b+mp3)

```
sudo apt-get installlibk3b2-extracodecs
```

thanks...works great!

---

