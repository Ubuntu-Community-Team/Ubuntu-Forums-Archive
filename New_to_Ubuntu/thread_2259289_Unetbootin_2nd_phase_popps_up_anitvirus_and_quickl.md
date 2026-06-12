---
title: "Unetbootin 2nd phase popps up anitvirus and quickly not responding"
date: 2015-01-03
forum: New to Ubuntu
---

### Post by doit2 on 2015-01-03
Hello,

Im almost a week in dedicating hours to change the OS in two of my computers, and achive 0 progress. I decided to open a new thread regarding this minor issue, so i can get at least some progress. Actually, i say 0 progress but i almost had a big regression, when putting Ubuntu on a USB using [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows) which didn't mention this may erase everything on it.

Trying to be very careful i took advice here, but up until now, as i say, we are at ground 0 because i couldn't back up one computer and couldn't find out how to check the backup in the other one. It's all in this thread:
[http://ubuntuforums.org/showthread.php?t=2258720](http://ubuntuforums.org/showthread.php?t=2258720)

Out of frustration i decided the hell with backing up the old computer, and just go check Ubuntu on it directly. This time i used "Unetbootin" as recommended here. I also used this tutorial which i find quite useful, It explains things the way a child could do it:
[https://www.youtube.com/watch?v=rvsDHM68jM8](https://www.youtube.com/watch?v=rvsDHM68jM8)

I did everything the way this guy described and eventually got to the 4th Phase ("Installation complete, Reboot.") but not without trouble. The first time Avira antivirus popped and blocked one autorun file during extraction (2nd phase), quickly causing the operation to not respond. on the second time the blocking reoccurred but the extraction was eventually complete.

Now because i became really afraid of doing something wrong that will harm my computers, i wish to know what happened and should i continue testing this USB on my old Asus EEE notepad?

To help you guys help me, i attached the the warning avira wrote, twice during the extraction:

---

### Post by yancek on 2015-01-03
Your Avira anti-virus probably doesn't know anything about Linux so I don't think that would be a problem.  If I understand correctly, you apparently finished the install of Ubuntu using the unetbootin software, is that correct?  If so, you should be able to either re-boot the computer with the flash in and enter setup (BIOS) and set the usb drive to first boot priority and boot.  If you are really paranoid and want to test it on another older computer, use the same process to boot the flash and see what happens.  If the install with unetbootin is not successful, you will usually get some type of error message.

---

### Post by doit2 on 2015-01-03
Yes i wish to try it out on the old computer, to revive it and test the LIVE VERSION first.
I reached Bios using F2, but the got "cold feet" as the boot priority didn't mention Ubuntu but used "cruzer disk" instead. I pulled out of BIOS as quick as possible.
If i would set "cruzer disk" prior to the current setting, should i still be able to get the live version (which i understood doesn't delete anything and able me to just run a test?)

thank you!

---

### Post by Bucky Ball on 2015-01-03
If you have installed to a USB or burnt the ISO image to USB with Unetbootin, the cruzer disk IS Ubuntu. BIOS will not see it or list it as Ubuntu.

Back to the BIOS and make the Cruzer the first boot device and tell us how you go.

---

### Post by doit2 on 2015-01-03
Ok **IT DIDNT WORK!** i went into BIOS and pressed
BOOT
BOOT DEVICE PRIORITY
and then set it to
1st: Usb: SanDisk Cruzer
2nd: Removable Device
3rd: HDD:PM-ST9250... (which i guess is windows?)

But nothing happened. Just took me to "Windows Error recovery" and loaded up windows as usual.

---

### Post by Bucky Ball on 2015-01-03
I had this problem on a machine of a friend's I was installing on. If you hit F12 at boot instead of whatever you hit to get to BIOS, does that give you a list of devices to boot? If so, choose the Cruzer there. That worked for me.

---

### Post by doit2 on 2015-01-03
Yes Yes! finally some progress!
So i selected "try ubuntu without installing" and got to the desktop
I have no mouse cruser and it seems Ubuntu can't read my touchpad yet
so i can only rotate by using Alt (which brings me to "commends")
But that's about it.
1. What shell i do from here? I remind that my wish for the live version is to test weather everything work normally before i go all the way with Ubuntu.
2. If i plug out the USB, should everything return to it's old nature?

---

### Post by doit2 on 2015-01-03
Im very exited to finally explore just a little bit of Ubuntu.

I have been able to cruse around with the alt/tab, and had trouble connecting to Wi-Fi. The computer found my Router, but as i pressed it immediately an Error screen appears. I will upload the exact Error later.

---

### Post by Bucky Ball on 2015-01-03
Errors with wifi on a Live boot are not unusual. You probably need a third-party driver for the card, which you would be able to install once Ubuntu is installed to the hard drive. 

If you can manage to open a terminal, type in:

```
sudo lshw -C network
```

... and take note of the 'Network Controller'. That will tell you what kind of wifi chip you have. Let us know. You should be able to get online with a cable fine, though.

Also, what mouse are you using? Generic or fancy one? I'm not familiar with the setup of a straight Ubuntu install, but you might be able to get them going by heading to settings and looking for 'Touchpad and mouse settings' or something like that. Someone familiar with Ubuntu config might be able to elucidate ...

---

### Post by doit2 on 2015-01-20
Hello again,
After the bit of progress i made, i took some rest from Linux.
Now i had some time to continue with connecting the ASUS harware and Ubuntu
But all of a sudden i can't get to BIOS again. Windows comes up automatically, even without the page where i would press F12.
The USB stick is inside, what shell i check?

---

### Post by Jonathan Precise on 2015-01-20
Hello doit2.

I personally have had many problems with Unetbootin. If you're in Windows, try [Linux Live USB Creator]("http://www.linuxliveusb.com/") (LiLi, I personally recommend this one as long as you don't use virtualization) or Pendrive Linux, but beware that with any of them, it **will** erase anything you have in your USB.

---

### Post by Bucky Ball on 2015-01-21
> **Jonathan Precise said:**
> ... beware that with any of them, it **will** erase anything you have in your USB.

You SHOULD erase everything on the USB before using UNetbootin or anything else. If you're not, then that could be the issue. Format the USB to FAT32 then try. Problem is, if you have a file on the USB and then chuck on the Ubuntu ISO, that file will still be there. Causes major headaches. You want to start with a clean, wiped, freshly formatted USB stick, then burn the image to it. (Even having one photo file on the stick will cause probs ... wipe it all clean.) ;)

---

### Post by Jonathan Precise on 2015-01-22
> **Bucky Ball said:**
> You SHOULD erase everything on the USB before using UNetbootin or anything else. If you're not, then that could be the issue. Format the USB to FAT32 then try. Problem is, if you have a file on the USB and then chuck on the Ubuntu ISO, that file will still be there. Causes major headaches. You want to start with a clean, wiped, freshly formatted USB stick, then burn the image to it. (Even having one photo file on the stick will cause probs ... wipe it all clean.) ;)

Yes, it actually is very true that putting a file afterwards or not formatting the USB before turns into a headache, but I'm just warning the OP that he/she shouldn't have any valuable info there that he/she can't afford getting erased, just in case.

Regards.

---

### Post by doit2 on 2015-01-24
Well yes, i think i did the mounting properly. it was already a minor success, as it entered Ubuntu and i could cruse around in it a little. But since then, i can't get to BIOS and it automatically directs me to windows. Shell i format the USB once again?

---

### Post by Jonathan Precise on 2015-01-25
> **doit2 said:**
> Well yes, i think i did the mounting properly. it was already a minor success, as it entered Ubuntu and i could cruse around in it a little. But since then, i can't get to BIOS and it automatically directs me to windows. Shell i format the USB once again?

Well, as log as you don't have anything there that can't be erased, give it a shot. But PLEASE don't use Unetbootin, as it causes too many headaches, not only with me, but I've also seen videos when they can't boot Ubuntu with Unetbootin at all, and they just use another program. Use [LiLi USB Creator]("http://www.linuxliveusb.com/") without the virtualization option, and you should be good.

---

### Post by sammiev on 2015-01-25
As of late UNetbootin has been a pain in my back side and I have used it forever without having problems. I now use [MKUSB]("https://help.ubuntu.com/community/mkusb/v9") and it works perfectly.

---

