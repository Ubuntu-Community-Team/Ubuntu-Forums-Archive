---
title: "Installed mplayer but it is not listed in sound and video"
date: 2013-08-25
forum: New to Ubuntu
---

### Post by ShermW0829 on 2013-08-25
Is there a configuration file for sound and video installed on my system? I am using Ubuntu 64 bit. I installed mplayer by using apt-get install. I can not launch the video in mplayer since mplayer is not listed.

Thank you;

Sherman

---

### Post by deadflowr on 2013-08-25
mplayer is command line application.
As such it will NOT be listed with the GUI applications.

to run open a terminal and type mplayer filename(/home/user/Videos/video.extension)

an overview can be seen with mplayer -h, or man mplayer.

---

### Post by ShermW0829 on 2013-08-25
Thank you, deadflowr. I didn't realize that mplayer is not a gui application.

Sherman

---

### Post by deadflowr on 2013-08-25
Yeah, I've done that with a few programs before too.
I think if installed through the Ubuntu Software Center, it has a reference to Terminal somewhere.


The program smplayer is a frontend for mplayer, if that helps.

---

### Post by SeijiSensei on 2013-08-25
"sudo apt-get install smplayer" will solve your problem.

---

