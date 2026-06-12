---
title: "New guy, have many questions and problems"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by JCDenton1o1 on 2008-05-14
Hello! I just installed Ubuntu last night. I am enjoying this OS very much but I do have some questions and problems.


1) I have installed programs that seem to refuse to show up anywhere. Xmms is one of them

2) Some of my programs are not making sounds, my SNES emulator and Amsn are refusing to make any sounds no matter what I do.

Those are my problems right now. Thank you for any help I can get! :)

---

### Post by Het Irv on 2008-05-14
1) type ```
xmms
``` in the terminal and see what happens.  If that works, I can help you make a launcher.

2)type ```
alsamixer
``` in the terminal.  Are the first two slides up? If not, they should be.  If yes, type ```
lspci
``` and post the output here.

---

### Post by Drakkor on 2008-05-14
Alternately,you could just install Audacious from the repos, it's alike like xmms or winamp.

---

### Post by JCDenton1o1 on 2008-05-14
> **Het Irv said:**
> 1) type ```
xmms
``` in the terminal and see what happens.  If that works, I can help you make a launcher.

2)type ```
alsamixer
``` in the terminal.  Are the first two slides up? If not, they should be.  If yes, type ```
lspci
``` and post the output here.

ok, when I type Xmms in the terminal, it tells me it cant find anything


heres the output to Lspci

00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:08.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)

---

### Post by papuccino1 on 2008-05-14
OP I'm not sure if you know this program already but try using Amarok. It's the best sound player out there (in all the OS's).

---

### Post by mbarak on 2008-05-14
> **JCDenton1o1 said:**
> Hello! I just installed Ubuntu last night. I am enjoying this OS very much but I do have some questions and problems.


1) I have installed programs that seem to refuse to show up anywhere. Xmms is one of them

2) Some of my programs are not making sounds, my SNES emulator and Amsn are refusing to make any sounds no matter what I do.

Those are my problems right now. Thank you for any help I can get! :)

for the sound the problem is that the particular program without sound is using an older sound-system (oss) instead of the newer (ALSA or PulseAudio) sound-systems, which have the ability to play more than one sound at a time - unlike the older one.

In amsn you can fix this in the preferences, under the "other" tab - in the box where it asks you to specify the program to play sound enter use the program "aplay" instead of play

alternatively, you can install alsa-oss
```
sudo apt-get alsa-oss
```
which will trick all your oss programs to use the newer alsa system
ex: to run amsn
```
aoss amsn
```
***hint: edit the menu entry of amsn and your snes emulator in system>preferences>main menu and add "aoss" before the command

---

### Post by Matrixcubed on 2008-05-14
It sounds as if xmms hasn't been installed, or their was an error during installation.  Load up Add/Remove Programs and search for xmms. Make sure the box next to the info for xmms is checked.

If it is and still can't be accessed, try unchecking it and applying the changes. Then recheck its box and apply changes again.

If that doesn't work you may need to fiddle with synaptic to reinstall/fix it.

---

### Post by ace007 on 2008-05-14
you'll find that not all programs you install have a nice shortcut placed in the applications menu.  you may have to access the application by invoking the name of it at the terminal.  

I am not sure but I think its at the discretion of the author of the application if it appears in the menu.

---

### Post by mbarak on 2008-05-14
Since xmms is an old program (and isn't even being developed anymore) it's entry isn't in the menu since at the time of writing the program the menu wasn't standardized (or maybe not enough for xmms)
All (or most) newer, graphical programs should have an entry in the menu

of course, you can always make a menu entry for any program you desire including, and not limited to, xmms

---

### Post by SlappyPappy on 2008-05-14
Are you using Gutsy or Hardy version of Ubuntu?

I have Gutsy and installed XMMS and it put a shortcut in the menu no problem.  :)

---

### Post by JCDenton1o1 on 2008-05-14
Thanks very much everyone!

Amsn is now working one hundred percent.

I've switched to a better sound player.


thank you for all your help!!

---

