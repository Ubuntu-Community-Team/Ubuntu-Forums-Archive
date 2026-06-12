---
title: "Lucid and installing Skype"
date: 2012-04-12
forum: New to Ubuntu
---

### Post by Primus1 on 2012-04-12
Hi I wanted to install skype so went to Ubuntu software center and chose skype internet telephony. 
It says "this software is available from the 'lucid-partner source, which you are not currently using."
I searched for 'lucid partner source on my computer but it came up with nothing. Am I going about installing skype in the right way? I have downloaded Skype for ubuntu 2.2.0.35_1 i386.deb from Skype.com. Should I use this instead of the Ubuntu Software Center?
Thanks

---

### Post by Krytarik on 2012-04-12
The Skype version currently in the Canonical Partner repository is not much older, 2.2.0.35-0, so I'd prefer to just use that. Just make sure to enable the entry "http://archive.canonical.com/ubuntu lucid partner" in your "Software Sources -> Other Software".

Regards.

---

### Post by Primus1 on 2012-04-13
Thank you Krytarik, I ticked the other software sources you mention - I would never have thought to do that. A warning came up to update something so I let it do that.

cheers :P

---

### Post by Primus1 on 2012-04-14
Ah, glad I didn't mark this thread solved.
I can't log on to skype it says there is another 'instance', can't see that anywhere. Also my headset has no sound when I try the skype test call. Any ideas why this is happening?

---

### Post by mörgæs on 2012-04-14
Do you have a green Skype tick sitting on the top bar?

---

### Post by xedi on 2012-04-14
1. The quickest way to close all skype instances is to type

```
killall skype
```

into the terminal or in the run command line. 

(Open the terminal by typing terminal into the dash (click on Ubuntu Icon on the top-left corner or click the super key/ windows key) or use ctrl + alt + t)
(open the run command line by pushing alt + f2)

You can also look for skype instances by running the system monitor. Or if you're really lazy, just log out and back in. Did this solve the problem or does it continue to appear?

2. Maybe you did not say Ubuntu that it should use your headset. Look into your sound options (by typing sound into the dash e.g. or looking in system settings). Check the input and output settings, is your headset selected? If not, do so and it should remember that you want to use it the next time you plug it in.

---

### Post by Primus1 on 2012-04-14
@ morgaes - no green skype tick on teh top bar.

@ xedi - Thanks for the options, I stopped the instances using System Monitor, I am noting your examples for future use. The thing I am wondering is why there are multiple instances of skype. Anyway once they are terminated skype lets me login and I have the sound working too now. I will test tomorrow and if all is well I'll mark this as solved. Thanks for the help guys.

---

### Post by xedi on 2012-04-14
> **Primus1 said:**
> @ morgaes - no green skype tick on teh top bar.

@ xedi - Thanks for the options, I stopped the instances using System Monitor, I am noting your examples for future use. The thing I am wondering is why there are multiple instances of skype. Anyway once they are terminated skype lets me login and I have the sound working too now. I will test tomorrow and if all is well I'll mark this as solved. Thanks for the help guys.

My speculation is the following: If you close skype by clicking on X, skype still runs in the background and you can get it back by clicking on the skype icon in the panel... which for some reason you don't have. 

I have for some reason the same problem on my second computer where I run the 12.04 beta. In it I have to download skype from skpye.com and there I have the same problem.

In my main machine where I'm running 11.10 everything is working fine where I have skype from the software-center.

Maybe somebody else has an idea why the icon is not popping up in the icon?

---

### Post by Primus1 on 2012-04-15
Thanks Xedi

I installed skype from the Ubuntu Software Centre as [Krytarik]("http://ubuntuforums.org/member.php?u=1187548") recommended in thise thread above.
I have been shutting down skype by clicking on 'x' also.

---

