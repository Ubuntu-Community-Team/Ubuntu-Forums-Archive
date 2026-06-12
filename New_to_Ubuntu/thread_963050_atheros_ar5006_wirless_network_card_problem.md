---
title: "atheros ar5006 wirless network card problem"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by niepyta on 2008-10-29
hi, sorry for the noob question. i tried googling it before and reading help in ubuntu but no solution so far.

im playing a bit with ubuntu. im using it booting from cd (hasent installed it yet)to see how it is.

all is nice but i cannot get my wirless to work. in the internet manager (where is shows if im connected to internet) i got exclamation mark. when i click it it show only "no internet" or sth something like this. if i try to configure it, i got only two option "wired internet" and i guess "dial-up connection" and no wirless connection.

so far i have tried:

installing windows drivers for my wireless card atheros ar5006x which i downloaded from hp website as im using hp pavillion dv6710ea. after installing drivers im getting message that the hardware is present but still no connnection and no "wirless option" in the connection manager only wired and dial-up.
what am i doing wrong ? how can i solve it ? 

if there is someone willing to help please do a little how-to.

one more thing, in th upper right corner where all time and internet manager is i got small icon informing me that some periferials are not support by ubuntu and it is my wireless card and one more wirless layer or something like this. both of them are enabled, to do what, i dont know.

thanks for ur help in advance

---

### Post by randy78 on 2008-10-29
I found this: "10/14/08 10:50:45 changed by nick

I had the same problem, but now I figure it out! My OS is ubuntu and the kernel is 2.6.25.7. When I installed madwifi (just as most websites say: make; make install; modprobe ath_pci) at the first time, nothing happened but can not find the driver (ath0 and wifi0). It really depressed me. After looking for the answer for a long time, at last I changed the file /etc/default/linux-restricted-modules-common:

DISABLED_MODULES="ath_hal"

I deleted all the madwifi files which had installed. and I installed it again!

everything just goes on the way :)

I am a fresh man about linux.I do not know the exact reason. I think it is a kernel thing(HAL).

it may help you solve the problems."

It was posted here: [http://madwifi.org/ticket/808]("http://madwifi.org/ticket/808")

---

### Post by bumanie on 2008-10-30
I got an atheros AR242x going yesterday by using ndiswrapper.[ Look here]("http://ubuntuforums.org/archive/index.php/t-766169.html").

---

### Post by nothingspecial on 2008-10-30
Have a look at this

[http://ubuntuforums.org/showthread.php?t=943189](http://ubuntuforums.org/showthread.php?t=943189)

---

### Post by SpinningAround on 2008-10-30
Is there any possibility to get AR242x working without using madwifi?

I did follow this guide [http://ubuntuforums.org/showthread.php?t=940048](http://ubuntuforums.org/showthread.php?t=940048) after blacklisting ath_pci & ath_hal did my wireless actully work! Then after I updated to the new kernel did it stop working. So I guess something broke the fix but what?

---

### Post by nothingspecial on 2008-10-30
Try my link. Read it to the end. It tells you what to do in case of a kernel update.

---

