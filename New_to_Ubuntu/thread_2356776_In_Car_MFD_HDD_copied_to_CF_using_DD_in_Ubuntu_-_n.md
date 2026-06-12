---
title: "In Car MFD HDD copied to CF using DD in Ubuntu - not booting"
date: 2017-03-27
forum: New to Ubuntu
---

### Post by vanwell on 2017-03-27
Hi Everyone,

I'm new to Linux (Ubuntu) and this forum but I'm loving playing around with and learning about this great OS. I've even ditched XP Pro off my old laptop and installed Ubuntu permanently. But most of the time, I'm using Ubuntu via a live USB on my new laptop that has Windows 10 installed.....

I'm hoping the collective wisdom can steer me in the right direction with my problem because I've already spent dozens of hours trying to figure it out and it's driving me mad. I will explain everything I have done to give you as much info and background as possible, to minimize the 'did you try this, did you do that' suggestions and hopefully get to the crux of the matter; although I realise with computers and software, there are many ways to skin a cat!

In my 2007 Peugeot 407 car I have a Magneti Marelli RT4 in car stereo/satnav/MFD with at it's heart, a Hitachi Endurastar 30GB HDD (IDE). The HDD has the latest firmware and works half the time.... because after 10 years, the HDD is starting to fail. Unfortunately, this means I can't use any functions from listening to music, radio, A/C controls, CD stacker, phone system, Sat Nav and the vehicle system info. It's a great system but 2007 is the changeover period when most car manufacturers went to Bluetooth systems. It would cost me thousands to modernise because most new units won't work with all the functions, like the steering wheel controls.

Many Peugeot owners have upgraded the failing 30GB HDD to a stable 32GB CF card with no problem whatsoever. Initially, I tried what they have all done via a thread on a Peugeot forum but that thread has gone cold (it was an old thread) and the info on it isn't helping me any further. The gist of it is -:

Remove RT4 30GB HDD (before it completely fails) 
Buy a new 32GB CF card, a CF to 44 pin IDE adapter (being careful to set it to 'slave'), an IDE to USB adapter and a CF card reader

Then most people (they are in Europe, I'm in Australia) install the blank CF card in the RT4, start the car, whereupon it asks 'insert upgrade CD' and takes 50mins to write the latest firmware and the 4 partitions the system uses. Then they copy all the data from the original HDD to Ubuntu (using a live USB) in it's 4 partitions, hook up the freshly partitioned CF card and carefully copy the files across to the correct partitions, and voila! insert the CF card back in the RT4 (with 44 pin adapter) and everything works again, sat nav maps, stored music, vehicle parameters, everything!

I don't have the Peugeot update CD, can't get one from a dealer and the ones I've tried to burn from internet torrents don't work. Never mind, because Ubuntu has DD! One of the Peugeot forum members did it like that, just cloned everything on the old HDD to the new CF card using DD on Ubuntu - but it hasn't worked for me!

Just a bit more background before I ask the collective advice - I tried copying everything on the HDD to the CF on my Windows 10 laptop with EaseUS. Then I found out that EaseUS still misses stuff. I then found How to Geek's excellent tutorial 'clone a HDD using Ubuntu live CD' using DD. So, I carefully formatted the CF card in Ubuntu back to FAT32 and one partition (selecting make compatible with most file systems). Shut down the computer. Re-started then hooked up the RT4 HDD and the newly formatted CF card and typed in the Terminal sudo fdisk -l
up popped the HDD with it's 4 partitions /dev/sdc 1-4, and the CF card /dev/sdd
I then typed (very carefully) sudo dd if=/dev/sdc of=/dev/sdd
after about 2 hours, I got the xxxxxxx records in xxxxxxx records out, xGB copied popping up. Looking good....
I then typed sudo fdisk -l and there in front of me were two exact same drives (one sdc, one sdd) with identical partitions and data
I then went to 'disc' and checked that the newly copied CF card had the same partitions and they were the same (1st boot partition FAT16, second Fat32, third FAT16, fourth FAT32. Exactly the same as the original.
I pop the CF card back into the RT4 (with adapter) and nothing...... well, the initial Peugeot logo that always comes up and then black screen, reload, try again, reload, etc.
I've done this so many times, re-read the Peugeot forum, searched and read everything I can find on the net. Everyone on the Peugeot forum did this once with success. I'm going mental wondering what went wrong.
A couple more bits of info. One of the guys said his didn't work but then realised Ubuntu created extra 'trash' files. He said he needed to load the CF card into Windows to 'see' and delete these trash files, and it all worked. Well, when I load the original HDD and the freshly dd cloned CF card onto Windows 10, and go to disk manager, it shows the original HDD's 4 partitions, with 'healthy', GB data and FAT 32 (for some reason Windows 10 doesn't recognise the two FAT 16 partitions and just labels them FAT32) But the exact same partitions on the CF card come up with only the first partition showing a 'drive letter' and healthy, etc; the other 3 partitions are there but blank with no drive letter or anything at all. At the top of the page in disk manager, it lists all the partitions and their drive letters but again not the 3 'blank' partitions? This could just be a Windows 10 thing, but I mention it in case it is important. Finally, when I load up Ubuntu to double check again, there are both drives, identical, same exact parameters and data, files in the same order - an exact clone.

I hope that all makes sense. I know screen shots would probably help but no can do. At the end of the day, this should've worked, dozens of non-geek dudes have done it successfully first time and DD is a powerful copying (or cloning) tool that copies everything, including the firmware. Right? What am I missing? Maybe something like the chinese 44 pin CF to IDE adapter I bought on eBay is faulty?? I don't think so....but maybe.

I have triple checked everything. Yesterday, I plugged the original HDD back in the RT4 - booted right up (it hasn't totally failed yet). Oh, one last thing I tried. I loaded both old and new drives into Windows 10 again and opened up EaseUS. It recognised both drives, the respective 4 partitions, etc but in the front of the 3 partitions on the CF card that disk manager didn't show up, it had asterisks *??

---

### Post by sudodus on 2017-03-27
Welcome to the Ubuntu Forums :-)

It seems to me that you have done things correctly. You know that ***dd*** is powerful but also dangerous, and that you must check very carefully, that you get everything correct. Otherwise, you might destroy valuable data.

But maybe the CF card or the card adapter is not 100% reliable. Windows should not 'see' the original drive and cloned drive differently. dd copies (clones) every byte as it is, but what happens during the transfer via the interfaces and the adapter? It is also possible the the cloning process had not finished before you unplugged the card. You can make sure that all data in the buffers are written to the target drive with ***sync***.

***So either continue with dd and be very careful, or use [mkusb](https://help.ubuntu.com/community/mkusb), which wraps a safety belt around dd and also runs sync before finishing.***

Identify the source drive and the target drive (find the actual drive letters to replace x and y in the following command lines)

```
sudo lsblk -f
sudo parted -ls
```
Unmount all partitions that might be mounted on the source drive and the target drive
```
sudo umount /dev/sdx*
sudo umount /dev/sdy*
```
Clone (block size 4096 bytes will usually make it faster)
```
sudo dd if=/dev/sdx of=/dev/sdy bs=4096
```
Flush the buffers alias synchronize
```
sync
```

When the sync command has finished and the shell has returned to prompt, you can unplug the card and try again in the car.

If this does not work, I suggest that you try with another CF card or another card reader.

-o-

By the way, you might want to run Ubuntu or maybe the light-weight Lubuntu ***persistent live*** instead of live-only in your laptop. See the following links

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

---

### Post by vanwell on 2017-03-27
sudodus, thanks for the detailed reply. So, now I know that something either went wrong during the cloning process or there's hardware issues with adapter(s)/CF card, etc. because you have confirmed that Windows should equally 'see' both drives. Awesome!
I will try again using your suggestions and ending with the sync command.
And I will look at the links you provided to run Ubuntu in my newer Windows 10 laptop. I can't use my old laptop for the DD cloning process (which I have installed Ubuntu onto) because it doesn't power up the IDE drive via the usb slot - my newer laptop does. That's why I've been using the live usb.
Again, thanks so much for the guidance.

Oh, and just to elaborate, I already created a live usb using Unetbootin a while back and that's what I've been using on my new Windows 10 laptop - pressing F2 on startup and changing the secure boot, boot order sequence and UEFI to Legacy so I can 'try Ubuntu without installing'. However, my old laptop was clean other than having XP Pro installed, so I wasn't risking anything when I chose 'Erase the disk and install Ubuntu'. I figured that this is the perfect way to experiment and 'play' with Ubuntu. I already ran these -

sudo apt-get update
sudo apt-get dist-upgrade

and the command that gets rid of old kernels. As I said above, unfortunately I can't use this older laptop for the dd cloning because it doesn't give the IDE HDD enough juice via the usb input, to fire up. But that's cool..... good for the learning curve.

I'm going to order a new CF card reader and try again. I hope it isn't the CF card because those suckers aren't cheap......

---

### Post by sudodus on 2017-03-27
You might find that ***Lubuntu*** with a lighter desktop environment will work better in your old computer. It has the same basic gnu-linux tools under the hood, but the desktop environment and some application programs are suitable for older and weaker computers.

-o-

Did you finish trying to clone and finish with sync? Do that before buying new equipment. You could even try in another computer, if there is some kind of mismatch between your computer and the card reader.

Good luck :-)

---

### Post by vanwell on 2017-03-27
I just tried to use sync in the other (older) laptop. It's about 9 years old and came loaded with Vista; it's an Intel Celeron CPU 900 2.2GHz. I have since upgraded the RAM (4GB) and installed a bigger HDD (160GB) in it. I bought a CD copy of XP Pro on eBay to install on it to run some old software but no longer need XP for that, so have now installed Ubuntu, as above.
I just tried typing in sync with the CF card on this laptop. Nothing happened. I then typed the command sync /dev/sdb and got an error message (sdb is the CF card drive with the newly cloned data). So I stopped there because I didn't want to screw anything up.
Can I still 'sync' this CF card or has the horse bolted? I have ordered a new (and better quality) CF card reader because I remembered that I inserted the CF card upside down initially and bent 1 pin. I then straightened the pin and inserted the CF card correctly but maybe this is why there were cloning errors??!! When I get the new reader in the mail, I will retry from scratch with the CF card formatted using your advice above. 
Just a question about formatting the CF card - in Ubuntu (and on EaseUS) you can wipe it clean, no partition, no nothing. Last time, after doing that, I created 1 partition, set it as FAT 32 (the way the CF card came) and compatible with Most File Systems (to allow for the 2 x FAT16 partitions that are on the source HDD I want to clone).
Is that the correct way to format it? Or should I leave it blank, wiped clean? Wiped clean isn't 'read' by windows - plugging it in a usb port illicits no response from Windows as recognised drive. However, Ubuntu does 'see' it. Which way should I format the CF card to get it back to how it was 'out of the box'?

---

### Post by sudodus on 2017-03-28
> **vanwell said:**
> I just tried to use sync in the other (older) laptop. It's about 9 years old and came loaded with Vista; it's an Intel Celeron CPU 900 2.2GHz. I have since upgraded the RAM (4GB) and installed a bigger HDD (160GB) in it. I bought a CD copy of XP Pro on eBay to install on it to run some old software but no longer need XP for that, so have now installed Ubuntu, as above.
I just tried typing in sync with the CF card on this laptop. Nothing happened. I then typed the command sync /dev/sdb and got an error message (sdb is the CF card drive with the newly cloned data). So I stopped there because I didn't want to screw anything up.
Can I still 'sync' this CF card or has the horse bolted?

The correct command is ```
sync
``` (without any parameters) and it will synchronize whatever needs to be synced (flushed from buffers to drives). If nothing needs to be synced the command will finish quickly and the terminal window will return to prompt 'at once'.
> 
I have ordered a new (and better quality) CF card reader because I remembered that I inserted the CF card upside down initially and bent 1 pin. I then straightened the pin and inserted the CF card correctly but maybe this is why there were cloning errors??!! When I get the new reader in the mail, I will retry from scratch with the CF card formatted using your advice above. 
Just a question about formatting the CF card - in Ubuntu (and on EaseUS) you can wipe it clean, no partition, no nothing. Last time, after doing that, I created 1 partition, set it as FAT 32 (the way the CF card came) and compatible with Most File Systems (to allow for the 2 x FAT16 partitions that are on the source HDD I want to clone).
Is that the correct way to format it? Or should I leave it blank, wiped clean? Wiped clean isn't 'read' by windows - plugging it in a usb port illicits no response from Windows as recognised drive. However, Ubuntu does 'see' it. Which way should I format the CF card to get it back to how it was 'out of the box'?

***Cloning will overwrite whatever was written on the drive, so there is no need to format the drive before the cloning process.***

There is one thing to consider, that I forgot to mention before. If there is a GUID partition table, GPT, and the cloned copy has a different size (is bigger as in your case, 30 GB --> 32 GB), a backup partition table must be written separately at the very end of the drive. This can be done with ***gdisk***, or automatically with the script ***gpt-fix***, [http://phillw.net/isos/linux-tools/uefi-n-bios/gpt-fix](http://phillw.net/isos/linux-tools/uefi-n-bios/gpt-fix).

But if there is an MSDOS partition table, you need not worry about any backup partition table at the very end of the drive. The car (and the system on its hard disk drive) is from 2007, so I would guess it has an MSDOS partition table, but you had better check that. The following command line will show what it is:

```
sudo parted -ls
```

Look for a line in your local language, ```
Partition Table: msdos
``` or ```
Partition Table: gpt
```

---

### Post by vanwell on 2017-03-28
OK, I confirmed the source HDD (original car HDD) is **msdos** using

sudo parted -ls

it was displayed as you suggested above

Partition Table: msdos

---

### Post by sudodus on 2017-03-28
Good. You need ***not*** worry about any backup partition table at the very end of the drive :-)

---

### Post by vanwell on 2017-03-28
> **sudodus said:**
> Good. You need ***not*** worry about any backup partition table at the very end of the drive :-)


Great. When the new CF card reader arrives I will go again. 

I read the links you provided above regarding booting Ubuntu as 'persistent live', etc. I'm afraid at this stage that is way over my head ;)
I'm only a neophyte...... :confused:

ATM, I'll stick with booting from the live usb. All the other guys on the Peugeot forum did it that way without any problems.

---

### Post by vanwell on 2017-03-30
I'm still waiting for the new CF card reader to arrive in the mail and I also decided to buy another 'CF to IDE 44 pin adapter' in case it was faulty.
Doing a bit more research regarding Windows and the copied 4 partitions on the CF card, apparently it's common that Windows only recognizes 1 partition (which logically would be the 1st).
In any case, once the new hardware arrives, I will start again from scratch using the process you outlined. As a back up, I emailed a mate in Paris and asked if he could go to a Peugeot dealer and get an 'official' upgrade CD for the RT4 firmware...... that will be my last resort. I am so over trying to make this work but I do appreciate your help, sudodus.

---

### Post by vanwell on 2017-04-09
Well, new CF card reader arrived and I also bought a new CF to IDE 44 pin adapter for safe measure...... but nada. It still doesn't work and It's driving me crazy. I have a carefully cloned CF card - cloned by dd and when I compare the two drives in Ubuntu, they are exactly the same. Although, of course they can't be because the original HDD boots in the car and the CF card doesn't?

I suppose I could buy a refurbished 30GB HDD (like the original) and dry copying (cloning using dd) to it? What do you think? Any other ideas?

---

### Post by sudodus on 2017-04-17
It's too bad that the CF card does not boot. It seems to me that you have cloned in the correct way. Maybe the problem is how the CF card is connected in the car (the adapter).

It should work with a cloned HDD or SSD of exactly the same storage size or bigger (not one single byte smaller) and of the same form factor (geometrically) and with the same sector size, so that it can be plugged in to replace the old HDD.

I think that you are trying hard enough and you will succeed sooner or later, I hope and wish sooner :-)

---

### Post by vanwell on 2017-04-25
OK, it's been a while and in short nothing I have tried is working regards copying the original HDD to a CF card. So, I have bought a refurbished 30GB IDE HDD on eBay which is the same type as the original. It's being sent from Germany but hopefully it will be a straight forward HDD to HDD copy?
Do you recommend I copy (clone) the HDD to the new HDD using dd as I have been trying with the CF card? Anything different I should do regarding formatting or whatever. Or just let dd do it's thing.
This has gotta work now, surely!

---

### Post by sudodus on 2017-04-26
Try with [Clonezilla](clonezilla.org) (safer) or with dd (which you know already). Clone the whole drive (not separate partitions). Double-check, that everything is correct before you start the cloning operation.

---

### Post by vanwell on 2017-04-26
> **sudodus said:**
> Try with [Clonezilla]("http://clonezilla.org") (safer) or with dd (which you know already). Clone the whole drive (not separate partitions). Double-check, that everything is correct before you start the cloning operation.

OK will do. I will report back hopefully with a success story.....  ;)

---

### Post by vanwell on 2017-05-20
OK, I have success but not with all of the above, unfortunately....... The CF card was just not working for me.
I ended up buying a refurbished 30gb IDE HDD on eBay (they are hard to find these days) and copying everything over to it. I stuck it in the RT4, put everything back in the car and voila! Thanks for all your help, sudodus!

---

### Post by sudodus on 2017-05-20
Congratulations and thanks for sharing your solution :KS

Finally, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

