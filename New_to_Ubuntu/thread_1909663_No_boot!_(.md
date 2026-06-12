---
title: "No boot! :("
date: 2012-01-15
forum: New to Ubuntu
---

### Post by bombz4 on 2012-01-15
Hi all, firstly huge apologies as I am new to ubuntu/linux and will obviously show being a noob!

My problem is that I attempted to install ubuntu alongside windows but installed it to an external hard drive (not windows drive). Since finally installing (and uninstall reinstall etc) I am met by the grub rescue (obv no boot!) I have read around a little and not found an answer! I used to have windows 7 (possibly not standard) and I have no boot disk to recover windows.

I have instead been getting to know ubuntu via disk! it seems great apart from I want the real thing working properly! I have ordered the original boot disk from my old house mate but will have to wait to recover windows. Is there a way that I can get this thing to boot now tho? I have tried reinstalling it with new partitions etc but i still get stuck at no working option but to go back to the disk.

Just to clear things i have changed bios to but from external hard drive and every other option but nothing will work! If some one could help it would be awesome as I know have pretty much no pc!

---

### Post by drs305 on 2012-01-15
Hi *bombz4*

Welcome to Ubuntu and the Ubuntu Forums.  :-)

If you have the LiveCD working, install the Boot Repair package and let it try to fix your Grub settings. If it can't get your Ubuntu OS to boot it may still restore operation of Windows.

You can get more information by clicking the "Boot Repair" link in my signature line.

---

### Post by bombz4 on 2012-01-15
Thanks for the quick reply! I'll get on it now:D

---

### Post by bombz4 on 2012-01-15
I dont think it is running properly, should it auto boot? I'm getting this at the end?


W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/Release  Unable to find expected entry 'restricted/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)

any ideas? Sorry to be so useless!

I have also just tried to install another boot program and got the same above error message, does my disk have a malformed file? confused!

---

### Post by drs305 on 2012-01-15
> **bombz4 said:**
> W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/Release  Unable to find expected entry 'restricted/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)

We were all new to Ubuntu/Linux at one time - no worries!

I'm not sure how you are booting but this message is from the file that looks for packages in the Ubuntu repositories. One of the listings is for the original installation CD. Normally the message is similar to what you posted and and the system is reporting that it can't find that CD (because it is not inserted). Your message is slightly different so I'm not sure if it's the same problem or not.

If it is because the original installation CD is not installed, you have two options:

1. If you are currently not using the CD-ROM during boot, insert the LiveCD you installed 11.10 with before you run the command that generates the error.

2. A better solution: Permanently correct this by changing the repository listings so that the system no longer looks for that LiveCD. In Ubuntu 11.10, you would click the Dash Home button (upper left corner of the screen), type 'Software Sources' and then click on the Software Sources link. 

On the Ubuntu Software tab, in the bottom section, untick/deselect the CD ROM option. Enter your password when asked for it.

This should remove the error about not finding the CD ROM. However, this error normally is produced when booting to a regular installation. I'm not sure if you are booting a Boot Repair disk or some other media. But if you are getting to an Ubuntu Desktop try the above and see if the error is corrected.

If you still get the error, please tell us how and what you are currently booting, and where it ends up (command prompt, Ubuntu Desktop, etc). If you are using a Boot Repair CD, I am not familiar with how the Boot Repair disc boots - I've only used it as an app installed from a running LiveCD or normal system.

---

### Post by bombz4 on 2012-01-18
After the umteenth reinstall I now have Ubuntu!!! I have lost windows, well it's there it just wont boot! But at least this half works:) Will now try to learn how to dual boot with windows on a different (internal) HDD

Thanks alot for the attempts to help drs305!

---

### Post by Double.J on 2012-01-18
Glad you have a working Ubuntu now bomz4 :D

Just bare in mind that once you fix the windows install with the windows disk, you'll have to go through the boot-repair steps advise by drs305 to get the multiboot working - those basically are the steps :)

In short
 - reinstall/fix windows on the first partitions of the drive.
repair ubuntu's boot loader - it should then auto detect the windows install and let you choose between them when you turn the machine on.

Best of luck!

---

### Post by bombz4 on 2012-01-18
Hi, thanks for that but it might not be so simple, I got the windows disk and I cant repair windows! There is apparently no system image and the auto repairs/back ups wont work! My only option now is to reinstall windows. Although now I have ubuntu working I can at least back everything up, move stuff around then reinstall windows. Im just a little unsure how the hell I get dual boot working, now ubuntu works, but I think once I install windows back to the internal HDD it will loos this boot, also at the moment I cant even see the ubuntu boot, after the first few start up screens the tv/monitor goes out of range untill the ubuntu log in!

I will figure it out though, I'm already hitting whiskey and lemonade in triumph of ubuntu working windows can wait!!:P

---

### Post by Double.J on 2012-01-18
Don't worry it's not too bad - you should be able to copy anything off of the windows partition using ubuntu then back up and reinstall as you say :)

to get dual boot running, have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1769482") as advised by drs305. If you can make a USB installer of ubuntu, run it and click "try" then copy and paste that long command in the thread into the terminal to get boot repair, if it's disk only use one of the links in the thread ;)

Just a bit of info for the future! Enjoy your drink - you have earned it :)

---

### Post by bombz4 on 2012-01-19
Thanks GNU I did enjoy my drink!

Ok my progress is that I am using an old laptop hard drive to store all useful windows items, big issue is that boot loader stops responding during system search, so I never get to the actual graphical interface (only the searching box). This pretty much leaves me no choice but to reinstall a clean windows, but as this will be on the internal HDD I have no idea if ubuntu will boot up once windows is installed or if I will finally get dual boot (I'm sort of hoping by changing the bios to search external then internal/windows or ubuntu will load). If not then I will have to partition the internal hard drive and install both systems to it following the guides.  
Will report back once I have ruined my PC yet again!
:popcorn:

---

### Post by bombz4 on 2012-01-20
Ok now I'm getting annoyed, today I have reinstalled windows created an 80gig partition and installed ubuntu, now the pc boots straight into ubuntu, fine. But inorder to use dual boot I am trying to get boot repair to run. Which it doesn't. terminal says it is installed, and clicking on it in unity makes me enter my password but never opens the file (no pic in side bar either). 

Anyone got any ideas now? I'm lost....

---

### Post by drs305 on 2012-01-20
> **bombz4 said:**
> Ok now I'm getting annoyed, today I have reinstalled windows created an 80gig partition and installed ubuntu, now the pc boots straight into ubuntu, fine. But inorder to use dual boot I am trying to get boot repair to run. Which it doesn't. terminal says it is installed, and clicking on it in unity makes me enter my password but never opens the file (no pic in side bar either). 

Anyone got any ideas now? I'm lost....

First, have you tried updating Grub after the installation? Sometimes running "sudo update-grub" after the installation will allow G2 to find Windows and include it in the menu. The first command will update Grub 2. Watch to see if os-prober runs and looks at other partitions during the update command execution. The second command will check to see if Windows is now included in the menu:
```
sudo update-grub
grep "Windows" /boot/grub/grub.cfg
```

As for running Boot Repair, see what messages you get (if any) when you try to open it from a terminal:
```
gksu boot-repair
```

---

### Post by bombz4 on 2012-01-20
Just for the sake of it, just had a slightly epic thought possibly this is working but the screen goes out of range when the boot begins, maybe i just cant see the option and the 10 sec wait kicks ubuntu in automatically!--- Maybe??? Anyway heres the terminal telling me windows is there!

bombz4@bombz4-P55-USB3:~$ sudo update-grub
[sudo] password for bombz4: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-15-generic
Found initrd image: /boot/initrd.img-3.0.0-15-generic
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

bombz4@bombz4-P55-USB3:~$ grep "Windows" /boot/grub/grub.cfg
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {

^ looking good

---

### Post by drs305 on 2012-01-20
> **bombz4 said:**
> Just for the sake of it, just had a slightly epic thought possibly this is working but the screen goes out of range when the boot begins, maybe i just cant see the option and the 10 sec wait kicks ubuntu in automatically!--- Maybe??? 
^ looking good

Yes, that is a possibility. Grub 2 has found Windows and added it to that OS's grub menu. If that is the OS that is controlling the boot, Windows should be in the menu. As you mention, scroll down if the screen is full and you don't see Windows in the menu (it looks like it will be the last entry).

---

### Post by bombz4 on 2012-01-20
Ok it all works! Almost! win7 loads up but ubuntu (since entering windows) doesn't. I get an error script thing saying monutall; plymouth     {ok} or something there about and it just waits for me to type into it.

I am back in ubuntu now but by booting the recovery and then opting for normal load in the first option. TBH i can live with this, but would be nice to sort out properly!

Either way thanks so much for helping me get this far!!

Already have more problems too, cant get dual monitors to run correctly in ubuntu one screen just goes nuts but I can just use one for now!

---

### Post by drs305 on 2012-01-20
> **bombz4 said:**
> Ok it all works! Almost! win7 loads up but ubuntu (since entering windows) doesn't. I get an error script thing saying monutall; plymouth     {ok} or something there about and it just waits for me to type into it.

I am back in ubuntu now but by booting the recovery and then opting for normal load in the first option. TBH i can live with this, but would be nice to sort out properly!

Either way thanks so much for helping me get this far!!

Already have more problems too, cant get dual monitors to run correctly in ubuntu one screen just goes nuts but I can just use one for now!

I'm happy you are at least making (some) progress. You are now venturing into areas on which I am less knowledgeable about.

I've looked at Google and you will probably find an answer applicable to your situation with "boot Plymouth mountall". There are lots of returns to limit the search to posts less than 6 months old.

Since your original title is 'no boot' you could continue here but if you don't get new responses and can't figure it out yourself you may have more success posting a new thread for each problem.

---

### Post by bombz4 on 2012-01-20
Yeah I realize that, I will worry about it again, for now its Friday night! Thanks again for your help! 
I have had a look on google and it seems quite a large topic that may take some figuring! but atleast I can safely boot into both in some way! I can finally unpack my old windows and return that to normal, and find out what ubuntu can do! :D

---

