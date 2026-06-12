---
title: "[SOLVED] re-enabling wireless?"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by TheWhatkin on 2008-06-05
Hokay. I had a bit of trouble with my AR5007EG wireless card when I first upgraded to hardy, but after a clean reinstall, I got the madwifi drivers installing properly, and all was good.
 
Recompiled the drivers after each kernel upgrade, no issues.

Then I clicked the 'disable wireless' box in the drop down menu to see what it did...and apparently completely killed it. <_< I'm no longer seeing /any/ wireless options on the menu, and recompiling madwifi does nothing. 

Help?

---

### Post by NikoC on 2008-06-05
Hmmz, I'm not really a network expert and it has been several months since I had problems with my wifi so I'm going on a limb here. In a terminal type:

ifconfig eth1

I'm guessing eth1 is the 'name' of your wifi card (wired is usually eth0). Does this give you an output with a hardware address for the wifi card? If so make sure that your hardware switch on your laptop (if it is a laptop and it has one) is 'on', if not I have no further clue.

In a terminal type:

ifup eth1

This used to bring wifi back in the ol' days on my machine...

Cheers...

---

### Post by jualin on 2008-06-05
what is the output of > ifconfig on the terminal?

---

### Post by st33med on 2008-06-05
It could have crashed as well...

Try this: Press Alt-F2 and type in **nm-applet**

---

### Post by TheWhatkin on 2008-06-05
...Okay, I feel stupid. After finishing running errands and plugging in the ethernet cable(my laptop dual boots Vista, and I was running that to post), the wireless option reappeared. O_o Hit the checkbox, and we're good.

Thanks for the advice anyhow. o-o

---

