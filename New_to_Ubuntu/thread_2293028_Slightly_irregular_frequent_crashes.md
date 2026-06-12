---
title: "Slightly irregular frequent crashes"
date: 2015-09-02
forum: New to Ubuntu
---

### Post by Aric_Wildeboer on 2015-09-02
Hi, I'm having issues with ubuntu crashing at various phases, which are consistent but still slighlty sperratic. Ubuntu freezes during a few different stages, when i type my user password in and press enter sometimes it will freeze immediately, other times it will go blank as if it is about to pull up the taskbar and desktop and it freezes often at this point as well, also sometimes once the desktop and taskbar come up. It normally takes me 10-20 minutes of repeated trying to get the system operational enough to use the internet/skype, and even then it will sometimes randomly freeze during normal use. One thing I have noticed is it freezes everytime without fail if i try to access the brightness/lock settings. I have searched the internet forums for similar issues but have found no resolve, among fixes i have tried are making sure my graphics drivers are up to date and using the terminal to ensure all packages were installed correctly. I am running ubuntu on a MSI GT70 dragon edition with a Intel I7-4810MQ @2.8 Ghz Nvidia GeForce 870m. I am also running ubuntu through windows 8.1, both of which are located on my SSD. any help on this matter would be greatly appreciated, as skype is my only form of communication and for some reason my mic wont work in 8.1 no matter how many times I check all my system settings.

---

### Post by Bucky Ball on 2015-09-02
Welcome. Boot to Ubuntu, once it's stable, run these commands in a terminal:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

Post back any and all errors and that will give us some idea of where we are. 

When you say you are running Ubuntu through Windows 8, do you mean you are using Wubi? If so, it is no longer supported by Canonical, hasn't been in awhile, and you will get little support for it here. No one uses it anymore so can't give much advice. It was only ever intended for users to 'try before you buy', never as a long-term solution.

Now you can try Ubuntu directly from the install media. If it is a Wubi install, uninstall and do a dual-boot, Windows and Ubuntu on separate partitions. We can help you with that.

---

### Post by tgalati4 on 2015-09-02
Welcome to the forums.  Is this a laptop?  If so, remove the battery and boot from the AC power cord only.  Sometimes a bad battery will cause power issues.

---

### Post by Aric_Wildeboer on 2015-09-02
I can verify this is not a power issue due to my time working in a college IT department. As for my statement of running through windows i believe that was a slight mistatement. When i downloaded Ubuntu I chose the 64 bit option most suited for windows 8 which I then selected to option to install it alongside windows, and and nearly positive i am not using wubi as i rechecked to make sure. The results were only one error during all command issues, which was when I ran sudo apt-get upgrade and i got the following error: (gtk-update-icon-cache-3.0:6067): GdkPixbuf-WARNING **:Cannot open Pixbuf Loader module file '/usr/lib/x86_64-Linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache  This likely means your installation is broken.

---

### Post by ian-weisser on 2015-09-02
Are there any recent .crash files in /var/crash?

If so, please attach one.

---

### Post by Aric_Wildeboer on 2015-09-02
There are no files in my /var/crash folder

---

### Post by ian-weisser on 2015-09-02
When you say 'freeze', which do you mean?

- Mouse and keyboard completely unresponsive for a brief time, then returns to normal.
- Either mouse or keyboard unresponsive, but the other works.
- Mouse and keyboard completely unresponsive requiring a hard poweroff and restart.

---

### Post by Aric_Wildeboer on 2015-09-02
The most latter, where mouse and keyboard do not work and i have to do a hard reset.

---

### Post by ian-weisser on 2015-09-02
Are there any useful error messages in /var/log/syslog?
Are there any useful error messages in /var/log/dmesg?
Exactly which version of Ubuntu are you running? 12.04? 14.04? 15.04? Something else?
What's the full result of the 'uname -r' command?

---

### Post by Aric_Wildeboer on 2015-09-04
I was unable to locate either the sylog or th dmesg folder, and I downloaded 14.04 x64 bit, and as of last nite installed the most recent update. the uname -4 command yielded 3.19.0-26-generic. Update on more current issues; I am unable to access my SSD or HDD due to what linux is saying is a mounting issue. Also sometimes on startup, everything works fine except for my sound and mic (this happened once in a guest session and once under my login) and I have also encountered a freeze where I can move my mouse but nothing else works.

---

### Post by ian-weisser on 2015-09-04
> **Aric_Wildeboer said:**
> I was unable to locate either the sylog or th dmesg folder
They are located in /var/log/ , not your /home.
Without the information they contain, we can merely guess.

My mere guess, based on the surprising variety of intermittent freezes and crashes  you  describe, including after a reinstall, is a hardware fault.
Perhaps an overheating or poorly-seated video card.
Merely incompatible hardware would simply fail to work...consistently

---

### Post by Bucky Ball on 2015-09-05
That is an old kernel for 14.04. Run these commands:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

That will NOT upgrade you to a new release, just upgrade the software you have installed. That should get you to the latest kernel and some of your problems may go away.

---

### Post by Aric_Wildeboer on 2015-09-08
I would still very much appreciate help with this. Switching back between two operating systems cos one hardly works and the other one wont run some programs right is incredibly annoying. If I had the money i would get the equipment to backup my files on a hard drive and do a complete system wipe and then boot an operating system onto my computer until I get it right, but I don't have the money so I can't. My laptop will be very important to me in the near future as I will be trying to start an online business and need it to run smoothly.

---

### Post by ian-weisser on 2015-09-08
We're awating your result from trying Bucky Ball's quite sensible advice.
If crashes persist after upgrading to a more recent kernel, then we need to see a complete post-update .crash file.

---

### Post by Bucky Ball on 2015-09-08
> **ian-weisser said:**
> We're awating your result from trying Bucky Ball's quite sensible advice.
If crashes persist after upgrading to a more recent kernel, then we need to see a complete post-update .crash file.

+1. We can only help you if you help us by providing info requested. Thanks. :)

---

### Post by Aric_Wildeboer on 2015-09-11
apologies as i just now realised there was a second page and the section didnt get longer with comments, which is definately due to my own idiocy. im about to boot linux and will post back with the information.

---

### Post by Aric_Wildeboer on 2015-09-11
I ran the commands and will report back with further issues. I found the folders by typing the directory into my browser, and my dmesg folder had 6 errors which are as follows[COLOR=#000000] 
[/COLOR]```
 0.190401] ACPI Error: No handler for Region [EC__] (ffff8803430bd168) [EmbeddedControl] (20141107/evregion-163)
[    0.190404] ACPI Error: Region EmbeddedControl (ID=3) has no handler (20141107/exfldio-299)
[    0.190406] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC__._REG] (Node ffff8803430bced8), AE_NOT_EXIST (20141107/psparse-536)
[FONT=Verdana]11.221107] ACPI Error: [\_SB_.PCI0.GFX0.DD02._BCL] Namespace lookup failure, AE_NOT_FOUND (20141107/psargs-359)
[/FONT][   11.221110] ACPI Error: Method parse/execution failed [\_SB_.PCI0.PEG0.PEGP.DD02._BCL] (Node ffff8803430f0a50), AE_NOT_FOUND (20141107/psparse-536)

```
The syslog folder on the other hand contained 367 errors (which i would say is an issue) which I will not be posting, but if you could give me an idea of what errors to look for i could post back with specifics. Secondly on the subject of hardware failure I can't rule this out entirely as I know my laptop does have strange hardware issues, but I can not verify them all as I no longer work in IT and havnt had the money to get any of the tools I would need, nor can i send it to the manufacturer since I voided the warranty doing freelance work (a simple removal of my HDD to replace it with another that I then reformatted and replaced in its proper pc, and also replaced mine with no complications). I can say that the only hardware issue I had with windows was my microphone not working (as I've said before) and again this was fixed as soon as I switched to linux. The only hardware issues im currently are aware of have to do with the keyboard/touchpad and the housing for my screen.

---

### Post by Bucky Ball on 2015-09-11
Post a new thread for support issues not related to this one. Thanks. :)

Also, please use code tags for terminal output so it is readable. See last link in my signature for how.

---

### Post by Aric_Wildeboer on 2015-09-12
Everything I've said is related? I was told check log folders and post back info and that it might be a hardware issue, so I provided further knowledge on these subjects? Ubuntu is crashing mor frequently now than it has been since I ran the commands you told me to.

---

### Post by Aric_Wildeboer on 2015-09-12
According to the wiki the sytem log file deals with the functionality of the Ubuntu system, and since my syslog folder contained 367 errors I believe it is safe to say that this is the main issue that I'm dealing with. Im currently looking for a way to repair or re-download the system log files but as of yet have not had any luck. Can anyone direct me or tell me that my theory is wrong?

---

### Post by ian-weisser on 2015-09-12
> **Aric_Wildeboer said:**
> my syslog folder contained 367 errors
...
Can anyone direct me or tell me that my theory is wrong?

Not sure what theory you have, so it's hard to say.

> **Aric_Wildeboer said:**
> if you could give me an idea of what errors to look for i could post back with specifics. 
Unfortunately, that would require us to be psychic.
Probably better to post them all. tgalati4's instructions below are excellent.

Look for relationships between the many errors.
Is there one type of error that occurs more than others?
In a group of errors, is one type of error first? or last?
Do the same errors occur at certain times of day? When you do certain actions? When certain software runs?

---

### Post by tgalati4 on 2015-09-12
Post the output of:

```
grep -E error /var/log/syslog
```

---

