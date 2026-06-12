---
title: "Device Name in VLC?"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by cpeachey on 2008-04-23
I have installed VLC to play my DVD's. The dvd launches VLC but I do not know how to make it play! In "open" "device name" the entry is /dev/hdc
Is this right for 1 of my 2 DVD drives?
Chris
Ubuntu 7.1 since last week!

---

### Post by riven0 on 2008-04-23
First thing is to check where the kernel sees your your dvd drive. So open the terminal and copy and paste this command:

**cat /etc/fstab**


You should see an entry for a dvd drive. Something like /dev/hdc0 or something similar. That's the drive you want. If it still doesn't work, make sure the propriety codecs are installed correctly.

---

### Post by cpeachey on 2008-04-23
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

Looks like the entry is correct. So how do I launch the film?
(I did try Totem which launched the DVD OK and tried to play it but it would not. The Forum consensus was that VLC was best.
Chris

---

### Post by riven0 on 2008-04-23
Alright, looks good. So, do you have the codecs installed? First thing, go to System > Administration > Software Sources and make sure all the repositories are checked, including the Restricted and non-free. Then click Ok and Reload when it asks. Then, open the terminal and copy and paste these commands: 

**sudo apt-get install libdvdcss2 libdvdread3**

**sudo /usr/share/doc/libdvdread3/install-css.sh**

OR, if that doesn't work:

**sudo /usr/share/doc/libdvdread3/examples/install-css.sh**

If you still can't play the dvd, try this command:

**sudo apt-get install ubuntu-restricted-extras**

That may or may not work.

---

### Post by cpeachey on 2008-04-23
Thanks for your help. Still no go. I will try again another time.
Chris

---

### Post by natirips on 2008-04-23
Try going to Add/Remove programs and try looking under Audio and Video for something that sounds good. There is a possibility you can find some program that doesn't require codecs (has them integrated). Although, so far as I know, VLC also has numerous codecs integrated...
And yes, preferably look for programs that have an option to open DVDs from the hard drive, this way you can manually open a DVD from your DVD drive in the same manner as you would from your HD, thus avoiding the case when the program wouldn't detect your DVD drive as an acctual DVD drive. Acctually, you didn't have to read all this nonsense :).

---

