---
title: "Out of range"
date: 2012-04-28
forum: New to Ubuntu
---

### Post by rosswmcgee on 2012-04-28
I have been using 12.04 as an upgrade and am happy. So I decided to 

do a clean install on another machine. The install goes fine, but after

boot up I get a blank screen with the out of range blinking. So I installed 

it again and got the same thing. What to do?

---

### Post by sffvba[e0rt on 2012-04-28
Hold left-shift when booting.

When the grub menu comes up, press e to edit the boot parameters and add "nomodeset" to the options (typically in the same line as quitesplash)... Then you press Ctrl+X to boot.

Picture how-to if you click [HERE]("http://askubuntu.com/questions/38780/how-to-set-nomodeset-for-installation") :)

Once booted look for restricted drivers for your graphics card and install it.



404

---

### Post by rosswmcgee on 2012-04-28
I did that and same problem, I get the ubuntu start up sound but still get our of range. After that there was no splash line. I tried the rescue mode too. No change.



I am burning a new dvd will try it. Other wise install 11.10 and try an upgrade. 

Never had this problem with any other distro. in 20 year with linux.

OK re-installed using new dvd, this time I do not get out of range but just a dark screen.

OK now by right clicking I get the ubuntu screen without any panel.

---

### Post by rosswmcgee on 2012-04-28
I give up cannot install 12.04 tried 3 times two different dvds.

I am installing 11.10 and will try an upgrade. cancel that I am trying  install 12.04 one more time, then will do 11.10

this time without updates and extra codecs.

---

### Post by greenelf on 2012-04-28
```
sudo nano /etc/default/grub
GRUB-GFXMODE=text
sudo update-grub

```

(uncomment GRUB-GFXMODE by deleting the # sign)

For more documentation on Grub resolution:
[https://help.ubuntu.com/community/Grub2#Resolution_Settings](https://help.ubuntu.com/community/Grub2#Resolution_Settings)

---

### Post by smcrossman on 2012-04-28
Do you by chance have a NVidia graphics on this machine?  I have that same issue EVERY time I do a clean install with my NVidia. If it eventually goes on into your login then it is simply changing the font in the startup. (and doing the install of restricted drivers to prevent future problems).

If that is the problem and it doesn't take you to log-in there is some way to preset certain setting when installing, but I haven't done it and don't remember where I saw that documentation.  The launchpad.net forum has more on this issue if an upgrade doesn't work for you.

---

### Post by rosswmcgee on 2012-04-28
No I do not.

---

### Post by rosswmcgee on 2012-04-28
I cannot run commands with out being logged in.

---

### Post by sffvba[e0rt on 2012-04-28
What graphics card are you using?


404

---

### Post by rosswmcgee on 2012-04-28
Problem solved three times a charm. This time using no updates or codecs did it.

---

### Post by sffvba[e0rt on 2012-04-28
> **rosswmcgee said:**
> Problem solved three times a charm. This time using no updates or codecs did it.

Weird.


404

---

### Post by rosswmcgee on 2012-04-29
Now that I have everything set up and working well I installed the nvidia recomended drivers. Now re-boot I am back to the out of range screen and cannot log in. 
12.04  is a trying experience. What to do now except re-install, any ideas, cannot 
log in for heavens sake. I do not think I am going to be able to use 12.04 unless someone has an idea this would
be the 4th re-install. Help!!

---

### Post by SeijiSensei on 2012-04-29
People with older NVIDIA cards have been reporting problems with 12.04.  If you're using a 6xxx or older chipset, I'd avoid using the proprietary driver for the time being until a fix is released.

---

### Post by rosswmcgee on 2012-04-29
Well is there a way to deal with that driver other than a re-install, or should I simply ignore the driver icon on the panel or is there a way to remove the icon , or should I re- install 11.10???


I did my 4th re-install of 12.04 avoided all driver installs and am now in business. Hardest distro install ever.

---

