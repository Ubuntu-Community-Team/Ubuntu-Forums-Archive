---
title: "Can anyone get the Einstein game to run on 8.04?"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by sfordin on 2008-08-01
My screen resolution is currently set to 1280x1024, so when I try to run the Einstein game on Kubuntu 8.04, I think the game is getting confused. Specifically, the game attempts to start in full screen mode, but doesn't seem to be able to handle the resolution, so the screen goes blank. The only thing for it then is to hit Esc to exit the program. The .einstein/einsteinrc file contains nothing, there don't appear to be any command line options, and there doesn't appear to be any documentation anywhere.

Any clues on how I can get the Einstein game to run in a window?

Thanks in advance, and my apologies if this is not the correct place to post this question.

Scott

---

### Post by overdrank on 2008-08-01
Moved to ABT

---

### Post by JorritLin on 2008-09-07
> **sfordin said:**
> My screen resolution is currently set to 1280x1024, so when I try to run the Einstein game on Kubuntu 8.04, I think the game is getting confused. Specifically, the game attempts to start in full screen mode, but doesn't seem to be able to handle the resolution, so the screen goes blank. The only thing for it then is to hit Esc to exit the program. The .einstein/einsteinrc file contains nothing, there don't appear to be any command line options, and there doesn't appear to be any documentation anywhere.

Any clues on how I can get the Einstein game to run in a window?

Thanks in advance, and my apologies if this is not the correct place to post this question.

Scott

Edit ~/.einstein/einsteinrc and enter the following line:
fullscreen = 0;

For people that are not comfortable with console editing and only get a warning on the screen, obscuring the window.:
Go to Options, check the top check box and click [OK]
That created the line mentioned above.

First of all: Thanks to the creators of this game for making it and releasing it under the GPL.

Secondly: Some helpful docs or inline help would be nice indeed.
I've posted some feedback on their site, so hopefully they will include some docs or options in the next release if there will ever be one.
As they have released the code to GPL, a patch could be made by a programmer.
Unfortunately the devs. did not comment their code...

--

Kind Regards,

Jorrit Linnert

---

