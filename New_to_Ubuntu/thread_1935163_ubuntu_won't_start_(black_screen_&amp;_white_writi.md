---
title: "ubuntu won't start (black screen &amp; white writing)"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by epicer on 2012-03-03
Hi
My problem is whenever I try to start my laptop it brings up a black screen with white writing like this ;
       BusyBox v1.18.4 (unbunta 1:1.28.4-2ubuntu) built-shell (ash)
       Enter 'help' for a list of built-in commands.
       (initramfs)

I don't know alot about computers so any help and I will be really grateful
P.s I'm a beginner so things will have to be made simple for me to understand.
Thanks.
Epicer

---

### Post by MG&amp;TL on 2012-03-03
For some reason, something's gone badly wrong in Ubuntu (I guess you could have guessed that!). What hardware do you have?

---

### Post by epicer on 2012-03-03
Sorry like I said I haven't got a clue about computer
All I know is that its a packard bell laptop with ubuntu

---

### Post by MG&amp;TL on 2012-03-03
Okay, are you experiencing this problem immediately after installation, or after the OS had been working?

---

### Post by epicer on 2012-03-03
It was working perfectly before

---

### Post by nd456 on 2012-03-03
> **MG&TL said:**
> For some reason, something's gone badly wrong in Ubuntu (I guess you could have guessed that!). What hardware do you have?

Turn your computer upside down and look on the bottom for a model...

---

### Post by MG&amp;TL on 2012-03-04
> **epicer said:**
> It was working perfectly before

Okay, did you update anything, install anything new?

---

### Post by epicer on 2012-03-05
Not that I'm aware of but I could have updated from the update manager. At the bottom it says ALP - HORUS G
Also my friend says its a Intel pentium
dual core cpu t2390 that had windows vista installed
but was changed to ubuntu.

---

### Post by MG&amp;TL on 2012-03-05
Well, BusyBox is an application that launches when the OS is seriously in trouble. Something has gone badly wrong, and I don't think any of us here can do anything to fix it as such. (I could be wrong here folks!)

My advice is to burn a live CD of Ubuntu, copy your files off your hard drive (open the file manager, press the "file system"  button at the side, open /home, then copy anything in there to a USB or your backup medium of choice.  Then install Ubuntu over your broken Ubuntu, and now it should be good as new. Then copy your backed up files to your hard drive.

---

### Post by nd456 on 2012-03-05
> **MG&TL said:**
> Well, BusyBox is an application that launches when the OS is seriously in trouble. Something has gone badly wrong, and I don't think any of us here can do anything to fix it as such. (I could be wrong here folks!)

My advice is to burn a live CD of Ubuntu, copy your files off your hard drive (open the file manager, press the "file system"  button at the side, open /home, then copy anything in there to a USB or your backup medium of choice.  Then install Ubuntu over your broken Ubuntu, and now it should be good as new. Then copy your backed up files to your hard drive.
I have to agree, with even a Ubuntu expert, it would be extremely difficult to fix. Sometimes it's just easier to reformat.

---

### Post by bedpotato on 2012-03-05
Before you do anything drastic, wait for PM. :) I had this same problem and someone kind fixed it for me with loads of complicated patient instructions via PM, so I will copy them to you for you to try as well (or, with the user's permission, maybe post them on this thread).

---

### Post by bedpotato on 2012-03-06
Here are the first set of instructions PMd to me by winh8r. This first set of instructions did not work for me but they may work for other people - who knows?

>  Lets try this for a start:

switch on the computer

keep tapping on the "shift " key as it tries to start up.

This should bring you to a black screen with a box of text in it.

there should be entries for Ubuntu near the top of the list.

I would say that the second option probably has all the ubuntu stuff , kernel version etc and then the words "recovery mode" written in brackets after it.

You need to use the "arrow" keys on your keyboard to move the highlighter onto this entry with recovery mode written beside it, then when it is highlighted press "enter" on your keyboard.

The system will reboot and it should bring you to a screen with another menu.

Use the arrow keys again and select the entry that reads "update grub bootloader" or something along those lines. when it is selected hit enter and it will update the grub bootloader.

It should take you back to the same menu again and you can select "repair broken packages" and hit enter . NOTE you will need to have an internet connection available for it to do this , but run it anyway.

Once you have done these steps you need to select "resume normal boot" and hit enter. and it should hopefully reboot and be working again.

If at any point you get dropped to a text only screen with a flashing cursor (like a big terminal screen) just enter your username at the prompt and hit enter, then enter your password at the next one and hit enter. this will log you in.
then just type these commands:

sudo update-grub


hit enter

(it will ask you for your password)

then when it has done that enter the following command:

sudo reboot now

(hit enter, and again it will ask for your password,before rebooting the computer)

This should fix the issue, as I dont think you have any issues with graphics cards since you have had a couple of normal sessions already.

(that last part was only relevant to me, but possibly to you as well)

Try these instructions first. Hopefully it will fix it but I'll post more of winh8r's other directions below in a minute.

---

### Post by bedpotato on 2012-03-06
Here are some more instructions from the helpful winh8r:

>  Here is what we will try now.

get your Ubuntu live CD.

put it in the drive and restart the computer.

let it boot up and select "try Ubuntu" and let it get to a desktop.

now on ubuntu 11.10 you need to go to the Dashboard search box and type in "Disk Utility" and open it.

You need to select your Hard Disk from the menu on the left, it will say something like "80Gb Hard Disk" with a reference code below it.

Click on it and a window will open with a big rectangular box in the middle that should have something like "80GB ext4" written in it.

Anyway , look at the top right of the window and you will see some information in the right hand column. What you are looking for is the "Device" and the name that is written after it, it will appear as something like /dev/sda but it might be a different letter than "a", write the name of the device down as it is /dev/sda or whatever.

Once you have done this you can close Disk Utility.

You need to open a terminal now which you can do by pressing Control + Alt + T 
When the terminal opens you need to type in the following command as it is , up to the bit where it says /dev/sda, you need to type in whatever you wrote down a moment ago in place of the bit that says /dev/sda. I hope that this is clear enough, I just re-read it and it might be a bit confusing.


Anyway, the command you need is as follows:


sudo e2fsck -C0 -p -f -v /dev/sda

Once it is in the terminal hit enter and let it run.
It should not give any error messages.

If it does say something about manual e2fsck then run the following command, but only if it asks you to:


e2fsck /dev/sda

again replacing the /dev/sda with your device name.

Once this is all done you can shutdown the live cd and remove it from the drive, then restart your computer.

Hopefully it will boot successfully and when it does you need to open a terminal and type in


sudo update-grub

it will ask for your password and then it will run a grub bootloader update .

once that has finished it would be best to run 

sudo apt-get update

Hopefully this will solve your problem. 

---

### Post by bedpotato on 2012-03-06
The above instructions only worked for me up to a certain point. I got a funny error message saying something about something-or-other being mounted. This is what winh8r said to do next, but it may not be applicable to others with the same problem, if they are able to do all the above (I wasn't.) You may not get the error message because your computer is different to mine.

So, fellow newbies - do not go typing things into terminals without checking with an expert if the commands are applicable to YOU! 

Please note I AM NOT AN EXPERT and don't know what these things mean, but the things being pasted here did solve my problem. 

Here's what I did next as instructed by winh8r.

Only do this if you are unable to complete the above instructions due to something-or-other being mounted. 




>  Ok lets try this method:


run the live cd

open a terminal and enter:

sudo fdisk -l

this should give you an output something like this:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00023337

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19202   154234880   83  Linux
/dev/sda2           19202       19458     2053121    5  Extended
/dev/sda5           19202       19458     2053120   82  Linux swap / Solaris
now the first entry above is in my system and shows as /dev/sda1 and it is marked as the boot partition by the little * in the column named "boot"

this is the partition we need to find on your system.
So whatever is listed with the little * in it is the name you need to use for the following command.


umount /dev/-whatever-yours-says

this should tell you that the device is not mounted, which is exactly what we want.

now you can enter the following:


sudo e2fsck -f -p -C0 /dev/as-you-entered-above

this will run a check on the file system and automatically repair any errors it finds.

Once it is finished, 

type in :


sudo update-grub

there should be no errors.

once this is done ,shutdown the live cd and remove it from the drive then restart your computer.

If it does not boot first time, try tapping the "shift" key under the enter key from when you switch it on and get to the GRUB Boot Menu like yesterday, (the black and white screen)

Select the Ubuntu entry nearest the top with "RECOVERY MODE" written beside it and hit enter.

then use the arrow keys to select the "update grub bootloader" option and hit enter.

once this has completed select "resume normal boot from the menu and hit enter again.

the computer should reboot and start normally.

Hopefully! 

It worked!

Hooray!
Everyone give winh8r a big round of applause and a medal!

---

### Post by epicer on 2012-03-06
> **bedpotato said:**
> Here are the first set of instructions PMd to me by winh8r. This first set of instructions did not work for me but they may work for other people - who knows?



(that last part was only relevant to me, but possibly to you as well)

Try these instructions first. Hopefully it will fix it but I'll post more of winh8r's other directions below in a minute.


Thank You so much this worked also thanks everyone for the help:)

---

### Post by epicer on 2012-03-06
Thanks everyone this has now been solved by bedpotato and winh8r

also thanks to everyone else that chipped in any potential help im 
very grateful and you've all saved me time and money.:D:D:D

---

### Post by MG&amp;TL on 2012-03-06
Brilliant! Glad you got it sorted.

Question for bedpotato-you can do an fsck directly through recovery mode, why do you need a live cd and messing around with fdisk to see if which partition you're on if it will do it for you? Just something for the future if I'm right. Or if you need specialised fsck (e2fsck), you can do that through the root console. But hey, whatever works. :)

---

### Post by bedpotato on 2012-03-06
> **MG&TL said:**
> 

Question for bedpotato-you can do an fsck directly through recovery mode, why do you need a live cd and messing around with fdisk to see if which partition you're on if it will do it for you? )

Well...

As I already explained, (edit: or at least, I thought I did, but I apologise if I haven't) I could not access recovery mode.  It was showing up as an option, but when I selected it I just kept getting back to a frozen screen again.

Therefore, Winh8r's first set of instructions did not work for me, but I posted them here in case they worked for anybody else.

For those who can access recovery mode, they can ignore all the extra (more complicated) instructions and simply do it the first way (as did Epicer).

Hope this explains things. :)

---

