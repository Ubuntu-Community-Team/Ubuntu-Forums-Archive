---
title: "Black Idle screen (tried multiple downloads)"
date: 2013-08-23
forum: New to Ubuntu
---

### Post by john_jackson2 on 2013-08-23
I've tried everything. I installed Linux with my hard-drive and when I try to load the OS it says "missing or corrupted files" but it never matters which download I use I can never get into the OS. I've tried the USB one, used a program to do it for me; [unetbootin-windows-585.exe]("file:///C:/Users/John/Downloads/unetbootin-windows-585.exe") . As soon as I press install linux or try linux it just goes to a black screen while my fan goes crazy and sits there. I've read multiple things about "pressing shift while in the purple menu" but I never gotten to a purple menu? all it is, is black doing nothing like a nightmare. Been up for 3 hours just trying to load it and try it out. I would love if anyone could help me!

Hardware:

Processor: AMD E1-1200 APU with Radeon(tm) HD Graphics     1.40GHz
Ram: 4gb (3.59 usuable) 64 bit
Windows 8 


Why I can't find it anywhere else? Sorry if there is somewhere but they keep telling me to press shift in the purple menu but there is none for me. I don't know if I'm doing anything wrong this is my first time trying Linux and I really want to see what its like.

Thanks!

---

### Post by hg-knight on 2013-08-23
if any good try [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

if not try another distro and see if that is the same
which version are you trying to install
have you a graphic card on pc ?

---

### Post by su:bhatta on 2013-08-23
Have you actually been able to install Ubuntu on that system once?

Try this method once and see(Basically this is same as the link given above ):

On the first boot from the Ubuntu DVD you will find a **purple screen with a Man=keyboard** sign at the bottom of the screen:

1)At that screen you hit **Enter**...
it gives you a next screen where by default you will get a list of languages with English selected as default..

2)on that screen select English/or what you want---> hit enter... It will get you the Try Ubuntu/Install Ubuntu Screen

at the bottom of the screen you will see options underneath F1 F2 F3 etc.. ... **Hit F6** on that screen.. 
You will see a **pop up Box** at the bottom of the screen... use the arrow keys to go down to: "**NOMODESET**" hit enter... **a small Cross(X) **will appear beside 'nomodeset'

3)Press escape

Then choose Try/Install 

Also, You might as well try with 13.04, which is the latest stable Ubuntu available !

BTW, All 'nomodeset' does is, it stops installing the video drivers at the beginning...
Since you r using AMD, you may have to download proprietary drivers(Once   installed) to get the right screen resolution & all.... 

Are you sure itz not an UEFI problem?
Best of Luck, and do let know how it turns up!

---

### Post by john_jackson2 on 2013-08-23
I've tried Ubuntu 12.04 And Ubuntu 13.04 on the USB boot and also installing from hard-drive. The problem is, I never get a purple screen. I only get a black idle screen, the fan kicks up but it seems like its doing nothing.

As requested Graphics Card: AMD Radeon HD 7310

Thanks for the replies! I might try some more, but I don't know if they will work..

---

### Post by su:bhatta on 2013-08-24
Hi, what I don't understand is how did you install if all you get is the black screen?

---

### Post by Jonathan Precise on 2013-08-24
> **bhattabhishek said:**
> Have you actually been able to install Ubuntu on that system once?
...
On the first boot from the Ubuntu DVD you will find a **purple screen with a Man=keyboard** sign at the bottom of the screen...



I have installed ubuntu on a laptop with UEFI, and the **purple screen with a "Man=keyboard" sign** doesn't show up. Instead, a Grub-2 Menu shows up:

[IMG]http://pix.toile-libre.org/upload/original/1347445084.png[/IMG]
This is normal, and just means that the DVD/USB is booting in EFI mode (used in windows 8). Select your preferred option, but **DO NOT PRESS ENTER!!!!!!!!!!** Instead, press 'e' (with no quotes). Then add 'nomodeset' (again, without quotes) at the end. Then press F10. That (should) get you up-and-running!

---

### Post by su:bhatta on 2013-08-26
> **Jonathan Precise said:**
> I have installed ubuntu on a laptop with UEFI, and the **purple screen with a "Man=keyboard" sign** doesn't show up. 

The Op says all he gets is a 'Black Idle Screen', not a purple, neither the Grub screen,

Wonder how he installed from thereon...

---

### Post by john_jackson2 on 2013-08-26
I installed from my harddrive the second time..

I got it to work. I changed my settings in the BIOS menu to no fast boot, something other then EUFI mode, and to boot USB first. I tried to split my hard-drive but accidentally unallocated all memory so I didn't end up dual booting.. as my computer didn't recognize the other OS after that.

---

