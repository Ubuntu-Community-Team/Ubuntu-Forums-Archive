---
title: "Can't escape black screen"
date: 2017-10-13
forum: New to Ubuntu
---

### Post by debdrex on 2017-10-13
[COLOR=#000000]I posted this message last night in General Info but have copied it here with a new title and new information.
I tried out ubuntu 16.04.3 on an HP Spectre x360 using live USB and inadvertently removed the USB before it was done shutting down. I now have a black screen with a long list of squashfs errors and have no idea how to get out of this screen. I'm new to Ubuntu and only just learning to work with Command line (i.e. pretty clueless). The first 2 lines follow. I'm typing on another computer so am not putting in the whole list. Hopefully, this will be enough?[/COLOR]
[COLOR=#000000][ 422.794744] SQUASHFS error: Unable to read page, block bd60692, size a6b0[/COLOR]
[COLOR=#000000][ 422.795700] SQUASHFS error: Unable to read fragment cache entry [bd60692] [/COLOR]
[COLOR=#000000]Can anyone help me escape from this? Have I done bad things to the laptop?

[/COLOR]The next day. I pressed Alt + F4 and the squashfs errors disappeared and are slowly replaced by:
[COLOR=#000000][FONT=Calibri]**[54127.307759] **[/FONT][/COLOR][COLOR=#000000][FONT=Calibri]**systemd-journald**[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][B][1205]: Failed to send WATCHDOG=1 notification message: Transport endpoint is not connected

[/B][/FONT][/COLOR]I'm unable to leave this screen. Can't restart, can't go forward. Laptop stuck in this place. Please help!

[COLOR=#000000]Thanks, Debbie[/COLOR]

---

### Post by Autodave on 2017-10-13
Are you dual booting with Windows? If not (and it sounds like you just tried installing Ubuntu) why can't you just reinstall it?

Even if you are dual booting, you should be able to reinstall: just do it like you did the first time and when you get to the screen to choose where to install, just choose "Replace Ubuntu 16.04.

Of course, amke SURE that you have everything backed up first!!!

---

### Post by debdrex on 2017-10-13
Autodave, thanks for your quick reply!

I ran the live USB on Windows to try out Ubuntu on this machine. The USB isn't connected anymore though I did try replacing it. That didn't help. I can't get the computer to move off of the black screen. Can't reboot. I can type into the black screen but don't know what to type. So I'm stuck and can't get into Windows or Ubuntu. I have a backup.

---

### Post by Autodave on 2017-10-13
I am confused now. Exactly how did you try to install Linux?  Were you in Windows when you tried that? Are you trying to put Linux on the machine and also keeping Windows?

---

### Post by debdrex on 2017-10-13
I have been able to restart in Windows by (duh) pressing the power button to turn off the machine and then pressing it again. Everything is back to normal. I'd tried this last night but apparently didn't press POWER long enough.

To answer your question my long-term goal is to dual boot Ubuntu on a Windows 10 machine but I was running it from the live USB of Ubuntu on the same Windows laptop and accidentally removed the USB stick before Ubuntu was finished closing out. Which is what caused the problem.

Thanks.

---

### Post by leunam12 on 2017-10-14
next time pres alt and sysrq keys simultaneously and type R E I S U B

---

### Post by yancek on 2017-10-14
If you haven't resolved this issue, I would suggest you read the link at the Ubuntu documentation below before trying again. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

