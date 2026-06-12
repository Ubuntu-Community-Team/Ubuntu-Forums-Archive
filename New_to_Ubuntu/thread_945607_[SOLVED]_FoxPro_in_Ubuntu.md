---
title: "[SOLVED] FoxPro in Ubuntu"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by aprilmot on 2008-10-12
Hello all,
I would like to use the DOS FoxPro in Ubuntu.  I tried with wine but I am not sure how to configure it.  Or could you please recommend me any other ubuntu software which is capable of opening FoxPro database file.

Thank you in Advance.

---

### Post by patrickballeux on 2008-10-12
If it is a DOS application, then use the Dosbox package since Wine is for Windows only.

> sudo apt-get install dosbox

Then, inside that emulator, you can run any DOS application like in the old times...

> dosbox .
So your C:\ drive will be in the folder where you are currently in your terminal.

Here is a good example how to play a game in Dosbox: [URL="http://blog.mypapit.net/2007/05/dosbox-how-to-play-dos-games-in-ubuntu-linux.html"]http://blog.mypapit.net/2007/05/dosbox-how-to-play-dos-games-in-ubuntu-linux.html
[/URL]

I haven't found any software that could open a foxpro database for now, so Google will be your friend for now...

Good luck!

---

### Post by aprilmot on 2008-10-12
> **patrickballeux said:**
> If it is a DOS application, then use the Dosbox package since Wine is for Windows only.

> sudo apt-get install dosbox

Then, inside that emulator, you can run any DOS application like in the old times...

> dosbox .
So your C:\ drive will be in the folder where you are currently in your terminal.

Here is a good example how to play a game in Dosbox: [URL="http://blog.mypapit.net/2007/05/dosbox-how-to-play-dos-games-in-ubuntu-linux.html"]http://blog.mypapit.net/2007/05/dosbox-how-to-play-dos-games-in-ubuntu-linux.html
[/URL]

I haven't found any software that could open a foxpro database for now, so Google will be your friend for now...

Good luck!

Very Much Thank you for your solution.
It works fine. 

Thank you one again=D>

---

