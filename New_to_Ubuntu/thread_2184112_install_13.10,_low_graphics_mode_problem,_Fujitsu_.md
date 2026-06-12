---
title: "install 13.10, low graphics mode problem, Fujitsu c-series lifebook"
date: 2013-10-27
forum: New to Ubuntu
---

### Post by porter_sg on 2013-10-27
Hi All,
As of an hour ago a complete ubuntu noob. My wife had an old Fujitsu C-series (1200 I think) lifebook lying around and I installed 13.10 on it so I could use it & play with ubuntu before doing a change over of OPs on the main computers in the new year.
Installation went well, but got "the system is running in low-graphic mode" issues. Everything I did resulted in nothing, even the "for just one session" option didn't do anything after leaving it for 10 minutes to reconfigure.
I did another clean install and the same problem.

"Review the start up errors" shows nothing.
It won't let me "edit the configuration file" not that I would know how to anyway.
"reconfigure graphics" leads to dead-ends
"exit to console login" just gives me a blank screen (just like the one session option)

It might be that the hardware is too old? Although everything was visible ad not distorted on the install screens, so don't think this would be the issue

The installs were done without connection to the internet and connection to the internet won't be possible where I am (don't ask) so if this is the problem (i.e. downloading the drivers whilst installing 13.10) I'll have to do this at a mate's house.

Any ideas would be gratefully received.

---

### Post by mörgæs on 2013-10-28
Hi, welcome to the fora.

Please run

```
sudo lshw -sanitize > lshw.txt 
```

in a live boot or a real install and post lshw.txt in CODE tags.

---

### Post by porter_sg on 2013-10-28
Sorry for taking so long to respond, many thanks for your offer of help - much appreciated. I'm in the process of another install (3rd time's a charm and all that). One thing I couldn't find was a command prompt to enter the above command. The screens that presented themselves didn't give me the chance to type anything in. Is there a hotkey or other way of bringing up command prompt?

---

### Post by porter_sg on 2013-10-28
Re-install complete. Upon restart the ubuntu logo comes up, a white fuzzy screen appears twice (graphics failing to render) and then the "the system is running in low-graphics mode" appears. 
After clicking OK, you get 4 options: 
run in low graphics mode for one sessions - gives me a black screen and nothing further
reconfigure graphics which leads to two options which don't do anything when selected
troubleshoot the error - review the xserver log file - which produces lots of text (the only way realistically of getting that info to you is photos)
review the startup errors - none shown
edit config file - no action when this selected
exit to control login  -which brings up a permanently dark screen.

I can't see an obvious way of entering in commands.

---

### Post by porter_sg on 2013-10-28
Sorry to keep posting, found out about 'grub' and entered the command line as suggested, but it says syntax error.

---

### Post by mörgæs on 2013-10-28
The command must run in Buntu, not at the Grub prompt. 

Have you tried installing Lubuntu 13.10 or running it in a live boot? Ubuntu is too heavy for a C-series, and even Lubuntu might need some modifications.

---

### Post by porter_sg on 2013-10-28
Unfortunately, I've been a bit hasty with this and did a full install over xp. Having made no progress with ubuntu, tried to install lubuntu but that seemed to have exactly the same problem. I then tried to put in the xp recovery disc but that won't boot up as grub kicks in and kills the recovery discs progress. 
It's a bit of a mess. 
It might be worth trying to complete remove ubuntu (in a format harddive style) but I'm not sure I can do this through grub.

---

### Post by mörgæs on 2013-10-28
If we forget installing for a moment, can you run Lubuntu in a live boot?

---

### Post by Tony Bilbrough on 2013-10-29
I too am having trouble getting Ubuntu 13.10 to boot to Home.
The machine is HP Compaq D530cmt w 2Gb RAM.
Installation is fine, all the way to the reboot. Then it shows the Ubuntu background but no Unity icons.
No Home or shut down Icons
Tried downloading a second iso, but have the same result.
Perhaps the machine is too old?
Any help much apreciated

---

### Post by mastablasta on 2013-10-29
> **porter_sg said:**
> Unfortunately, I've been a bit hasty with this and did a full install over xp. Having made no progress with ubuntu, tried to install lubuntu but that seemed to have exactly the same problem. I then tried to put in the xp recovery disc but that won't boot up as grub kicks in and kills the recovery discs progress. 
It's a bit of a mess. 
It might be worth trying to complete remove ubuntu (in a format harddive style) but I'm not sure I can do this through grub.

just boot it (from the live CD or LiveUSB), select try it. once inside the os, find the terminal  (in lubuntu it will be lxterm in ubunut it's terminal or alt+t shortcut). then copy and paste the command given here into terminal (right click and paste) and press enter.

the ocmmand will give system specs (including GPU chip, CPU etc). mark it all and copy it and then paste it here  in the forums inside the code tags = icon (#).

---

### Post by mastablasta on 2013-10-29
> **Tony Bilbrough said:**
> I too am having trouble getting Ubuntu 13.10 to boot to Home.
The machine is HP Compaq D530cmt w 2Gb RAM.
Installation is fine, all the way to the reboot. Then it shows the Ubuntu background but no Unity icons.
No Home or shut down Icons
Tried downloading a second iso, but have the same result.
Perhaps the machine is too old?
Any help much apreciated

first don't steal other peoples thread. rather create your own. you only assume your issue is the same but it's probably not. do follow the same advice as for the starter of this thread. try lubuntu (or Xubuntu) and get the info on specs using the command. btw the mashcine is not too old to run a modern linux OS.
and also after you download don't forget to do a md5sum check.: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

[h=2][SIZE=2]Suggestions on how to get your support questions answered as quickly as possible: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

[/SIZE][/h]

---

