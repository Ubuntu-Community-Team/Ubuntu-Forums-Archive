---
title: "Newby has a freeze problem"
date: 2016-09-18
forum: New to Ubuntu
---

### Post by yithmas on 2016-09-18
Hi everybody.

I am completely new to Linux and just yesterday installed Ubuntu 16.04.1 LTS on my Toshiba  Satellite L50-B-1PV. Everything runs really smoothly except for a complete freeze I get every now and then when I either watch a video (from my hard drive) or have a youtube or soundcloud playlist running in the background while typing in LibreOffice.
I do not experience the problem when I do not have a video running or Firefox closed/no video/audio from the web.

Now I have two questions:

Could this be a media-reated problem?

and

is there something like a task manager or anything I can do when the screen freezes? Str-Alt-Del does nothing in those cases.


Best,

Yithmas

---

### Post by mastablasta on 2016-09-19
1. try ctrl. + alt+backspace (this should reset the desktop)
2. or crtl.+alt+F1 (this drops you to command line console - crtl+alt+f8 to get back to desktop)
3. you can also try REISUB command: "Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB will get you safely restarted."


Freezes are hard to troubelshoot. it can be that memory and CPU is used up and only appears as a freezse. to monitor usage use top or htop command in CLI or some sort of system monitor in GUI.

second most often reason is overheating. to monitor the heat install for example psensor (detailed instructions here: [https://wpitchoune.net/psensor/](https://wpitchoune.net/psensor/) ).
in case of overheating some cleaning might help (blow air from compressed air through vents).

next is the RAM - when you boot and if you hold down left shift while booting you will enter GRUB. from here you can perform a memorry test. do that and let it do at leats two passes. see if any errors pop up.

finally, you should always post your system specs so others can have a look. perhaps there are known issues with certain hardware or drivers. here is how you do it in linux: [https://ubuntuforums.org/showthread.php?t=1422475](https://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by yithmas on 2016-09-19
Thanks mastablasta.
It is not a heat problem (the computer did not get hot at all, actually) and I do not think it's a CPU issue, either, but I will try the 1-3 you suggest and I will follow the instructions in the thread you mentioned.
Thank you for your help!

---

### Post by mastablasta on 2016-09-20
if heat is really not an issue, then you can use log viewer or manually check logs found in /var/log to see if any errors are reported before the crash. in any case if heat is not the isuse then you need to write down some hardware specs.

---

### Post by yithmas on 2016-09-23
Going through the logs is a great idea. Which log do I need to check, exactly (I found the folder) and can you recommend a log viewer?

---

### Post by mastablasta on 2016-09-25
i use Kubuntu, so i don't know what the default log viewer is in Ubuntu but it should do fine whichever it is. Check dmesg, dmesg.ol, kernel logs, syetem logs. all the main ones basically. usually they display in viewer.

---

