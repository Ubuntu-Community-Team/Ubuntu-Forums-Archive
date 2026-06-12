---
title: "System setting changes not taking effect"
date: 2011-12-16
forum: New to Ubuntu
---

### Post by TessaRact on 2011-12-16
Hello. I have recently started using Ubuntu and am having a bit of difficulty changing things around Systems Settings in 11.10. Any changes I make in Systems Settings, like in Appearance, Keyboard/Language, Screen, Time & Date, and everything else barring volume control and screen dim, do not take effect. After closing systems settings, when I revisit, the options remain changed as I wanted. But nothing really happens.

I am not sure why this is happening but I noticed that this started after an update few days ago but I'm not quite sure what it was that made system settings ineffective/faulty. I don't mind working with terminal and commands but I'm not quite sure where to start. If someone could point me in the right direction, it would be much appreciated. Thank you.

---

### Post by amjjawad on 2011-12-17
> **TessaRact said:**
> Hello. I have recently started using Ubuntu and am having a bit of difficulty changing things around Systems Settings in 11.10. Any changes I make in Systems Settings, like in Appearance, Keyboard/Language, Screen, Time & Date, and everything else barring volume control and screen dim, do not take effect. After closing systems settings, when I revisit, the options remain changed as I wanted. But nothing really happens.

I am not sure why this is happening but I noticed that this started after an update few days ago but I'm not quite sure what it was that made system settings ineffective/faulty. I don't mind working with terminal and commands but I'm not quite sure where to start. If someone could point me in the right direction, it would be much appreciated. Thank you.

Hello and Welcome to Ubuntu Forum :)

1- How did you install Ubuntu? is this Normal Installation? 

2- Is this a PC or Laptop? I have noticed the same behavoir on my Laptop which has Ubuntu 11.10, Lubuntu 11.10 and Windows 7.

3- What Kernel are you using?
```
uname -a
```

4- Have you searched Launchpad for similar issue?

5- In case it's a bug, you need to report it to Launchpad because developers don't really look at forums.

---

### Post by TessaRact on 2011-12-17
> **amjjawad said:**
> Hello and Welcome to Ubuntu Forum :)

1- How did you install Ubuntu? is this Normal Installation? 

2- Is this a PC or Laptop? I have noticed the same behavoir on my Laptop which has Ubuntu 11.10, Lubuntu 11.10 and Windows 7.

3- What Kernel are you using?
```
uname -a
```

4- Have you searched Launchpad for similar issue?

5- In case it's a bug, you need to report it to Launchpad because developers don't really look at forums.

Thanks for the reply, amjjawad.

1. If by normal installation you mean full installation and not on removable device, yes.

2. This is a laptop. [HP G50 104NR]("http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&dlc=en&docname=c01607613&lang=en&lc=en&product=3806964") to be exact. Came with windows something, had vista and 7 but finally made it to ubuntu.

3.Linux T 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

4. I wasn't aware of Launchpad. Thanks. I did just search it briefly but couldn't find anything that I found relevant.

5. I wish I could localize the problem but I'm not quite where to start searching for what is wrong with it. There are few other problems as well, none of the external storage devices are recognized (it used to) and my trackpad also stopped working. I haven't really tinkered with anything so I presume it was the updates that somehow messed with some files, somewhere. I'm now considering uninstalling all the updates (if that is even possible - I would assume that it would be) and hopefully figure out what update(s) are causing issues but there has been literally over 100 updates and I would hope to find a smarter and not-so-brute force way to figure out the problem.

---

### Post by amjjawad on 2011-12-18
> **TessaRact said:**
> Thanks for the reply, amjjawad.

You most welcome!

> 1. If by normal installation you mean full installation and not on removable device, yes.

What I meant by "normal installation" is whether it's a Wubi Installation or not?

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

I personally avoid it but that's me.
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

> 2. This is a laptop. [HP G50 104NR]("http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&dlc=en&docname=c01607613&lang=en&lc=en&product=3806964") to be exact. Came with windows something, had vista and 7 but finally made it to ubuntu.
Mine is Lenovo G570 (Core i5 2nd generation and 4GB RAM).


> 3.Linux T 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
This is the latest Kernel in Ubuntu 11.10. I don't think it's a Kernel issue but I was just checking which one you have :) sometimes, upgrading the Kernel could solve some issues.


> 4. I wasn't aware of Launchpad. Thanks. I did just search it briefly but couldn't find anything that I found relevant.

Launchpad is where users need to report bugs because the developers don't look at forums, they have lots to do ;)

If there is no bug report similar to your case (mine as well), I think it's time to report one :)

> 5. I wish I could localize the problem but I'm not quite where to start searching for what is wrong with it. 

I'm not sure which package is responsible so I must do some search and get back to you. I'm not an Ubuntu User anymore, I'm Lubutnu Addicted and Loving it but since I posted here, I'll do my best, no worries. If someone else better than me will jump in, that's even better :)


> There are few other problems as well, none of the external storage devices are recognized (it used to) and my trackpad also stopped working. 

Are you saying everything was ok before?

> I haven't really tinkered with anything so I presume it was the updates that somehow messed with some files, somewhere. I'm now considering uninstalling all the updates (if that is even possible - I would assume that it would be) and hopefully figure out what update(s) are causing issues but there has been literally over 100 updates and I would hope to find a smarter and not-so-brute force way to figure out the problem.

As far as what I've seen over here, in rare cases, updates could do that but we are not sure yet whether the same applies to you.

I think there is a way to revert back. I think the easiest way is at the GRUB Menu where you can choose the previous Kernel to boot into instead of the latest one.

---

### Post by TessaRact on 2011-12-18
Ah, I wasn't too sure about what you meant by normal. It was from LiveUSB. While I don't think it should matter, the computer was infected when it ran Windows. I didn't bother formatting it and just installed Ubuntu.



Yep, everything worked fine (however brief that period was) before a couple of updates ago. I will report it as a bug on LaunchPad and try GRUB and see what I can do with it. Thanks!

---

### Post by amjjawad on 2011-12-18
> **TessaRact said:**
> Ah, I wasn't too sure about what you meant by normal. It was from LiveUSB.
I'm sure you do now :) 

> While I don't think it should matter, the computer was infected when it ran Windows. I didn't bother formatting it and just installed Ubuntu.
You mean it was infected with a virus or something?



> I'll try GRUB and see what I can do with it. Thanks!

Please let me know what will happen :)

---

