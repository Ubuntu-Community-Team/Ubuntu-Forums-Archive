---
title: "External hd not mounting"
date: 2012-08-21
forum: New to Ubuntu
---

### Post by 1994mattmichael on 2012-08-21
GUYS,I AM NEW TO UBUNTU.....I HAVE A EXTERNAL HD.....IT USED TO WORK PERFECTLY IN UBUNTU UNTIL ONE DAY I HAD TO EXIT IT URGENTLY...AFTER THAT IT IS NT MOUNTING....IT IS WORKIN =G IN WINDOWS...BUT I NEED TO USE IT IN UBUNTU SO BADLY......WHEN IT IS PLUGGED FOLLOWING MESSGAE IS SHOWN....AM NEW TO UBUNTU....URGENT HELP NEEDED.

Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdc1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.


HELP NEEDED URGENTLY.....!!!

---

### Post by nothingspecial on 2012-08-21
Prefix changed from lubuntu to ubuntu.

---

### Post by 1994mattmichael on 2012-08-21
SRY...I DONT GET U,,,,,newwibie to  ubuntu :(

---

### Post by rukiaEnix on 2012-08-21
Well, you should try first what the message tells you, try the chkdsk.

Have you try mounting manually your device?

---

### Post by 1994mattmichael on 2012-08-21
chkdsk can be done in windows na???? well am nt available with windows now  :(

---

### Post by 1994mattmichael on 2012-08-21
and y is this message shown??? it used to work perfectly

---

### Post by rukiaEnix on 2012-08-21
Yes it its in windows... Have  you try mounting manually? Or how are you mounting the device? 

But I still think the best is to try chkdsk first.

---

### Post by 1994mattmichael on 2012-08-21
plz excuse me......how do u mean by mounting it manually?

---

### Post by rukiaEnix on 2012-08-21
With the mount command or do you just plug it in at appears in graphic mode?

---

### Post by 1994mattmichael on 2012-08-21
juz plug it in ma usb...dunno much abt command in ubuntu

---

### Post by rukiaEnix on 2012-08-21
OK, first of all create a new directory inside /media:

```

mkdir /media/new_dir

```

Then mount your device on that directory:

```

mount -t ntfs /dev/sdc1 /media/new_dir

```

The option -t is for specifying the filesystem type, I put NTFS but you should put the filesystem of your HD.

---

### Post by 1994mattmichael on 2012-08-22
Thank u......got it back...

---

### Post by 1994mattmichael on 2012-08-22
@rukiaEnix :guitar:

---

### Post by rukiaEnix on 2012-08-22
Did it work then?.... If yes, change the thread to solved and good to hear it works again. ;)

---

