---
title: "Noob can't get External Hard drive working"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by Cjmkee on 2008-09-25
Hey guys I am very new to Linux and can't get my external hard drive working. I posted this thread under the Hardware section but I figured since I am new maybe I should post it here instead. 

I can't get my Western Digital external hard drive to mount on Ubuntu Hardy. I have been searching forums and websites all day trying different things. Most of the post I found are about External Hard drives or USBs being seen but not auto mounting. My problem is it seems like it's not even recognizing that there is a hard drive plugged into the USB port. I have tried mounting it using terminal (ie making a directory then mounting it) but that doesn't work. I don't really have any experience with command line work so I don't feel very confident that I am doing it correctly. 

Help from other thread: I was told to run lsusb in Terminal to see if the computer recognizes the drive, I did and it does not see the drive in either port. 

Does anyone else have any ideas?

---

### Post by callan79 on 2008-09-25
> **Cjmkee said:**
> I was told to run lsusb in Terminal to see if the computer recognizes the drive, I did and it does not see the drive in either port.

Suggest you run lsusb and note the output. Then plug the HDD in, turn it on, run lsusb again. Anything new show up?

If so, great we can move to the ext step.

If not, can you confirm that other USB devices work in that port?

Also, i terminal, ```
tail -f /var/log/messages
``` might help you find out what's going on.

Will wait for results :)

Callan

---

### Post by bigken on 2008-09-25
if its formated to ntfs go to aplplication add/remove and install NTFS Configuration Tool

---

### Post by Cjmkee on 2008-09-25
Ok this blows my mind...I have been trying for 2 days now to get it to connect and it would never recognize the drive. I unsuspend the machine, run lsusb with out it plugged in and its blank, I plug in the drive, run lsusb and its there now!! So it is now seeing the drive, what is the next step? and why do you think all of a sudden it sees it? 

On a side note, I noticed you are in Adelaide I did a study abroad there my jr year at UniSA. You Aussies are a lot of fun

---

### Post by Cjmkee on 2008-09-25
OK I just unplugged the drive, and plugged it back in to try again, ran lsusb, and it is not there anymore. Why do you think it will sometimes see the drive in the USB port and sometimes it wont?

---

### Post by Tux.Ice on 2008-09-25
Do any other USB devices work in this port?

---

### Post by Cjmkee on 2008-09-25
No, no USB drives have been recognized when I plug them in. When I plug in one with the light on it it just blinks rapidly and nothing happens.

---

### Post by Cjmkee on 2008-09-25
Ohh and BigKen...Unfortunately, I work at a Nuc Plant and can't connect my laptop (the machine with linux on it) to the internet here. But when I get home I will try installing the NTFS Configuration Tool 

and yes the Drive is formatted as NTFS

---

### Post by groundshaker on 2008-09-25
I had the same problem,also tryed with force mount

1.sudo mount -t ntfs-3g -o force /dev/sdb1 /mnt
2.sudo umount /mnt

but it didn't worked,then i plugged the Ext HD in to windows pc,clicked on remove hardware safely ... and i plugged it back in to my ubuntu pc and it worked without any problem.

---

### Post by Cjmkee on 2008-09-25
I plugged it back into the Windows machine, safely removed it, and it still is not recognized by linux. I am beginning to wonder if the HD isn't a figment of my imagination lol.

Any other suggestions guys?

---

### Post by callan79 on 2008-09-25
> **Cjmkee said:**
> I plugged it back into the Windows machine, safely removed it, and it still is not recognized by linux.


When you do this, does /var/log/messages or /var/log/syslog show anything useful?

The last NTFS drive I used had been UN-safely removed from Windows, and would not mount. I only found this out by looking in the logs, and saw all this output about unclean file system etc.

What do your log files (messages and syslog) say?

If you do a "tail -f" on these files, then as new log data is written your screen will refresh, so you can see exactly what's happening right as you connect the drive.

Cheers
Callan

---

### Post by Cjmkee on 2008-09-28
When I try those commands it says Permission Denied. I tried loggin in as Root and it still says permission denied. Also when I do lsusb it doesn't show that my usb is plugged in. what do you recommend next. Sorry about not replying right away, I have been out of town. Thanks for the help so far though.

---

