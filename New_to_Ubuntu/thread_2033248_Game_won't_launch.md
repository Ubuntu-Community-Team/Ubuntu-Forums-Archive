---
title: "Game won't launch"
date: 2012-07-25
forum: New to Ubuntu
---

### Post by Sequoia Bird on 2012-07-25
I just installed Ubuntu 12.04 on my brother's computer. I downloaded Sauerbraten from the Ubuntu Software Centre. The icon appears on the launcher, but I click on it and nothing happens. I installed Sauerbraten on my other (ubuntu) computer and it worked with no problems. This is what happens when I try to start it in terminal:

```
mason@mason-HP-Pavilion-dv6-Notebook-PC:/usr/games$ ./sauerbraten
Using home directory: /home/mason/.sauerbraten
init: sdl
init: net
init: game
init: video: mode
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  13
  Current serial number in output stream:  13

```How can I make it work?

Thanks for your help.

---

### Post by Futant on 2012-07-25
Try un- and re-installing it? Has worked for me a couple of times...

---

### Post by Sequoia Bird on 2012-07-26
I've tried downloading Sauerbraten numerous times, from sourceforge AND the ubuntu software center. I have also re-installed Ubuntu four times (due to various bugs), before settling on the 32-bit version. 

Thanks again.

The brightness still doesn't adjust and the icons in the launcher cannot be resized, but that's another forum post. -_____________________________________________-

---

### Post by anewguy on 2012-07-26
What are your hardware specs, particulary your video adapter?

---

### Post by Sequoia Bird on 2012-07-26
Graphics card is Radeon HD 6490M. The computer is an HP pavillion dv6.

One of the proprietary drivers failed to install. This seems like a video card driver problem, so we tried to install the driver from the AMD site. We have a .run file, but we don't know what to do with it.

---

### Post by Sequoia Bird on 2012-07-26
Got it! I went into terminal, navigated to the directory with the .run file, then typed in
```
sudo sh ./filename.run
```

The icons are resizable and the games launch. The brightness isn't adjustable, but that's a problem for another day.

---

