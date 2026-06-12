---
title: "Nothing Happens!"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by chinmoy1955 on 2008-08-26
Hello,
First of all let me congratulate the Ubuntu folks for such prompt action in sending me a Ubuntu bootable CD. Thanks a lot. A few years back I had requested Ubuntu CD's which were posted to me promptly. I had tried to boot my computer with the Ubuntu CD, but unfortunately, though the boot process started normally, after sometimes the computer got locked; just a blank screen and no activity. The latest CD (Version 8.04.1 LTS Desktop Edition) which I received today, is also behaving in the same manner. After the initial boot screen, on pressing the Enter key, the progress bar started normally, but after a few minutes the monitor screen goes blank; CD and hard disk activity continues for some more time, after which there is total silence! I have to reboot by pressing the reset button and the whole process starts all over again. I am very keen to try out Ubuntu, but even the latest version seems to have some bugs or maybe the hardware support is insufficient. I am sorry to say that I have never faced this kind of problem in any of the other numerous Linux distros, especially the CD bootable versions eg. PC Linux. Puppy Linux etc. My system specs are as follows:
AMD Athlon XP 2000+
512 MB RAM
Graphics Card nVidia GeForce 6200 A-LE
Motherboard chipset VIA KM400
80 GB hard disk drive
Can someone please guide as to what is going wrong?

---

### Post by shane19174 on 2008-08-26
Same computer setup then as now?

---

### Post by Michael.Godawski on 2008-08-26
Do you get no error messages whatsoever?
Have you tried to boot into the safe graphic mode?
Or have you tried the text-based installation?

It is rather difficult to say whats going wrong judging only by a black screen:)

---

### Post by bitninja on 2008-08-26
You may want to try the alternate install disc. If you go to the main Ubuntu download page, you can check a little box that says something about the alternate install disc, and it will download that instead. The installer in that version of the disc is all text-based, and in my opinion it's a little faster than using the live CD, as you don't have to wait for the desktop to load and junk before you install. Try that out.

---

### Post by shane19174 on 2008-08-26
The reason I asked whether it was the same computer: I have a laptop that does this with Ubuntu (as well as K/Xubuntu), but not other distros. Why? I don't know. Anyway, when booting from the live CD, it seems to stall but if I wait a while (really, 10 minutes or so) it continues as if nothing ever happened. If I install Ubuntu to the hard disk in the same laptop, it starts without delay. Like I said, I don't have a clue why it does this. So anyway, have you just walked away from the computer and checked in again after, say, a half an hour? If not, maybe it's worth a try.

---

### Post by Tom--d on 2008-08-26
Ok.
You could see what its hanging at. 
When booting into the liveCD and at the menu.
Press F6 or other (the futhest one to the right) and then with backspace, get rid of quiet and splash and press enter. (also the 2 -- can go aswell).
Now you will see text scrolling down. where does it hang etc.

---

### Post by chinmoy1955 on 2008-08-26
> **shane19174 said:**
> The reason I asked whether it was the same computer: I have a laptop that does this with Ubuntu (as well as K/Xubuntu), but not other distros. Why? I don't know. Anyway, when booting from the live CD, it seems to stall but if I wait a while (really, 10 minutes or so) it continues as if nothing ever happened. If I install Ubuntu to the hard disk in the same laptop, it starts without delay. Like I said, I don't have a clue why it does this. So anyway, have you just walked away from the computer and checked in again after, say, a half an hour? If not, maybe it's worth a try.

Thanks Shane.
No, they are not the same computers. Though both are AMD systems, but the rest of the hardware are totally different. But I am really amused by your "wait half an hour" boot process :) I will definitely try it out and get back to you. By the way, even if it does work, I'll say there is something rather funny going on inside Ubuntu!

---

### Post by shane19174 on 2008-08-26
Well, at least something funny with the Ubuntu + my old laptop combination! Like I said, though, this is only with the live CD. Once I get it installed on the hard drive, everything's fine.
Shane

---

### Post by Daveski on 2008-08-26
> **Michael.Godawski said:**
> Have you tried to boot into the safe graphic mode?

Certainly try this option.
Also, silly questions, but it is not that the screen saver has kicked in is it? Try pressing up-arrow or down-arrow (I use these as they seem least likely to cause an issue if the key presses do get processed by something).

---

### Post by Bucky Ball on 2008-08-26
Hmm. Maybe boot into the recovery mode and see if it throws any errors or gets you any further. You could also try adding this at the end of your kernel line at boot (press 'e' to edit);

noapic

Good luck ... :)

---

### Post by chinmoy1955 on 2008-08-26
> **Daveski said:**
> Certainly try this option.
Also, silly questions, but it is not that the screen saver has kicked in is it? Try pressing up-arrow or down-arrow (I use these as they seem least likely to cause an issue if the key presses do get processed by something).

Hi everybody,
Solved my problem!
Daveski, I don't think a screen saver can kick in before the OS has booted fully. Moreover, none of the keyboard keys responded to pressing.
What worked was Michael's suggestion of booting into safe graphics mode. But it booted into a higher resolution of 1280X1024 which is a bit troublesome for a 17" monitor, so I had to manually reduce the resolution to 1024X768 for a more comfortable view.
By the way, let me mention that I am a newbie to Linux. I have been a diehard user of Windows for the past 18 years or so. As a natural outcome, I find Ubuntu lacking in various ways. But as I have mentioned, being a newbie, maybe I am unable to see the virtues of Linux in its proper perspective. In this regard, I would appreciate the help of this community. After using Ubuntu for a few hours, I have come up with a few queries:
1. The default pdf reader is too basic and simplistic. Is there anything equivalent to Adobe reader?
2. The picture viewer Eye of GNOME 2.22.2 is again very basic. I am used to ACDSee for windows, which is a highly evolved and superior software. Especially the refresh rate while changing pics is blinding fast in ACDSee, but in Eye of GNOME 2.22.2 it is quite visible. Is there anything like ACDSee in Linux?
3. I extensively use audio editing software like Cubase SX, Sound Forge etc. I can't see anything like these apps in Ubuntu. I know that Audacity for Linux is available, but Audacity is no match for Cubase or Cooledit Pro.
4. I am unable to configure my printer. I have a HP Deskjet 3745 printer which does not show in the configuration window. How do I configure and activate my printer? It may be a silly question for most of you, but I am new to LINUX.
Thanks to everyone.

---

### Post by philinux on 2008-08-26
> **chinmoy1955 said:**
> 
1. The default pdf reader is too basic and simplistic. Is there anything equivalent to Adobe reader?
2. The picture viewer Eye of GNOME 2.22.2 is again very basic. I am used to ACDSee for windows, which is a highly evolved and superior software. Especially the refresh rate while changing pics is blinding fast in ACDSee, but in Eye of GNOME 2.22.2 it is quite visible. Is there anything like ACDSee in Linux?
3. I extensively use audio editing software like Cubase SX, Sound Forge etc. I can't see anything like these apps in Ubuntu. I know that Audacity for Linux is available, but Audacity is no match for Cubase or Cooledit Pro.
4. I am unable to configure my printer. I have a HP Deskjet 3745 printer which does not show in the configuration window. How do I configure and activate my printer? It may be a silly question for most of you, but I am new to LINUX.
Thanks to everyone.

1. Enable medibuntu and install acroread [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

2. Gthumb or gimp are very good.

4. HP are one of the best supported printers in linux. Try the 3740 driver.

---

### Post by shane19174 on 2008-08-26
Glad to hear you got it booted. As to your other questions, they might be best addressed in separate threads.

But quickly:

1) and 2): I have no need for other programs. Even under Windows, I always used a non-Adobe PDF reader. But search in Synaptic (System -> Administration -> Synaptic Package Manager for "PDF" or "PDF reader" if you want something else. I seem to recall that even Adobe reader is available if you enable the Medibuntu repository (if you don't know what I mean, search in the forum for Medibuntu). And as for Eye of Gnome, there are also lots of alternatives, including even Google's Picasa.

3) Maybe you should check out UbuntuStudio, and read up about it on the forums (mostly under the forum category "Multimedia Production").

4) Search for your printer in the forum, or just google "HP Deskjet 3745 ubuntu".

Hope this helps,
Shane

---

### Post by philinux on 2008-08-26
Search here for any equivalents.

[http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)

---

### Post by Bucky Ball on 2008-08-27
[quote=chimnoy1955]3. I extensively use audio editing software like Cubase SX, Sound Forge etc. I can't see anything like these apps in Ubuntu. I know that Audacity for Linux is available, but Audacity is no match for Cubase or Cooledit Pro.[/quote]

Actually, Audacity for Windows is available! Audacity open source all along and ported to windows.

As mentioned, Ubuntu Studio is what you are after and specifically Rosegarden. That is the equivalent (but is *not*) Cubase. There are others.

Good luck and have fun exploring. I use an XP box for ProTools, Cubebase etc. There is no equivalent (although Rosegarden gets better and better). Don't know how seriously you are into sound manipulation (synthesis) and building your own software contraptions, but programs like Pure Data etc you will find are also open source. You might be interested in this OS also:

[http://code.goto10.org/projects/puredyne/](http://code.goto10.org/projects/puredyne/)

Some hard core tools there. And this next OS opens up a whole realm of interesting possibilities (especially for educational purposes and those that need to take their software with them quickly and easily):

[http://www.dynebolic.org/](http://www.dynebolic.org/)

Have fun! :)

ps: you can also add Rosegarden through Synaptics, but you may have to install a bunch of stuff with it. Lilypond comes with Rosegarden, a notation editor.

---

