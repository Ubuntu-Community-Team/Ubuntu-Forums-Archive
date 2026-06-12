---
title: "black screen after log in"
date: 2018-10-14
forum: New to Ubuntu
---

### Post by lilkod on 2018-10-14
Hello guys, i installed the latest version of ubuntu on my laptop yesterday and everything went perfectly fine. It opened normally and installed latest updates. I also tried opening mozilla just to see that everything is smooth because i saw little lags when clicking around. Today i tried to turn on my laptop.while i was navigating in mozilla,i saw an error message pop-up saying something i cant remember,i clicked to send error data and then restart. When my laptop was restarting,it took like 10-15 minutes and my screen was like a cmd spamming lines i couldnt read because they were very fast. After it restarted and went to the log in screen,i entered my password and all i got was the "loading" screen you get before you see the desktop. My laptop sounded like it was on 100% load and so i waited for like 30 minutes to see if anything happens but nothing changed.i forced shut down and tried some fixes i saw on the internet through recovery mode(tried apt-get update and installing nvidia drivers but both failed).i even tried to reinstall ubuntu and erase all disk but after i pressed continue on the normal-minimal install screen my laptop froze and was again running at 100% load.Can anybody help?

---

### Post by Bashing-om on 2018-10-14
lilkod; Hello - Welcome to the forum :)

OH Boy --- where to start with this ?

What exact release did you install ?
The latest release is version 18.04, while there is the beta 18.10.

We also need to know what the hardware is:
Who is the manufacturer ? 
what graphics do you have (hybrid ?) ?
What processor (CPU) ?

What results when you boot the installer to "try ubuntu" mode ?
At this point we can not discount hardware problems.

[INDENT][INDENT]we do as we can
[/INDENT][/INDENT]

---

### Post by lilkod on 2018-10-14
Thank you for replying.
Sorry i didnt know that i had to mention this stuff. I am running on a hp pavilion 15-au101nv. It has i5-7200U at 2.5 GHz with 6GB of RAM and a Nvidia GeForce 940MX. Unfortunately i didn't try the "try ubuntu" mode.Also, i installed the 18.04.1 LTS version which i downloaded from the original site. Though the file that i downloaded is named ubuntu-18.04.1-desktop-amd64. Does that mean that i downloaded and installed an ubuntu version made for amd CPU's?

---

### Post by Bashing-om on 2018-10-14
lilkod; Smile =

All to the good .
> 
Though the file that i downloaded is named ubuntu-18.04.1-desktop-amd64. Does that mean that i downloaded and installed an ubuntu version made for amd CPU's?

Naw, just that AMD owns the rights to the architecture - a "trade name" . You are good .
 
OK, nvidia graphics .
Try with the nomodeset boot parameter:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) <- How to set NOMODESET and other kernel boot options in grub2

If it is good here then we install the proprietary nvidia graphic's driver.
But be aware that nvidia does not play nice, to this time, with the Wayland desktop. Make sure you are booting the default Xorg . 

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by hackman86 on 2018-10-14
It really sounds like missing the proper nvidia drivers. Do you have dual boot or did you removed Windows?

---

### Post by lilkod on 2018-10-14
i tried the nomodeset method from [https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu/38782#38782](https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu/38782#38782) saying that i have to put nomodeset before quiet splash. I pressed Ctrl+X and my laptop has been doing this for the past 45 minutes.[https://scontent-sof1-1.xx.fbcdn.net/v/t1.15752-9/s2048x2048/44022928_1148046585344513_4460779378954993664_n.jpg?_nc_cat=100&oh=ae83ed77656df369a11156be3bae9448&oe=5C14953A](https://scontent-sof1-1.xx.fbcdn.net/v/t1.15752-9/s2048x2048/44022928_1148046585344513_4460779378954993664_n.jpg?_nc_cat=100&oh=ae83ed77656df369a11156be3bae9448&oe=5C14953A)

---

### Post by lilkod on 2018-10-14
> **hackman86 said:**
> It really sounds like missing the proper nvidia drivers. Do you have dual boot or did you removed Windows?
if so then why would it run in the first day and a little bit in the second?

---

### Post by Bashing-om on 2018-10-14
lilkod; Yukkie - 
1) bad .iso ?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

2) Bad burn to the install medium ?
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

3) Hardware issues ?
Who knows :( ... 1st make sure is not a software issue.

[INDENT][INDENT]bad things do happen
[/INDENT][/INDENT]

---

### Post by hackman86 on 2018-10-15
I don't know why, but I had the same issue. It was working after installation was complete and 2 days later the issues came across the corner....

---

### Post by lilkod on 2018-10-15
Thank you anyways guys but i have one more question,
as i said,whenever i try to reformat my laptop and erase all disk data it goes at full load one step before i get to that point and i can't do anything about it. 
What should i do? Windows where perfectly working before i installed linux. Should i get my laptop to a technician? 
On the other hand, what else will he do? Do you guys have any suggestions?

---

### Post by Bashing-om on 2018-10-15
lilkod; Well -

We just do not know yet ..not enough information to make a determination.

What results when you boot a verified liveUSB(DVD) ?
We need to isolate to a software or hardware issue.

[INDENT]maybe this
[INDENT][INDENT][INDENT]could be that
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lilkod on 2018-10-16
Hello again,
I tried to boot from live usb. It worked but everything was lagging.
I tried to open mozzila and it took like 10 seconds to load.
After 20-30 seconds i heard my laptop going again at 100% load and everything started to lag more.
I clicked on the drop-down menu on the top right of the screen to turn off the computer and pressed the shut down button but it wouldn't respond.
So i had to force shut down with the button.

---

### Post by lilkod on 2018-10-16
UPDATE:
I tried making a windows bootable usb and try to delete all disk data during the installation procedure.
This is what came up [https://scontent.fath6-1.fna.fbcdn.net/v/t1.15752-9/44109275_575510056200167_2173908485828247552_n.jpg?_nc_cat=103&oh=9fac777a7cb6afce1927c7d0c4ce0e43&oe=5C4D67DC](https://scontent.fath6-1.fna.fbcdn.net/v/t1.15752-9/44109275_575510056200167_2173908485828247552_n.jpg?_nc_cat=103&oh=9fac777a7cb6afce1927c7d0c4ce0e43&oe=5C4D67DC)
I don't know how this happened but i delete both drives and I am downloading again ubuntu 18.04.1 from the original site to try re-installing.

---

### Post by lilkod on 2018-10-16
UPDATE v2:
I tried usb live. The system run perfectly but when i tried to shut down i got the same result as before.
[https://scontent.fath6-1.fna.fbcdn.net/v/t1.15752-9/s2048x2048/44022928_1148046585344513_4460779378954993664_n.jpg?_nc_cat=100&oh=03f2239e2e157e1da40eecd1d82013a1&oe=5C3C223A](https://scontent.fath6-1.fna.fbcdn.net/v/t1.15752-9/s2048x2048/44022928_1148046585344513_4460779378954993664_n.jpg?_nc_cat=100&oh=03f2239e2e157e1da40eecd1d82013a1&oe=5C3C223A)
I had to force shut down.Then i tried installing ubuntu and this has been happening for the past 15 minutes.
[https://scontent.fath6-1.fna.fbcdn.net/v/t1.15752-9/44298338_314385656007344_2354589659662647296_n.jpg?_nc_cat=111&oh=5dd45b38a9b2152aa11ef5cb9941dca9&oe=5C581DE9](https://scontent.fath6-1.fna.fbcdn.net/v/t1.15752-9/44298338_314385656007344_2354589659662647296_n.jpg?_nc_cat=111&oh=5dd45b38a9b2152aa11ef5cb9941dca9&oe=5C581DE9)
As seen in the image,I pressed continue and my laptop is on full load again and just stays there

---

### Post by Bashing-om on 2018-10-16
lilkod; Ouch !

Do we have a hard drive failing ?

At this point I would see what the health of the drive is.
Boot the liveUSB to "try ubuntu" mode.
Install the tool:
```

sudo apt install smartmontools

```
Identify the hard drive name (sdb ??): where it is likely that sda is the USB device.
```

sudo fdisk -lu

```
Now see what the drive reports:
```

sudo smartctl -a /dev/sdb

```

stuck on hardware fault - need to know we are past that.
else we go looking for a suitable boot parameter.


[INDENT][INDENT]fingers crossed
[/INDENT][/INDENT]

---

### Post by lilkod on 2018-10-16
At this point I have also tried installing Elementary OS but my pc still freezes at the same exact point. 
I have already run an extensive hard drive check and it passed....

---

### Post by Bashing-om on 2018-10-16
lilkod; Ho Kay -

> 
I have already run an extensive hard drive check and it passed....


Then next up is to verify the install media's integrity:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

[INDENT][INDENT]there is a process
[/INDENT][/INDENT]

---

### Post by lilkod on 2018-10-17
Hello once again,
I tried your methods and all worked good.
I burn the iso using rufus and compared the checksum and it was ok.I even tried using another usb drive but it didn't seem to be the problem.
I also tried another method.I installed the OS without connecting to the internet and although it took like an hour to install it actually did.
Though when i connected my laptop to the internet in order to install updates I had the same problem(laptop goes on full load and everything freezes plus when i try to shut down it starts spamming white lines on my screen).

---

### Post by lilkod on 2018-10-17
I would also like to add that whenever I try to install and make a partition i get an error message saying that the partition couldn't be made.
I am starting to think that it's a disk problem even though it the test.

---

### Post by Bashing-om on 2018-10-17
lilkod; Hummmm ..

Maybe best at this point to look at how that hard drive is split up.
Post back:
```

sudo fdisk -lu
sudo parted -l

```
take a look at the numbers-

---

### Post by ariamedtour on 2018-12-10
thanks for sharing this information

---

