---
title: "Running Ubuntu on Vbox"
date: 2010-06-03
forum: Philippine Team
---

### Post by kapitanluffy on 2010-06-03
I am new in ubuntu..and im still trying to figure things out so i installed ubuntu on a vbox. (sun vbox to be exact) and then after doing that i started nibbling on it..i researched on how to make my user to be a default root. I found something here.

[http://www.linux.com/learn/tutorials/8254-ten-tips-for-new-ubuntu-users](http://www.linux.com/learn/tutorials/8254-ten-tips-for-new-ubuntu-users)

so i added:
**kapitanluffy ALL=(ALL) ALL **on the **/etc/sudoers**

after that i installed the vbox guest additions, i restarted the vbox
after restarting..everything looks fine but when after logging in. the vbox's monitor doesn't seem to refresh. it displays only the background. when i switched to another window e.g. firefox (not inside vbox) and then goes back to the vbox. the firefox *window seems to be stucked xD

:confused:

[[IMG]http://img63.imageshack.us/img63/9290/vboxw.th.png[/IMG]]("http://img63.imageshack.us/my.php?image=vboxw.png")
[URL="http://img63.imageshack.us/my.php?image=vboxw.png"]
[/URL]

---

### Post by dodimar on 2010-06-03
The first user account that you create (the one during installation) on Ubuntu is automatically a sudoer, meaning you can do administrative privileges by using the sudo command on the command line or entering your account password when it ask for it.

With regards to vbox window not showing up, what is the specification of the computer you are using?

---

### Post by kapitanluffy on 2010-06-03
> **dodimar said:**
> The first user account that you create (the one during installation) on Ubuntu is automatically a sudoer, meaning you can do administrative privileges by using the sudo command on the command line or entering your account password when it ask for it.

With regards to vbox window not showing up, what is the specification of the computer you are using?

128mb vid card..that may cause the problem..or maybe the vbox's guest additions 
thanks :)

oh i have another question. i managed to put ubuntu 10 on a 4gb usb (too small i know) i wanted to remove the default user 'ubuntu' how could i do that? :P

---

### Post by jaceleon on 2010-06-07
You did a LiveUSB version of Ubuntu. That is a non-permanent system. Thus the user UBUNTU cannot be removed. Gawa ka permanent install USB ng Ubuntu.

Bago ka mag install ng Ubuntu sa USB nang permanente, eto ang tanong?

1. Ready ka bang umikli lifespan ng USB mo? Unless External Hard Disk yan, sagutin mo to ng yes. Pag no, wag mo na ituloy.

2. Ano brand ng USB mo? Hindi pwede CDR King at hindi tatagal yan sa madalas na read/write ng system. Advisable ang Transcend at Kingston. Pangit and Ridata, never boots the permanent Ubuntu on my experience. Any other brand, well bahala ka na....

3. Ilang GB USB mo? maliit ang 4G sa Permanent install ng USB. Ako nga e, pinartition ko USB kong 16GB into 10/6, 10GB yung Ubuntu partition at 6GB ang Storage na NTFS. I suggest an 8GB USB or higher. KUng 4Gb pa rin gamit mo, well sa install pa lang ng 15-20 apps e puno ka na, wala ka pang swap space niyan. 

So installing it permanently on a USB is actually rather easy.

1. Disconnect temporarily ANY Hard disk and USB except sa target mo on the computer. Leave only the USB plugged the whole time of installation. Ibabalik mo rin yan after installation. Format your USB using HP Format utility para maging NTFS yang USB target mo. Then resize it on Gparted.

2. Use a CD to install Ubuntu on USB. I suggest IDE CD/DVD ROM. Don't even try using another liveUSB for installing on Ubuntu since malaking chance na maging SDA ang LiveUSB mo at SDB ang USB target. Hindi mag boot ang SDB niyan at madugo pa yan pag pinilit mong i boot ang SDB. The target USB **MUST** appear as SDA. (to know kung SDA or SDB ang USB mo, use GParted to confirm)

3. Install it normally na parang hard disk lang yan.

Ngayon to boot that on another PC, just plug it and change the boot to a USB. Select your Target USB as the boot device.

Hayan ah, tanong ka na lang pag ok ka na diyan or pag me problema ka dyan.

Hint: I always call that Ubuntu as USBuntu :P.

---

