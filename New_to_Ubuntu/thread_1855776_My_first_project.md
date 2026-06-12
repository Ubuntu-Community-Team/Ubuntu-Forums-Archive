---
title: "My first project"
date: 2011-10-06
forum: New to Ubuntu
---

### Post by Nyght on 2011-10-06
A great friend got my on Linux because he knew once I got past the begginner crap that I would do well consider my background in computer technology.

I really am not so good at learn by reading so I am dividing up my lessons into small tasks that w/o fail will get me oriented the fastest.

Project One: How to find and intall Linux audio drivers-

Realtek audio ac'97 high definition (my ***) ---I went to realtek site and they have drivers for Linux 2 and 4 (idk what that means) and that is all the Linux drivers they have for my chipset, I dled 4 but I have no sweet clue on how to install it. Z/Z


Edit: I read a few threads...it seems nobody knows how to do anything exactly. Apparently there is a install button I hit using a version of linux I am not using to enable any unenabled drivers. the name of this button and its location are top-secret information it seems. I can partition a hard drive six ways from sunday using fdisk but if u tell me to hit the "whoosit" button chances are I am not going to know wth u r talking about. Z/Z

---

### Post by wolfen69 on 2011-10-06
There should be no need to install drivers for realtek ac97. Did you check your sound settings?

---

### Post by dFlyer on 2011-10-06
> **Nyght said:**
> A great friend got my on Linux because he knew once I got past the begginner crap that I would do well consider my background in computer technology.

I really am not so good at learn by reading so I am dividing up my lessons into small tasks that w/o fail will get me oriented the fastest.

Project One: How to find and intall Linux audio drivers-

Realtek audio ac'97 high definition (my ***) ---I went to realtek site and they have drivers for Linux 2 and 4 (idk what that means) and that is all the Linux drivers they have for my chipset, I dled 4 but I have no sweet clue on how to install it. Z/Z


Edit: I read a few threads...it seems nobody knows how to do anything exactly. Apparently there is a install button I hit using a version of linux I am not using to enable any unenabled drivers. the name of this button and its location are top-secret information it seems. I can partition a hard drive six ways from sunday using fdisk but if u tell me to hit the "whoosit" button chances are I am not going to know wth u r talking about. Z/Z

Try turning up the volume, you shouldn't have to install drivers for your sound card. Click on the speaker icon and increase the volume should do it for you.

---

### Post by Nyght on 2011-10-06
> **dFlyer said:**
> Try turning up the volume, you shouldn't have to install drivers for your sound card. Click on the speaker icon and increase the volume should do it for you.

On the top bar there is a speaker icon...I have no idea how it is supposed to work but I know mouse clicks do nothing to it. And even my friend who got me into the enigma that is Linux sez he has no idea where the master volume control is. My friend sed just to try adjusting the volume from the keyboard. It is really funny actually becuz he can identify nearby wireless networks with linux but has no idea how to adjust the volume :)  Z/Z

---

### Post by wolfen69 on 2011-10-06
What happens if you right-click the speaker icon?

---

### Post by LowSky on 2011-10-06
open terminal

type: ```
 alsamixer
```

make sure nothing is muted or off.

---

### Post by Nyght on 2011-10-06
I just flipped over to linux (which I think runs much smoother than 7...I am an adult I don't require a sugared up OS).

Master volume brings up the typical slider if u right-click but...adjusting it of trying to set prefs results in an error msg along the lines of waiting for sound to respond. Z/Z

Edit: I could reboot...I am fairly certain there were a few device failure msgs there. Z/Z

Edit: The boot record doesn't show any problems with devices but neither does it indicate it recognizes my audio chipset. The audio is not a serious issue but if I can't resolve the audio issue I don't think I going to have much luck when I comes to using a new command line (the 3rd or 4th I have learned since I began programming when I was 13).Z/Z

---

### Post by wolfen69 on 2011-10-07
Have you done all system updates?

---

### Post by Nyght on 2011-10-07
probably not...partly due to the fact I have no idea how to do that on linux and partly due to the fact that my friend may have neglected to do that while he was making a beeline to install google chome (and i can see why...every other browser eats resources like crazy) Z/Z


@wolfen69: "and we like to monkey around...we're too busy singing to put anybody down." Z/Z

I looked around and found something called "Main Menu"...in the is supposedly a way to enable something called "System Tools" but it doesn't show up on the menu. Z/Z

Edit: I never found that update manager thing but I did find an article about audio for my variant OS and it was fixed properly...audio is working fine...just had to add something under startup apps.

First Project: Successful...Imma post tomorrow with my second project...if you need the command I entered in startup apps just ask and I'll good look it up again and add it here. Z/Z

---

