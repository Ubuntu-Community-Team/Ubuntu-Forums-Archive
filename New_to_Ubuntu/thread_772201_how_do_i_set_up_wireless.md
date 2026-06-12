---
title: "how do i set up wireless?"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by smile-its-smiley on 2008-04-28
i have recenty installed hardy on a toshiba a210 19t laptop it has a realtek wireless card and i cant seem to get ubuntu to pick it up. please help

---

### Post by kesman on 2008-04-28
What do you have on system -> administration -> hardware drivers ?
Maybe you just have to enable a restricted driver for it to work.

---

### Post by Michael.Godawski on 2008-04-28
Perhaps you are lucky and there are some restricted drivers for your chipset.

Nevertheless pleas post the output from this terminal command to identify your current network status:
```

sudo lshw -C netowrk
```

---

### Post by smile-its-smiley on 2008-04-28
the hardware driver came up with just ATI FIRE GL which i presume is somthing to do with my graphics. and nothing came up in terminal ive looked on the realtek site and there are linux drivers available but i have no idea how id go about installing them

---

### Post by lrbradford on 2008-04-28
I feel your pain.  I installed Ubuntu Hardy on my Toshiba A215, and it wouldn't even find my router with a wire running to it.  ALthough i did finally get a window pop up telling me I was trying to connect to a secure network, and I don't have the wired network secure.

Anyway, I got ahead of myself, and forgot to print out my hardware specs from Vista, so I wasn't even sure what model of Realtek I even had.  So, I have Vista back on it.

Once I have the hardware report in hand, I'll try Ubuntu 8.04 again, and hit the forums to see what works.  But only when I'm back home setting next to my XP machine so I can surf the Net.  I love these suggestions on the forum that say use apt-get...how can I??  I can't connect, fellas??

The Linux terminal commands are so different from my old DOS commands, that it gets frustrating trying to query the system for info.  I did use the ls-something command to find the model of ATI card my laptop has.  

I want my Linux!!!

---

### Post by smile-its-smiley on 2008-04-28
luckily for me i guess im daul booting it with vista ive used 6.06 before and absulotly fell in love with it, but i stupidly droped my old laptop and the screen fell off so i got this new toshiba which is beuatiful just need the internet on it i read somewear that you can use the windows .inf files to help configer the hardware

---

