---
title: "TIPS &amp; TRICKS: AMOR + KDE-DCOP + fortune cookies."
date: 2006-12-03
forum: Outdated Tutorials &amp; Tips
---

### Post by nixclusive on 2006-12-03
TIPS & TRICKS: AMOR + KDE-DCOP + fortune cookies.

Note: This HOWTO is applicable to the KDE Desktop Environment. If you are using GNOME or something
else, please ensure that your environment supports DCOP.

AMOR (Amusing Misuse of Resources) provides several different characters who prance around your X s
creen doing tricks and giving you tips. However, the tips provided with the AMOR installation are l
imited in number are one may get really bored after a while. Fortunately, AMOR supports the KDE-DCO
P (Desktop Communication Protocol) and thus allows us to interface its messaging functionality with
 'fortune' using showMessage and showTip DCOP calls.

Consequently, we can now have a desktop creature which prances around our X screen and shows us som
e funny epigrams. Here's the procedure:

1. Install AMOR and additional fortune cookies. Open the Konsole and type:

```
sudo apt-get install amor fortunes fortunes-off
``` and press <enter>.

Note: The 'fortunes-off' package contains maxims that may be offensive to you or your family. If yo
u have such concerns, please do not install the 'fortunes-off' package.

2. Now copy and paste the following into the terminal:

```
ln -s `which amor` ~/.kde/Autostart/
cat > ~/.kde/Autostart/fdcop << EOF
#!/bin/bash

dcop amor &> /dev/null
if [ "$?" != 0 ] ; then
    exit 1
fi

#This ensures that the script exits if AMOR is not running.
while test "$?" = "0"
do
        sleep 60;
        dcop amor AmorIface showMessage "`fortune -as`"
done

exit 0

EOF
amor
~/.kde/Autostart/fdcop &
```

If you did that correctly, you should now have an AMOR creature on your desktop and it should displ
ay a random fortune cookie every 60 seconds.

Enjoy... ;-)


Troubleshooting: If you happen to quit AMOR and then start is again from the K-Menu, you may not re
cieve any more fortune cookies. To correct this, open Konsole and type:```
ps -e | grep fdcop[/co
de] If you don't see any output, then the script probably exited due to AMOR not running. To start
the script again, enter the follwing in the Konsole:[code]~/.kde/Autostart/fdcop &
``` Enter the
 previous command again and you should see some output.

PS: Improvements are invited. Thanks.

---

### Post by forestwalkerjoe on 2009-07-10
ok. you seem to know a little bit about these buggers.. maybe you can help me code a small change to the Amor i have. I did install it on my own ubuntu already. I am now in the upgraded 904. No trouble.. but i did an install for a family friend, of the Ubuntu 810 and the only complaint they have is that the AMOR turns itself off every time you reboot. 
IS there some sort of mod we can create some place that causes it to start every time you reboot? THEN, if they DIDNt want it.. they could just right click and turn it off , like they can now? 
I want this sort of feature too.. but hasn't the first clue on how to write such a Mod. 
Anyone out there willing to make a Go of it? 

FWJ

---

