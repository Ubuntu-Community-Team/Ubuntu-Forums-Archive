---
title: "windows 7 and ubuntu sa netbook"
date: 2010-06-05
forum: Philippine Team
---

### Post by astigfighter on 2010-06-05
meron akong acer aspire one na netbook... ang os niya ay windows 7 starter edition.. gusto ko po sana  idual boot itong netbook ko with ubuntu 10.04 desktop edition.. maaari po ba mangyari un? maraming salamat ..

---

### Post by aljoriz on 2010-06-05
POSSIBLE!  

Download the Ubuntu lucid iso.. burn to CD at the lowest possible burning speed.
Re-boot with the CD as the boot device, tapos try the live, then click installer sa live when you get to the portion of partition during the install by default ubuntu will be installed side by side with your existing OS partition.

WELCOME to the FOSS (Free Open Source System) world!

---

### Post by antoniomiguel on 2010-06-05
Apparently Aljoriz missed out that Acer Aspire One is a netbook and it doesn't come with a cd tray. But if the box comes with an external cd drive (i suddenly remember my officemate got one when she bought her AspireOne), then it should be ok.

You might want to manually install (instead of the default side-by-side), this way you can have the control over the capacity allocations on your hd.

edit: if you dont have cd drive, then making a live-cd over a USB drive is the way.

---

### Post by killer_d76 on 2010-06-05
this link might help!... [clicky here for the tutorial]("http://www.hackourlives.com/dual-boot-windows-7-and-ubuntu-10-04-lucid-lynx/")... and you might want to check this first since netbooks don't have cd/dvd rom tray [Install Ubuntu on a USB using Windows]("http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/")

hope this helps!

;)

---

### Post by antoniomiguel on 2010-06-05
> **killer_d76 said:**
> this link might help!... [clicky here for the tutorial]("http://www.hackourlives.com/dual-boot-windows-7-and-ubuntu-10-04-lucid-lynx/")... 

This is a nice step-by-step procedure.


Just wanted to add a little tweak. On the "Prepare partitions" part, i suggest you first add an "Extended" partition and later on create the needed partitions in it.

Under the Extended Partition:
[INDENT]"/"  -(root partition - ext4), this is where all your ubuntu packages and apps will be installed[/INDENT]
[INDENT]"/home"  - (home partition - ext4), your data drive[/INDENT]
[INDENT]"/swap"  - (swap partition)[/INDENT]

---

### Post by zilu54 on 2010-06-05
sa pag kakaalam ku, gagamit siya ng UNE/UNR instead of UDE (Desktop Edition) may wubi install rin ba sa netbook edition para mag dual boot sa W7?

---

### Post by killer_d76 on 2010-06-05
it's a matter of choice... if he prefers Netbook Remix or the usual Desktop look and feel.. though both works perfectly on Acer Aspire One!

---

### Post by antoniomiguel on 2010-06-05
I'll go for UNR, this is what it is made for. On top of the default layout, there are other format choices on the log-in menu (UNR 2D, 3D) for a UDE feel.

---

### Post by astigfighter on 2010-06-06
meron ako na external cdrom kaso ndi ko pa nakukuha.. pag dumating un uumpisahan ko na ung pagdual boot ng win7 and ubuntu.. ang gusto ko din po malaman ay kung katulad ba ng pagdual boot sa desktop ang pagdual boot din dito sa netbook? like pag nasa loob ng windows pagnilagay ang cd and nagautorun.. makikita ung install inside windows.. gnun din ba ang paraan mga sir?? mejo naguguluhan po kasi ako .

---

### Post by antoniomiguel on 2010-06-06
@astigfighter
Pakibasa na lang yung quick guide ni killer_d76, malinaw na doon yung procedure.

> **astigfighter said:**
> ..like pag nasa loob ng windows pagnilagay ang cd and nagautorun.. makikita ung install inside windows.. gnun din ba ang paraan mga sir??
Medyo iba. Yung live-cd kasi is hindi na papasok pa sa Windows. Bootable na sya, then straight na sa pagpa-partition ng harddrive, then installation na kagad.

Meron sya i-install na dual-boot app (GRUB) so everytime na i-start mo netbook mo (after ng successful installation above) e pipili ka ng OS na ira-run.

---

### Post by killer_d76 on 2010-06-06
@astigfighter

I understand where you are coming from bro.. kasi ganyan din halos ang mga tanong ko nun the First time i was planning to dualboot our Windows XP lappie with Ubuntu (now we have Ubuntu and Mac.. no more windows).. pero no need to worry bro (lakasan lang ng loob yan hehehe).. ubuntu is a **super newbie user friendly linux OS** (my own opinion) and guides are provided all-through-the-install-process... since you'll be using a USB external cd rom drive.. ganito gawin mo bro.. make sure you have the power supply plugged-in on your netbook (well ubuntu will be asking you to plug it to a power supply just in case you forgot it as well hehehe).. plug the USB cd rom drive on your netbook.. press start button.. then press F12 and choose to boot from your USB cd rom drive (no need to change your boot set-up on bios).. make sure you have your Ubuntu CD on your USB CD Rom drive.. wait for a few seconds then it will give options on your screen.. make sure to choose **"Try Ubuntu without changing your set-up"** or something like that.. then follow the tutorial link I have posted..

If you have 1GB USB stick I would suggest for you to use that to install Ubuntu there rather than burn the .iso on CD... mas mabilis kasi ang response and installation process using USB stick installer.

---

### Post by Ravskie on 2010-06-07
> **killer_d76 said:**
> @astigfighter

I understand where you are coming from bro.. kasi ganyan din halos ang mga tanong ko nun the First time i was planning to dualboot our Windows XP lappie with Ubuntu (now we have Ubuntu and Mac.. no more windows).. pero no need to worry bro (lakasan lang ng loob yan hehehe).. ubuntu is a **super newbie user friendly linux OS** (my own opinion) and guides are provided all-through-the-install-process... since you'll be using a USB external cd rom drive.. ganito gawin mo bro.. make sure you have the power supply plugged-in on your netbook (well ubuntu will be asking you to plug it to a power supply just in case you forgot it as well hehehe).. plug the USB cd rom drive on your netbook.. press start button.. then press F12 and choose to boot from your USB cd rom drive (no need to change your boot set-up on bios).. make sure you have your Ubuntu CD on your USB CD Rom drive.. wait for a few seconds then it will give options on your screen.. make sure to choose **"Try Ubuntu without changing your set-up"** or something like that.. then follow the tutorial link I have posted..

If you have 1GB USB stick I would suggest for you to use that to install Ubuntu there rather than burn the .iso on CD... mas mabilis kasi ang response and installation process using USB stick installer.


WELL SAID..... +1 sa yo Sir Killer_D76 ..... easy lang installation for dual boot one suggestion use UNE/UNR much better ( in my opinion ) ..... I'm also using eeepc with dual boot Win7 and UBUNTU of course and it is awesome nag karoon lang ng konting problem nung una sa freezing screen but with new kernel seems ok .....

---

