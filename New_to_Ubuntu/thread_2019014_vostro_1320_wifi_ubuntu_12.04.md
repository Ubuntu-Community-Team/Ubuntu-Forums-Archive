---
title: "vostro 1320 wifi ubuntu 12.04"
date: 2012-07-06
forum: New to Ubuntu
---

### Post by nocoment on 2012-07-06
Hello I am new to ubuntu so I downloaded it alongside of windows. I like everything about it so far except...
     I cant seem to enable my wifi, I have a hard switch on the side. (which is on)
     I go to the terminal and it says that the hard block and soft block are on
     So I tried to rfkill unblock all, to see no change.
     I have the sta driver it downloaded automatically and says its active.
     The laptop I am using is a dell vostro 1320 
please help

---

### Post by anewguy on 2012-07-07
Please post back the output of:

lspci

---

### Post by Bucky Ball on 2012-07-07
> **anewguy said:**
> Please post back the output of:

lspci

... or:

```
sudo lshw -C network
```

That will tell us more ... ;)

I know this sounds too simple and you've probably looked, but when you right click the network icon do you have 'Enable Wireless' and 'Enable Networking' both ticked? Sometimes this can untick for some reason.

---

### Post by nocoment on 2012-07-07
The enable wireless is uncheckable as it says my hard switch is on  though it isn't, and I know its not broken cause it works in windows  just fine.
   here is the result of the sudo lshw -C network command

---

### Post by Bucky Ball on 2012-07-07
Ok. Have you gotten online with an ethernet cable, gotten updates, then checked 'Additional Drivers'??? You have a Broadcom card which should work fine. If you haven't done that, do it and post back.

If you have and there's nothing there, install:

b43-fwcutter
firmware-b43-installer

Pretty sure that second one is right but you should see it there. The one with b43, firmware and installer in the name. :)

UPDATE: Seems you need a slightly different installer and routine. Check '6. Answers' down the page here from the line starting at '5 This is a common problem to Broadcom wireless chip.':

[http://askubuntu.com/questions/125529/wireless-doesnt-work-on-a-broadcom-bcm4312](http://askubuntu.com/questions/125529/wireless-doesnt-work-on-a-broadcom-bcm4312)

---

### Post by nocoment on 2012-07-07
ok updated and I already had the additional driver that was offered.
where do I go to get b43-fwcutter I am having trouble downloading it. I am not very Ubuntu savvy yet

---

### Post by Bucky Ball on 2012-07-07
Depending on the release Software Centre or Synaptics Package Manager. Don't forget the firmware-b43-lpphy-installer also. Follow this:

> Do the following, run
  sudo apt-get remove bcmwl-kernel-source in terminal. If  the command run successfully try to switch on wireless. If it doesn't  work or the command failed saying there is no such module, then
  Open ubuntu software center, search and install the following packages,
  
[LIST]
[*]b43-fwcutter
[*]firmware-b43-lpphy-installer
[/LIST]
  Reboot once. Now the wireless should work.
 
... from the link I provided. You need to be online with a cable to do this procedure.

---

### Post by nocoment on 2012-07-08
I did sudo apt-get remove bcmwl-kernel-source in the terminal, and downloaded b43 and b43 installer from software center, and rebooted several times.  Still no luck I can't tell that anything has changed, I don't understand this
The enable wireless still just won't let you enable it
 Thank you for helping me as long as you have.

---

