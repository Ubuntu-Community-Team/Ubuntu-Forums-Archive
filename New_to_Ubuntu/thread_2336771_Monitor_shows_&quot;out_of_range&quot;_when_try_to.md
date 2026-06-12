---
title: "Monitor shows &quot;out of range&quot; when try to install ubuntu 16.04 from live usb"
date: 2016-09-11
forum: New to Ubuntu
---

### Post by cr7778 on 2016-09-11
Below are my PC spec:
AMD FX-8350 
GTX 1070

No onboard graphics to boot from.

Please help solve the "out of range" issue.
I wanted to move to linux but, this type of issues preventing me from doing so.

---

### Post by carl4926 on 2016-09-11
Try nomodeset
see: [http://askubuntu.com/questions/484132/trying-to-install-ubuntu-14-04-monitor-says-mode-unsupported-out-of-range](http://askubuntu.com/questions/484132/trying-to-install-ubuntu-14-04-monitor-says-mode-unsupported-out-of-range)

---

### Post by cr7778 on 2016-09-11
Thanks, [**[COLOR=#DD4814][B]carl4926**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=809261"). It worked!

---

### Post by Bucky Ball on 2016-09-11
Welcome. Once you have installed, open 'Additional Drivers', install the correct NVidia driver you will find there and reboot.

The 'nomodeset' will only last for the boot you apply it to. Once rebooted, you will need to run the nomodeset option again until you have the correct driver installed (or you make 'nomodeset' option permanent, which is necessary in some situations, but shouldn't be with you).

Presuming you are using 16.04 LTS? With that card, if you're not, you probably should be.

Please mark the thread as solved to help others. See 'Thread Tools' at the top right or the blue link in my signature at bottom of post. Thanks.

---

