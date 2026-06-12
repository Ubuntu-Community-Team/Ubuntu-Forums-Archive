---
title: "system crashed yet again"
date: 2013-11-16
forum: New to Ubuntu
---

### Post by okkie on 2013-11-16
my 10.04 Ubuntu crashed over night leaving among other the following messages which I think is important:

mounting /dev/mapper/ubuntu--vg-root on root failed. Also failed  /root/dev,/root/sys and/root/proc
mounting proc on /root/proc failed   no such file or directory.
no init found
init ; line352 :cant open /root/dev/console     No such file
kernel panic-not synching
attemted to kill init

I have no idea what all this means except that computer will not boot this morning.I have been trying to open a file with wine application and suspect that may be the reason.Also played a lot of music using VLC and tried to burn a data cd with brasero disk burner which was unsuccessful.
Only 10.04 installed on 1T disk and new 4 gig motherboard.
I thought I eventually had the ultimate system up and running after all these years till this happened just like with all the others since 2007.
Any help will do thanks. Pity I once again must use a windows machine to send this problem.

---

### Post by heir4c on 2013-11-16
Try boot-repair like suggested in the answer in this link:
[http://askubuntu.com/questions/272597/ubuntu-12-10-doesnt-load-after-grub](http://askubuntu.com/questions/272597/ubuntu-12-10-doesnt-load-after-grub)

10.04 is End of Live, so backup al your stuff and do a new install of 12.04 or try to do a upgrade from 10.04 to 12.04. I do never a upgrade but you can try it. But don't forget to do a backup.

---

### Post by Impavidus on 2013-11-16
Usually I upgrade, but if it is already broken a fresh install may be better. Also, directories like /root/dev and /root/sys sound suspicious. /dev and /sys exist directly under the / directory. /root is just the root user's home directory, which normally doesn't contain directories like those.

---

### Post by okkie on 2013-11-17
thanks so far, but how do I save everything if I cannot get into the computer?
computer will also not read an  Ubuntu disk

---

### Post by heir4c on 2013-11-17
Hardware problem? Bios battery? Bad memory?

For your data recovery try this (see it just 5 min. ago in a tread):
[http://www.addictivetips.com/windows-tips/redo-backup-recovery-live-cd-that-recovers-your-hard-drive/](http://www.addictivetips.com/windows-tips/redo-backup-recovery-live-cd-that-recovers-your-hard-drive/)

---

### Post by okkie on 2013-12-01
HOPE SOMEONE STILL READING!

I managed to get computer to read install disk, opted for reinstall saving all data and reinstall started.The process is however very slow but activity in the bottom of the install window is ongoing, fot over a week already. The data I am trying to save is in the region of about 45 gigg.
Is this the reason why the reinstall takes so long or am I wasting my time?

I tried boot repair and other things mentioned in the post above without success.
Is there any other way I can save my music photos and documents and do a complete reinstall?
Thanks

---

### Post by heir4c on 2013-12-01
When you make a backup than just do a backup of all your files on a external disk. You can do that from a live-session. So boot up with a live-cd/dvd or live-usb and safe your files.
Than do a fresh install of Ubuntu.

---

### Post by okkie on 2013-12-02
heir4c, ek sien jy praat Hollands, ek is n ou boerseun in RSA. Dankie vir jou hulp.
I have the original cd I installed 13.04 with.If I put it in the drive It offers me the standard options to install, reinstall or try Ubuntu. In try Ubuntu I can see my problem hard disk, but cannot get into it to save my files. Is the live cd you talk about something different ?

As I said the computer is working on the reinstall and is at the moment at the bottom of the install window busy installing with the heading "saving installed packages". IT IS JUST EXTREMELY SLOW

Groete

---

### Post by jdeca57 on 2013-12-02
> **okkie said:**
> 
I have the original cd I installed 13.04 with.If I put it in the drive It offers me the standard options to install, reinstall or try Ubuntu. In try Ubuntu I can see my problem hard disk, but cannot get into it to save my files. Is the live cd you talk about something different ?

As I said the computer is working on the reinstall and is at the moment at the bottom of the install window busy installing with the heading "saving installed packages". IT IS JUST EXTREMELY SLOW

Does that vg means you use LVM? Because mounting an LVM is different, look at:
[http://www.dannytsang.co.uk/index.php/mounting-lvm-using-ubuntu-live-cd/](http://www.dannytsang.co.uk/index.php/mounting-lvm-using-ubuntu-live-cd/)
That's someone who had the same problem as you seem to have.
If you can mount it you can copy to an external drive. And what that 'saving installed packages' may mean is not clear to me, but I doubt it are your data.

---

### Post by okkie on 2013-12-03
Thanks. I have 13.04 installed and that is what crashed and will not boot.You say I must use a 12.04 disk. Is this correct?

---

### Post by kgandhiok on 2013-12-03
You can try installing 12.04 since it's the next LTS after 10.04.

---

### Post by jdeca57 on 2013-12-03
> **okkie said:**
> Thanks. I have 13.04 installed and that is what crashed and will not boot.You say I must use a 12.04 disk. Is this correct?
What happened to 10.04?
In each case, booting with 12.04 won't help you more than booting with 13.04 if you want to rescue data.
If you have a backup, then by all means install what you want.
Two further remarks:
1. Do create a separate partition for /home
2. Avoid LVM (I know I'm stepping on thin ice here) simply because it adds a layer of complexity for a benefit you're most likely never to use.

---

### Post by jimmyh1972 on 2013-12-03
Just boot from live cd of ubutnu, save your important stuff to external HD and reinstall a fresh copy.
you can use ubuntu 12.04 as a rescue disk &than install it...

---

### Post by okkie on 2013-12-03
Sorry for all the inconvenience. 7 years 13 install/reinstalls and worst of all everytime losing vital documents etc. And  still not a reliable simple working system. Updates caused most of my problems and of course a lack of knowledge and if you are way into your sixties not easy to catch up.
I reinstalled 13.04 and this time arround will not do updates and will store all my documents etc. On an external drive  to avoid 'system will not boot after update'

what is badly needed is after a system will not boot, to insert the disk, go to try ubuntu and unlike now, be able to access the hard disk which is denied, so you can recover your data. Maybe there is a way i and thousands more are not aware of.

Are regular updates run on a test computer  before we get it ?

Where do the system crashes come from?

Maybe this thread can still serve some purpose !

---

