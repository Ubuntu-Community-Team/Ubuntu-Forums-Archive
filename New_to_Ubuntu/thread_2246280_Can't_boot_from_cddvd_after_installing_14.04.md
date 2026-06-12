---
title: "Can't boot from cd/dvd after installing 14.04"
date: 2014-09-29
forum: New to Ubuntu
---

### Post by zombie3 on 2014-09-29
Hi and thanks for any help and also a cool OS. My laptop - HP pavillion notebook  pre-installed with windows 8 but updated to 8.1.My problem- I have just installed Ubuntu64 using dvd so i know its not a dvd issue also i have set the correct boot order and every other just to be sure although i knew it was pointless.When i first installed ubuntu it kept booting into windows which i fixed with the boot repair.Everything is running perfectly apart from i can not boot from disc.I was going to install mint on another partition but i can no longer install from disc.Just to let you know my disk drive works for everything else so its not that.I have googled but can't find a workable solution for laptop. Thanks for any help                                                                                                                     Zombie

---

### Post by snowmobiler on 2014-09-29
Not that I have an answer for you but I have a question. Is it just the Mint disk that won't boot. Have you tried booting from the Ubuntu disk (as if you were going to re-install)? Maybe its the Mint image that's bad.

---

### Post by zombie3 on 2014-09-29
Hi thanks.I've tried a windows 7,Ubuntu and the mint disk. Its quite annoying because if i get any serious problems and need to reinstall i am stuck.

---

### Post by zombie3 on 2014-09-29
I could wipe everything and start again but i fear doing so might not make any difference and i will be without an OS.

---

### Post by snowmobiler on 2014-09-29
does it do 'nothing' or does it boot into one of the others?

---

### Post by zombie3 on 2014-09-29
yeah it just goes to the OS choice screen Ubuntu or windows.It just ignores the boot from disc first option which i set in the bios

---

### Post by Forbees on 2014-09-29
to me it still sounds BIOS related.... i guess double check the BIOS see's the disk drive, make you save and exit, not just exist (dumb but i've done it before) a lot BIOS will give you a boot from option... so instead of hitting DEL or F2 to get in the BIOS, sometimes it's like F11 or F10 to open the boot menu, then you should be able to select the disk drive from there

you could always just go around and do a USB install but that doesn't really fix whatever is causing this... just sounds hard to believe installing ubuntu could do this lol

---

### Post by zombie3 on 2014-09-29
Hi forbees. I think it sounds BIOS related but changing the BIOS makes no difference.I save and exit.The boot from cd-rom is enabled. Secure boot is off. I've even pulled half my hair out.lol. The only changes i have made are 1-install ubuntu from dvd by setting boot order for dvd to boot first,which worked. Did a boot repair to get windows and ubuntu to show up in the loading screen.When i switch my pc on it loads the ubuntu pinky/purple screen which has 4 option 1 is Ubuntu 2 is boot options 3 is windows 8 and 4 is setup. It always skips booting from cd/dvd and goes straight to the pinky/purple screen.  I have read other forums with the same issue after installing ubuntu alongside windows but they are desktops and suggest removing the harddrive which isn't an option. I am unsure what to do now.I just hope someone who has had this problem sees this and knows what the issue is because one day i may be screwed. I know i can boot from usb but don't have one at the moment but others with this issue couldn't boot with either so i need a fix. Would a factory reset fix it or a BIOS update or rollback. I suspect wiping my harddrives won't make a difference but one day i will if i have to. I don't need to boot from disk now but i will one day. Thanks for any suggestions

---

### Post by zombie3 on 2014-09-29
this is the guide i used to install ubuntu [http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)    but i used a disc instead of a usb stick.

---

### Post by snowmobiler on 2014-09-30
try setting the bios back to normal (boot from HDD), then reboot the machine and then instead of going into the bios(f2), hit f12 to go to the boot menu and choose the dvd drive (one time boot change), see if it boots that way. something may have gone awry with the boot repair. this is the way I would do it always, not change the bios order.

---

### Post by zombie3 on 2014-09-30
I just tried a usb to test if i can install with it but it won't boot from usb or disc so i am screwed if anything goes wrong, I really cant understand how installing ubuntu can cause this.I wonder if hp are responsible.There is no advanced settings in the bios just the normal settings.I am really gutted. There doesn't seem to be a solution.  All the other threads on other sites about this problem have no solution.This is the type of problem that could make my laptop useless.

---

### Post by zombie3 on 2014-09-30
would turning legacy mode on in the bios help or would this cause more problems

---

### Post by snowmobiler on 2014-09-30
Have u tried what i suggested by using F12 and choosing boot from disc, not just setting the boot order to look for disc first?

---

### Post by zombie3 on 2014-10-01
hi sorry forgot to say i can't boot from f12 its quite frustrating now.I must have searched a hundred sites for any clue.Thanks for the suggestions its appreciated.I am waiting to see if HP can help shed some light on it but most their answers are vague at best.HP don't care kind of answer.This is a " computer says no!" moment.lol

---

### Post by Michael_McKenney on 2014-10-01
Usually on most boards you can hit F11 or F12 to change the boot device.  I would first check your BIOS to verify your DVD drive is in the boot order.  Set up legacy devices on to.   Verify your SATA controller that the DVD is enabled.   Does your device see any disks?

---

### Post by Vladlenin5000 on 2014-10-01
Is it me or this thread has become quite insane?

First of all, a comment:
- Under no circumstances an OS installation - any OS, single or dual-boot - can adversely affect the BIOS/UEFI in the way you're supposing it can. BIOS/UEFI runs BEFORE any other code.

Keeping that in mind, please try to select the optical drive (or any other you intend to boot) in the one-time boot menu as suggested. For that you need to timely press the assigned key depending on the system you have. **Such key is shown in the BIOS splash screen. It can be F12 or any other**. You MUST know which one either by attentively observing the boot process where it's shown or by RTFM, your choice.

In a nutshell, I see one problem here so far: The user.

---

### Post by zombie3 on 2014-10-01
Thanks for your  comment  Vladlenin. I installed ubuntu to my pc using a dvd everything installed fine. I am not a pc noob. Then i went to install Mint and it wouldn't boot. I have changed the boot order to make dvd first although originally if i put a bootable disc in it just boots straight away.  I did not change any settings until after i couldn't boot. I know the os shouldn't change any settings but that doesn't change the fact it won't boot from disc.  I can get to my bios screen

---

### Post by Vladlenin5000 on 2014-10-01
I'm not saying you're a PC noob. I'm saying you're a UEFI noob like most people. UEFI is at times an entirely new beast. Often optical drives don't behave like they use to at boot with the old BIOS.

Nevertheless, you were asked more than once - and I subscribe - to give the one-time boot selection menu a try just in case. This should help and the key you're looking for is **F9**: [http://h10010.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&tmp_geoLoc=true&docname=c01443326#N83](http://h10010.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&tmp_geoLoc=true&docname=c01443326#N83)

Also read and understand this, for now and for future reference: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by snowmobiler on 2014-10-01
Zombie, just out of curiosity, what is boot repair and why did you run it? You have Ubuntu running side by side w Windows, correct? Or on another drive? Seems like things went to pot after the boot repair. Almost sounds like its being forced to one spot. Don't know how old your pc is, but maybe look for a bios update that my undo the boot repair. I tried a dual boot (separate drives) w/ ubuntu and Win 7. but I did it in an odd way. My main drives are IDE (9yr old Dell 8300). But I didn't realize there was an acutal Sata port on my mobo. So I put in an old 80GB sata drive and used the molex power plug (the old drives have a covered slot for the 4 pronged power). But once I did that, even though I wanted the IDE drive running 7 to boot first, the PC defaulted to the Sata drive everytime, and I had the IDE drive listed 1st in the boot order (unless I hit f12 and chose the IDE drive).

---

### Post by zombie3 on 2014-10-01
hi i thought i answered the one time boot question earlier sorry but yes i've been pressing f9 almost every boot after changing settings but the only things that show up is Ubuntu and os manager. When i tried legacy mode the usb with mint had shown up and i could launch it but when i restarted the pc to check it was still working it had gone from the list.  Hi snowmobiler this is how i installed ubuntu i used boot repair as instructed in step 7 half way down the page.

---

### Post by zombie3 on 2014-10-01
Link to how i installed Ubuntu  [http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

---

### Post by snowmobiler on 2014-10-01
Well as I said, it all went downhill after the boot repair. Could be differences between Dell and HP. So I guess you have the options of having Ubuntu and 8.1 and nothing else or removing Ubuntu and starting over (or not). Crossing your fingers couldn't hurt either. Good luck!!

---

### Post by zombie3 on 2014-10-01
hi snowmobiler the crossed fingers helped.lol, i've kind of fixed it. I'll write down what i did for anyone who has the same issue with HP pavillion notebooks.First press F9 at boot then go to the option "Boot from EFI file" then click on your cd or usb option.Mine was labelled "no volume label" and then random letters with cd-rom near the end.I clicked it then clicked EFI then BOOT then BOOT64.exe. Then it loaded. I am now a happy chappy. It still won't work without me doing this procedure but hey it works. Note that i was using a dvd with Linux Mint on it so it may be slightly different depending on what os your trying to install but its basically the same. Thanks to all that offered help. I hope this helps somebody else. Now i am going to try find out why i cant boot a usb or dvd the usual way.  This is the first laptop i've had this issue with. Thanks all who helped

---

### Post by snowmobiler on 2014-10-01
cool beans! Even the guy who wrote outlined the procedure you followed had the disclaimer that it might not work for every system. So who knows how your HP reacted to the boot repair and bootloader fixing in windows. As long as you found the work around. Vlad should be happy now.

---

### Post by Vladlenin5000 on 2014-10-02
Yes, I'm happy indeed.

---

### Post by zombie3 on 2014-10-02
Lol. The truth is I'm bored  with windows and have been wanting to install ubuntu and mint for a long time so i may have thrown too much caution to the wind.Got there in the end though."Phew"

---

